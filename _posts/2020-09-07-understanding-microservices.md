---
layout: single
title:  "Hiểu về Microservices"
desc: "Hiểu về Microservices"
keywords: "Microservices"
categories: [Microservices]
tag: [Microservices]
---

Hiểu về Microservices
=====================

 Đây là chương đầu tiên trong cuốn sách [Python Microservices Development](https://www.sitepoint.com/premium/books/python-microservices-development/read/1) của tác giả Tarek Ziade. Các bạn có thể tìm bản đầy đủ hơn trong link ở trên. Sau đây là nội dung đã được dịch sang tiếng việt của chương này.

---

Chúng tôi luôn cố gắng cải thiện cách chúng tôi xây dựng phần mềm và kể từ kỷ nguyên thẻ đục lỗ, chúng tôi đã cải thiện rất nhiều, ít nhất là.

Xu hướng microservices là một cải tiến đã xuất hiện trong vài năm gần đây, một phần dựa trên sự sẵn sàng tăng tốc chu kỳ phát hành của các công ty. Họ muốn vận chuyển các sản phẩm mới và các tính năng mới cho khách hàng của họ càng nhanh càng tốt. Họ muốn trở nên _nhanh nhẹn_ bằng cách lặp lại thường xuyên và họ muốn giao hàng, vận chuyển và giao hàng lại.

Nếu hàng nghìn, thậm chí hàng triệu khách hàng sử dụng dịch vụ của bạn, đưa vào sản xuất một tính năng thử nghiệm và loại bỏ nó nếu nó không hoạt động, được coi là phương pháp hay thay vì nướng nó trong nhiều tháng trước khi bạn xuất bản.

Các công ty như Netflix đang quảng bá các kỹ thuật phân phối liên tục của họ, nơi những thay đổi nhỏ được thực hiện rất thường xuyên trong quá trình sản xuất và thử nghiệm trên một nhóm nhỏ cơ sở người dùng. Họ đã phát triển các công cụ như Spinnaker ( [http://www.spinnaker.io/](http://www.spinnaker.io/) ) để tự động hóa nhiều bước nhất có thể để cập nhật sản xuất và vận chuyển các tính năng của họ trên đám mây dưới dạng các dịch vụ vi mô độc lập.

Nhưng nếu bạn đọc Tin tức Hacker hoặc Reddit, có thể khá khó để tìm ra đâu là thông tin hữu ích cho bạn và đâu chỉ là thông tin kiểu báo chí tuân thủ buzzwords.

> "Viết một bài báo hứa hẹn sự cứu rỗi, biến nó thành một cái gì đó có cấu trúc hoặc một cái gì đó ảo, hoặc trừu tượng, phân tán hoặc cấp cao hơn hoặc ứng dụng và bạn gần như có thể chắc chắn đã bắt đầu một giáo phái mới.
> 
> \- Edsger W. Dijkstra

Chương này sẽ giúp bạn hiểu microservices là gì và sau đó sẽ tập trung vào các cách khác nhau mà bạn có thể triển khai chúng bằng Python. Nó bao gồm một số phần sau:

*   Một từ về Kiến trúc hướng dịch vụ
*   Cách tiếp cận nguyên khối của việc xây dựng một ứng dụng
*   Cách tiếp cận microservices của việc xây dựng ứng dụng
*   Lợi ích của microservices
*   Cạm bẫy trong microservices
*   Triển khai microservices với Python

Hy vọng rằng khi bạn đã đọc đến cuối chương, bạn sẽ có thể đi sâu vào việc xây dựng các microservices với sự hiểu biết tốt về chúng là gì và chúng không phải là gì - và cách bạn có thể sử dụng Python.

Nguồn gốc của kiến ​​trúc hướng dịch vụ
---------------------------------------

Có rất nhiều định nghĩa ngoài kia, vì không có tiêu chuẩn chính thức cho microservices. Mọi người thường đề cập đến **Kiến trúc hướng dịch vụ** ( **SOA** ) khi họ đang cố gắng giải thích microservices là gì.

> SOA có trước microservices và nguyên tắc cốt lõi của nó là ý tưởng rằng bạn tổ chức các ứng dụng thành một đơn vị chức năng rời rạc có thể được truy cập từ xa và hoạt động và cập nhật một cách độc lập.
> 
> \- Wikipedia

Mỗi đơn vị trong định nghĩa trước này là một dịch vụ khép kín, thực hiện một khía cạnh của doanh nghiệp và cung cấp tính năng của nó thông qua một số giao diện.

Mặc dù SOA tuyên bố rõ ràng rằng các dịch vụ phải là các quy trình độc lập, nhưng nó không thực thi các giao thức nào nên được sử dụng để các quy trình đó tương tác với nhau và khá mơ hồ về cách bạn triển khai và tổ chức ứng dụng của mình.

Nếu bạn đọc **Tuyên ngôn SOA** ( [http://www.soa-manifesto.org](http://www.soa-manifesto.org) ) mà một số chuyên gia đã xuất bản trên web vào khoảng năm 2009, họ thậm chí không đề cập đến việc các dịch vụ có tương tác qua mạng hay không.

Các dịch vụ SOA có thể giao tiếp qua Giao tiếp **giữa các quá trình** ( **IPC** ) bằng cách sử dụng các ổ cắm trên cùng một máy, thông qua bộ nhớ dùng chung, thông qua hàng đợi tin nhắn gián tiếp hoặc thậm chí với **Cuộc gọi thủ tục từ xa** ( **RPC** ). Các tùy chọn rất phong phú và vào cuối ngày, SOA có thể là mọi thứ và bất cứ thứ gì miễn là bạn không chạy tất cả mã ứng dụng của mình vào một quy trình duy nhất.

Tuy nhiên, người ta thường nói rằng microservices là một chuyên môn của SOA, đã bắt đầu xuất hiện trong vài năm qua, vì chúng thực hiện một số mục tiêu của SOA là xây dựng ứng dụng với các thành phần độc lập tương tác với nhau.

Bây giờ nếu chúng ta muốn đưa ra một định nghĩa đầy đủ về microservices là gì, cách tốt nhất để làm điều đó là trước tiên hãy xem xét cách hầu hết các phần mềm được cấu trúc.

Cách tiếp cận đơn nguyên
------------------------

Hãy lấy một ví dụ rất đơn giản về một ứng dụng nguyên khối truyền thống: trang web đặt phòng khách sạn.

Bên cạnh nội dung HTML tĩnh, trang web có tính năng đặt phòng cho phép người dùng đặt khách sạn ở bất kỳ thành phố nào trên thế giới. Người dùng có thể tìm kiếm khách sạn, sau đó đặt phòng bằng thẻ tín dụng của họ.

Khi người dùng thực hiện tìm kiếm trên trang web của khách sạn, ứng dụng sẽ thực hiện các bước sau:

1.  Nó chạy một vài truy vấn SQL dựa trên cơ sở dữ liệu khách sạn của nó.
2.  Yêu cầu HTTP đối với dịch vụ của đối tác được thực hiện để thêm nhiều khách sạn hơn vào danh sách.
3.  Trang kết quả HTML được tạo bằng công cụ mẫu HTML.

Từ đó, khi người dùng đã tìm thấy khách sạn hoàn hảo và nhấp vào đó để đặt phòng, ứng dụng sẽ thực hiện các bước sau:

1.  Khách hàng được tạo trong cơ sở dữ liệu nếu cần và phải xác thực.
2.  Thanh toán được thực hiện bằng cách tương tác với dịch vụ web của ngân hàng.
3.  Ứng dụng lưu chi tiết thanh toán trong cơ sở dữ liệu vì lý do pháp lý.
4.  Biên nhận được tạo bằng trình tạo PDF.
5.  Một email tóm tắt được gửi đến người dùng sử dụng dịch vụ email.
6.  Email đặt phòng được chuyển tiếp đến khách sạn của bên thứ ba bằng dịch vụ email.
7.  Một mục cơ sở dữ liệu được thêm vào để theo dõi việc đặt chỗ.

Tất nhiên, quá trình này là một mô hình đơn giản hóa, nhưng khá thực tế.

Ứng dụng tương tác với một cơ sở dữ liệu chứa thông tin của khách sạn, chi tiết đặt phòng, thanh toán, thông tin người dùng, v.v. Nó cũng tương tác với các dịch vụ bên ngoài để gửi email, thanh toán và nhận thêm khách sạn từ các đối tác.

Trong kiến trúc **LAMP** ( **Linux-Apache-MySQL-Perl / PHP / Python** ) cũ tốt, mỗi yêu cầu đến sẽ tạo ra một loạt các truy vấn SQL trên cơ sở dữ liệu và một vài lệnh gọi mạng đến các dịch vụ bên ngoài và sau đó máy chủ tạo ra phản hồi HTML sử dụng công cụ mẫu.

Sơ đồ sau minh họa kiến ​​trúc tập trung này:

![](https://d1rxzn6szs9jwr.cloudfront.net/premium/reeedr/books/python-microservices-development/images/000012.jpg)

Ứng dụng này là một nguyên khối điển hình, và nó có rất nhiều lợi ích rõ ràng.

Điểm lớn nhất là toàn bộ ứng dụng nằm trong một cơ sở mã duy nhất và khi mã hóa dự án bắt đầu, nó làm cho mọi thứ đơn giản hơn. Việc xây dựng phạm vi kiểm tra tốt rất dễ dàng và bạn có thể tổ chức mã của mình theo cách gọn gàng và có cấu trúc bên trong cơ sở mã. Lưu trữ tất cả dữ liệu vào một cơ sở dữ liệu duy nhất cũng giúp đơn giản hóa sự phát triển của ứng dụng. Bạn có thể điều chỉnh mô hình dữ liệu và cách mã sẽ truy vấn nó.

Việc triển khai cũng không có gì phải bàn cãi: chúng ta có thể gắn thẻ cơ sở mã, xây dựng một gói và chạy nó ở đâu đó. Để mở rộng quy mô, chúng tôi có thể chạy một số phiên bản của ứng dụng đặt phòng và chạy một số cơ sở dữ liệu với một số cơ chế sao chép tại chỗ.

Nếu ứng dụng của bạn vẫn nhỏ, mô hình này hoạt động tốt và dễ bảo trì cho một nhóm.

Nhưng các dự án thường đang phát triển và chúng lớn hơn những gì dự định ban đầu. Và việc có toàn bộ ứng dụng trong một cơ sở mã duy nhất mang lại một số vấn đề khó chịu trên đường đi. Ví dụ: nếu bạn cần thực hiện một thay đổi sâu rộng có phạm vi lớn như thay đổi dịch vụ ngân hàng hoặc lớp cơ sở dữ liệu của bạn, toàn bộ ứng dụng sẽ rơi vào trạng thái rất không ổn định. Những thay đổi này là một vấn đề lớn trong vòng đời của dự án và chúng đòi hỏi nhiều thử nghiệm bổ sung để triển khai một phiên bản mới. Và những thay đổi như thế này _sẽ_ xảy ra trong vòng đời của một dự án.

Những thay đổi nhỏ cũng có thể tạo ra thiệt hại về tài sản thế chấp vì các phần khác nhau của hệ thống có các yêu cầu về thời gian hoạt động và độ ổn định khác nhau. Việc đặt các quy trình thanh toán và đặt chỗ gặp rủi ro vì chức năng tạo tệp PDF làm hỏng máy chủ là một chút vấn đề.

Tăng trưởng không kiểm soát là một vấn đề khác. Ứng dụng nhất định phải có các tính năng mới và với việc các nhà phát triển rời đi và tham gia dự án, tổ chức mã có thể bắt đầu lộn xộn, các bài kiểm tra chậm hơn một chút. Sự phát triển này thường kết thúc với một cơ sở mã spaghetti khó duy trì, với một cơ sở dữ liệu lông lá cần các kế hoạch di chuyển phức tạp mỗi khi một số nhà phát triển cấu trúc lại mô hình dữ liệu.

Các dự án phần mềm lớn thường mất vài năm để hoàn thiện, và sau đó chúng dần dần biến thành một mớ hỗn độn khó hiểu và khó duy trì. Và nó không xảy ra bởi vì các nhà phát triển tồi. Điều đó xảy ra bởi vì khi sự phức tạp ngày càng tăng, càng ít người hiểu hết tác động của mỗi thay đổi nhỏ mà họ thực hiện. Vì vậy, họ cố gắng làm việc cô lập ở một góc của cơ sở mã và khi bạn nhìn vào góc nhìn 10.000 foot của dự án, bạn có thể thấy sự lộn xộn.

Tất cả chúng tôi đã ở đó.

Thật không vui chút nào và các nhà phát triển làm việc trong một dự án như vậy mơ ước xây dựng ứng dụng từ đầu với khung công tác mới nhất. Và khi làm như vậy, họ thường lại rơi vào những vấn đề tương tự - cùng một câu chuyện được lặp lại.

Những điểm sau đây tóm tắt những ưu và nhược điểm của cách tiếp cận đơn nguyên:

*   Bắt đầu một dự án như một nguyên khối rất dễ dàng và có lẽ là cách tiếp cận tốt nhất.
*   Cơ sở dữ liệu tập trung giúp đơn giản hóa việc thiết kế và tổ chức dữ liệu.
*   Việc triển khai một ứng dụng rất đơn giản.
*   Bất kỳ thay đổi nào trong mã có thể ảnh hưởng đến các tính năng không liên quan. Khi một cái gì đó bị hỏng, toàn bộ ứng dụng có thể bị hỏng.
*   Các giải pháp để mở rộng quy mô ứng dụng của bạn bị hạn chế: bạn có thể triển khai một số phiên bản, nhưng nếu một tính năng cụ thể bên trong ứng dụng chiếm hết tài nguyên, nó sẽ ảnh hưởng đến mọi thứ.
*   Khi cơ sở mã phát triển, thật khó để giữ cho nó sạch sẽ và được kiểm soát.

Tất nhiên, có một số cách để tránh một số vấn đề được mô tả ở đây.

Giải pháp rõ ràng là chia ứng dụng thành các phần riêng biệt, ngay cả khi mã kết quả vẫn sẽ chạy trong một quy trình duy nhất. Các nhà phát triển làm điều này bằng cách xây dựng ứng dụng của họ với các thư viện và khuôn khổ bên ngoài. Những công cụ đó có thể là nội bộ hoặc từ cộng đồng **Phần mềm nguồn mở** ( **OSS** ).

Việc xây dựng một ứng dụng web bằng Python nếu bạn sử dụng một khuôn khổ như **Flask** , cho phép bạn tập trung vào logic nghiệp vụ và làm cho việc ngoại hóa một số mã của bạn thành các phần mở rộng Flask và các gói Python nhỏ rất hấp dẫn. Và chia nhỏ mã của bạn thành các gói nhỏ thường là một ý tưởng hay để kiểm soát sự phát triển ứng dụng của bạn.

> "Nhỏ là đẹp."
> 
> \- Triết lý UNIX

Ví dụ: trình tạo PDF được mô tả trong ứng dụng đặt phòng khách sạn có thể là một gói Python riêng biệt sử dụng **Reportlab** và một số mẫu để thực hiện công việc.

Rất có thể gói này có thể được sử dụng lại trong một số ứng dụng khác và thậm chí có thể được xuất bản lên **Chỉ mục gói Python** ( **PyPI** ) cho cộng đồng.

Nhưng bạn vẫn đang xây dựng một ứng dụng duy nhất và một số vấn đề vẫn còn, như không thể mở rộng các bộ phận theo cách khác nhau hoặc bất kỳ vấn đề gián tiếp nào được đưa ra bởi sự phụ thuộc lỗi.

Bạn thậm chí sẽ nhận được những thách thức mới, bởi vì bạn hiện đang sử dụng các phụ thuộc. Một vấn đề bạn có thể nhận được là _địa ngục phụ thuộc_ . Nếu một phần ứng dụng của bạn sử dụng thư viện, nhưng trình tạo PDF chỉ có thể sử dụng một phiên bản cụ thể của thư viện đó, thì rất có thể cuối cùng bạn sẽ phải đối phó với nó bằng một số cách giải quyết xấu xí hoặc thậm chí phân nhánh phụ thuộc để có một tùy chỉnh sửa chữa ở đó.

Tất nhiên, tất cả các vấn đề được mô tả trong phần này không xuất hiện trong ngày 1 ngày 2 khi dự án bắt đầu, mà là chồng chất theo thời gian.

Bây giờ chúng ta hãy xem xét cùng một ứng dụng sẽ trông như thế nào nếu chúng ta sử dụng microservices để xây dựng nó.

Phương pháp tiếp cận microservice
---------------------------------

Nếu chúng ta xây dựng cùng một ứng dụng bằng cách sử dụng microservices, chúng ta sẽ tổ chức mã thành một số thành phần riêng biệt chạy trong các quy trình riêng biệt. Thay vì có một ứng dụng duy nhất chịu trách nhiệm về mọi thứ, chúng tôi sẽ chia nó thành nhiều microservices khác nhau, như thể hiện trong sơ đồ sau:

![](https://d1rxzn6szs9jwr.cloudfront.net/premium/reeedr/books/python-microservices-development/images/000016.jpg)

Đừng sợ số lượng thành phần hiển thị trong sơ đồ này. Các tương tác nội bộ của ứng dụng nguyên khối chỉ được hiển thị bằng các phần riêng biệt. Chúng tôi đã thay đổi một số sự phức tạp và kết thúc với bảy thành phần độc lập sau:

1.  **Giao diện người dùng đặt trước** : Một dịch vụ giao diện người dùng, tạo giao diện người dùng web và tương tác với tất cả các dịch vụ nhỏ khác.
2.  **Dịch vụ báo cáo PDF** : Một **dịch vụ** rất đơn giản có thể tạo các tệp PDF cho biên lai hoặc bất kỳ tài liệu nào khác với một mẫu và một số dữ liệu.
3.  **Tìm kiếm** : Một dịch vụ có thể được truy vấn để có được danh sách các khách sạn với tên thành phố. Dịch vụ này có cơ sở dữ liệu riêng của nó.
4.  **Thanh toán** : Một dịch vụ tương tác với dịch vụ ngân hàng của bên thứ ba và quản lý cơ sở dữ liệu thanh toán. Nó cũng gửi e-mail khi thanh toán thành công.
5.  **Đặt trước:** Đặt trước cửa hàng và tạo tệp PDF.
6.  **Người dùng** : Lưu trữ thông tin người dùng và tương tác với người dùng qua email.
7.  **Xác thực** : Dịch vụ dựa trên OAuth 2 trả về mã thông báo xác thực mà mỗi microservice có thể sử dụng để xác thực khi gọi người khác.

Các dịch vụ nhỏ đó, cùng với một số dịch vụ bên ngoài như dịch vụ email, sẽ cung cấp một bộ tính năng tương tự như ứng dụng nguyên khối. Trong thiết kế này, mỗi thành phần giao tiếp bằng giao thức HTTP và các tính năng được cung cấp thông qua các dịch vụ web RESTful.

Không có cơ sở dữ liệu tập trung, vì mỗi microservice xử lý nội bộ với các cấu trúc dữ liệu riêng của nó và dữ liệu vào và ra sử dụng định dạng bất khả tri ngôn ngữ như JSON. Nó có thể sử dụng XML hoặc YAML miễn là nó có thể được tạo ra và sử dụng bằng bất kỳ ngôn ngữ nào cũng như di chuyển qua các yêu cầu và phản hồi HTTP.

Dịch vụ Giao diện người dùng đặt chỗ hơi đặc biệt về vấn đề đó, vì nó tạo **Giao diện Người dùng** ( **UI** ). Tùy thuộc vào khung giao diện người dùng được sử dụng để xây dựng giao diện người dùng, đầu ra Giao diện người dùng đặt chỗ có thể là sự kết hợp của HTML và JSON hoặc thậm chí là JSON đơn giản nếu giao diện sử dụng công cụ phía máy khách dựa trên JavaScript tĩnh để tạo giao diện trực tiếp trong trình duyệt.

Nhưng bên cạnh trường hợp giao diện người dùng cụ thể này, một ứng dụng web được thiết kế với microservices là một thành phần của một số microservices, có thể tương tác với nhau thông qua HTTP để cung cấp cho toàn bộ hệ thống.

Trong bối cảnh đó, microservices là đơn vị logic tập trung vào một nhiệm vụ rất cụ thể. Đây là một nỗ lực xác định đầy đủ:

#### Ghi chú

Một microservice là một ứng dụng nhẹ, cung cấp danh sách các tính năng được thu hẹp với một hợp đồng được xác định rõ ràng. Đó là một _thành phần có một trách nhiệm duy nhất_ , có thể được phát triển và triển khai độc lập.

Định nghĩa này không đề cập đến HTTP hoặc JSON, vì bạn có thể coi một dịch vụ nhỏ dựa trên UDP trao đổi dữ liệu nhị phân như một dịch vụ vi mô chẳng hạn.

Nhưng trong trường hợp của chúng tôi và trong suốt cuốn sách, tất cả các dịch vụ vi mô của chúng tôi chỉ là các ứng dụng web đơn giản sử dụng giao thức HTTP và sử dụng và sản xuất JSON khi nó không phải là giao diện người dùng.

Lợi ích của microservice
------------------------

Mặc dù kiến ​​trúc microservices trông phức tạp hơn so với cấu trúc nguyên khối, nhưng lợi thế của nó là rất nhiều. Nó cung cấp những điều sau:

*   Tách mối quan tâm
*   Các dự án nhỏ hơn cần giải quyết
*   Nhiều tùy chọn mở rộng và triển khai hơn

Chúng tôi sẽ thảo luận chi tiết hơn về chúng trong các phần sau.

### Tách mối quan tâm

Trước hết, mỗi microservice có thể được phát triển độc lập bởi một nhóm riêng biệt. Ví dụ, xây dựng một dịch vụ đặt chỗ có thể là một dự án đầy đủ của riêng nó. Nhóm phụ trách có thể tạo nó bằng bất kỳ ngôn ngữ lập trình và cơ sở dữ liệu nào, miễn là nó có API HTTP được ghi chép đầy đủ.

Điều đó cũng có nghĩa là sự phát triển của ứng dụng được kiểm soát nhiều hơn so với nguyên khối. Ví dụ: nếu hệ thống thanh toán thay đổi các tương tác cơ bản của nó với ngân hàng, tác động sẽ được bản địa hóa bên trong dịch vụ đó và phần còn lại của ứng dụng vẫn ổn định và có thể không bị ảnh hưởng.

Sự kết hợp lỏng lẻo này cải thiện rất nhiều tốc độ tổng thể của dự án, khi chúng tôi áp dụng, ở cấp độ dịch vụ, một triết lý tương tự như nguyên tắc _trách nhiệm duy nhất_ .

Nguyên tắc trách nhiệm duy nhất được Robert Martin định nghĩa để giải thích rằng một lớp học chỉ nên có một lý do để thay đổi; nói cách khác, mỗi lớp nên cung cấp một tính năng duy nhất, được xác định rõ ràng. Được áp dụng cho microservices, điều đó có nghĩa là chúng tôi muốn đảm bảo rằng mỗi microservice tập trung vào một vai trò duy nhất.

### Các dự án nhỏ hơn

Lợi ích thứ hai là phá vỡ sự phức tạp của dự án. Khi bạn thêm một tính năng vào ứng dụng, chẳng hạn như báo cáo PDF, ngay cả khi bạn làm điều đó một cách rõ ràng, bạn sẽ làm cho mã cơ sở lớn hơn, phức tạp hơn và đôi khi, chậm hơn. Việc xây dựng tính năng đó trong một ứng dụng riêng biệt sẽ tránh được vấn đề này và giúp bạn viết nó dễ dàng hơn bằng bất kỳ công cụ nào bạn muốn. Bạn có thể cấu trúc lại nó thường xuyên, rút ​​ngắn chu kỳ phát hành và luôn cập nhật mọi thứ. Sự phát triển của ứng dụng vẫn nằm trong tầm kiểm soát của bạn.

Xử lý một dự án nhỏ hơn cũng làm giảm rủi ro khi cải thiện ứng dụng: nếu một nhóm muốn dùng thử ngôn ngữ lập trình hoặc khung công tác mới nhất, họ có thể lặp lại nhanh chóng trên một nguyên mẫu triển khai cùng một API microservice, dùng thử và quyết định xem có hay không để gắn bó với nó.

Một ví dụ thực tế trong tâm trí là dịch vụ lưu trữ Firefox Sync. Hiện có một số thử nghiệm để chuyển từ triển khai Python + MySQL hiện tại sang triển khai dựa trên Go, lưu trữ dữ liệu của người dùng trong cơ sở dữ liệu SQLite độc ​​lập. Nguyên mẫu đó mang tính thử nghiệm cao, nhưng vì chúng tôi đã tách biệt tính năng lưu trữ trong một microservice với một API HTTP được xác định rõ, nên thật dễ dàng để thử với một nhóm nhỏ cơ sở người dùng.

### Mở rộng và triển khai

Cuối cùng, việc chia ứng dụng của bạn thành các thành phần giúp dễ dàng mở rộng quy mô tùy thuộc vào các ràng buộc của bạn. Giả sử bạn bắt đầu nhận được nhiều khách hàng đặt phòng khách sạn hàng ngày và thế hệ PDF bắt đầu nóng lên các CPU. Bạn có thể triển khai dịch vụ vi mô cụ thể đó trong một số máy chủ có CPU lớn hơn.

Một ví dụ điển hình khác là các dịch vụ siêu nhỏ ngốn RAM như các dịch vụ tương tác với cơ sở dữ liệu bộ nhớ như **Redis** hoặc **Memcache** . Do đó, bạn có thể điều chỉnh các triển khai của mình bằng cách triển khai chúng trên các máy chủ có ít CPU hơn và nhiều RAM hơn.

Do đó, chúng tôi có thể tóm tắt những lợi ích của microservices như sau:

*   Một nhóm có thể phát triển từng dịch vụ vi mô một cách độc lập và sử dụng bất kỳ công nghệ nào có ý nghĩa. Họ có thể xác định một chu kỳ phát hành tùy chỉnh. Tất cả những gì họ cần xác định là một API HTTP bất khả tri ngôn ngữ.
*   Các nhà phát triển chia độ phức tạp của ứng dụng thành các thành phần hợp lý. Mỗi microservice tập trung vào làm tốt một việc.
*   Vì microservices là các ứng dụng độc lập, nên có sự kiểm soát tốt hơn đối với việc triển khai, giúp mở rộng quy mô dễ dàng hơn.

Kiến trúc microservices rất tốt trong việc giải quyết nhiều vấn đề có thể phát sinh khi ứng dụng của bạn bắt đầu phát triển. Tuy nhiên, chúng ta cần lưu ý một số vấn đề mới mà chúng cũng mang lại trong thực tế.

Cạm bẫy của microservices
-------------------------

Như đã nói trước đó, việc xây dựng một ứng dụng với microservices có rất nhiều lợi ích, nhưng nó không phải là một viên đạn bạc.

Bạn cần biết những vấn đề chính sau đây mà bạn có thể phải đối phó khi viết mã microservices:

*   Phân tách phi logic
*   Nhiều tương tác mạng hơn
*   Lưu trữ và chia sẻ dữ liệu
*   Những vấn đề tương thích
*   Thử nghiệm

Những vấn đề này sẽ được đề cập chi tiết trong các phần sau.

### Phân tách phi logic

Vấn đề đầu tiên của kiến ​​trúc microservice là cách nó được thiết kế. Không có cách nào một nhóm có thể đưa ra kiến ​​trúc microservice hoàn hảo trong lần chụp đầu tiên. Một số dịch vụ vi mô như trình tạo PDF là một trường hợp sử dụng rõ ràng. Nhưng ngay sau khi bạn xử lý logic nghiệp vụ, rất có thể mã của bạn sẽ di chuyển xung quanh trước khi bạn nắm được cách tách mọi thứ thành một bộ microservices phù hợp.

Thiết kế cần hoàn thiện với một số chu kỳ thử-và-sai. Và việc thêm và xóa các microservices có thể khó khăn hơn việc cấu trúc lại một ứng dụng nguyên khối.

Bạn có thể giảm thiểu vấn đề này bằng cách tránh chia nhỏ ứng dụng của mình trong các microservices nếu việc phân chia không rõ ràng.

> Tách sớm là gốc rễ của mọi điều ác.

Nếu có bất kỳ nghi ngờ nào về việc phân tách có ý nghĩa, thì việc giữ mã trong cùng một ứng dụng là cách an toàn. Việc tách một số mã thành một microservice mới luôn dễ dàng hơn là hợp nhất trở lại hai microservices trong cùng một cơ sở mã bởi vì quyết định này hóa ra là sai.

Ví dụ: nếu bạn luôn phải triển khai hai dịch vụ vi mô cùng nhau hoặc nếu một thay đổi trong một dịch vụ vi mô ảnh hưởng đến mô hình dữ liệu của một dịch vụ khác, thì khả năng cao là bạn đã không phân chia ứng dụng một cách chính xác và hai dịch vụ đó nên được kết hợp lại.

### Nhiều tương tác mạng hơn

Vấn đề thứ hai là số lượng tương tác mạng được thêm vào để xây dựng cùng một ứng dụng. Trong phiên bản nguyên khối, ngay cả khi mã lộn xộn, mọi thứ diễn ra theo cùng một quy trình và bạn có thể gửi lại kết quả mà không cần phải gọi quá nhiều dịch vụ phụ trợ để xây dựng phản hồi thực tế.

Điều đó đòi hỏi phải chú ý thêm về cách mỗi dịch vụ phụ trợ được gọi và đặt ra rất nhiều câu hỏi như sau:

*   Điều gì xảy ra khi Giao diện người dùng đặt phòng không thể kết nối với dịch vụ báo cáo PDF do mạng bị chia tách hoặc dịch vụ chậm?
*   Giao diện người dùng Đặt chỗ gọi các dịch vụ khác đồng bộ hay không đồng bộ?
*   Điều đó sẽ ảnh hưởng như thế nào đến thời gian phản hồi?

Chúng tôi sẽ cần phải có một chiến lược vững chắc để có thể trả lời tất cả những câu hỏi đó và chúng tôi sẽ giải quyết những câu hỏi đó trong Chương 5, _Tương tác với các Dịch vụ Khác_ .

### Lưu trữ và chia sẻ dữ liệu

Một vấn đề khác là lưu trữ và chia sẻ dữ liệu. Một microservice hiệu quả cần phải độc lập với các microservice khác và lý tưởng là không nên chia sẻ cơ sở dữ liệu. Điều này có ý nghĩa gì đối với ứng dụng đặt phòng khách sạn của chúng tôi?

Một lần nữa, điều đó đặt ra rất nhiều câu hỏi như sau:

*   Chúng tôi có sử dụng cùng một ID của người dùng trên tất cả các cơ sở dữ liệu hay chúng tôi có các ID độc lập trong mỗi dịch vụ và giữ nó như một chi tiết triển khai ẩn?
*   Khi người dùng được thêm vào hệ thống, chúng tôi có sao chép một số thông tin của họ trong các cơ sở dữ liệu dịch vụ khác thông qua các chiến lược như bơm dữ liệu hay đó là quá mức cần thiết?
*   Chúng tôi giải quyết việc xóa dữ liệu như thế nào?

Đây là những câu hỏi khó trả lời và có nhiều cách khác nhau để giải quyết những vấn đề đó, chúng ta sẽ tìm hiểu trong suốt cuốn sách.

#### Ghi chú

Tránh sao chép dữ liệu nhiều nhất có thể trong khi giữ các microservices riêng biệt là một trong những thách thức lớn nhất trong việc thiết kế các ứng dụng dựa trên microservices.

### Những vấn đề tương thích

Một vấn đề khác xảy ra khi một thay đổi tính năng ảnh hưởng đến một số dịch vụ nhỏ. Nếu một thay đổi ảnh hưởng đến dữ liệu di chuyển giữa các dịch vụ theo cách không tương thích ngược lại, bạn sẽ gặp một số rắc rối.

Bạn có thể triển khai dịch vụ mới của mình và nó có hoạt động với các phiên bản cũ hơn của các dịch vụ khác không? Hay bạn cần thay đổi và triển khai nhiều dịch vụ cùng một lúc? Nó có nghĩa là bạn vừa vấp phải một số dịch vụ có lẽ nên được hợp nhất lại với nhau?

Một phiên bản tốt và vệ sinh thiết kế API giúp giảm thiểu những vấn đề đó, như chúng ta sẽ khám phá trong phần thứ hai của cuốn sách khi chúng ta xây dựng ứng dụng của mình.

### Thử nghiệm

Cuối cùng, khi bạn muốn thực hiện một số thử nghiệm đầu cuối và triển khai toàn bộ ứng dụng của mình, bây giờ bạn phải đối mặt với nhiều khối hình. Bạn cần phải có một quy trình triển khai mạnh mẽ và nhanh nhẹn để đạt hiệu quả. Bạn cần có thể chơi với toàn bộ ứng dụng của mình khi bạn phát triển nó. Bạn không thể kiểm tra hoàn toàn mọi thứ chỉ với một mảnh ghép.

Hy vọng rằng hiện nay có nhiều công cụ hỗ trợ triển khai các ứng dụng được xây dựng với một số thành phần, như chúng ta sẽ tìm hiểu trong suốt cuốn sách này. Và tất cả những công cụ đó có lẽ đã giúp thành công và áp dụng microservices và ngược lại.

#### Ghi chú

Kiến trúc kiểu microservices thúc đẩy đổi mới các công cụ triển khai và các công cụ triển khai hạ thấp ngưỡng cho phép kiến ​​trúc kiểu microservices.

Những cạm bẫy của việc sử dụng microservices có thể được tóm tắt như sau:

*   Việc tách ứng dụng thành microservices có thể dẫn đến các vấn đề về kiến ​​trúc
*   Tương tác mạng giữa các microservices thêm điểm yếu và chi phí bổ sung
*   Kiểm tra và triển khai các dịch vụ nhỏ có thể phức tạp
*   Và thách thức lớn nhất - chia sẻ dữ liệu giữa các microservices rất khó

Bạn không nên lo lắng quá nhiều về tất cả các cạm bẫy được mô tả trong phần này ngay bây giờ.

Chúng có vẻ áp đảo và ứng dụng nguyên khối truyền thống có thể trông giống như một sự đặt cược an toàn hơn, nhưng về lâu dài, việc chia nhỏ dự án của bạn thành các microservices sẽ làm cho nhiều nhiệm vụ của bạn, với tư cách là nhà phát triển hoặc **người điều hành** ( **Ops** ), dễ dàng hơn.

Triển khai microservices với Python
-----------------------------------

Python là một ngôn ngữ linh hoạt đáng kinh ngạc.

Như bạn có thể đã biết, nó được sử dụng để xây dựng nhiều loại ứng dụng khác nhau - từ các tập lệnh hệ thống đơn giản thực hiện các tác vụ trên máy chủ đến các ứng dụng hướng đối tượng lớn chạy dịch vụ cho hàng triệu người dùng.

Theo một nghiên cứu được thực hiện bởi Philip Guo vào năm 2014, được công bố trên trang web của **Hiệp hội Máy tính Máy tính** ( **ACM** ), Python đã vượt qua Java trong các trường đại học hàng đầu của Hoa Kỳ và là ngôn ngữ phổ biến nhất để học khoa học máy tính.

Xu hướng này cũng đúng trong ngành công nghiệp phần mềm. Python hiện nằm trong năm ngôn ngữ hàng đầu trong chỉ mục TIOBE ( [http://www.tiobe.com/tiobe-index/](http://www.tiobe.com/tiobe-index/) ) và nó có lẽ còn lớn hơn trong lĩnh vực phát triển web, vì các ngôn ngữ như C hiếm khi được sử dụng làm ngôn ngữ chính để xây dựng các ứng dụng web.

#### Ghi chú

Cuốn sách này đưa ra giả định rằng bạn đã quen thuộc với ngôn ngữ lập trình Python. Nếu bạn không phải là một nhà phát triển Python có kinh nghiệm, bạn có thể đọc cuốn sách _Expert Python Programming, Second Edition_ , nơi bạn sẽ học các kỹ năng lập trình nâng cao bằng Python.

Tuy nhiên, một số nhà phát triển chỉ trích Python là chậm và không thích hợp để xây dựng các dịch vụ web hiệu quả. Python chậm, và điều này là không thể phủ nhận. Nhưng nó vẫn là một ngôn ngữ được lựa chọn để xây dựng các dịch vụ nhỏ và nhiều công ty lớn đang hài lòng sử dụng nó.

Phần này sẽ cung cấp cho bạn một số thông tin cơ bản về các cách khác nhau mà bạn có thể viết microservices bằng Python, một số thông tin chi tiết về lập trình không đồng bộ so với lập trình đồng bộ và kết luận với một số chi tiết về hiệu suất Python.

Phần này bao gồm năm phần:

*   Tiêu chuẩn WSGI
*   Greenlet và Gevent
*   Xoắn và Lốc xoáy
*   asyncio
*   Biểu diễn ngôn ngữ

### Tiêu chuẩn WSGI

Điều gây ấn tượng với hầu hết các nhà phát triển web bắt đầu với Python là việc thiết lập và chạy một ứng dụng web dễ dàng như thế nào.

Cộng đồng web Python đã tạo ra một tiêu chuẩn (lấy cảm hứng từ **Giao diện cổng chung** hoặc **CGI** ) được gọi là **Giao diện cổng máy chủ web** ( **WSGI** ). Nó đơn giản hóa rất nhiều cách bạn có thể viết một ứng dụng Python để phục vụ các yêu cầu HTTP.

Khi mã của bạn sử dụng tiêu chuẩn đó, dự án của bạn có thể được thực thi bởi các máy chủ web tiêu chuẩn như **Apache** hoặc **ng** **inx** , sử dụng các phần mở rộng WSGI như uwsgihoặc mod\_wsgi.

Ứng dụng của bạn chỉ phải xử lý các yêu cầu đến và gửi lại phản hồi JSON và Python bao gồm tất cả những điều tốt đẹp đó trong thư viện chuẩn của nó.

Bạn có thể tạo một microservice đầy đủ chức năng trả về thời gian cục bộ của máy chủ bằng mô-đun Python vani có ít hơn 10 dòng. Nó được đưa ra như sau:

    import jsonimport time def application(environ, start_response):     headers = [('Content-type', 'application/json')]     start_response('200 OK', headers)     return [bytes(json.dumps({'time': time.time()}), 'utf8')]

Kể từ khi được giới thiệu, giao thức WSGI đã trở thành một tiêu chuẩn thiết yếu và cộng đồng web Python đã áp dụng rộng rãi nó. Các nhà phát triển đã viết phần mềm trung gian, là các chức năng mà bạn có thể kết nối trước hoặc sau chức năng ứng dụng WSGI, để thực hiện điều gì đó trong môi trường.

Một số khuôn khổ web, như **Bottle** ( [http://bottlepy.org](http://bottlepy.org) ), đã được tạo riêng theo tiêu chuẩn đó, và sớm thôi, mọi khuôn khổ ngoài kia có thể được sử dụng thông qua WSGI theo cách này hay cách khác.

Tuy nhiên, vấn đề lớn nhất với WSGI là bản chất đồng bộ của nó. Hàm ứng dụng bạn thấy trong mã trước được gọi chính xác một lần cho mỗi yêu cầu đến và khi hàm trả về, nó phải gửi lại phản hồi. Điều đó có nghĩa là mỗi khi bạn gọi hàm, nó sẽ chặn cho đến khi phản hồi sẵn sàng.

Và việc viết microservices có nghĩa là mã của bạn sẽ luôn phải đợi phản hồi từ các tài nguyên mạng khác nhau. Nói cách khác, ứng dụng của bạn sẽ không hoạt động và chỉ cần chặn máy khách cho đến khi mọi thứ sẵn sàng.

Đó là một hành vi hoàn toàn ổn đối với các API HTTP. Chúng tôi không nói về việc xây dựng các ứng dụng hai chiều như các ứng dụng dựa trên ổ cắm web. Nhưng điều gì sẽ xảy ra khi bạn có nhiều yêu cầu gọi đến ứng dụng của bạn cùng một lúc?

Máy chủ WSGI sẽ cho phép bạn chạy một nhóm các luồng để phục vụ một số yêu cầu đồng thời. Nhưng bạn không thể chạy hàng nghìn cái trong số chúng và ngay sau khi pool cạn kiệt, yêu cầu tiếp theo sẽ chặn quyền truy cập của khách hàng ngay cả khi microservice của bạn không làm gì ngoài việc chạy không tải và chờ phản hồi của các dịch vụ phụ trợ.

Đó là một trong những lý do tại sao các khung công tác không phải WSGI như **Twisted và** **Tornado,** và trong vùng đất JavaScript, **Node.js,** trở nên rất thành công - nó hoàn toàn không đồng bộ.

Khi mã hóa ứng dụng Twisted, bạn có thể sử dụng lệnh gọi lại để tạm dừng và tiếp tục công việc đã thực hiện để tạo phản hồi. Điều đó có nghĩa là bạn có thể chấp nhận các yêu cầu mới và bắt đầu xử lý chúng. Mô hình đó làm giảm đáng kể thời gian chạy không tải trong quá trình của bạn. Nó có thể phục vụ hàng nghìn yêu cầu đồng thời. Tất nhiên, điều đó không có nghĩa là ứng dụng sẽ trả về từng phản hồi đơn lẻ nhanh hơn. Nó chỉ có nghĩa là một quy trình có thể chấp nhận nhiều yêu cầu đồng thời hơn và tung hứng giữa chúng khi dữ liệu sẵn sàng được gửi lại.

Không có cách nào đơn giản với tiêu chuẩn WSGI để giới thiệu một thứ gì đó tương tự, và cộng đồng đã tranh luận trong nhiều năm để đi đến sự đồng thuận - và đã thất bại. Tỷ lệ cược là cuối cùng cộng đồng sẽ bỏ tiêu chuẩn WSGI cho một thứ khác.

Trong thời gian chờ đợi, việc xây dựng các microservices với các khuôn khổ đồng bộ vẫn có thể thực hiện được và hoàn toàn ổn nếu việc triển khai của bạn có tính đến giới hạn _một yêu cầu == một luồng_ của tiêu chuẩn WSGI.

Tuy nhiên, có một mẹo để thúc đẩy các ứng dụng web đồng bộ **\-** Greenlet, được giải thích trong phần sau.

### Greenlet và Gevent

Nguyên tắc chung của lập trình không đồng bộ là quá trình xử lý một số bối cảnh thực thi đồng thời để mô phỏng song song.

Các ứng dụng không đồng bộ sử dụng vòng lặp sự kiện tạm dừng và tiếp tục các ngữ cảnh thực thi khi một sự kiện được kích hoạt - chỉ một ngữ cảnh hoạt động và chúng thay phiên nhau. Chỉ dẫn rõ ràng trong mã sẽ cho vòng lặp sự kiện biết rằng đây là nơi nó có thể tạm dừng việc thực thi.

Khi điều đó xảy ra, quy trình sẽ tìm kiếm một số công việc đang chờ xử lý khác để tiếp tục. Cuối cùng, quá trình sẽ quay trở lại chức năng của bạn và tiếp tục nó ở nơi nó đã dừng. Chuyển từ một ngữ cảnh thực thi sang một ngữ cảnh khác được gọi là **chuyển mạch** .

Các **Greenlet** dự án ( [https://github.com/python-greenlet/greenlet](https://github.com/python-greenlet/greenlet) ) là một gói phần mềm dựa trên **Stackless** dự án, một CPython thực hiện cụ thể, và cung cấp _greenlets_ .

Greenlet là các tiểu trình _giả_ rất rẻ để khởi tạo, không giống như các tiểu trình thực và có thể được sử dụng để gọi các hàm Python. Trong các chức năng đó, bạn có thể _chuyển đổi_ và trao lại quyền điều khiển cho một chức năng khác. Việc chuyển đổi được thực hiện với một vòng lặp sự kiện và cho phép bạn viết một ứng dụng không đồng bộ bằng cách sử dụng mô hình giao diện giống như luồng.

Đây là một ví dụ từ tài liệu Greenlet:

    from greenlet import greenletdef test1(x, y):    z = gr2.switch(x+y)    print(z)def test2(u):     print (u)     gr1.switch(42) gr1 = greenlet(test1) gr2 = greenlet(test2) gr1.switch("hello", " world")

Hai greenlet trong ví dụ trước chuyển đổi rõ ràng từ cái này sang cái kia.

Để xây dựng các dịch vụ vi mô dựa trên tiêu chuẩn WSGI, nếu mã cơ bản sử dụng greenlet, chúng tôi có thể chấp nhận một số yêu cầu đồng thời và chỉ chuyển từ yêu cầu này sang yêu cầu khác khi chúng tôi biết một cuộc gọi sẽ chặn yêu cầu - như yêu cầu I / O.

Tuy nhiên, việc chuyển từ một greenlet này sang một greenlet khác phải được thực hiện một cách rõ ràng và mã kết quả có thể nhanh chóng trở nên lộn xộn và khó hiểu. Đó là nơi Gevent có thể trở nên rất hữu ích.

Các **Gevent** dự án ( [http://www.gevent.org/](http://www.gevent.org/) ) được xây dựng trên đầu trang của Greenlet, và cung cấp một cách ngầm và tự động chuyển đổi giữa greenlets, trong số rất nhiều những thứ khác.

Nó cung cấp một phiên bản hợp tác của mô-đun _socket_ , sử dụng greenlets để tự động tạm dừng và tiếp tục thực thi khi một số dữ liệu có sẵn trong socket. Thậm chí còn có một tính năng _vá khỉ_ , tự động thay thế ổ cắm thư viện tiêu chuẩn bằng phiên bản của Gevent. Điều đó làm cho mã đồng bộ tiêu chuẩn của bạn không đồng bộ một cách kỳ diệu mỗi khi nó sử dụng các ổ cắm - chỉ với một dòng bổ sung:

    from gevent import monkey; monkey.patch_all()     def application(environ, start_response):     headers = [('Content-type', 'application/json')]     start_response('200 OK', headers)     # ...do something with sockets here...     return result

Ma thuật tiềm ẩn này có một cái giá phải trả. Để Gevent hoạt động tốt, tất cả mã bên dưới cần phải tương thích với bản vá mà Gevent thực hiện. Một số gói từ cộng đồng sẽ tiếp tục chặn hoặc thậm chí có kết quả không mong muốn vì điều này - đặc biệt, nếu chúng sử dụng phần mở rộng C và bỏ qua một số tính năng của thư viện chuẩn Gevent đã được vá.

Nhưng nó hoạt động tốt cho hầu hết các trường hợp. Các dự án hoạt động tốt với Gevent được gọi là _xanh_ và khi một thư viện hoạt động không tốt và cộng đồng yêu cầu tác giả của nó _làm cho nó xanh_ , điều đó thường xảy ra.

Chẳng hạn, đó là thứ được sử dụng để mở rộng dịch vụ Firefox Sync tại Mozilla.

### Xoắn và Lốc xoáy

Nếu bạn đang xây dựng các microservices trong đó việc tăng số lượng yêu cầu đồng thời mà bạn có thể giữ là quan trọng, bạn nên bỏ tiêu chuẩn WSGI và chỉ sử dụng một khuôn khổ không đồng bộ như **Tornado** ( [http://www.tornadoweb.org/](http://www.tornadoweb.org/) ) hoặc **Twisted** ( [https : //twistedmatrix.com/trac/](https://twistedmatrix.com/trac/) ).

Twisted đã có từ lâu. Để triển khai cùng một microservices, bạn cần viết một đoạn mã dài dòng hơn một chút như sau:

    import time  import jsonfrom twisted.web import server, resource from twisted.internet import reactor, endpoints class Simple(resource.Resource):     isLeaf = True     def render_GET(self, request):         request.responseHeaders.addRawHeader(b"content-type",                                                 b"application/json")         return bytes(json.dumps({'time': time.time()}), 'utf8')     site = server.Site(Simple())     endpoint = endpoints.TCP4ServerEndpoint(reactor, 8080)     endpoint.listen(site)     reactor.run()

Mặc dù Twisted là một khuôn khổ cực kỳ mạnh mẽ và hiệu quả, nhưng nó gặp phải một số vấn đề khi xây dựng các dịch vụ vi mô HTTP, như sau:

*   Bạn cần triển khai mỗi điểm cuối trong microservice của mình với một lớp dẫn xuất từ ​​một Resourcelớp và triển khai từng phương thức được hỗ trợ. Đối với một số API đơn giản, nó bổ sung rất nhiều mã soạn sẵn.
*   Mã xoắn có thể khó hiểu và khó gỡ lỗi do tính chất không đồng bộ của nó.
*   Thật dễ dàng rơi vào **địa ngục gọi lại** khi bạn chuỗi quá nhiều chức năng được kích hoạt liên tiếp lần lượt - và mã có thể trở nên lộn xộn.
*   Việc kiểm tra đúng ứng dụng Twisted của bạn rất khó và bạn phải sử dụng mô hình kiểm tra đơn vị cụ thể cho Twisted.

Tornado dựa trên một mô hình tương tự, nhưng hoạt động tốt hơn ở một số khu vực. Nó có một hệ thống định tuyến nhẹ hơn và làm mọi thứ có thể để làm cho mã gần với Python thuần túy. Tornado cũng sử dụng mô hình gọi lại, vì vậy việc gỡ lỗi có thể khó khăn.

Nhưng cả hai khung công tác đang làm việc chăm chỉ để thu hẹp khoảng cách để dựa vào các tính năng không đồng bộ mới được giới thiệu trong Python 3.

### asyncio

Khi Guido van Rossum bắt đầu làm việc để thêm các tính năng không đồng bộ trong Python 3, một phần của cộng đồng đã thúc đẩy một giải pháp giống như Gevent, bởi vì nó có ý nghĩa rất nhiều khi viết các ứng dụng theo cách đồng bộ, tuần tự thay vì phải thêm các lệnh gọi lại rõ ràng như trong Tornado hoặc Twisted.

Nhưng Guido đã chọn kỹ thuật rõ ràng và thử nghiệm trong một dự án mang tên **Tulip** lấy cảm hứng từ Twisted. Cuối cùng, mô-đun **asyncio** được sinh ra từ dự án phụ đó và được thêm vào Python.

Nhìn lại, triển khai cơ chế vòng lặp sự kiện rõ ràng bằng Python thay vì theo cách Gevent có rất nhiều ý nghĩa. Cách các nhà phát triển cốt lõi Python mã hóa asyncio và cách họ mở rộng ngôn ngữ một cách trang nhã với các từ khóa asyncvà awaitđể triển khai các coroutines, khiến các ứng dụng không đồng bộ được xây dựng bằng mã vanilla Python 3.5+ trông rất thanh lịch và gần với lập trình đồng bộ.

#### Ghi chú

Coroutines là các chức năng có thể tạm ngừng và tiếp tục thực hiện chúng. Chương 12, _Tiếp theo là gì?_ , giải thích chi tiết cách chúng được triển khai bằng Python và cách sử dụng chúng.

Bằng cách này, Python đã thực hiện một công việc tuyệt vời trong việc tránh tình trạng lộn xộn cú pháp gọi lại mà chúng ta đôi khi thấy trong các ứng dụng Node.js hoặc Twisted (Python 2).

Và ngoài coroutines, Python 3 đã giới thiệu một tập hợp đầy đủ các tính năng và trình trợ giúp trong gói asyncio để xây dựng các ứng dụng không đồng bộ, hãy tham khảo [https://docs.python.org/3/library/asyncio.html](https://docs.python.org/3/library/asyncio.html) .

Python hiện có khả năng biểu đạt cao như các ngôn ngữ như **Lua** để tạo các ứng dụng dựa trên quy trình đăng ký và hiện có một số khung công tác mới nổi áp dụng các tính năng đó và sẽ chỉ hoạt động với Python 3.5+ để được hưởng lợi từ điều này.

**Aiohttp** của **KeepSafe** ( [http://aiohttp.readthedocs.io](http://aiohttp.readthedocs.io) ) là một trong số đó và việc xây dựng cùng một microservice, hoàn toàn không đồng bộ, với nó sẽ đơn giản chỉ cần vài dòng thanh lịch sau:

    from aiohttp import web  import time async def handle(request):     return web.json_response({'time': time.time()}) if __name__ == '__main__':     app = web.Application()     app.router.add_get('/', handle)     web.run_app(app)

Trong ví dụ nhỏ này, chúng ta đang tiến rất gần đến cách chúng ta sẽ triển khai một ứng dụng đồng bộ. Gợi ý duy nhất mà chúng tôi đang sử dụng asynclà asynctừ khóa, đánh dấu hàm xử lý là một quy trình.

Và đó là những gì sẽ được sử dụng ở mọi cấp độ của một ứng dụng Python không đồng bộ trong tương lai. Đây là một ví dụ khác sử dụng aiopg, thư viện PostgreSQL cho asyncio từ tài liệu dự án:

    import asyncio import aiopg dsn = 'dbname=aiopg user=aiopg password=passwd host=127.0.0.1' async def go():     pool = await aiopg.create_pool(dsn)     async with pool.acquire() as conn:         async with conn.cursor() as cur:             await cur.execute("SELECT 1")             ret = []             async for row in cur:                 ret.append(row)             assert ret == [(1,)] loop = asyncio.get_event_loop() loop.run_until_complete(go())

Với một vài asyncvà awaittiền tố, hàm thực hiện truy vấn SQL và gửi lại kết quả trông rất giống một hàm đồng bộ.

Nhưng các khung và thư viện không đồng bộ dựa trên Python 3 vẫn đang nổi lên và nếu bạn đang sử dụng asyncio hoặc một khung như aiohttp, bạn sẽ cần phải tuân theo các triển khai không đồng bộ cụ thể cho từng tính năng bạn cần.

Nếu bạn cần sử dụng một thư viện không đồng bộ trong mã của mình, để sử dụng nó từ mã không đồng bộ của bạn có nghĩa là bạn sẽ cần phải thực hiện một số công việc bổ sung và đầy thử thách nếu bạn muốn ngăn chặn vòng lặp sự kiện.

Nếu các dịch vụ vi mô của bạn xử lý với một số tài nguyên hạn chế, nó có thể quản lý được. Nhưng có lẽ sẽ an toàn hơn vào thời điểm viết bài này là gắn bó với một khuôn khổ đồng bộ đã tồn tại được một thời gian hơn là một khuôn khổ không đồng bộ. Hãy tận hưởng hệ sinh thái hiện có của các gói trưởng thành và đợi cho đến khi hệ sinh thái asyncio trở nên tinh vi hơn.

Và có rất nhiều khuôn khổ đồng bộ tuyệt vời để xây dựng microservices với Python, như **Chai** , **Kim tự tháp** với **Cornice** hoặc **Flask** .

#### Ghi chú

Có nhiều khả năng ấn bản thứ hai của cuốn sách này sẽ sử dụng một khuôn khổ không đồng bộ. Nhưng đối với ấn bản này, chúng tôi sẽ sử dụng khung Flask trong suốt cuốn sách. Nó đã được khoảng một thời gian, và rất khỏe mạnh và trưởng thành. Tuy nhiên, hãy nhớ rằng bất kỳ khuôn khổ web Python nào bạn sử dụng, bạn sẽ có thể chuyển đổi tất cả các ví dụ trong cuốn sách này. Điều này là do hầu hết các mã liên quan khi xây dựng microservices đều rất gần với Python thuần túy và khung công tác chủ yếu là để định tuyến các yêu cầu và cung cấp một vài trình trợ giúp.

### Biểu diễn ngôn ngữ

Trong các phần trước, chúng ta đã xem qua hai cách khác nhau để viết microservices: không đồng bộ so với đồng bộ và bất kỳ kỹ thuật nào bạn sử dụng, tốc độ của Python ảnh hưởng trực tiếp đến hiệu suất của microservice của bạn.

Tất nhiên, mọi người đều biết Python chậm hơn Java hoặc Go, nhưng tốc độ thực thi không phải lúc nào cũng được ưu tiên hàng đầu. Một microservice thường là một lớp mã mỏng nằm trong phần lớn vòng đời của nó để chờ một số phản hồi mạng từ các dịch vụ khác. Tốc độ cốt lõi của nó thường ít quan trọng hơn tốc độ truy vấn SQL của bạn sẽ mất để trả về từ máy chủ Postgres của bạn, vì tốc độ sau sẽ đại diện cho phần lớn thời gian dành để xây dựng phản hồi.

Nhưng mong muốn một ứng dụng càng nhanh càng tốt là điều hợp pháp.

Một chủ đề gây tranh cãi trong cộng đồng Python xung quanh việc tăng tốc ngôn ngữ là cách mutex **Global Interpreter Lock** ( **GIL** ) có thể làm hỏng hiệu suất, vì các ứng dụng đa luồng không thể sử dụng một số quy trình.

GIL có lý do chính đáng để tồn tại. Nó bảo vệ các phần không an toàn theo luồng của trình thông dịch CPython và tồn tại trong các ngôn ngữ khác như Ruby. Và tất cả các nỗ lực để loại bỏ nó cho đến nay đều không mang lại hiệu quả triển khai CPython nhanh hơn.

#### Ghi chú

Larry Hasting đang thực hiện một dự án CPython không có GIL có tên là **Gilectomy** ( [https://github.com/larryhastings/gilectomy](https://github.com/larryhastings/gilectomy) ). Mục tiêu tối thiểu của nó là đưa ra triển khai không có GIL, có thể chạy một ứng dụng đơn luồng nhanh như CPython. Tính đến thời điểm viết bài này, việc triển khai này vẫn còn chậm hơn CPython đó. Nhưng thật thú vị khi theo dõi công việc này và xem liệu một ngày nào đó nó có đạt tốc độ ngang bằng hay không. Điều đó sẽ làm cho một cuộc thi CPython không có GIL rất hấp dẫn.

Đối với microservices, bên cạnh việc ngăn chặn việc sử dụng nhiều lõi trong cùng một quá trình, GIL sẽ làm giảm nhẹ hiệu suất khi tải cao do hệ thống gọi chi phí do mutex đưa vào.

Tuy nhiên, tất cả các nghiên cứu kỹ lưỡng xung quanh GIL đều có lợi: trong những năm qua đã có nhiều công việc được thực hiện để giảm bớt sự tranh chấp GIL trong trình thông dịch và trong một số lĩnh vực, hiệu suất của Python đã được cải thiện rất nhiều.

Hãy nhớ rằng ngay cả khi nhóm cốt lõi loại bỏ GIL, Python vẫn là ngôn ngữ được thông dịch và thu thập rác và phải chịu các hình phạt về hiệu suất cho các thuộc tính đó.

Python cung cấp dismô-đun nếu bạn quan tâm để xem cách trình thông dịch phân rã một hàm. Trong ví dụ sau, trình thông dịch sẽ phân rã một hàm đơn giản tạo ra các giá trị tăng dần từ một chuỗi trong không ít hơn 29 bước:

    >>> def myfunc(data): ...     for value in data: ...         yield value + 1 ... >>> import dis >>> dis.dis(myfunc)     2           0 SETUP_LOOP              23 (to 26)                 3 LOAD_FAST                0 (data)                 6 GET_ITER         >>    7 FOR_ITER                15 (to 25)                 10 STORE_FAST              1 (value)     3         13 LOAD_FAST                 1 (value)             16 LOAD_CONST                1 (1)             19 BINARY_ADD             20 YIELD_VALUE             21 POP_TOP             22 JUMP_ABSOLUTE        7         >>    25 POP_BLOCK         >>    26 LOAD_CONST                0 (None)             29 RETURN_VALUE

Một hàm tương tự được viết bằng ngôn ngữ biên dịch tĩnh sẽ giảm đáng kể số lượng các thao tác cần thiết để tạo ra cùng một kết quả. Tuy nhiên, có nhiều cách để tăng tốc độ thực thi Python.

Một là viết một phần mã của bạn thành mã đã biên dịch bằng cách xây dựng phần mở rộng C hoặc sử dụng phần mở rộng tĩnh của ngôn ngữ như Cython ( [http://cython.org/](http://cython.org/) ), nhưng điều đó làm cho mã của bạn phức tạp hơn.

Một giải pháp khác, hứa hẹn nhất là chạy ứng dụng của bạn đơn giản bằng trình thông dịch **PyPy** ( [http://pypy.org/](http://pypy.org/) ).

PyPy triển khai trình biên dịch **Just-In-Time** ( **JIT** ). Trình biên dịch này trực tiếp thay thế, trong thời gian chạy, các đoạn Python bằng mã máy có thể được sử dụng trực tiếp bởi CPU. Toàn bộ thủ thuật đối với JIT là phát hiện trong thời gian thực, trước khi thực hiện, khi nào và làm như thế nào.

Ngay cả khi PyPy luôn đi sau CPython một vài phiên bản Python, nó đã đạt đến mức bạn có thể sử dụng nó trong sản xuất và hiệu suất của nó có thể khá tuyệt vời. Trong một trong những dự án của chúng tôi tại Mozilla cần thực thi nhanh, phiên bản PyPy gần như nhanh bằng phiên bản Go và chúng tôi đã quyết định sử dụng Python ở đó.

#### Ghi chú

Trang web của speed Pypy là một nơi tuyệt vời để xem PyPy so với CPython ( [http://speed.pypy.org/](http://speed.pypy.org/) ) như thế nào .

Tuy nhiên, nếu chương trình của bạn sử dụng phần mở rộng C, bạn sẽ cần phải biên dịch lại chúng cho PyPy và đó có thể là một vấn đề. Đặc biệt, nếu các nhà phát triển khác duy trì một số tiện ích mở rộng mà bạn đang sử dụng.

Nhưng nếu bạn xây dựng microservice của mình với một bộ thư viện tiêu chuẩn, rất có thể nó sẽ hoạt động hiệu quả với trình thông dịch PyPy, vì vậy điều đó đáng để thử.

Trong mọi trường hợp, đối với hầu hết các dự án, lợi ích của Python và hệ sinh thái của nó phần lớn vượt qua các vấn đề về hiệu suất được mô tả trong phần này, bởi vì chi phí trong một microservice hiếm khi là một vấn đề. Và nếu hiệu suất là một vấn đề, thì phương pháp microservice cho phép bạn viết lại các thành phần quan trọng về hiệu suất mà không ảnh hưởng đến phần còn lại của hệ thống.

Tóm lược
--------

Trong chương này, chúng tôi đã so sánh cách tiếp cận nguyên khối so với microservice để xây dựng các ứng dụng web và rõ ràng đó không phải là một thế giới nhị phân, nơi bạn phải chọn một mô hình vào ngày đầu tiên và gắn bó với nó.

Bạn sẽ thấy microservices là sự cải tiến của một ứng dụng bắt đầu cuộc sống của nó như một khối nguyên khối. Khi dự án trưởng thành, các phần của logic dịch vụ sẽ chuyển sang các microservices. Đó là một cách tiếp cận hữu ích như chúng ta đã học trong chương này, nhưng nó nên được thực hiện cẩn thận để tránh rơi vào một số bẫy phổ biến.

Một bài học quan trọng khác là Python được coi là một trong những ngôn ngữ tốt nhất để viết các ứng dụng web và do đó, microservices - vì những lý do tương tự, nó là ngôn ngữ được lựa chọn trong các lĩnh vực khác và cũng vì nó cung cấp rất nhiều khung công tác trưởng thành và gói để thực hiện công việc.

Chúng tôi đã nhanh chóng xem qua chương ở một số khuôn khổ, cả đồng bộ và không đồng bộ, và đối với phần còn lại của cuốn sách, chúng tôi sẽ sử dụng Flask.

Chương tiếp theo sẽ giới thiệu về framework tuyệt vời này, và nếu bạn chưa quen với nó, có thể bạn sẽ thích nó.

Cuối cùng, Python là một ngôn ngữ chậm và đó có thể là một vấn đề trong những trường hợp rất cụ thể. Nhưng biết điều gì làm cho nó chậm và các giải pháp khác nhau để tránh vấn đề này thường sẽ đủ để làm cho vấn đề đó không liên quan.