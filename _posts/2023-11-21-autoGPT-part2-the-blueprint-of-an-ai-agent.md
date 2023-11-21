---
layout: single
title:  "AutoGPT Forge: Bản thiết kế của một đặc vụ AI"
desc: ""
keywords: "autoGPT"
categories: [AI]
tag: [AI]
---

AutoGPT Forge: Bản thiết kế của một đặc vụ AI
=====================================================

![](https://miro.medium.com/v2/resize:fit:700/1*6Iufk9iMhAUfxibQaSE8zg.png)

Xin chào các bạn tiên phong của biên giới AI!

Nếu bạn đã đến đây, rất có thể bạn đã bị lỗi AI cắn, mong muốn khai thác sức mạnh đáng kinh ngạc của Mô hình ngôn ngữ lớn (LLM) để xây dựng các tác nhân thông minh của riêng bạn, thường được gọi là AutoGPT. Bạn có nhớ cảm giác hồi hộp khi chúng ta thiết lập dự án đầu tiên trong phần hướng dẫn ban đầu không? Thôi, thắt dây an toàn nhé, vì mọi thứ sắp trở nên thú vị hơn rồi!

Trong hướng dẫn này — [phần tiếp theo của cuộc phiêu lưu AI của chúng ta](/2023-11-20-autoGPT-part1-a-comprehensive-guide.md) — chúng ta sẽ bắt đầu cuộc hành trình vào chính trái tim của một đặc vụ AI. Hãy tưởng tượng bóc từng lớp củ hành, nhưng thay vì nước mắt, lại có vô số kiến ​​thức chờ đợi ở mỗi lớp. Chúng ta sẽ khám phá mạng lưới các thành phần phức tạp giúp các tác nhân này được đánh dấu, tham gia chuyến tham quan có hướng dẫn về cấu trúc dự án của AutoGPT Forge đáng kính và vâng, hãy quay trở lại các rãnh mã hóa để nâng cao chức năng từng bước.

Vào thời điểm chúng tôi kết thúc, bạn sẽ không chỉ có một đại lý do LLM hỗ trợ đang hoạt động; bạn sẽ có một chiếc vượt qua bài kiểm tra “ghi tệp” cần thiết, một minh chứng cho năng lực ngày càng tăng của bạn trong thế giới phát triển AI.

Vì vậy, các nhà phát triển đại lý đồng nghiệp của tôi, các bạn đã sẵn sàng bước vào thế giới nơi mã gặp gỡ nhận thức chưa? Hãy để cuộc thám hiểm bắt đầu!

Đại lý AI dựa trên LLM là gì?
=============================

Mô hình ngôn ngữ lớn (LLM) là mô hình học máy tiên tiến khai thác lượng kiến ​​thức web khổng lồ. Nhưng điều gì sẽ xảy ra khi bạn kết hợp các LLM này với các tác nhân tự trị? Bạn nhận được các tác nhân AI dựa trên LLM - một loại trí tuệ nhân tạo mới hứa hẹn đưa ra quyết định giống con người hơn.

Các tác nhân tự trị truyền thống hoạt động với kiến ​​thức hạn chế, thường bị giới hạn trong các nhiệm vụ hoặc môi trường cụ thể. Chúng giống như những chiếc máy tính - hiệu quả nhưng bị giới hạn ở những chức năng được xác định trước. Mặt khác, các đại lý dựa trên LLM giống như có một bộ bách khoa toàn thư kết hợp với một máy tính. Họ không chỉ tính toán; họ hiểu, suy luận và sau đó hành động dựa trên nguồn thông tin khổng lồ.

![](https://miro.medium.com/v2/resize:fit:700/1*kiwCmVv6bIWrkKUq0AwvSg.png)

AI trực quan hóa các nhà nghiên cứu AI đang làm việc chăm chỉ

Khảo [sát Cảnh quan Đặc vụ](https://arxiv.org/abs/2308.11432) nhấn mạnh sự phát triển này, trình bày chi tiết về tiềm năng đáng chú ý của LLM trong việc đạt được trí thông minh giống con người. Chúng không chỉ có nhiều dữ liệu hơn; chúng thể hiện một cách tiếp cận toàn diện hơn đối với AI, thu hẹp khoảng cách giữa kiến ​​thức nhiệm vụ riêng biệt và thông tin web mở rộng.

Mở rộng hơn nữa về vấn đề này, [Sự trỗi dậy và tiềm năng của các tác nhân dựa trên mô hình ngôn ngữ lớn: Một khảo sát](https://arxiv.org/abs/2309.07864) mô tả LLM là nền tảng cho thế hệ tác nhân AI tiếp theo. Các tác nhân này cảm nhận, quyết định và hành động, tất cả đều được hỗ trợ bởi kiến ​​thức toàn diện và khả năng thích ứng của LLM. Đây là một nguồn kiến ​​thức đáng kinh ngạc về Nghiên cứu tác nhân AI với gần 700 bài báo được tham khảo và sắp xếp theo lĩnh vực nghiên cứu.

Cấu trúc của một tác nhân AI dựa trên LLM
=========================================

Đi sâu vào cốt lõi của tác nhân AI dựa trên LLM, chúng tôi thấy nó có cấu trúc giống con người, với các thành phần riêng biệt như tính cách, trí nhớ, quá trình suy nghĩ và khả năng. Hãy chia nhỏ những điều này:

![](https://miro.medium.com/v2/resize:fit:700/1*9fDToDTOEc3tzMSDIJ-Tng.png)

Giải phẫu của một đặc vụ từ [Khảo sát bối cảnh đặc vụ](https://arxiv.org/abs/2308.11432)

1\. Hồ sơ
---------

Khi con người chúng ta tập trung vào nhiều nhiệm vụ khác nhau, chúng ta sẽ tạo điều kiện cho bản thân thực hiện những nhiệm vụ đó. Cho dù chúng ta đang viết, thái rau, lái xe hay chơi thể thao, chúng ta đều tập trung và thậm chí áp dụng những lối suy nghĩ khác nhau. Khả năng thích ứng này là điều mà khái niệm _hồ sơ_ ám chỉ khi thảo luận về các tác nhân. Nghiên cứu đã [chỉ ra](https://arxiv.org/abs/2305.14688) rằng chỉ cần thông báo cho đại lý rằng họ là chuyên gia trong một nhiệm vụ cụ thể có thể nâng cao hiệu suất của nó.

Mô-đun định hình có các ứng dụng tiềm năng ngoài kỹ thuật nhanh chóng. Nó có thể được sử dụng để điều chỉnh các chức năng bộ nhớ của tác nhân, các hành động có sẵn hoặc thậm chí mô hình ngôn ngữ lớn (LLM) cơ bản điều khiển tác nhân.

2\. Trí nhớ
-----------

Đối với một tác nhân, bộ nhớ không chỉ là nơi lưu trữ — nó là nền tảng về nhận dạng, khả năng và nền tảng để nó học hỏi. Giống như ký ức của chúng ta thông báo về các quyết định, phản ứng và thậm chí cả tính cách của chúng ta, ký ức của tác nhân đóng vai trò là bản ghi tích lũy về các tương tác, học hỏi và phản hồi trong quá khứ. Hai loại ký ức chính hình thành nên nhận thức của một tác nhân: dài hạn và ngắn hạn.

Trí **nhớ dài hạn** giống như kiến ​​thức nền tảng của tác nhân, một kho lưu trữ khổng lồ bao gồm dữ liệu và các tương tác kéo dài trong thời gian dài. Đó là kho lưu trữ lịch sử của tác nhân, hướng dẫn các hành vi và hiểu biết cốt lõi của tác nhân.

Mặt khác, **Trí nhớ Ngắn hạn (hoặc Đang hoạt động)** tập trung vào những ký ức tức thời, xử lý những ký ức thoáng qua giống như hồi ức của chúng ta về các sự kiện gần đây. Mặc dù cần thiết cho các nhiệm vụ thời gian thực, nhưng không phải tất cả ký ức ngắn hạn đều được lưu trữ lâu dài của tác nhân.

Một khái niệm mới nổi trong lĩnh vực này là Phản ánh ký ức. Ở đây, tác nhân không chỉ lưu trữ ký ức mà còn tích cực xem lại chúng. Sự xem xét nội tâm này cho phép tác nhân đánh giá lại, ưu tiên hoặc thậm chí loại bỏ thông tin, giống như việc con người hồi tưởng và học hỏi từ kinh nghiệm trong quá khứ.

3\. Lập kế hoạch
----------------

Lập kế hoạch là lộ trình giải quyết vấn đề của tác nhân. Khi đối mặt với một thách thức phức tạp, theo bản năng, con người chia nó thành các nhiệm vụ vừa phải, dễ quản lý — một chiến lược được phản ánh trong các tác nhân dựa trên LLM. Cách tiếp cận có phương pháp này cho phép các nhân viên giải quyết vấn đề bằng tư duy có cấu trúc, đảm bảo các giải pháp toàn diện và có hệ thống.

Có hai chiến lược nổi trội trong bộ công cụ lập kế hoạch của đại lý. Đầu tiên, Lập kế hoạch có phản hồi, là một cách tiếp cận thích ứng. Ở đây, tác nhân tinh chỉnh chiến lược của mình dựa trên kết quả, giống như lặp lại qua các phiên bản của thiết kế dựa trên phản hồi của người dùng.

Thứ hai, Lập kế hoạch không có phản hồi, coi tác nhân như một nhà chiến lược, chỉ dựa vào kiến ​​thức và tầm nhìn xa có sẵn của nó. Đó là một trò chơi cờ vua, trong đó người đại diện dự đoán trước các thử thách và chuẩn bị trước một số nước đi.

4\. Hành động
-------------

Sau khi xem xét nội tâm của trí nhớ và lập chiến lược lập kế hoạch, sẽ đến phần cuối cùng: Hành động. Đây là nơi các quá trình nhận thức của tác nhân biểu hiện thành các kết quả hữu hình bằng cách sử dụng **Khả năng** của tác nhân . Mọi quyết định, mọi suy nghĩ đều đạt đến đỉnh điểm trong giai đoạn hành động, biến những khái niệm trừu tượng thành những kết quả rõ ràng.

Cho dù đó là viết phản hồi, lưu tệp hay bắt đầu một quy trình mới, thành phần hành động đều là đỉnh cao trong hành trình ra quyết định của tổng đài viên. Đó là cầu nối giữa nhận thức kỹ thuật số và tác động trong thế giới thực, biến các xung điện tử của tác nhân thành các kết quả có ý nghĩa và có mục đích.

Giao thức tác nhân: Ngôn ngữ học của giao tiếp AI
-------------------------------------------------

Sau khi đi sâu vào giải phẫu của một tác nhân, hiểu các thành phần cốt lõi của nó, một câu hỏi quan trọng xuất hiện: Làm thế nào để chúng ta giao tiếp hiệu quả với các tác nhân đa dạng, được thiết kế phức tạp này? Câu trả lời nằm ở [Giao thức đại lý](https://agentprotocol.ai) .

Hiểu giao thức đại lý
---------------------

Về bản chất, Giao thức tác nhân là một giao diện truyền thông được tiêu chuẩn hóa, một “ngôn ngữ” phổ quát mà mọi tác nhân AI, bất kể cấu trúc hoặc thiết kế cơ bản của nó, đều có thể hiểu được. Hãy coi nó như một phái viên ngoại giao đảm bảo các cuộc trò chuyện suôn sẻ giữa các đại lý và nhà phát triển, công cụ của họ hoặc thậm chí các đại lý khác.

Trong một hệ sinh thái nơi mỗi nhà phát triển có thể có cách tiếp cận riêng để tạo ra các tác nhân, Giao thức tác nhân đóng vai trò như một cầu nối thống nhất. Nó giống như một phích cắm được tiêu chuẩn hóa phù hợp với bất kỳ ổ cắm nào hoặc một trình dịch đa năng giải mã vô số ngôn ngữ.

AutoGPT Forge: Tìm hiểu bên trong mẫu đại lý LLM
================================================

Bây giờ chúng ta đã hiểu kiến ​​trúc của một tác nhân, hãy nhìn vào bên trong Forge. Đó là một mẫu được tổ chức tốt, được thiết kế tỉ mỉ để đáp ứng nhu cầu của các nhà phát triển đại lý. Hãy bắt tay vào một chuyến tham quan có hướng dẫn để hiểu nội bộ của nó.

![](https://miro.medium.com/v2/resize:fit:1000/1*-P2uqf9WmafICD3UieLP_Q.png)

Bố cục lò rèn

Cấu trúc dự án của Forge: Một cái nhìn toàn cảnh
------------------------------------------------

Cấu trúc thư mục của Forge có thể được ví như một thư viện được tổ chức tốt, trong đó mọi cuốn sách (tệp hoặc thư mục) đều có vị trí được chỉ định:

*   `agent.py`: Trái tim của Lò rèn, nơi chứa đựng logic của tác nhân.
*   `prompts`: Một kho tàng các mẫu được xác định trước, công cụ hướng dẫn phản hồi của LLM.
*   `sdk`: Mã soạn sẵn và nền tảng nền tảng của Lò rèn.

Hãy xem xét các phần cốt lõi này.

Làm sáng tỏ SDK
---------------

Thư `sdk`mục là trung tâm điều khiển của Forge. Hãy coi nó như phòng máy của một con tàu, chứa các bánh răng và cơ cấu dẫn động toàn bộ con tàu. Đây là những gì nó gói gọn:

*   **Thành phần cốt lõi:** SDK lưu trữ các phần không thể thiếu của Lò rèn, như Bộ nhớ, Khả năng và Lập kế hoạch. Những thành phần này là nền tảng cho nhận thức và hành động của một tác nhân.
*   **Các tuyến giao thức tác nhân:** Trong `routes`thư mục con, bạn sẽ tìm thấy cách triển khai Giao thức tác nhân đã thảo luận trước đó của chúng tôi. Tại đây, giao diện truyền thông tiêu chuẩn được đưa vào cuộc sống.
*   **Cơ sở dữ liệu** ( `db.py`) **:** Ngân hàng bộ nhớ của tác nhân. Đó là nơi lưu trữ kinh nghiệm, bài học và dữ liệu quan trọng khác.
*   **Công cụ nhắc nhở** ( `prompting.py`) **:** Công cụ này sử dụng các mẫu từ `prompts`thư mục để tạo các truy vấn cho LLM, đảm bảo các tương tác nhất quán và phù hợp.
*   **Lớp tác nhân:** Đóng vai trò là cầu nối, kết nối logic của tác nhân với các tuyến Giao thức tác nhân.

Cấu hình và môi trường
----------------------

Cấu hình là chìa khóa để đảm bảo đại lý của chúng tôi hoạt động liền mạch. Tệp `.env.example`cung cấp mẫu để thiết lập các biến môi trường cần thiết. Trước khi đi sâu vào Forge, các nhà phát triển cần sao chép tệp này sang một `.env`tệp mới và điều chỉnh cài đặt:

*   **Khóa API:** `OPENAI_API_KEY` là nơi bạn cắm khóa API OpenAI của mình.
*   **Cấp độ nhật ký:** Với `LOG_LEVEL`, kiểm soát mức độ chi tiết của nhật ký.
*   **Kết nối cơ sở dữ liệu:** `DATABASE_STRING` xác định vị trí và cách thức lưu trữ dữ liệu của tác nhân.
*   **Cổng:** `PORT` chỉ định cổng nghe cho máy chủ của tác nhân.
*   **Workspace:** `AGENT_WORKSPACE` trỏ tới thư mục làm việc của Agent.

Kết thúc: Từ kế hoạch chi tiết đến hiện thực
============================================

Và chúng ta đã có nó — một chuyến đi sâu toàn diện vào thế giới AutoGPT. Chúng tôi đã vượt qua các con đường phức tạp của giải phẫu tác nhân, hiểu cách Giao thức tác nhân phù hợp và xem xét bên trong Lò rèn, hiểu các thành phần và cấu trúc cốt lõi của nó.

Nếu hướng dẫn này là một cuộc hành trình, hãy coi nó như một chuyến đi bộ lên núi. Chúng tôi bắt đầu từ cơ sở, với cái nhìn bao quát về các tác nhân AI dựa trên LLM, hiểu được tầm quan trọng và tiềm năng của chúng. Khi chúng tôi leo lên, con đường dẫn chúng tôi đến phần giải phẫu của các tác nhân này, mổ xẻ cấu trúc và chức năng của chúng. Gần hội nghị thượng đỉnh, chúng tôi đã đi sâu vào Giao thức tác nhân, hiểu được vai trò then chốt của nó trong việc tiêu chuẩn hóa hoạt động giao tiếp. Và cuối cùng, đứng trên đỉnh, chúng tôi đã có cái nhìn toàn cảnh về Lò rèn, quan sát cách bố trí có tổ chức của nó và đánh giá cao sự phức tạp trong thiết kế của nó.

Nhưng hãy nhớ, mỗi đỉnh núi đều là đáy của một cuộc phiêu lưu khác. Sau khi nắm bắt được các khía cạnh lý thuyết, đã đến lúc chuyển từ bản thiết kế sang thực tế. Giờ đây, nền tảng đã được đặt ra, các bước tiếp theo của chúng tôi liên quan đến việc thổi hồn vào những khái niệm này, biến các dòng mã thành tác nhân thông minh, phản hồi nhanh.

Gửi tới tất cả các nhà phát triển đại lý mới chớm nở ngoài kia, hãy chuẩn bị cho [giai đoạn tiếp theo trong chuyến thám hiểm của chúng tôi](/2023-11-22-autoGPT-part3-interacting-with-your-agent.md) — thời gian thực hành! Cho đến lúc đó, hãy giữ cho ngọn lửa AI luôn cháy sáng và không ngừng khám phá.

<div style="text-align: right">Theo <a href="https://aiedge.medium.com/autogpt-forge-the-blueprint-of-an-ai-agent-75cd72ffde6">Craig Swift</a></div>