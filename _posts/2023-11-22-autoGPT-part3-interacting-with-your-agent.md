---
layout: single
title:  "AutoGPT Forge: Tương tác với agent của bạn"
desc: ""
keywords: "autoGPT"
categories: [AI]
tag: [AI]
---

AutoGPT Forge: Tương tác với agent của bạn
=====================================================

![](https://miro.medium.com/v2/resize:fit:700/1*tbaEwa7Usz4V5q7aQp4hbA.png)

Sau khi thực hiện [những bước đầu tiên vào lĩnh vực AutoGPT Forge](/ai/autoGPT-part1-a-comprehensive-guide) và [làm sáng tỏ kế hoạch chi tiết của tác nhân AI,](/ai/autoGPT-part2-the-blueprint-of-an-ai-agent) giờ đây bạn đã sẵn sàng tìm hiểu sâu hơn. Giai đoạn tiếp theo trong hướng dẫn của chúng tôi tập trung vào khía cạnh thực hành của hành trình, nhấn mạnh tính thực tiễn của việc tương tác với tổng đài viên bằng giao diện người dùng.

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn từng bước về cách giao tiếp hiệu quả với tổng đài viên của bạn thông qua giao diện người dùng, đảm bảo rằng bạn không chỉ có thể tạo nhiệm vụ mà còn có thể giám sát và phân tích chúng một cách liền mạch. Hơn nữa, không thể đánh giá thấp tầm quan trọng của điểm chuẩn trong hệ sinh thái AI. Do đó, chúng tôi sẽ hướng dẫn bạn quy trình chạy điểm chuẩn, hiểu hiệu suất của tổng đài viên và giới thiệu cách gửi những điểm số quan trọng nhất đó lên bảng xếp hạng.

Hướng dẫn này được thiết kế để chuyển kiến ​​thức lý thuyết của bạn thành các kỹ năng hữu hình. Cuối cùng, bạn sẽ cảm thấy tự tin khi điều hướng giao diện người dùng AutoGPT Forge, tiến hành đo điểm chuẩn và tham gia cạnh tranh trên bảng xếp hạng.

Vì vậy, với kiến ​​thức nền tảng có được từ các hướng dẫn trước đây của chúng tôi, hãy cùng khám phá sâu hơn và làm chủ thế giới tương tác của AutoGPT Forge. Bắt đầu nào!

Khởi tạo đại lý
===============

Trước khi chúng ta đi sâu vào giao diện người dùng, hãy đảm bảo rằng nhân viên hỗ trợ của bạn đã sẵn sàng và đang chạy.

Trong thiết bị đầu cuối, điều hướng đến thư mục gốc của kho lưu trữ mà bạn đã nhân bản trong hướng dẫn giới thiệu của chúng tôi. Nếu bạn bỏ lỡ bước này hoặc cần xem lại, bạn có thể [làm theo hướng dẫn ban đầu của chúng tôi tại đây](/ai/autoGPT-part1-a-comprehensive-guide) .

Thực hiện lệnh sau để khởi động tác nhân của bạn:

./run đại lý bắt đầu đại lý\_name

Đảm bảo thay thế `agent_name`bằng tên của đại lý cụ thể của bạn.

Truy cập giao diện người dùng AutoGPT
=====================================

![](https://miro.medium.com/v2/resize:fit:1000/1*PeroM3T-_YHR011FmIOTPg.png)

Màn hình đăng nhập AutoGPT

Khi tác nhân của bạn đang chạy, hãy mở trình duyệt web ưa thích của bạn và điều hướng đến Giao diện người dùng AutoGPT, bạn có thể tìm thấy nó tại [http://localhost:8000](http://localhost:8000) . Ảnh chụp màn hình ở trên là những gì bạn sẽ được chào đón — màn hình đăng nhập cho giao diện người dùng AutoGPT.

Để truy cập giao diện người dùng, hãy xác thực bằng tài khoản GitHub hoặc Google của bạn. Những nền tảng này đảm bảo quá trình đăng nhập an toàn.

Màn hình tác vụ
===============

Sau khi xác thực thành công, bạn sẽ được chuyển đến trung tâm chính của giao diện người dùng: màn hình tác vụ.

![](https://miro.medium.com/v2/resize:fit:1000/1*LvKfgROkUgDUhcWwvW3Rvg.png)

Màn hình tác vụ và trang đích sau khi đăng nhập

Thiết kế gợi nhớ đến ChatGPT, cung cấp giao diện giống trò chuyện. Những người quen thuộc với ChatGPT sẽ thấy cách bố trí này trực quan.

Hãy chia nhỏ các thành phần của màn hình này:

**Điều hướng bên** : Ở phía trên bên trái, bạn sẽ thấy ba nút chính:

*   **Nhiệm vụ** : Đây là màn hình hiện tại của bạn, nơi bạn tương tác và giám sát các nhiệm vụ.
*   **Đo điểm chuẩn** : Chuyển sang phần này khi bạn đã sẵn sàng chạy điểm chuẩn cho đại lý của mình.
*   **Cài đặt** : Tại đây, bạn có thể điều chỉnh tùy chọn, quản lý cấu hình tác nhân và tùy chỉnh trải nghiệm giao diện người dùng.

Khu vực màn hình chính được chia thành hai phần:

*   **Danh sách nhiệm vụ** : Ngay bên phải Thanh điều hướng bên, phần này liệt kê tất cả các nhiệm vụ hoặc bộ kiểm tra điểm chuẩn bạn đã chạy. Nó cung cấp cái nhìn ngắn gọn về các tương tác trước đó, giúp việc xem lại hoặc phân tích các nhiệm vụ cụ thể trở nên dễ dàng hơn.
*   **Giao diện tác vụ:** Ở bên phải màn hình, bạn sẽ tìm thấy không gian tương tác chính. Nhập nhiệm vụ, xem phản hồi của nhân viên hoặc giám sát các nhiệm vụ đang diễn ra trong thời gian thực từ bảng này.

Tạo tác vụ với giao diện người dùng AutoGPT Forge
=================================================

Bây giờ bạn đã quen với cách bố trí giao diện người dùng AutoGPT Forge, hãy đi sâu vào quá trình tạo và quản lý tác vụ.

Bắt đầu một nhiệm vụ mới
------------------------

Bắt đầu bằng cách tìm nút **Nhiệm vụ mới** ở đầu phần **Danh sách nhiệm vụ** và nhấp vào nút đó.

Nhập chi tiết nhiệm vụ
----------------------

Sau khi bắt đầu một tác vụ mới, bạn có thể nhập tác vụ mong muốn vào **Giao diện tác vụ** . Đây là nơi bạn sẽ tương tác với đại lý của mình.

![](https://miro.medium.com/v2/resize:fit:1000/1*G9Qo_hwtzefATMWq4oUnaA.png)

Gửi nhiệm vụ cho đại lý
-----------------------

Khi bạn đã nhập nhiệm vụ của mình, bạn sẽ thấy hai nút ở bên phải hộp nhập liệu. Bấm vào **nút đầu tiên** (Gửi) để truyền nhiệm vụ cho đại lý. Hành động này thực thi bước đầu tiên của tác vụ như được minh họa bên dưới:

![](https://miro.medium.com/v2/resize:fit:1000/1*lVImDh9isK66Okt6O8xWoA.png)

Tiếp tục tương tác
------------------

Cuộc đối thoại không kết thúc ở đó! Vui lòng tiếp tục trò chuyện với đại lý của bạn bằng cách nhập thêm tin nhắn và nhấn nút gửi, như được thấy ở đây:

![](https://miro.medium.com/v2/resize:fit:1000/1*8fLtRhG2O0UtW5yjL-xxIQ.png)

Tận dụng chế độ liên tục
------------------------

AutoGPT Forge UI cũng giới thiệu tính năng \*\*Chế độ liên tục\*\*. Bằng cách sử dụng chế độ này, tác nhân có thể thực hiện các bước trong vòng lặp cho đến khi tác vụ đi đến kết thúc.

Tuy nhiên, xin lưu ý: khi bạn nhấp vào \*\*nút thứ hai\*\* trong hộp nhập tác vụ, một thông báo cảnh báo sẽ xuất hiện. Cảnh báo này rất quan trọng vì nó cảnh báo người dùng về khả năng các tác nhân bị mắc kẹt trong các vòng lặp vô tận, đặc biệt nếu các điều kiện nhiệm vụ không rõ ràng.

![](https://miro.medium.com/v2/resize:fit:1000/1*JTrFoBFmYTJz-kk7opJ6qg.png)

Đối với những người không hoàn toàn chắc chắn về hành vi của nhân viên hoặc các chi tiết cụ thể của nhiệm vụ, bạn nên thực hiện từng bước một. Bạn có thể thực hiện việc này bằng cách nhấn liên tục nút gửi và nhập “y” cho đến khi tác vụ hoàn thành.

Đo điểm chuẩn: Đánh giá mức độ thành thạo của đại lý của bạn
============================================================

Đo điểm chuẩn là trọng tâm của quá trình phát triển đại lý. Đó là thước đo để đo lường năng lực và khả năng của đặc vụ. Điểm chuẩn đóng vai trò là những thách thức có cấu trúc, đẩy giới hạn của những gì nhân viên có thể làm. Vượt qua tất cả, và bạn đang nhìn thấy một trong những đặc vụ tổng hợp quyền lực nhất thế giới!

Dưới đây là hướng dẫn từng bước để hiểu và thực thi điểm chuẩn trong giao diện người dùng AutoGPT Forge:

Truy cập trang đo điểm chuẩn
----------------------------

Bắt đầu mọi thứ bằng cách nhấp vào \*\*biểu tượng Cúp\*\* nằm ở bên trái màn hình.

![](https://miro.medium.com/v2/resize:fit:1000/1*TC7PuuAlerm8ebCIyl5O8g.png)

Màn hình điểm chuẩn

Màn hình này trình bày cấu trúc dạng cây, hiển thị vô số thách thức có sẵn để nhân viên hỗ trợ của bạn giải quyết.

Điều hướng các danh mục thử thách
---------------------------------

Ở góc trên bên trái, có một menu thả xuống. Nó cho phép bạn xem qua và chọn từ các danh mục thử thách cụ thể. Hạng mục **Chung** là một chiếc ô bao trùm mọi thách thức.

![](https://miro.medium.com/v2/resize:fit:1000/1*H-a2KgelWixmQIEYmAwbPw.png)

Chọn cây thử thách

Đi sâu hơn vào các danh mục:

**Những thách thức về dữ liệu**

![](https://miro.medium.com/v2/resize:fit:1000/1*nZG9xBMLS2acVYDtd89aLQ.png)

Cây thách thức dữ liệu

**Những thách thức về cạo và tổng hợp**

![](https://miro.medium.com/v2/resize:fit:1000/1*OPSo8xpb1vYDf7foLuw2cg.png)

Cây cạo và tổng hợp

**Thử thách mã hóa**

![](https://miro.medium.com/v2/resize:fit:1000/1*Uwiz41ZgivDGlLr8SWi3pg.png)

Cây thách thức mã hóa

Ra mắt bộ điểm chuẩn
--------------------

Quay lại trang chung, nhấp vào bất kỳ nút nào. Hành động này tiết lộ lộ trình các thử thách leo thang dẫn đến nút bạn đã chọn. Tập hợp các bài kiểm tra lũy tiến này tạo thành cái mà chúng tôi gọi là một **bộ** .

![](https://miro.medium.com/v2/resize:fit:1000/1*ePw8CUBZww5DjlOXtb-F9g.png)

Chọn một nút

Để bắt đầu bộ phần mềm, hãy nhấp vào nút **Bắt đầu bộ thử nghiệm** .

Giám sát việc chạy điểm chuẩn
-----------------------------

Khi bộ phần mềm bắt đầu, trạng thái của từng thử thách riêng lẻ sẽ hiển thị. Nó cung cấp một bản cập nhật theo thời gian thực, hiển thị:

*   **Các thử thách đã vượt qua** : Biểu thị bằng màu xanh lục.
*   **Thử thách thất bại** : Được đánh dấu màu đỏ.
*   **Thử thách đang diễn ra** : Được biểu thị bằng một vòng tròn quay.

![](https://miro.medium.com/v2/resize:fit:1000/1*hFy_oz8feDkDFAxPnbv_UQ.png)

Điểm chuẩn chạy

Phía bên phải của màn hình hiển thị chủ động tác vụ hiện đang thực thi, cho phép bạn theo dõi hiệu suất thời gian thực của tổng đài viên.

![](https://miro.medium.com/v2/resize:fit:1000/1*YCl45gZR8_9ng3oQO0auew.png)

Điểm chuẩn đã hoàn thành

Dưới đây là cái nhìn thoáng qua về bộ thử nghiệm toàn diện hơn:

![](https://miro.medium.com/v2/resize:fit:1000/1*FUtuKfKrfyJ2xzC33CUjsw.png)

Điểm chuẩn không thành công Giữa kỳ

Điều quan trọng cần lưu ý: nếu một thử thách thất bại ở giữa bộ, các thử thách tiếp theo sẽ dừng lại và quá trình chạy sẽ kết thúc.

So sánh chuẩn vừa là thước đo vừa là động lực. Đó là bằng chứng cho thấy đại lý của bạn đã tiến được bao xa và là biển chỉ dẫn hướng tới những bước tiến mà đại lý có thể đạt được trong tương lai. Vì vậy, hãy thử thách người đại diện của bạn, học hỏi từ kết quả, lặp lại và vượt qua những ranh giới đó!

Gửi năng lực của đại lý của bạn lên bảng xếp hạng
=================================================

Khi quá trình đo điểm chuẩn của bạn đã hoàn tất, đã đến lúc chia sẻ thành tích của bạn và xem người đại diện của bạn so sánh với những người khác như thế nào! Đây là cách bạn có thể gửi điểm số của mình lên bảng xếp hạng:

Bắt đầu gửi
-----------

Sau khi chạy thành công bộ thử nghiệm, hãy chú ý nút **Gửi lên Bảng xếp hạng** sẽ chuyển sang màu xanh lục, cho biết trạng thái hoạt động của nó.

Nhấp vào nó sẽ dẫn bạn đến biểu mẫu gửi:

![](https://miro.medium.com/v2/resize:fit:1000/1*ENCy4m_FaW99HT7PaU6_uw.png)

Mẫu gửi

Điền vào mẫu gửi
----------------

Tại đây, bạn sẽ cần nhập một số chi tiết quan trọng:

\- **Tên đội** : Nhập tên đội của bạn. Những người tham gia [AutoGPT Arena Hacks](https://lablab.ai/event/autogpt-arena-hacks) phải đảm bảo tên này khớp chính xác với tên đội đã đăng ký trên LabLab để tránh bất kỳ sự khác biệt nào.

\- **Github Repo URL** : Đây là địa chỉ web của kho lưu trữ rẽ nhánh mà bạn đã tạo. Nếu bạn đang vẽ trống, hãy truy cập trang hồ sơ GitHub của bạn; nó sẽ liệt kê tất cả các kho lưu trữ của bạn.

\- **Cam kết SHA** : Xương sống cho việc gửi của bạn. Đảm bảo cam kết tất cả các thay đổi bạn đã thực hiện đối với kho lưu trữ của mình. Điều hướng đến thư mục gốc của repo của bạn và chạy lệnh `git rev-parse HEAD`. Điều này sẽ mang lại một hàm băm git duy nhất. Sao chép hàm băm này và dán nó vào trường được chỉ định. Bước này là tối quan trọng vì nó cung cấp ảnh chụp nhanh về công việc của bạn, đảm bảo khả năng truy nguyên các thay đổi được thực hiện đối với đại lý của bạn.

Gửi và so sánh
--------------

Khi biểu mẫu hoàn tất, hãy nhấp vào **Gửi** . Điểm số của bạn hiện đang trên đường đến bảng xếp hạng. Để xem mức độ của bạn so với những người khác, hãy truy cập [bảng xếp hạng](https://leaderboard.agpt.co) .

![](https://miro.medium.com/v2/resize:fit:1000/1*Kp1BRIhdNdVcvJawg0oRwg.png)

Bảng xếp hạng AutoGPT

Chúc mừng! Bằng cách gửi lên bảng xếp hạng, bạn không chỉ thể hiện khả năng của nhân viên mà còn có một bước nhảy vọt trong quá trình phát triển AI dựa vào cộng đồng. Hãy kiểm tra lại thường xuyên để biết vị trí của bạn và tiếp tục tinh chỉnh đại lý của mình để leo lên các cấp bậc đó!

Tóm lại
========

Và bạn đã có nó — hướng dẫn toàn diện về cách điều hướng giao diện người dùng AutoGPT Forge, tương tác với tổng đài viên của bạn và đánh giá các khả năng của nó. Từ việc bắt đầu nhiệm vụ cho đến gửi điểm số của bạn lên bảng xếp hạng, giờ đây bạn đã thành thạo trong việc khai thác sức mạnh của Lò rèn. Nhưng, như với tất cả những câu chuyện hay, đây chỉ là một chương.

Như bạn có thể đoán, còn nhiều điều nữa sẽ đến. Hướng dẫn tiếp theo của chúng tôi sẽ tập trung vào trọng tâm của yếu tố tạo nên một tác nhân thực sự thông minh — logic đằng sau nó. Trong “ [Chế tạo logic tác nhân thông minh](/ai/autoGPT-part4-crafting-intelligent-agent-logic) ”, chúng tôi đang chuyển bánh răng từ tương tác giao diện sang đi sâu vào mã, cho phép bạn chứng kiến ​​vẻ đẹp của LLM hoạt động như trung tâm nhận thức của tác nhân của chúng tôi. Thông qua một nhiệm vụ đơn giản nhưng hấp dẫn, bạn sẽ tận mắt chứng kiến ​​cách nhân viên của chúng tôi, chỉ với một hướng dẫn khái quát, có thể suy luận các bước một cách thông minh và thực hiện lệnh một cách liền mạch.

Hãy chú ý theo dõi vì chúng tôi sẽ bắt tay vào cuộc phiêu lưu viết mã này, làm sáng tỏ tiềm năng của LLM đang hoạt động. Hãy tin tưởng chúng tôi, bạn sẽ không muốn bỏ lỡ nó đâu. Cho đến lúc đó, hãy tiếp tục thử nghiệm và khám phá những chân trời rộng lớn của AI với AutoGPT!

<div style="text-align: right">Theo <a href="https://aiedge.medium.com/autogpt-forge-interacting-with-your-agent-1214561b06b">Craig Swift</a></div>