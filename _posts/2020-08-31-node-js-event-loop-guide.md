---
layout: single
title:  "Vòng lặp sự kiện Node.js: Hướng dẫn dành cho nhà phát triển về khái niệm & mã"
desc: "Vòng lặp sự kiện Node.js: Hướng dẫn dành cho nhà phát triển về khái niệm & mã"
keywords: "loop, javascript"
categories: [javascript]
tag: [javascript]
---

**Không đồng bộ trong bất kỳ ngôn ngữ lập trình nào là khó. Các khái niệm như đồng thời, song song và deadlock khiến ngay cả những kỹ sư dày dạn kinh nghiệm nhất cũng phải rùng mình. Mã thực thi không đồng bộ là không thể đoán trước và khó theo dõi khi có lỗi. Vấn đề là không thể tránh khỏi vì máy tính hiện đại có nhiều lõi. Có một giới hạn nhiệt trong mỗi lõi đơn của CPU và không có gì nhanh hơn. Điều này gây áp lực lên nhà phát triển trong việc viết mã hiệu quả tận dụng lợi thế của phần cứng.**

JavaScript là một luồng, nhưng điều này có hạn chế Node sử dụng kiến ​​trúc hiện đại không? Một trong những thách thức lớn nhất là xử lý nhiều luồng vì tính phức tạp vốn có của nó. Việc tạo ra các luồng mới và quản lý chuyển đổi ngữ cảnh ở giữa rất tốn kém. Cả hệ điều hành và lập trình viên phải làm rất nhiều việc để đưa ra một giải pháp có nhiều trường hợp phức tạp. Trong phần này, tôi sẽ chỉ cho bạn cách Node đối phó với vũng lầy này thông qua vòng lặp sự kiện. Tôi sẽ khám phá mọi phần của vòng lặp sự kiện Node.js và chứng minh cách nó hoạt động. Một trong những tính năng “ứng dụng sát thủ” trong Node là vòng lặp này, vì nó đã giải quyết một vấn đề khó theo cách mới triệt để.

Vòng lặp sự kiện là gì?
-----------------------

Vòng lặp sự kiện là một vòng lặp đơn luồng, không chặn và đồng thời không đồng bộ. Đối với những người không có bằng khoa học máy tính, hãy tưởng tượng một yêu cầu web thực hiện tra cứu cơ sở dữ liệu. Một chủ đề chỉ có thể làm một việc tại một thời điểm. Thay vì đợi cơ sở dữ liệu phản hồi, nó tiếp tục nhận các tác vụ khác trong hàng đợi. Trong vòng lặp sự kiện, vòng lặp chính giải nén ngăn xếp cuộc gọi và không đợi các cuộc gọi lại. Vì vòng lặp không chặn nên có thể miễn phí làm việc trên nhiều yêu cầu web cùng một lúc. Nhiều yêu cầu có thể được xếp hàng đợi cùng một lúc, điều này làm cho nó đồng thời. Vòng lặp không đợi mọi thứ từ một yêu cầu hoàn thành, mà nhận các lệnh gọi lại khi chúng đến mà không bị chặn.

Bản thân vòng lặp là bán vô hạn, có nghĩa là nếu ngăn xếp cuộc gọi hoặc hàng đợi gọi lại trống, nó có thể thoát khỏi vòng lặp. Hãy nghĩ về ngăn xếp cuộc gọi như một mã đồng bộ để giải nén, giống như `console.log`, trước khi vòng lặp thăm dò để tìm thêm công việc. Node sử dụng libuv dưới vỏ bọc để thăm dò hệ điều hành về các cuộc gọi lại từ các kết nối đến.

Bạn có thể tự hỏi, tại sao vòng lặp sự kiện lại thực thi trong một luồng đơn? Các luồng có bộ nhớ tương đối nặng cho dữ liệu mà nó cần cho mỗi kết nối. Luồng là tài nguyên hệ điều hành xoay tròn và điều này không mở rộng đến hàng nghìn kết nối đang hoạt động.

Nhiều chủ đề nói chung cũng làm phức tạp câu chuyện. Nếu một lệnh gọi lại quay trở lại với dữ liệu, nó phải điều phối ngữ cảnh quay trở lại chuỗi thực thi. Việc chuyển đổi ngữ cảnh giữa các luồng rất chậm, vì nó phải đồng bộ hóa trạng thái hiện tại như ngăn xếp cuộc gọi hoặc các biến cục bộ. Vòng lặp sự kiện sẽ xử lý các lỗi khi nhiều luồng chia sẻ tài nguyên vì nó là một luồng. Vòng lặp một luồng cắt các trường hợp cạnh an toàn luồng và có thể chuyển đổi ngữ cảnh nhanh hơn nhiều. Đây là thiên tài thực sự đằng sau vòng lặp. Nó sử dụng hiệu quả các kết nối và luồng trong khi vẫn có thể mở rộng.

Đủ lý thuyết; thời gian để xem điều này trông như thế nào trong mã. Vui lòng theo dõi trong REPL hoặc [tải xuống mã nguồn](https://github.com/beautifulcoder/event-loop-playground) .

Vòng lặp bán vô hạn
-------------------

Câu hỏi lớn nhất mà vòng lặp sự kiện phải trả lời là liệu vòng lặp còn tồn tại hay không. Nếu vậy, nó tính toán thời gian chờ đợi trong hàng đợi gọi lại. Tại mỗi lần lặp, vòng lặp sẽ giải phóng ngăn xếp cuộc gọi, sau đó thăm dò ý kiến.

Dưới đây là một ví dụ chặn vòng lặp chính:

    setTimeout(
      () => console.log('Hi from the callback queue'),
      5000); // Keep the loop alive for this long
    
    const stopTime = Date.now() + 2000;
    while (Date.now() < stopTime) {} // Block the main loop
    

Nếu bạn chạy mã này, hãy lưu ý rằng vòng lặp bị chặn trong hai giây. Nhưng vòng lặp vẫn tồn tại cho đến khi lệnh gọi lại thực thi sau năm giây. Sau khi vòng lặp chính bỏ chặn, cơ chế bỏ phiếu sẽ tính toán thời gian nó đợi khi gọi lại. Vòng lặp này sẽ chết khi ngăn xếp cuộc gọi mở ra và không còn lệnh gọi lại nào nữa.

Hàng đợi Gọi lại
----------------

Bây giờ, điều gì sẽ xảy ra khi tôi chặn vòng lặp chính và sau đó lên lịch gọi lại? Khi vòng lặp bị chặn, nó sẽ không đặt thêm lệnh gọi lại vào hàng đợi:

    const stopTime = Date.now() + 2000;
    while (Date.now() < stopTime) {} // Block the main loop
    
    // This takes 7 secs to execute
    setTimeout(() => console.log('Ran callback A'), 5000);
    

Lần này vòng lặp vẫn tồn tại trong bảy giây. Vòng lặp sự kiện là ngu ngốc trong sự đơn giản của nó. Nó không có cách nào để biết những gì có thể được xếp hàng trong tương lai. Trong một hệ thống thực, các cuộc gọi lại đến được xếp hàng đợi và thực thi vì vòng lặp chính được miễn phí để thăm dò ý kiến. Vòng lặp sự kiện trải qua một số giai đoạn _tuần tự_ khi nó được bỏ chặn. Vì vậy, để vượt qua cuộc phỏng vấn xin việc đó về vòng lặp, hãy tránh những biệt ngữ ưa thích như “bộ phát sự kiện” hoặc “mẫu lò phản ứng”. Đó là một vòng lặp đơn luồng khiêm tốn, đồng thời và không chặn.

Vòng lặp sự kiện với async / await
----------------------------------

Để tránh chặn vòng lặp chính, một ý tưởng là bọc I / O đồng bộ xung quanh async / await:

    const fs = require('fs');
    const readFileSync = async (path) => await fs.readFileSync(path);
    
    readFileSync('readme.md').then((data) => console.log(data));
    console.log('The event loop continues without blocking...');
    

Bất cứ thứ gì xuất hiện sau `await`hàng đợi gọi lại. Mã đọc giống như mã chặn đồng bộ, nhưng nó không chặn. Lưu ý async / làm cho chờ đợi `readFileSync` _thenable_ , trong đó có nó ra khỏi vòng lặp chính. Hãy coi bất cứ điều gì xảy ra sau đó `await`là không chặn thông qua một cuộc gọi lại.

if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_1'); }); }

Tiết lộ đầy đủ: đoạn mã trên chỉ dành cho mục đích trình diễn. Trong mã thực, tôi khuyên bạn nên sử dụng mã này, `fs.readFile`sẽ kích hoạt một cuộc gọi lại có thể được bao bọc bởi một lời hứa. Mục đích chung vẫn có hiệu lực, vì điều này sẽ loại bỏ việc chặn I / O khỏi vòng lặp chính.

Tiến xa hơn
-----------

Điều gì sẽ xảy ra nếu tôi đã nói với bạn rằng vòng lặp sự kiện có nhiều thứ hơn là ngăn xếp cuộc gọi và hàng đợi gọi lại? Điều gì sẽ xảy ra nếu vòng lặp sự kiện không chỉ là một vòng lặp mà là nhiều vòng lặp? Và điều gì sẽ xảy ra nếu nó có thể có nhiều chủ đề dưới bìa?

Bây giờ, tôi muốn đưa bạn đến sau mặt tiền và vào cuộc xung đột của nội bộ Node.

Các giai đoạn vòng lặp sự kiện
------------------------------

Đây là các giai đoạn của vòng lặp sự kiện:

![Các giai đoạn vòng lặp sự kiện](https://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2020/08/1598316584loop_iteration.png)

Nguồn hình ảnh: [tài liệu libuv](http://docs.libuv.org/en/v1.x/_images/loop_iteration.png)

1.  Dấu thời gian được cập nhật. Vòng lặp sự kiện lưu trữ thời gian hiện tại khi bắt đầu vòng lặp để tránh các cuộc gọi hệ thống liên quan đến thời gian thường xuyên. Các lệnh gọi hệ thống này là nội bộ của libuv.
    
2.  Vòng lặp còn sống không? Nếu vòng lặp có các chốt điều khiển đang hoạt động, yêu cầu đang hoạt động hoặc chốt điều khiển đóng, thì nó vẫn tồn tại. Như được hiển thị, các lệnh gọi lại đang chờ xử lý trong hàng đợi giữ cho vòng lặp tồn tại.
    
3.  Bộ hẹn giờ đến hạn thực thi. Đây là nơi `setTimeout`hoặc các lệnh `setInterval`gọi lại chạy. Vòng lặp kiểm tra bộ nhớ cache _ngay bây giờ_ để có các lệnh gọi lại đang hoạt động đã hết hạn thực thi.
    
4.  Các lệnh gọi lại đang chờ xử lý trong hàng đợi thực thi. Nếu lần lặp trước đó trì hoãn bất kỳ lệnh gọi lại nào, các lệnh gọi lại này sẽ chạy tại thời điểm này. Việc thăm dò ý kiến ​​thường chạy các lệnh gọi lại I / O ngay lập tức, nhưng vẫn có ngoại lệ. Bước này xử lý bất kỳ bộ phân vùng nào từ lần lặp trước.
    
5.  Các trình xử lý nhàn rỗi thực thi - chủ yếu là do đặt tên kém, bởi vì các trình xử lý này chạy ở mọi lần lặp và là nội bộ của libuv.
    
6.  Chuẩn bị các chốt để `setImmediate`thực hiện lệnh gọi lại trong vòng lặp. Các chốt điều khiển này chạy trước khối vòng lặp cho I / O và chuẩn bị hàng đợi cho kiểu gọi lại này.
    
7.  Tính toán thời gian chờ cuộc thăm dò. Vòng lặp phải biết nó chặn I / O trong bao lâu. Đây là cách nó tính toán thời gian chờ:
    
    if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_2'); }); }
    
    *   Nếu vòng lặp sắp thoát, thời gian chờ là 0.
    *   Nếu không có yêu cầu hoặc xử lý nào đang hoạt động, thời gian chờ là 0.
    *   Nếu có bất kỳ xử lý không hoạt động nào, thời gian chờ là 0.
    *   Nếu có bất kỳ xử lý nào đang chờ xử lý trong hàng đợi, thời gian chờ là 0.
    *   Nếu có bất kỳ chốt đóng nào, thời gian chờ là 0.
    *   Nếu không có điều nào ở trên, thời gian chờ được đặt thành bộ hẹn giờ gần nhất hoặc nếu không có bộ hẹn giờ nào hoạt động, thì _vô hạn_ .
8.  Vòng lặp chặn I / O với khoảng thời gian từ giai đoạn trước. Các lệnh gọi lại liên quan đến I / O trong hàng đợi thực thi tại thời điểm này.
    
9.  Kiểm tra thực thi lệnh gọi lại xử lý. Giai đoạn này là nơi `setImmediate`chạy, và nó là giai đoạn chuẩn bị tay cầm. Mọi lệnh `setImmediate`gọi lại được xếp hàng đợi giữa quá trình thực thi gọi lại I / O đều chạy ở đây.
    
10.  Thực hiện lệnh gọi lại đóng. Đây là những tay cầm hoạt động được xử lý từ các kết nối đã đóng.
    
11.  Lặp lại kết thúc.
    

Bạn có thể thắc mắc tại sao bỏ phiếu lại chặn I / O khi nó được cho là không chặn? Vòng lặp chỉ chặn khi không có lệnh gọi lại đang chờ xử lý nào trong hàng đợi và ngăn xếp cuộc gọi trống. `setTimeout`Ví dụ: trong Node, bộ hẹn giờ gần nhất có thể được đặt bằng . Nếu được đặt thành vô cùng, vòng lặp sẽ chờ các kết nối đến với nhiều công việc hơn. Đó là một vòng lặp bán vô hạn, bởi vì việc thăm dò giữ cho vòng lặp tồn tại khi không còn gì để làm và có một kết nối đang hoạt động.

Đây là phiên bản Unix của phép tính thời gian chờ này là tất cả vinh quang C của nó:

    int uv_backend_timeout(const uv_loop_t* loop) {
      if (loop->stop_flag != 0)
        return 0;
    
      if (!uv__has_active_handles(loop) && !uv__has_active_reqs(loop))
        return 0;
    
      if (!QUEUE_EMPTY(&loop->idle_handles))
        return 0;
    
      if (!QUEUE_EMPTY(&loop->pending_queue))
        return 0;
    
      if (loop->closing_handles)
        return 0;
    
      return uv__next_timeout(loop);
    }
    

Bạn có thể không quá quen thuộc với C, nhưng điều này đọc giống như tiếng Anh và thực hiện chính xác những gì trong giai đoạn bảy.

Trình diễn theo từng giai đoạn
------------------------------

Để hiển thị từng giai đoạn bằng JavaScript đơn giản:

    // 1. Loop begins, timestamps are updated
    const http = require('http');
    
    // 2. The loop remains alive if there's code in the call stack to unwind
    // 8. Poll for I/O and execute this callback from incoming connections
    const server = http.createServer((req, res) => {
      // Network I/O callback executes immediately after poll
      res.end();
    });
    
    // Keep the loop alive if there is an open connection
    // 7. If there's nothing left to do, calculate timeout
    server.listen(8000);
    
    const options = {
      // Avoid a DNS lookup to stay out of the thread pool
      hostname: '127.0.0.1',
      port: 8000
    };
    
    const sendHttpRequest = () => {
      // Network I/O callbacks run in phase 8
      // File I/O callbacks run in phase 4
      const req = http.request(options, () => {
        console.log('Response received from the server');
    
        // 9. Execute check handle callback
        setImmediate(() =>
          // 10. Close callback executes
           server.close(() =>
            // The End. SPOILER ALERT! The Loop dies at the end.
            console.log('Closing the server')));
      });
      req.end();
    };
    
    // 3. Timer runs in 8 secs, meanwhile the loop is staying alive
    // The timeout calculated before polling keeps it alive
    setTimeout(() => sendHttpRequest(), 8000);
    
    // 11. Iteration ends
    

Bởi vì lệnh gọi lại I / O của tệp chạy trong giai đoạn bốn và trước giai đoạn chín, dự kiến `setImmediate()`sẽ kích hoạt trước:

    fs.readFile('readme.md', () => {
      setTimeout(() => console.log('File I/O callback via setTimeout()'), 0);
      // This callback executes first
      setImmediate(() => console.log('File I/O callback via setImmediate()'));
    });
    

I / O mạng không có tra cứu DNS sẽ ít tốn kém hơn I / O tệp, vì nó thực thi trong vòng lặp sự kiện chính. Thay vào đó, tệp I / O được xếp hàng đợi thông qua nhóm luồng. Tra cứu DNS cũng sử dụng nhóm luồng, vì vậy điều này làm cho I / O mạng đắt như I / O tệp.

Nhóm chủ đề
-----------

Nội bộ nút có hai phần chính: công cụ JavaScript V8 và libuv. I / O tệp, tra cứu DNS và I / O mạng diễn ra thông qua libuv.

Đây là kiến ​​trúc tổng thể:

![Tổng quan về thiết kế hồ bơi chuỗi](https://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2020/08/1598316658architecture.png)

if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_3'); }); }

Nguồn hình ảnh: [tài liệu libuv](http://docs.libuv.org/en/v1.x/_images/architecture.png)

Đối với I / O mạng, vòng lặp sự kiện thăm dò bên trong luồng chính. Luồng này không an toàn cho luồng vì nó không chuyển đổi ngữ cảnh với một luồng khác. Tệp I / O và tra cứu DNS là dành riêng cho nền tảng, vì vậy cách tiếp cận là chạy chúng trong một nhóm luồng. Một ý tưởng là tự mình tra cứu DNS để tránh xa nhóm luồng, như được hiển thị trong đoạn mã trên. `localhost`Ví dụ, đưa vào một địa chỉ IP so với việc tra cứu ra khỏi nhóm. Nhóm luồng có sẵn một số luồng giới hạn, có thể được thiết lập thông qua `UV_THREADPOOL_SIZE`biến môi trường. Kích thước nhóm chủ đề mặc định là khoảng bốn.

V8 thực thi trong một vòng lặp riêng biệt, rút ​​ngăn xếp cuộc gọi, sau đó cấp lại quyền kiểm soát cho vòng lặp sự kiện. V8 có thể sử dụng nhiều luồng để thu gom rác bên ngoài vòng lặp của chính nó. Hãy nghĩ về V8 như một công cụ lấy JavaScript thô và chạy nó trên phần cứng.

Đối với các lập trình viên trung bình, JavaScript vẫn là một luồng vì không có sự an toàn cho luồng. Nội bộ V8 và libuv tạo ra các luồng riêng biệt của riêng họ để đáp ứng nhu cầu của riêng họ.

Nếu có vấn đề về thông lượng trong Node, hãy bắt đầu với vòng lặp sự kiện chính. Kiểm tra xem ứng dụng mất bao lâu để hoàn thành một lần lặp. Nó không được quá một trăm mili giây. Sau đó, kiểm tra tình trạng đói nhóm luồng và những gì có thể bị đuổi ra khỏi nhóm. Cũng có thể tăng kích thước của pool thông qua biến môi trường. Bước cuối cùng là đánh dấu microbenchmark mã JavaScript trong V8 thực thi đồng bộ.

Kết thúc
--------

Vòng lặp sự kiện tiếp tục lặp lại qua từng giai đoạn khi các lệnh gọi lại được xếp hàng đợi. Tuy nhiên, trong mỗi giai đoạn có một cách để xếp hàng một loại gọi lại khác.

### `process.nextTick()` vs `setImmediate()`

Vào cuối mỗi giai đoạn, vòng lặp thực hiện lệnh `process.nextTick()`gọi lại. Lưu ý rằng kiểu gọi lại này không phải là một phần của vòng lặp sự kiện vì nó chạy ở cuối mỗi giai đoạn. Các `setImmediate()`callback là một phần của vòng lặp sự kiện tổng thể, do đó, nó không phải là ngay lập tức như tên của nó. Vì `process.nextTick()`cần kiến ​​thức sâu sắc về vòng lặp sự kiện, tôi khuyên bạn nên sử dụng `setImmediate()`nói chung.

Có một số lý do tại sao bạn có thể cần `process.nextTick()`:

1.  Cho phép I / O mạng xử lý lỗi, dọn dẹp hoặc thử lại yêu cầu trước khi tiếp tục lặp lại.
    
2.  Có thể cần phải chạy một lệnh gọi lại sau khi ngăn xếp cuộc gọi được giải phóng nhưng trước khi vòng lặp tiếp tục.
    

Ví dụ, giả sử một trình phát sự kiện muốn kích hoạt một sự kiện trong khi vẫn ở trong phương thức khởi tạo của chính nó. Ngăn xếp cuộc gọi phải rút lại trước khi gọi sự kiện.

    const EventEmitter = require('events');
    
    class ImpatientEmitter extends EventEmitter {
      constructor() {
        super();
    
        // Fire this at the end of the phase with an unwound call stack
        process.nextTick(() => this.emit('event'));
      }
    }
    
    const emitter = new ImpatientEmitter();
    emitter.on('event', () => console.log('An impatient event occurred!'));
    

Cho phép ngăn xếp cuộc gọi để thư giãn có thể ngăn ngừa các lỗi như `RangeError: Maximum call stack size exceeded`. Một điểm cần lưu ý là đảm bảo `process.nextTick()`không chặn vòng lặp sự kiện. Việc chặn có thể gặp vấn đề với các cuộc gọi lại đệ quy trong cùng một pha.

Phần kết luận
-------------

Vòng lặp sự kiện là sự đơn giản trong sự tinh vi cuối cùng của nó. Nó gặp phải một vấn đề khó khăn như không đồng bộ, an toàn luồng và đồng thời. Nó loại bỏ những gì không hữu ích hoặc những gì nó không cần và tối đa hóa thông lượng theo cách hiệu quả nhất có thể. Do đó, các lập trình viên Node dành ít thời gian hơn để theo đuổi các lỗi không đồng bộ và nhiều thời gian hơn để cung cấp các tính năng mới.

<div style="text-align: right">Theo <a href="https://www.sitepoint.com/node-js-event-loop-guide/">sitepoint</a></div>