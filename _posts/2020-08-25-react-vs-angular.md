---
layout: single
title:  "React vs Angular: So sánh chuyên sâu"
desc: "React vs Angular: So sánh chuyên sâu"
keywords: "React, Angular"
categories: [javascript]
tag: [React, Angular, javascript]
---
**Tôi nên chọn Angular hay React? Mỗi khung công tác có rất nhiều thứ để cung cấp và không dễ để lựa chọn giữa chúng. Cho dù bạn là một người mới đang cố gắng tìm ra nơi bắt đầu, một người làm nghề tự do chọn một khuôn khổ cho dự án tiếp theo của bạn hay một kiến ​​trúc sư cấp doanh nghiệp lập kế hoạch tầm nhìn chiến lược cho công ty của bạn, bạn có thể sẽ được hưởng lợi từ việc có một cái nhìn được đào tạo về chủ đề này.**

Để giúp bạn tiết kiệm thời gian, hãy để tôi cho bạn biết một điều: bài viết này sẽ không đưa ra câu trả lời rõ ràng về khung công tác nào tốt hơn. Nhưng hàng trăm bài báo khác với tiêu đề tương tự cũng vậy. Tôi không thể nói với bạn điều đó, bởi vì câu trả lời phụ thuộc vào nhiều yếu tố làm cho một công nghệ cụ thể ít nhiều phù hợp với môi trường và trường hợp sử dụng của bạn.

Vì chúng tôi không thể trả lời câu hỏi trực tiếp, chúng tôi sẽ thử một cách khác. Chúng tôi sẽ so sánh Angular và React, để chứng minh cách bạn có thể tiếp cận vấn đề so sánh hai framework bất kỳ theo cách thức có cấu trúc và điều chỉnh nó cho phù hợp với môi trường của bạn. Bạn biết đấy, cách tiếp cận "dạy một người đàn ông câu cá" cũ. Bằng cách đó, khi cả hai được thay thế bằng BetterFramework.js trong thời gian một năm, bạn sẽ có thể tạo lại cùng một luồng suy nghĩ một lần nữa.

![Hai hiệp sĩ lao vào nhau, với biểu tượng React và Angular trên khiên của họ](https://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2017/04/1492644427RvsA_B-01.png)

_Chúng tôi vừa đại tu hướng dẫn này để phản ánh trạng thái của React, Angular và những ưu nhược điểm tương ứng của chúng vào năm 2020._

Bắt đầu từ đâu?
---------------

Trước khi chọn bất kỳ công cụ nào, bạn cần trả lời hai câu hỏi đơn giản: “Theo bạn thì đây có phải là một công cụ tốt không?” và "Nó sẽ hoạt động tốt cho trường hợp sử dụng của tôi chứ?" Cả hai đều không có ý nghĩa riêng, vì vậy bạn luôn cần ghi nhớ cả hai điều đó. Được rồi, các câu hỏi có thể không đơn giản như vậy, vì vậy chúng tôi sẽ cố gắng chia chúng thành những câu hỏi nhỏ hơn.

Các câu hỏi về chính công cụ:

*   Nó trưởng thành như thế nào và ai đứng sau nó?
*   Nó có những loại tính năng nào?
*   Nó sử dụng kiến ​​trúc, mô hình phát triển và mô hình nào?
*   Hệ sinh thái xung quanh nó là gì?

Câu hỏi để tự suy ngẫm:

*   Liệu tôi và các đồng nghiệp của mình có thể học công cụ này một cách dễ dàng không?
*   Nó có phù hợp với dự án của tôi không?
*   Trải nghiệm của nhà phát triển như thế nào?

Sử dụng bộ câu hỏi này, bạn có thể bắt đầu đánh giá của mình về bất kỳ công cụ nào và chúng tôi cũng sẽ dựa trên so sánh của chúng tôi về React và Angular dựa trên chúng.

Có một điều khác mà chúng tôi cần tính đến. Nói một cách chính xác, thật không công bằng khi so sánh Angular với React, vì Angular là một framework toàn diện, giàu tính năng, trong khi React chỉ là một thư viện thành phần UI. Thậm chí, chúng ta sẽ nói về React kết hợp với một số thư viện thường được sử dụng với nó.

Trưởng thành
------------

Một phần quan trọng của việc trở thành một nhà phát triển có kỹ năng là có thể giữ sự cân bằng giữa các phương pháp tiếp cận đã được thiết lập, chứng minh về thời gian và đánh giá công nghệ tiên tiến mới. Theo nguyên tắc chung, bạn nên cẩn thận khi sử dụng các công cụ chưa đến hạn do một số rủi ro nhất định:

*   Công cụ có thể có lỗi và không ổn định.
*   Nó có thể bị nhà cung cấp bỏ rơi bất ngờ.
*   Có thể không có sẵn cơ sở kiến ​​thức hoặc cộng đồng lớn trong trường hợp bạn cần trợ giúp.
*   Cả React và Angular đều xuất thân từ những gia đình tốt, vì vậy có vẻ như chúng ta có thể tự tin về mặt này.

### Phản ứng

[React](https://reactjs.org/) được phát triển và duy trì bởi Facebook và được sử dụng trong các sản phẩm của họ, bao gồm cả Instagram và WhatsApp. Nó đã xuất hiện khoảng từ năm 2013, vì vậy nó không hoàn toàn mới. Đây cũng là một trong những dự án nổi tiếng nhất trên GitHub, với hơn 150.000 ngôi sao vào thời điểm viết bài. Một số công ty đáng chú ý khác sử dụng React là Airbnb, Uber, Netflix, Dropbox và Atlassian. Nghe có vẻ tốt với tôi.

### Angular

[Angular](https://angular.io/) đã xuất hiện từ năm 2016, nó trẻ hơn một chút so với React, nhưng nó cũng không phải là một đứa trẻ mới trong khối. Nó được duy trì bởi Google và, [như Igor Minar đã đề cập](https://www.youtube.com/watch?v=rbFLorQWlOQ&feature=youtu.be&t=358) , thậm chí trong năm 2018 đã được sử dụng trong hơn 600 trăm ứng dụng trong Google như Bảng điều khiển Firebase, Google Analytics, Google Express, Google Cloud Platform và hơn thế nữa. Bên ngoài Google, Angular được Forbes, Upwork, VMWare và [những người khác sử dụng](https://www.madewithangular.com/) .

Đặc trưng
---------

Giống như tôi đã đề cập trước đó, Angular có nhiều tính năng hơn React. Đây có thể là điều tốt và điều xấu, tùy thuộc vào cách bạn nhìn nhận nó.

if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_1'); }); }

Cả hai khuôn khổ đều có chung một số tính năng chính: các thành phần, liên kết dữ liệu và kết xuất bất khả tri nền tảng.

### Angular

Angular cung cấp rất nhiều tính năng cần thiết cho một ứng dụng web hiện đại. Một số tính năng tiêu chuẩn là:

*   tiêm phụ thuộc
*   mẫu, dựa trên phiên bản mở rộng của HTML
*   các thành phần dựa trên lớp có móc vòng đời
*   định tuyến, được cung cấp bởi `@angular/router`
*   Ajax yêu cầu sử dụng `@angular/common/http`
*   `@angular/forms` để xây dựng hình thức
*   đóng gói CSS thành phần
*   Bảo vệ XSS
*   tách mã và tải chậm
*   người chạy thử nghiệm, khuôn khổ và các tiện ích cho thử nghiệm đơn vị.

Một số tính năng này được tích hợp vào cốt lõi của khuôn khổ và bạn không có tùy chọn không sử dụng chúng. Điều này đòi hỏi các nhà phát triển phải quen thuộc với các tính năng như chèn phụ thuộc để xây dựng ngay cả một ứng dụng Angular nhỏ. Các tính năng khác như máy khách HTTP hoặc biểu mẫu là hoàn toàn tùy chọn và có thể được thêm vào khi cần thiết.

### React

Với React, bạn đang bắt đầu với một cách tiếp cận tối giản hơn. Nếu chúng ta chỉ xem xét React, đây là những gì chúng ta có:

*   thay vì các mẫu cổ điển, nó có JSX, một ngôn ngữ giống như XML được xây dựng trên nền JavaScript
*   các thành phần dựa trên lớp có móc vòng đời hoặc các thành phần chức năng đơn giản hơn
*   quản lý nhà nước bằng setState và hooks.
*   Bảo vệ XSS
*   tách mã và tải chậm
*   ranh giới xử lý lỗi
*   tiện ích cho các thành phần kiểm tra đơn vị

Ngoài ra, React không cung cấp bất kỳ thứ gì để tiêm phụ thuộc, định tuyến, cuộc gọi HTTP hoặc xử lý biểu mẫu nâng cao. Bạn phải chọn bất kỳ thư viện bổ sung nào để thêm vào dựa trên nhu cầu của bạn, điều này có thể là điều tốt và điều xấu tùy thuộc vào mức độ kinh nghiệm của bạn với những công nghệ này. Một số thư viện phổ biến thường được sử dụng cùng với React là:

*   [React-router](https://reactrouter.com) để định tuyến
*   Tìm nạp (hoặc [axios](https://github.com/axios/axios) ) cho các yêu cầu HTTP
*   nhiều kỹ thuật khác nhau để đóng gói CSS
*   [](https://enzymejs.github.io/enzyme/)[Thư viện kiểm tra phản ứng](https://testing-library.com/docs/react-testing-library/intro) hoặc [Enzyme](https://enzymejs.github.io/enzyme/) cho các tiện ích kiểm tra đơn vị bổ sung

Các nhóm mà tôi đã làm việc cùng đã tìm thấy quyền tự do lựa chọn thư viện của bạn một cách thoải mái. Điều này cho chúng tôi khả năng điều chỉnh ngăn xếp của chúng tôi theo các yêu cầu cụ thể của từng dự án và chúng tôi không thấy chi phí học các thư viện mới cao như vậy.

Ngôn ngữ, Mô hình và Mẫu
------------------------

Quay lại một bước từ các tính năng của mỗi khung công tác, hãy xem loại khái niệm cấp cao nào phổ biến với cả hai khung công tác.

### Phản ứng

Một số điều quan trọng cần lưu ý khi nghĩ về React: JSX, các thành phần và hook.

#### JSX

Trái ngược với hầu hết các framework, React không có một ngôn ngữ tạo mẫu riêng. Thay vì theo cách tiếp cận cổ điển là tách đánh dấu và logic, React đã quyết định kết hợp chúng trong các thành phần bằng cách sử dụng [JSX](https://reactjs.org/docs/introducing-jsx.html) , một ngôn ngữ giống XML cho phép bạn viết đánh dấu trực tiếp trong mã JavaScript của mình.

Mặc dù lợi ích của việc kết hợp đánh dấu với JavaScript có thể gây tranh cãi, nhưng nó có một lợi ích không thể chối cãi: phân tích tĩnh. Nếu bạn mắc lỗi trong đánh dấu JSX của mình, trình biên dịch sẽ phát ra lỗi thay vì tiếp tục trong im lặng. Điều này giúp bạn ngay lập tức bắt lỗi chính tả và các lỗi ngớ ngẩn khác. Sử dụng JSX trong các dự án khác nhau - chẳng hạn như [MDX](https://github.com/mdx-js/mdx) , cho phép sử dụng JSX trong các tệp đánh dấu.

#### Các thành phần

Trong React, bạn có thể xác định [các thành phần](https://reactjs.org/docs/components-and-props.html) bằng cách sử dụng các hàm và lớp.

Các thành phần lớp cho phép bạn viết mã của mình bằng các lớp ES và cấu trúc logic thành phần thành các phương thức. Chúng cũng cho phép bạn sử dụng các phương thức vòng đời truyền thống của React để chạy logic tùy chỉnh khi một thành phần được gắn kết, cập nhật, tháo lắp, v.v. Mặc dù ký hiệu này dễ hiểu hơn đối với những người quen thuộc với lập trình OOP, nhưng bạn cần phải biết tất cả các sắc thái tinh tế mà JS có - ví dụ: cách `this`hoạt động và không quên ràng buộc các trình xử lý sự kiện.

Các thành phần chức năng được định nghĩa là các chức năng đơn giản. Chúng thường thuần túy và cung cấp ánh xạ rõ ràng giữa đạo cụ đầu vào và đầu ra được kết xuất. Mã chức năng thường ít ghép nối hơn và dễ sử dụng lại và kiểm tra hơn. Trước khi ra đời các hook, các thành phần chức năng không thể ở trạng thái hoạt động và không có giải pháp thay thế cho các phương thức vòng đời.

if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_2'); }); }

Các nhà phát triển React có xu hướng loại bỏ các thành phần lớp để ủng hộ các thành phần chức năng đơn giản hơn, nhưng với hook là một tính năng mới hơn, bạn sẽ thường thấy sự kết hợp của cả hai cách tiếp cận trong các dự án React lớn hơn.

#### Móc

[Hooks](https://reactjs.org/docs/hooks-intro.html) là một tính năng mới của React được giới thiệu trong phiên bản 16.8. Chúng là các hàm cho phép bạn phân loại các tính năng của trạng thái thành phần và vòng đời trong các thành phần chức năng. Có hai hook do React cung cấp: `useState`để quản lý trạng thái và `useEffect`để tạo các hiệu ứng phụ - chẳng hạn như tải dữ liệu hoặc chỉnh sửa thủ công DOM.

Hooks đã được giới thiệu để làm cho các thành phần chức năng đơn giản hơn và dễ kết hợp hơn. Giờ đây, bạn có thể chia các chức năng lớn thành các phần nguyên tử nhỏ hơn, cho phép bạn chia các phần chức năng liên quan - tách chúng khỏi logic kết xuất và sử dụng lại nó trong các thành phần khác nhau. Hook là một giải pháp thay thế rõ ràng hơn cho việc sử dụng các thành phần lớp và các mẫu khác, chẳng hạn như các chức năng kết xuất và các thành phần bậc cao - có thể nhanh chóng trở nên quá phức tạp.

React cung cấp các cách cấu trúc ứng dụng của bạn mà không liên quan đến nhiều lớp trừu tượng phức tạp. Việc sử dụng các thành phần chức năng cùng với hook cho phép bạn viết mã đơn giản hơn, nguyên tử hơn và có thể tái sử dụng. Mặc dù khái niệm kết hợp mã và mẫu có vẻ gây tranh cãi, việc tách bản trình bày và logic ứng dụng thành các chức năng khác nhau cho phép bạn đạt được kết quả tương tự.

### Angular

Angular cũng có một số điều thú vị, bắt đầu từ những trừu tượng cơ bản như các thành phần, dịch vụ và mô-đun, đến TypeScript, RxJS và Angular Elements, cũng như cách tiếp cận của nó đối với quản lý trạng thái.

#### Các khái niệm chính

Angular có mức độ trừu tượng cao hơn React, do đó giới thiệu [các khái niệm cơ bản](https://angular.io/guide/architecture) hơn để làm quen. Những điều chính là:

*   **các thành phần** : được định nghĩa là các lớp ES được trang trí đặc biệt chịu trách nhiệm thực thi logic ứng dụng và hiển thị mẫu
*   **dịch vụ** : các lớp chịu trách nhiệm thực hiện logic nghiệp vụ và ứng dụng, được sử dụng bởi các thành phần
*   **mô-đun** : về cơ bản là bộ chứa DI để nối dây các thành phần, dịch vụ, đường ống và các thực thể khác có liên quan với nhau.

Angular sử dụng nhiều các lớp cũng như các khái niệm như DI, ​​vốn ít phổ biến trong thế giới phát triển front-end, nhưng sẽ quen thuộc với bất kỳ ai có kinh nghiệm phát triển back-end.

#### TypeScript

[TypeScript](https://www.typescriptlang.org/) là một ngôn ngữ mới được xây dựng dựa trên JavaScript và được phát triển bởi Microsoft. Đó là một tập hợp siêu của JavaScript ES2015 và bao gồm các tính năng từ các phiên bản mới hơn của ngôn ngữ. Bạn có thể sử dụng nó thay vì Babel để viết JavaScript hiện đại. Nó cũng có hệ thống đánh máy cực kỳ mạnh mẽ có thể phân tích tĩnh mã của bạn bằng cách sử dụng kết hợp các chú thích và kiểu suy luận.

Ngoài ra còn có một lợi ích tinh tế hơn. TypeScript đã bị ảnh hưởng nhiều bởi Java và .NET, vì vậy nếu các nhà phát triển của bạn có kiến ​​thức nền tảng về một trong những ngôn ngữ này, họ có thể thấy TypeScript dễ học hơn JavaScript đơn thuần (lưu ý cách chúng tôi chuyển từ công cụ này sang môi trường cá nhân của bạn) . Mặc dù Angular là framework chính đầu tiên tích cực áp dụng TypeScript, nhưng hiện tại nó cũng đang được thu hút trong rất nhiều dự án khác, chẳng hạn như [Deno](https://www.sitepoint.com/deno-introduction/) (một thời gian chạy gốc của TypeScript), Puppeteer và TypeORM.

Cũng có thể (và khôn ngoan) khi sử dụng TypeScript cùng với React.

#### RxJS

[RxJS](https://rxjs-dev.firebaseapp.com/) là một thư viện lập trình phản ứng cho phép xử lý linh hoạt hơn các hoạt động và sự kiện không đồng bộ. Đó là sự kết hợp của các mẫu Observer và Iterator được pha trộn với lập trình chức năng. RxJS cho phép bạn xử lý bất kỳ thứ gì giống như một dòng giá trị liên tục và thực hiện các hoạt động khác nhau trên đó như ánh xạ, lọc, tách hoặc hợp nhất.

Thư viện đã được Angular áp dụng trong mô-đun HTTP của nó cũng như để sử dụng nội bộ. Khi bạn thực hiện một yêu cầu HTTP, nó trả về một Có thể quan sát thay vì Lời hứa thông thường. Cách tiếp cận này mở ra cánh cửa cho các khả năng thú vị, chẳng hạn như khả năng hủy một yêu cầu, thử lại nhiều lần hoặc làm việc với các luồng dữ liệu liên tục như WebSockets. Nhưng đây chỉ là bề nổi. Để thành thạo RxJS, bạn sẽ cần biết cách của mình về các loại Quan sát, Đối tượng, cũng như khoảng một trăm phương thức và toán tử.

#### Quản lý Nhà nước

Tương tự như React, các thành phần Angular có một khái niệm về trạng thái thành phần. Các thành phần có thể lưu trữ dữ liệu trong các thuộc tính lớp của chúng và liên kết các giá trị với các mẫu của chúng. Nếu bạn muốn chia sẻ trạng thái trên toàn ứng dụng, bạn có thể chuyển nó sang một dịch vụ trạng thái mà sau này có thể được đưa vào các thành phần. Vì lập trình phản ứng và RxJS là công dân hạng nhất trong Angular, nên việc sử dụng các khả năng quan sát để tính toán lại các phần của trạng thái dựa trên một số đầu vào là điều thường thấy. Tuy nhiên, điều này có thể trở nên phức tạp trong các ứng dụng lớn hơn vì việc thay đổi một số biến có thể kích hoạt dòng cập nhật đa hướng mà khó theo dõi. Có các thư viện cho Angular cho phép bạn đơn giản hóa việc quản lý trạng thái trên quy mô lớn. Chúng ta sẽ xem xét kỹ hơn về chúng sau.

if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_3'); }); }

#### Yếu tố góc

[Phần tử Angular](https://angular.io/guide/elements) cung cấp một cách để đóng gói các thành phần Angular dưới dạng các phần tử tùy chỉnh. Còn được gọi là các thành phần web, các phần tử tùy chỉnh là một cách được tiêu chuẩn hóa theo khung-bất khả tri để tạo các phần tử HTML tùy chỉnh được kiểm soát bởi mã JavaScript của bạn. Khi bạn xác định một phần tử như vậy và thêm nó vào sổ đăng ký của trình duyệt, nó sẽ tự động được hiển thị ở mọi nơi mà nó được tham chiếu trong HTML. Các phần tử Angular cung cấp một API tạo ra trình bao bọc cần thiết để triển khai API thành phần tùy chỉnh và làm cho nó hoạt động với cơ chế phát hiện thay đổi của Angular. Cơ chế này có thể được sử dụng để nhúng các thành phần khác hoặc toàn bộ ứng dụng Angular vào ứng dụng chủ của bạn, có khả năng được viết trong một khuôn khổ khác với chu kỳ phát triển khác.

Chúng tôi nhận thấy TypeScript là một công cụ tuyệt vời để cải thiện khả năng bảo trì cho các dự án của chúng tôi, đặc biệt là những dự án có cơ sở mã lớn hoặc miền / logic nghiệp vụ phức tạp. Mã được viết bằng TypeScript mang tính mô tả cao hơn, dễ theo dõi và cấu trúc lại. Ngay cả khi bạn không sử dụng Angular, chúng tôi khuyên bạn nên cân nhắc nó cho dự án JavaScript tiếp theo của mình. RxJS giới thiệu các cách mới để quản lý luồng dữ liệu trong dự án của bạn, nhưng yêu cầu bạn phải hiểu rõ về chủ đề này. Nếu không, nó có thể mang lại sự phức tạp không mong muốn cho dự án của bạn. Các phần tử Angular có tiềm năng sử dụng lại các thành phần Angular và thật thú vị khi xem điều này diễn ra như thế nào trong tương lai.

Hệ sinh thái
------------

Điều tuyệt vời về các framework mã nguồn mở là số lượng các công cụ được tạo ra xung quanh chúng. Đôi khi, những công cụ này thậm chí còn hữu ích hơn chính framework. Chúng ta hãy xem xét một số công cụ và thư viện phổ biến nhất được liên kết với mỗi khung công tác.

### Angular

#### CLI góc

Một xu hướng phổ biến với các khuôn khổ hiện đại là có một công cụ CLI giúp bạn khởi động dự án của mình mà không cần phải tự định cấu hình bản dựng. Angular có [Angular CLI](https://cli.angular.io/) cho điều đó. Nó cho phép bạn tạo và chạy một dự án chỉ với một vài lệnh. Tất cả các tập lệnh chịu trách nhiệm xây dựng ứng dụng, khởi động máy chủ phát triển và chạy thử nghiệm đều bị ẩn khỏi bạn `node_modules`. Bạn cũng có thể sử dụng nó để tạo mã mới trong quá trình phát triển và cài đặt các phụ thuộc.

Angular giới thiệu một cách mới thú vị để quản lý các phụ thuộc vào dự án của bạn. Khi sử dụng `ng add`, bạn có thể cài đặt phụ thuộc và nó sẽ tự động được cấu hình để sử dụng. Ví dụ: khi bạn chạy `ng add @angular/material`, Angular CLI tải Angular Material từ sổ đăng ký npm và chạy tập lệnh cài đặt của nó để tự động cấu hình ứng dụng của bạn để sử dụng Angular Material. Điều này được thực hiện bằng cách sử dụng sơ đồ Angular. Sơ đồ là một công cụ dòng công việc cho phép các thư viện thực hiện các thay đổi đối với cơ sở mã của bạn. Điều này có nghĩa là các tác giả thư viện có thể cung cấp các cách tự động giải quyết các vấn đề không tương thích ngược mà bạn có thể gặp phải khi cài đặt phiên bản mới.

#### Thư viện thành phần

Một điều quan trọng trong việc sử dụng bất kỳ khung JavaScript nào là có thể tích hợp chúng với một thư viện thành phần mà bạn chọn, để tránh phải xây dựng mọi thứ từ đầu. Angular cung cấp tích hợp với hầu hết các thư viện thành phần phổ biến cũng như các thư viện gốc của riêng nó. Ví dụ:

*   [ng-bootstrap](https://ng-bootstrap.github.io) để sử dụng các widget Bootstrap
*   [Giao diện người dùng Vật liệu](https://material.angular.io/) , dành cho các thành phần Thiết kế Vật liệu của Google
*   [NG-ZORRO](https://ng.ant.design/) , một thư viện các thành phần thực hiện đặc tả Thiết kế Kiến
*   [Onsen UI cho Angular](https://onsen.io/v2/guide/angular2/) , một thư viện các thành phần cho các ứng dụng di động
*   [PrimeNG](https://www.primefaces.org/primeng/) , một bộ sưu tập các thành phần Angular phong phú

#### Thư viện quản lý nhà nước

Nếu khả năng quản lý trạng thái gốc không đủ cho bạn, có một số thư viện bên thứ ba phổ biến có sẵn trong lĩnh vực này.

Một trong những phổ biến nhất là NgRx. Nó được lấy cảm hứng từ Redux của React nhưng cũng sử dụng RxJS để xem và tính toán lại dữ liệu trong trạng thái. Sử dụng [NgRx](https://ngrx.io/) có thể giúp bạn thực thi luồng dữ liệu một chiều dễ hiểu, cũng như giảm sự ghép nối trong mã của bạn.

[NGXS](https://www.ngxs.io/) là một thư viện quản lý nhà nước khác được lấy cảm hứng từ Redux. Trái ngược với NgRx, NGXS cố gắng giảm thiểu mã viết sẵn bằng cách sử dụng các tính năng TypeScript hiện đại và cải thiện đường cong học tập và trải nghiệm phát triển tổng thể.

[Akita](https://github.com/datorama/akita) là một đứa trẻ mới hơn trong khối, cho phép chúng tôi giữ trạng thái trong nhiều cửa hàng, áp dụng các bản cập nhật bất biến và sử dụng RxJS để truy vấn và truyền trực tuyến các giá trị.

#### Ionic Framework

[Ionic](https://ionicframework.com/) là một khuôn khổ phổ biến để phát triển các ứng dụng di động lai. Nó cung cấp một thùng chứa Cordova được tích hợp độc đáo với Angular và một thư viện thành phần vật liệu khá đẹp. Sử dụng nó, bạn có thể dễ dàng thiết lập và xây dựng một ứng dụng di động. Nếu bạn thích một ứng dụng kết hợp hơn một ứng dụng gốc, đây là một lựa chọn tốt.

#### Phổ góc

[Angular Universal](https://angular.io/guide/universal) là một dự án bao gồm các công cụ khác nhau để cho phép hiển thị phía máy chủ cho các ứng dụng Angular. Nó được tích hợp với Angular CLI và hỗ trợ một số khung Node.js, chẳng hạn như Express và Hapi, cũng như với lõi .NET.

#### Augury

[Augury](https://augury.rangle.io/) là một tiện ích mở rộng trình duyệt dành cho Chrome và Firefox, giúp gỡ lỗi các ứng dụng Angular đang chạy ở chế độ phát triển. Bạn có thể sử dụng nó để khám phá cây thành phần của mình, theo dõi phát hiện thay đổi và tối ưu hóa các vấn đề về hiệu suất.

if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_4'); }); }

#### Compodoc

[Compodoc](https://compodoc.app/) là một trình tạo tài liệu tĩnh cho Angular. Tương tự như các trình tạo tài liệu khác, nó có thể tạo tài liệu HTML tĩnh dựa trên các nhận xét TSDoc trong mã của bạn. Tuy nhiên, Compodoc đi kèm với các tính năng tiện lợi dành riêng cho Angular, chẳng hạn như duyệt cấu trúc mô-đun, các tuyến và phân loại các lớp thành các thành phần, dịch vụ, v.v.

#### Ngx-admin

[Ngx-admin](https://github.com/akveo/ngx-admin) là một khuôn khổ phổ biến để tạo trang tổng quan tùy chỉnh với Angular và sử dụng Nebular hoặc Angular Material làm thư viện thành phần.

Có rất nhiều thư viện và công cụ khác có sẵn trong [danh sách Awesome Angular](https://github.com/PatrickJS/awesome-angular) .

### Phản ứng

#### Tạo ứng dụng React

[Create React App](https://create-react-app.dev/) là một tiện ích CLI để React nhanh chóng thiết lập các dự án mới. Tương tự như Angular CLI, nó cho phép bạn tạo một dự án mới, chạy ứng dụng ở chế độ phát triển hoặc tạo gói sản xuất. Nó sử dụng Jest để kiểm tra đơn vị, hỗ trợ lập hồ sơ ứng dụng bằng cách sử dụng các biến môi trường, proxy back-end để phát triển cục bộ, TypeScript, Sass, PostCSS và nhiều tính năng khác.

#### Thư viện thành phần

Tương tự như Angular, React có rất nhiều thư viện thành phần để bạn lựa chọn:

*   [kiến thiết kế](https://ant.design/docs/react/introduce)
*   [Giao diện người dùng vật liệu](https://material-ui.com/)
*   [react-bootstrap](https://react-bootstrap.github.io/)
*   [Giao diện người dùng ngữ nghĩa](https://react.semantic-ui.com/)
*   [Onsen UI](https://onsen.io/) , được tối ưu hóa cho các ứng dụng di động
*   [Kế hoạch chi tiết](https://blueprintjs.com/) , để tạo các ứng dụng máy tính để bàn

#### Thư viện quản lý nhà nước

Sự ra đời của hook chắc chắn đã làm lung lay việc quản lý nhà nước trong React. Có những cuộc thảo luận đang diễn ra nếu thậm chí có nhu cầu về thư viện quản lý nhà nước của bên thứ ba. Mặc dù hook giải quyết nhu cầu ngay lập tức để làm việc với trạng thái, các thư viện khác vẫn có thể thúc đẩy điều này hơn nữa bằng cách cho phép chúng tôi sử dụng các mẫu triển khai đã được kiểm tra thời gian, nhiều thư viện bổ sung và công cụ phát triển.

[Redux](https://redux.js.org/) là một thư viện quản lý nhà nước lấy cảm hứng từ Flux, nhưng với một số đơn giản hóa. Ý tưởng chính của Redux là toàn bộ trạng thái của ứng dụng được thể hiện bằng một đối tượng duy nhất, được biến đổi bởi các hàm được gọi là bộ giảm thiểu. Bản thân các bộ giảm thiểu là các chức năng thuần túy và được thực hiện tách biệt với các thành phần. Điều này cho phép tách các mối quan tâm và khả năng kiểm tra tốt hơn.

[MobX](https://mobx.js.org/README.html) là một thư viện thay thế để quản lý trạng thái của một ứng dụng. Thay vì giữ trạng thái trong một cửa hàng bất biến duy nhất, như Redux làm, nó khuyến khích bạn chỉ lưu trữ trạng thái bắt buộc tối thiểu và lấy phần còn lại từ nó. Nó cung cấp một tập hợp các trình trang trí để xác định người quan sát và người quan sát và giới thiệu logic phản ứng cho trạng thái của bạn.

#### Thư viện tạo kiểu

Không giống như Angular, React không cung cấp khả năng đóng gói CSS gốc, vì vậy bạn cần tìm kiếm các giải pháp của bên thứ ba. Có rất nhiều giải pháp cho vấn đề này, nhưng không có nhà lãnh đạo rõ ràng nào trong số đó. Một số trong những cái phổ biến là:

*   [Các thành phần được tạo kiểu](https://styled-components.com/) , một thư viện cho phép bạn tạo các thành phần React với việc áp dụng kiểu của bạn, cũng như tạo kiểu cho các thành phần của bạn
*   [Mô-đun CSS](https://github.com/css-modules/css-modules) , cho phép bạn nhập tệp CSS và tạo tên lớp riêng biệt duy nhất để tham chiếu các kiểu
*   [Cảm xúc](https://github.com/emotion-js/emotion) , kết hợp các phương pháp của Thành phần được tạo kiểu và Mô-đun CSS vào một thư viện duy nhất

#### PropTypes

[PropTypes](https://reactjs.org/docs/typechecking-with-proptypes.html) là một tính năng tùy chọn của React, cho phép bạn giới thiệu xác thực thời gian chạy thành phần. Ngược lại với việc sử dụng kiểm tra kiểu tĩnh với TypeScript, PropTypes sẽ thực hiện kiểm tra kiểu khi ứng dụng của bạn thực sự đang chạy. Điều này đặc biệt hữu ích khi phát triển thư viện khi bạn không thể chắc chắn rằng khách hàng của mình đang sử dụng TypeScript, ngay cả khi bạn đang sử dụng. Kể từ React 15.5, các kiểu prop đã được chuyển sang một thư viện kiểu prop riêng và giờ đây hoàn toàn là tùy chọn. Cân nhắc lợi ích của nó, chúng tôi khuyên bạn nên sử dụng nó để cải thiện độ tin cậy của ứng dụng của bạn.

#### React Native

[React Native](https://reactnative.dev/) là một nền tảng do Facebook phát triển để tạo các ứng dụng di động gốc bằng React. Không giống như Ionic, tạo ra một ứng dụng lai, React Native tạo ra một giao diện người dùng gốc thực sự. Nó cung cấp một tập hợp các thành phần React chuẩn được liên kết với các đối tác gốc của chúng. Nó cũng cho phép bạn tạo các thành phần của mình và liên kết chúng với mã gốc được viết bằng Objective-C, Java hoặc Swift.

#### Next.js

[Next.js](https://nextjs.org/) là một khuôn khổ để hiển thị phía máy chủ của các ứng dụng React. Nó cung cấp một cách linh hoạt để hiển thị hoàn toàn hoặc một phần ứng dụng của bạn trên máy chủ, trả lại kết quả cho máy khách và tiếp tục trong trình duyệt. Nó cố gắng làm cho nhiệm vụ phức tạp của việc tạo các ứng dụng phổ biến trở nên dễ dàng hơn, vì vậy việc thiết lập được thiết kế đơn giản nhất có thể, với một số lượng tối thiểu các yêu cầu và nguyên thủy mới đối với cấu trúc dự án của bạn.

#### Quản trị viên React

[React-admin](https://github.com/marmelab/react-admin) là một khuôn khổ để xây dựng các ứng dụng SPA kiểu CRUD trên các API REST hoặc GraphQL hiện có. Nó đi kèm với các tính năng tiện dụng, chẳng hạn như giao diện người dùng được xây dựng bằng Material Design, quốc tế hóa, chủ đề, xác thực dữ liệu, v.v.

if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_5'); }); }

#### Môi trường phát triển giao diện người dùng

Một xu hướng chính trong phát triển giao diện người dùng trong vài năm qua là sự bùng nổ của các công cụ phát triển cho phép bạn phát triển, kiểm tra và ghi lại thành phần của mình một cách tương tác và tách biệt với ứng dụng. [Storybook](https://storybook.js.org/) đã tự khẳng định mình là một trong những nhà lãnh đạo trong lĩnh vực này, với sự hỗ trợ cho cả React và Angular. Tuy nhiên, có những lựa chọn thay thế khác cho React.

[React Styleguidist](https://github.com/styleguidist/react-styleguidist) , tương tự như Storybook, cho phép bạn tạo tài liệu tương tác về các thành phần của mình. Trái ngược với Storybook, giao diện người dùng được tạo giống như một readme tương tác hơn là một tập hợp các câu chuyện riêng biệt. Trong khi Storybook tỏa sáng như một môi trường phát triển, Styleguidist là một công cụ tài liệu hơn.

Chúng tôi cũng đã đề cập đến [MDX](https://github.com/mdx-js/mdx) trong bài viết này. Nó cho phép bạn thêm gia vị cho các tệp Markdown của mình bằng cách thêm các thành phần JSX tương tác.

#### Người trợ giúp thử nghiệm

Kiểm tra các thành phần giao diện người dùng thường bao gồm việc phải kết xuất chúng trong môi trường hộp cát, mô phỏng tương tác của người dùng và xác nhận kết quả đầu ra. Những công việc thường xuyên này có thể được đơn giản hóa bằng cách sử dụng các trình trợ giúp kiểm tra thích hợp. Đối với Angular, đây là [TestBed được tích hợp sẵn](https://angular.io/api/core/testing/TestBed) . Đối với React, có hai ứng cử viên phổ biến: Enzyme và Thư viện thử nghiệm.

[Enzyme](https://enzymejs.github.io/enzyme/) là sự lựa chọn tiêu chuẩn trên thực tế. Nó cho phép bạn kết xuất các thành phần của mình thành một DOM đầy đủ hoặc nông cũng như tương tác với thành phần được kết xuất. Nó chủ yếu tuân theo phương pháp thử nghiệm hộp trắng, trong đó các bài kiểm tra của bạn có thể tham chiếu một số nội dung bên trong của thành phần như các thành phần con, đạo cụ hoặc trạng thái của nó.

[Thư viện Kiểm thử](https://testing-library.com/) tuân theo một cách tiếp cận khác và thúc đẩy bạn tương tác với các thành phần của mình như người dùng làm mà không cần biết việc triển khai kỹ thuật. Các thử nghiệm được tạo ra theo cách này thường ít giòn hơn và dễ bảo trì hơn. Mặc dù nó phổ biến nhất với React, nhưng Thư viện Thử nghiệm cũng có sẵn cho Angular.

#### Gatsby

[Gatsby](https://www.gatsbyjs.org/) là một trình tạo trang web tĩnh sử dụng React.js. Nó cho phép bạn sử dụng GraphQL để truy vấn dữ liệu cho các trang web của bạn được xác định trong Markdown, YAML, JSON, các API bên ngoài và các hệ thống quản lý nội dung phổ biến.

#### React 360

[React 360](https://facebook.github.io/react-360/) là thư viện tạo ứng dụng thực tế ảo cho trình duyệt. Nó cung cấp một API React khai báo được xây dựng dựa trên các API trình duyệt WebGL và WebVR, do đó, việc tạo trải nghiệm VR 360 dễ dàng hơn.

#### Công cụ dành cho nhà phát triển React

[React Dev Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) là một tiện ích mở rộng của trình duyệt dành cho Chrome để gỡ lỗi các ứng dụng React, cho phép bạn xem qua cây thành phần React và xem các đạo cụ và trạng thái của chúng.

Có rất nhiều thư viện và công cụ khác có sẵn trong [danh sách Awesome React](https://github.com/enaqx/awesome-react) .

Nhận con nuôi, Đường cong học tập và Kinh nghiệm phát triển
-----------------------------------------------------------

Một tiêu chí quan trọng để chọn một công nghệ mới là nó dễ học như thế nào. Tất nhiên, câu trả lời phụ thuộc vào một loạt các yếu tố, chẳng hạn như kinh nghiệm trước đây của bạn và sự quen thuộc chung với các khái niệm và mẫu liên quan. Tuy nhiên, chúng tôi vẫn có thể thử đánh giá số lượng điều mới bạn sẽ cần học để bắt đầu với một khuôn khổ nhất định. Bây giờ, nếu chúng tôi giả định rằng bạn đã biết ES6 +, xây dựng các công cụ và tất cả những thứ đó, hãy xem bạn sẽ cần hiểu những gì khác.

### Phản ứng

Với React, điều đầu tiên bạn gặp phải là JSX. Nó có vẻ khó khăn khi viết cho một số nhà phát triển. Tuy nhiên, nó không làm phức tạp thêm: chỉ là các biểu thức, là JavaScript và cú pháp giống HTML đặc biệt. Bạn cũng sẽ cần học cách viết các thành phần, sử dụng đạo cụ để cấu hình và quản lý trạng thái bên trong. Bạn không cần phải học cú pháp mẫu mới, vì tất cả những thứ này đều là JavaScript thuần túy. Trong khi React hỗ trợ các thành phần dựa trên lớp, với sự ra đời của các hook, việc phát triển chức năng đang trở nên phổ biến hơn. Điều này sẽ yêu cầu bạn hiểu một số mô hình phát triển chức năng cơ bản.

Các [hướng dẫn chính thức](https://reactjs.org/tutorial/tutorial.html) là một nơi tuyệt vời để bắt đầu học Phản ứng. Khi bạn đã hoàn tất, hãy làm quen với bộ định tuyến. React Router có thể hơi phức tạp và độc đáo, nhưng không có gì phải lo lắng. Tùy thuộc vào quy mô, độ phức tạp và yêu cầu của dự án của bạn, bạn sẽ cần tìm và tìm hiểu một số thư viện bổ sung và đây có thể là phần phức tạp. Nhưng sau đó, mọi thứ nên thuận buồm xuôi gió.

if ( !!window.propertag ) { window.propertag.cmd.push(function() { proper\_display('sitepoint\_content\_6'); }); }

Chúng tôi thực sự ngạc nhiên về việc bắt đầu sử dụng React dễ dàng như thế nào. Ngay cả những người có nền tảng phát triển back-end và kinh nghiệm phát triển front-end hạn chế cũng có thể bắt kịp nhanh chóng. Các thông báo lỗi bạn có thể gặp phải thường rõ ràng và cung cấp giải thích về cách giải quyết vấn đề cơ bản.

Nhược điểm là bạn sẽ cần đầu tư thời gian vào việc lựa chọn thư viện để hỗ trợ các hoạt động phát triển của mình. Với số lượng người trong số họ ở đó, điều này có thể đặt ra một thách thức. Nhưng điều này có thể được thực hiện cùng với các hoạt động phát triển của bạn sau khi bạn đã cảm thấy thoải mái với chính framework.

Mặc dù TypeScript không bắt buộc đối với React, chúng tôi thực sự khuyên bạn nên đánh giá và áp dụng nó trong các dự án của mình.

### Angular

Học Angular sẽ giới thiệu cho bạn nhiều khái niệm mới hơn React. Trước hết, bạn cần làm quen với TypeScript. Đối với các nhà phát triển có kinh nghiệm về các ngôn ngữ được nhập tĩnh như Java hoặc .NET, điều này có thể dễ hiểu hơn JavaScript, nhưng đối với các nhà phát triển JavaScript thuần túy, điều này có thể đòi hỏi một số nỗ lực. Để bắt đầu hành trình của bạn, chúng tôi có thể giới thiệu hướng dẫn [Tour of Heroes](https://angular.io/tutorial) .

Bản thân khung công tác rất phong phú về các chủ đề để học, bắt đầu từ những chủ đề cơ bản như mô-đun, chèn phụ thuộc, trình trang trí, thành phần, dịch vụ, đường ống, mẫu và chỉ thị, đến các chủ đề nâng cao hơn như phát hiện thay đổi, vùng, biên dịch AoT và Rx .js. Tất cả đều được đề cập trong tài liệu. Rx.js tự nó là một chủ đề nặng nề và được mô tả rất chi tiết trên trang web chính thức. Mặc dù tương đối dễ sử dụng ở cấp độ cơ bản, nhưng nó sẽ phức tạp hơn khi chuyển sang các chủ đề nâng cao.

Nhìn chung, chúng tôi nhận thấy rằng rào cản gia nhập đối với Angular cao hơn đối với React. Số lượng tuyệt đối các khái niệm mới có thể quá sức đối với những người mới. Và ngay cả khi bạn đã bắt đầu, trải nghiệm có thể hơi khó khăn vì bạn cần lưu ý những điều như quản lý đăng ký Rx.js, hiệu suất phát hiện thay đổi và chuối trong hộp (vâng, đây là một lời khuyên thực tế từ tài liệu). Chúng tôi thường gặp các thông báo lỗi quá khó hiểu, vì vậy chúng tôi đã phải google chúng và cầu nguyện cho một kết quả chính xác.

Có vẻ như chúng tôi ủng hộ React ở đây, và chúng tôi chắc chắn làm vậy. Chúng tôi đã có kinh nghiệm giới thiệu các nhà phát triển mới cho cả các dự án Angular và React có quy mô và độ phức tạp tương đương, và bằng cách nào đó với React, nó luôn diễn ra suôn sẻ hơn. Tuy nhiên, như tôi đã nói trước đó, điều này phụ thuộc vào nhiều yếu tố và có thể hoạt động khác nhau đối với bạn.

Mức độ phổ biến và phản hồi của cộng đồng
-----------------------------------------

Cả hai khuôn khổ đều rất phổ biến và có cộng đồng người theo dõi và ủng hộ. Cũng có rất nhiều bài báo đề xuất bạn sử dụng công nghệ này hoặc công nghệ khác, chủ yếu nêu bật những mặt tích cực của chúng. Hãy xem liệu chúng ta có thể tìm ra cách khách quan hơn để thể hiện mức độ phổ biến của từng dự án và sự hài lòng của nhà phát triển hay không.

Các [NPM tải thống kê](https://www.npmtrends.com/@angular/core-vs-react) chương trình hơn gần năm lần tải cho Phản ứng hơn góc. [Các xu hướng của Google](https://trends.google.com/trends/explore?q=angular,react) cũng báo cáo nhiều tìm kiếm hơn cho React trên toàn thế giới.

Các [năm 2019 Nhà nước báo cáo hoạt Javascript](https://2019.stateofjs.com/front-end-frameworks/) danh sách Phản ứng như khuôn khổ front-end phổ biến nhất, với góc là thứ hai để cuối cùng, chỉ trước Ember. 71% người tham gia nói rằng họ đã [sử dụng React và sẽ sử dụng lại](https://2019.stateofjs.com/front-end-frameworks/react/) . Chỉ có [21% người tham gia](https://2019.stateofjs.com/front-end-frameworks/angular/) nói điều tương tự về Angular và 35% nói rằng họ đã sử dụng Angular và sẽ _không_ sử dụng nó nữa (chỉ 8% nói về React).

Các [Hacker Tin tức tuyển dụng Xu hướng cho năm 2019](https://www.hntrends.com/2019/dec-another-year-on-top-for-react.html) danh sách Phản ứng như công nghệ nã gắt gao nhất cho người lao động trong hơn 31 tháng liên tiếp.

[Stack Overflow](https://insights.stackoverflow.com/survey/2020#most-popular-technologies) liệt kê React là framework phổ biến thứ hai sau jQuery. Angular được liệt kê là cái thứ ba. Báo cáo [Khung trang web được yêu thích nhất, đáng sợ và bị truy nã](https://insights.stackoverflow.com/survey/2020#most-loved-dreaded-and-wanted) của họ vẽ nên một bức tranh tương tự với các khung khác.

[Báo cáo State of Developer Ecosystem 2020](https://www.jetbrains.com/lp/devecosystem-2020/javascript/) của Jet Brains khẳng định vị trí của React là framework giao diện người dùng phổ biến nhất.

Đưa ra một quyết định
---------------------

Bạn có thể đã lưu ý rằng mỗi khung công tác có một bộ khả năng riêng của nó, cả mặt tốt và mặt xấu của chúng. Nhưng phân tích này đã được thực hiện bên ngoài bất kỳ ngữ cảnh cụ thể nào và do đó không đưa ra câu trả lời về việc bạn nên chọn khung công tác nào. Để quyết định điều đó, bạn cần phải xem xét nó từ góc độ dự án của mình. Đây là điều bạn cần tự làm.

Để bắt đầu, hãy thử trả lời những câu hỏi này về dự án của bạn và khi bạn trả lời, hãy ghép câu trả lời với những gì bạn đã học về hai khuôn khổ. Danh sách này có thể không đầy đủ, nhưng đủ để bạn bắt đầu:

*   Dự án lớn như thế nào?
*   Nó sẽ được duy trì trong bao lâu?
*   Tất cả các chức năng có được xác định trước rõ ràng hay bạn dự kiến ​​sẽ linh hoạt?
*   Nếu tất cả các tính năng đã được xác định, bạn cần những khả năng nào?
*   Mô hình miền và logic nghiệp vụ có phức tạp không?
*   Bạn đang nhắm mục tiêu nền tảng nào? Web, điện thoại di động, máy tính để bàn?
*   Bạn có cần kết xuất phía máy chủ không? SEO có quan trọng không?
*   Bạn sẽ xử lý nhiều luồng sự kiện thời gian thực chứ?
*   Nhóm của bạn lớn đến mức nào?
*   Các nhà phát triển của bạn có kinh nghiệm như thế nào và nền tảng của họ là gì?
*   Có bất kỳ thư viện thành phần làm sẵn nào mà bạn muốn sử dụng không?

Nếu bạn đang bắt đầu một dự án lớn và bạn muốn giảm thiểu rủi ro đưa ra một lựa chọn tồi, trước tiên hãy xem xét việc tạo ra một sản phẩm bằng chứng về khái niệm. Chọn một số tính năng chính của các dự án và cố gắng triển khai chúng một cách đơn giản bằng cách sử dụng một trong các khuôn khổ. PoC thường không mất nhiều thời gian để xây dựng, nhưng chúng sẽ cung cấp cho bạn một số kinh nghiệm cá nhân có giá trị về cách làm việc với khuôn khổ và cho phép bạn xác thực các yêu cầu kỹ thuật chính. Nếu bạn hài lòng với kết quả, bạn có thể tiếp tục phát triển toàn diện. Nếu không, thất bại nhanh sẽ khiến bạn đau đầu về lâu dài.

Một khuôn khổ để cai trị tất cả?
--------------------------------

Khi bạn đã chọn một khuôn khổ cho một dự án, bạn sẽ bị cám dỗ sử dụng cùng một công nghệ chính xác cho các dự án sắp tới của mình. Đừng. Mặc dù bạn nên giữ cho ngăn xếp công nghệ của mình nhất quán, nhưng đừng mù quáng sử dụng cùng một cách tiếp cận mọi lúc. Trước khi bắt đầu mỗi dự án, hãy dành một chút thời gian để trả lời các câu hỏi tương tự một lần nữa. Có thể đối với dự án tiếp theo, câu trả lời sẽ khác hoặc cảnh quan sẽ thay đổi. Ngoài ra, nếu bạn có điều kiện thực hiện một dự án nhỏ với một đống công nghệ không quen thuộc, hãy tiếp tục. Những thí nghiệm như vậy sẽ cung cấp cho bạn kinh nghiệm vô giá. Giữ tâm trí của bạn cởi mở và học hỏi từ những sai lầm của bạn. Tại một số thời điểm, một công nghệ nhất định sẽ cảm thấy tự nhiên và đúng đắn.

<div style="text-align: right">Theo <a href="https://www.sitepoint.com/react-vs-angular/">sitepoint</a></div>