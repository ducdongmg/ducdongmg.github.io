---
layout: single
title:  "21 câu hỏi phỏng vấn Node.js kèm câu trả lời"
desc: "21 câu hỏi phỏng vấn Node.js kèm câu trả lời"
keywords: "Node.js"
categories: [Node.js]
tag: [Node.js]
---

**Chuẩn bị cho một cuộc phỏng vấn xin việc luôn là một nhiệm vụ khó khăn. Nhiều khả năng bạn không biết chính xác những gì mình sẽ được hỏi và dây thần kinh có thể dễ dàng chiếm lấy, khiến bạn thậm chí quên cả tên của chính mình. Tôi đã biên soạn 21 câu hỏi Node.js cho các cuộc phỏng vấn việc làm, từ những thứ rất đơn giản đến một số chủ đề nâng cao hơn về mặt kỹ thuật để giúp bạn trong quá trình này.**

Node.js không được sử dụng riêng trong back end. Chúng tôi cũng sử dụng nó để tạo các ứng dụng front-end và điều này đã trở thành một phần rất quan trọng của hệ sinh thái Phát triển Web. Điều này có nghĩa là nó rất hữu ích cho một nhà phát triển Node.js để làm quen với vai trò của công nghệ này trong các môi trường JavaScript khác nhau. Vì lý do này, tôi đã bao gồm một số câu hỏi và câu trả lời dọc theo những dòng đó.

### Guidelines
Tôi khuyên bạn nên cố gắng tự trả lời các câu hỏi trước khi đọc câu trả lời. Nếu bạn không nhận được tất cả, hãy thử lại vào ngày mai để xem bạn đã giữ lại được bao nhiêu.

Cũng có khả năng bạn đang ở đây để tìm kiếm các ví dụ câu hỏi phỏng vấn cho các ứng viên của mình. Tôi tin rằng những điều này phải đủ đa dạng như một điểm khởi đầu để giúp bạn đánh giá trình độ của họ.

Không chỉ trả lời đúng một câu hỏi, tôi nghĩ rằng đó là các chi tiết cho thấy mức độ hiểu biết của ai đó. Một câu trả lời hay có thể kích hoạt một cuộc trò chuyện có khả năng khiến trải nghiệm căng thẳng trở thành một cuộc trò chuyện bình thường với đồng nghiệp. Đó là một kết quả lý tưởng cho cả hai bên.

### Câu hỏi về Node.js
#### Node.js là gì?
Node.js là một môi trường thời gian chạy JavaScript dựa trên động cơ V8. Nó cho phép chúng tôi chạy JavaScript bên ngoài trình duyệt - thường là trong máy chủ web.

#### Node.js tốt cho điều gì?
Node.js rất tốt trong việc xử lý nhiều kết nối với độ phức tạp chu kỳ thấp, do bản chất đơn luồng của nó yêu cầu chúng ta giải phóng vòng lặp sự kiện càng sớm càng tốt. Điều này làm cho Node.js trở thành lựa chọn lý tưởng cho các dịch vụ nhỏ và các ứng dụng thời gian thực.

#### Npm là gì?
[npm](https://www.npmjs.com/) là viết tắt của Node.js Package Manager. Nó bao gồm một giao diện dòng lệnh mà chúng ta có thể sử dụng để truy cập vào sổ đăng ký trực tuyến của các gói công khai và riêng tư.

#### Làm cách nào để bạn tạo một ứng dụng Node.js từ đầu?
Chúng ta có thể bắt đầu bằng cách tạo một thư mục dự án. Sau đó, chúng tôi điều hướng đến thư mục đó trong dòng lệnh và chạy `npm init`. Cuối cùng, chúng tôi làm theo các bước để điền thông tin ứng dụng của chúng tôi.

#### “npm install” làm gì?
Nó cài đặt các phụ thuộc được tìm thấy trong file `package.json`.

#### Làm cách nào để bạn cài đặt một thư viện trong Node.js?
`npm install name-of-the-library` sẽ cài đặt thư viện của chúng tôi và bao gồm nó dưới dạng dependency. Nếu chúng ta thêm --save-devtham số, nó sẽ được bao gồm dưới dạng a devDependency.

#### Làm thế nào để bạn tạo một tập lệnh tùy chỉnh?
Chúng tôi cần phải đi vào `package.json` và thêm tập lệnh tùy chỉnh của chúng tôi trong trường `scripts`. Sau đó, chúng tôi có thể chạy tập lệnh của mình bằng cách đi tới thiết bị đầu cuối và chạy `npm run name-of-script`.

#### Có thể tạo ứng dụng front-end với Node.js không?
Trình duyệt không thể chạy ứng dụng Node.js, nhưng bạn có thể sử dụng thứ gì đó như webpack hoặc Parcel để đóng gói mã và biến nó thành thứ mà trình duyệt có thể chạy. Ngày nay, việc sử dụng môi trường Node.js để xây dựng các ứng dụng front-end là rất phổ biến. Một ví dụ điển hình về Node.js trong giao diện người dùng là khung công tác [Electron](https://www.electronjs.org/), sử dụng cả Node.js và chromium để xây dựng các ứng dụng “gốc” như [VS Code](https://code.visualstudio.com/) chẳng hạn .

#### Bạn có thể đề cập đến ba framework Node.js phổ biến không?
[Express.js](https://expressjs.com/) có lẽ là framework phổ biến nhất cho đến nay. [Koajs](https://koajs.com/) có lẽ là một trong những ứng dụng nhanh nhất và [Sails.js](https://sailsjs.com/) hoạt động hiệu quả cho các ứng dụng giao tiếp song phương thời gian thực nếu sử dụng socket.io.

#### Express.js tốt cho điều gì?
Express.js giúp bạn dễ dàng thiết lập các tuyến đường cho ứng dụng web của chúng tôi, điều này khiến nó trở thành một lựa chọn hiển nhiên để tạo các [REST API](https://www.sitepoint.com/developers-rest-api/) . Nó khá linh hoạt và dễ sử dụng, và kiến ​​trúc phần mềm trung gian của nó giúp duy trì một hệ thống đơn giản và có thể mở rộng.

#### Crypto là gì?
Crypto là một thư viện nội bộ của Node.js cung cấp chức năng mật mã để làm những việc như mã hóa và giải mã mật khẩu chẳng hạn.

#### Làm cách nào để chúng tôi xử lý phạm vi cục bộ và toàn cầu trong Node.js?
Không giống như JavaScript phía máy khách, trong Node.js các biến được khai báo `var` ở phạm vi cao nhất không phải là toàn cục; chúng là cục bộ của module mà chúng đang ở trong. Trên trình duyệt, chúng tôi có quyền truy cập vào đối tượng `window` nơi các biến toàn cục của chúng tôi cư trú và Node.js có một đối tượng được gọi là `global`.

#### Node.js có quyền truy cập vào hệ thống tệp không?
Đúng. Chúng ta có thể sử dụng mô-đun [fs](https://nodejs.org/api/fs.html) để đọc, ghi, sao chép và xóa các tệp và thư mục.


#### non-blocking có nghĩa là gì?
Nó có nghĩa là một đoạn mã, chẳng hạn như một hàm không đồng bộ, được lên lịch để chạy trong lần lặp tiếp theo của vòng lặp sự kiện, do đó, bỏ chặn phần còn lại của mã và cho phép nó tiếp tục chạy.

#### Vòng lặp sự kiện là gì và nó hoạt động như thế nào?

Vòng lặp sự kiện là thứ mang lại cho Node.js bản chất không đồng bộ của nó. Nó lập lịch trình thực hiện một tập hợp năm giai đoạn trong một vòng lặp. Giai đoạn đầu tiên chạy lệnh gọi lại [setTimeout](https://nodejs.org/api/timers.html#timers_settimeout_callback_delay_args) và [setInterval đã](https://nodejs.org/api/timers.html#timers_setinterval_callback_delay_args) lên lịch . Cái thứ hai chạy các lệnh gọi lại IO được lập lịch để chạy trên lần lặp hiện tại. Người thứ ba thăm dò các sự kiện sẽ được thực hiện trong lần lặp tiếp theo. Cái thứ tư chạy [lệnh](https://nodejs.org/api/timers.html#timers_setimmediate_callback_args) gọi lại [setIm Instant ()](https://nodejs.org/api/timers.html#timers_setimmediate_callback_args) . Cuối cùng, cái thứ năm chạy tất cả các lệnh gọi lại "đóng".

#### Các chức năng không đồng bộ có chạy song song không?

Không. Một hàm không đồng bộ sẽ thực thi trong lần lặp vòng lặp sự kiện tiếp theo trong khi một quá trình Song song chạy trong tiến trình hoặc luồng của chính nó.

#### Node.js có đa luồng không?

Quy trình Node.js chạy trong một luồng duy nhất, nhưng chúng ta có thể sử dụng `child_process`mô-đun để chạy nhiều quy trình song song hoặc `Workers`chạy nhiều luồng.

#### Mô-đun quy trình con là gì?

Các [child\_process](https://nodejs.org/api/child_process.html) mô-đun cho phép chúng ta đẻ trứng và quá trình ngã ba đứa trẻ. Đây là các quy trình độc lập chạy trong CPU của chính chúng và cho phép chúng ta truy cập vào các lệnh hệ thống.

#### Sự khác biệt giữa web worker và worker thread là gì?

[Web](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API) [worker](https://nodejs.org/api/worker_threads.html) được triển khai trong trình duyệt và các [luồng worker](https://nodejs.org/api/worker_threads.html) được triển khai trong Node.js. Cả hai đều giải quyết cùng một vấn đề, đó là cung cấp xử lý song song. Trên thực tế, API luồng công nhân dựa trên việc triển khai nhân viên web.

#### Lợi ích của việc sử dụng một chuỗi worker so với một process con là gì?

Trong khi một tiến trình con chạy tiến trình riêng của nó với không gian bộ nhớ riêng của nó, một luồng công nhân là một tiểu trình trong một quy trình có thể chia sẻ bộ nhớ với luồng chính. Điều này giúp tránh việc tuần tự hóa dữ liệu qua lại tốn kém.

#### Bạn sẽ sử dụng gì để mở kết nối hai chiều, thời gian thực với ứng dụng khách qua HTTP?

Chúng tôi có thể sử dụng WebSockets hoặc bỏ phiếu dài. Có những thư viện như soket.io và SignalR giúp đơn giản hóa việc này cho chúng tôi. Họ thậm chí còn cung cấp cho những khách hàng không phải bỏ phiếu lâu nếu WebSockets không khả dụng trong trình duyệt.

Phần kết luận
-------------

Chúng ta đã đi đến cuối con đường. Tôi hy vọng bạn thấy những câu hỏi này hữu ích. Bạn có thể làm cho chúng ổn chứ? Nếu bạn không thể, đừng lo lắng. Trừ khi bạn đang nhắm đến một vị trí cấp cao, nếu không, bạn không nên biết tất cả chúng. Chỉ cần đảm bảo rằng bạn nắm được các nguyên tắc cơ bản và bất cứ khi nào bạn tìm thấy lỗ hổng kiến ​​thức, hãy nỗ lực để vượt qua ranh giới của bạn. Tôi đảm bảo với bạn rằng nó sẽ không bị chú ý.

Tôi chúc bạn gặp nhiều may mắn với cuộc phỏng vấn của mình. Giữ bình tĩnh, tin tưởng những gì bạn biết và tử tế - điều sau có lẽ là quan trọng nhất. Hầu hết mọi người thà lấp đầy những lỗ hổng trong kiến ​​thức của một người tốt bụng, khiêm tốn hơn là ở trong văn phòng mỗi ngày với một cá nhân kiêu ngạo, ích kỷ, khó làm việc cùng mặc dù họ là một thiên tài.

Nếu bạn là người phỏng vấn, hãy nhớ rằng dây thần kinh có thể cản trở ai đó thể hiện họ giỏi như thế nào. Hãy làm cho họ cảm thấy thoải mái nhất có thể và cho họ biết bạn đứng về phía họ và bạn muốn họ làm điều này!

Đó là tất cả mọi người. Chúng tôi sẽ trở lại với một phần trong tương lai bao gồm các thử thách mã phỏng vấn Node.js phổ biến và các kỹ năng và mẫu tinh thần bạn sẽ cần để vượt qua chúng. Hẹn gặp lại các bạn trong bài tiếp theo

<div style="text-align: right">Theo <a href="https://www.sitepoint.com/node-js-interview-questions/">sitepoint</a></div>