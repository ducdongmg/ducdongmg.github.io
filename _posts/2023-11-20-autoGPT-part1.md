---
layout: single
title:  "AutoGPT Forge: Hướng dẫn toàn diện cho những bước đầu tiên của bạn"
desc: ""
keywords: "autoGPT"
categories: [AI]
tag: [AI]
---

AutoGPT Forge: Hướng dẫn toàn diện cho những bước đầu tiên của bạn
=====================================================

![](https://miro.medium.com/v2/resize:fit:700/1*xYubXgwj5nUEzxsHhJUt3Q.png)

Chào mừng bạn đến với Hướng dẫn bắt đầu! Hướng dẫn này được thiết kế để hướng dẫn bạn qua quá trình thiết lập và chạy tác nhân AutoGPT của riêng bạn trong môi trường Forge. Cho dù bạn là nhà phát triển AI dày dạn kinh nghiệm hay mới bắt đầu, hướng dẫn này sẽ trang bị cho bạn các bước cần thiết để bắt đầu hành trình của mình trong thế giới phát triển AI với AutoGPT.

Đây là phần 1 của loạt bài hướng dẫn về cách sử dụng cách xây dựng Tác nhân AI của riêng bạn bằng AutoGPT Forge.

Phần 2: [AutoGPT Forge: Bản thiết kế của một đặc vụ AI](/autogpt-forge-the-blueprint-of-an-ai-agent-75cd72ffde6)

Phần 3: [AutoGPT Forge: Tương tác với Đại lý của bạn](/autogpt-forge-interacting-with-your-agent-1214561b06b)

Phần 4: [AutoGPT Forge: Chế tạo logic tác nhân thông minh](/autogpt-forge-crafting-intelligent-agent-logic-bc5197b14cb4)

Phần 1: Tìm hiểu lò rèn
=======================

Forge đóng vai trò là mẫu toàn diện để xây dựng tác nhân AutoGPT của riêng bạn. Nó không chỉ cung cấp cài đặt để thiết lập, tạo và chạy tác nhân của bạn mà còn bao gồm hệ thống đo điểm chuẩn và giao diện người dùng. Các thành phần tích hợp này tạo điều kiện thuận lợi cho việc phát triển và đánh giá hiệu suất của đại lý của bạn.

Nó đóng một vai trò quan trọng trong hệ sinh thái AutoGPT, hoạt động như một phần gốc mà từ đó một tác nhân được tạo ra. Nó được thiết kế để tích hợp với giao thức tác nhân, hệ thống điểm chuẩn và giao diện AutoGPT, từ đó hình thành một môi trường gắn kết và mạnh mẽ để phát triển tác nhân.

Sự hài hòa này đảm bảo rằng các nhà phát triển tuân thủ một khuôn khổ tiêu chuẩn hóa, giúp hợp lý hóa đáng kể quá trình phát triển. Do đó, nó loại bỏ nhu cầu xây dựng mã soạn sẵn, cho phép các nhà phát triển hướng nỗ lực và sự sáng tạo của họ trực tiếp vào việc tạo ra “bộ não” của tác nhân. Bằng cách tập trung vào việc nâng cao trí thông minh và chức năng của tác nhân, các nhà phát triển có thể thực sự tận dụng tiềm năng của AutoGPT, tạo ra các tác nhân không chỉ hiệu quả mà còn sáng tạo và tiên tiến. Do đó, Forge được coi là ngọn hải đăng của sự đổi mới và hiệu quả, thúc đẩy sự phát triển của các đại lý AutoGPT lên một tầm cao mới.

yêu cầu hệ thống
================

Dự án này hỗ trợ Linux (dựa trên Debian), Mac và Hệ thống con Windows cho Linux (WSL). Nếu bạn đang sử dụng hệ thống Windows, bạn sẽ cần cài đặt WSL. Bạn có thể tìm thấy hướng dẫn cài đặt cho WSL [tại đây](https://learn.microsoft.com/en-us/windows/wsl/) .

Phần 2: Thiết lập môi trường rèn
================================

Để bắt đầu, bạn cần phân [nhánh kho lưu trữ](https://github.com/Significant-Gravitas/Auto-GPT) bằng cách điều hướng đến trang chính của kho lưu trữ và nhấp vào “Fork” ở góc trên bên phải. Hãy nhớ đánh dấu sao, nếu bạn chưa có!

![](https://miro.medium.com/v2/resize:fit:700/1*IHPD5zstb6WCeX9qH62_KA.png)

Kho lưu trữ Github

Làm theo hướng dẫn trên màn hình để hoàn tất quá trình.

![](https://miro.medium.com/v2/resize:fit:700/1*7IU6ZtmpYeWed_v7E6YDdg.png)

Trang tạo ngã ba

Nhân bản kho lưu trữ
====================

Tiếp theo, sao chép kho lưu trữ vào hệ thống cục bộ của bạn. Đảm bảo bạn đã cài đặt Git để tiến hành bước này. Bạn có thể tải xuống Git từ [đây](https://git-scm.com/downloads) . Sau đó sao chép repo bằng lệnh sau và url cho repo của bạn. Bạn có thể tìm thấy url chính xác bằng cách nhấp vào nút Mã màu xanh lá cây trên trang chính kho lưu trữ của bạn.

\# thay thế url bằng url cho bản sao git
 repo phân nhánh của bạn https://github.com/Significant-Gravitas/Auto-GPT.git

![](https://miro.medium.com/v2/resize:fit:616/1*z__ACiW97G6qkV33Yjv4tA.png)

Nhân bản repo ví dụ tôi đã tạo

Thiết lập dự án
===============

Khi bạn đã sao chép dự án, hãy thay đổi thư mục của bạn sang dự án mới được sao chép:

\# Tên của thư mục sẽ khớp với tên bạn đặt cho fork của mình. Mặc định là Auto-GPT
cd Auto-GPT

Để thiết lập dự án, hãy sử dụng lệnh _./run setup_ trong terminal. Làm theo hướng dẫn để cài đặt các phần phụ thuộc cần thiết và thiết lập mã thông báo truy cập GitHub của bạn.

> Lưu ý: dành cho người dùng nâng cao. Mã thông báo truy cập github chỉ cần thiết cho lệnh nhập đấu trường ./run để hệ thống có thể tự động tạo PR

![](https://miro.medium.com/v2/resize:fit:700/1*t3q0PeloeRH3MpqRD3Sa6g.png)

Thiết lập dự án

![](https://miro.medium.com/v2/resize:fit:660/1*hpVFg_6CxtuSmItB3J-aYQ.png)

Đầu ra của lệnh thiết lập khi tất cả các yêu cầu đã được đáp ứng

Phần 3: Tạo đại lý của bạn
==========================

Chọn một tên phù hợp cho đại lý của bạn. Nó phải là duy nhất và mang tính mô tả. Ví dụ về tên hợp lệ bao gồm swiftyosgpt, SwiftyosAgent hoặc swiftyos\_agent.

Tạo mẫu đại lý của bạn bằng lệnh:

./run tác nhân tạo YOUR\_AGENT\_NAME

Thay thế YOUR\_AGENT\_NAME bằng tên bạn đã chọn ở bước trước.

![](https://miro.medium.com/v2/resize:fit:675/1*3ZpVd3HJFrt3j3GLzjzyWA.png)

Bước Vào Đấu Trường
===================

Arena là tập hợp của tất cả các đại lý AutoGPT. Nó phục vụ như một môi trường cạnh tranh trong đó tất cả các đại lý được đánh giá để tìm ra đại lý tổng quát tốt nhất. Vào Đấu trường là bước bắt buộc để tham gia hackathons AutoGPT. Nó cho phép đại lý của bạn trở thành một phần của hệ sinh thái đa dạng và năng động, nơi đại lý được đánh giá định kỳ bằng điểm chuẩn để ghi điểm trên bảng xếp hạng chính thức.

Chính thức vào Đấu trường bằng cách thực hiện lệnh:

./run đấu trường nhập YOUR\_AGENT\_NAME

![](https://miro.medium.com/v2/resize:fit:700/1*LO4VR4guAEYHkZ82dGe83g.png)

Đầu ra của lệnh nhập đấu trường trông như thế nào

Phần 4: Điều hành đại lý của bạn
================================

Bắt đầu bằng cách khởi động tác nhân của bạn bằng lệnh:

./chạy đại lý bắt đầu YOUR\_AGENT\_NAME\`

Điều này sẽ khởi tạo tác nhân trên [_http://localhost:8000/_](http://localhost:8000/)

![](https://miro.medium.com/v2/resize:fit:700/1*FnCekFmvs8G9lWVDufX7cQ.png)

Khởi động đại lý

Đăng nhập và gửi nhiệm vụ cho đại lý của bạn
============================================

Truy cập giao diện người dùng tại _http://localhost:8000/_ và đăng nhập bằng tài khoản Google hoặc GitHub. Sau đó, bạn có thể gửi nhiệm vụ cho đại lý của mình thông qua giao diện.

![](https://miro.medium.com/v2/resize:fit:600/1*cbTwPv_ecc35Ar_GqlHO5Q.png)

![](https://miro.medium.com/v2/resize:fit:700/1*50AZ_GQT4dttRcNTvLyM4A.png)

Dừng và khởi động lại đại lý của bạn
====================================

Khi cần, hãy sử dụng Ctrl+C để kết thúc phiên hoặc sử dụng lệnh dừng:

./run đại lý dừng

Lệnh này buộc tác nhân dừng lại. Bạn cũng có thể khởi động lại nó bằng cách sử dụng lệnh start.

Phần kết luận
=============

Trong khám phá hôm nay, chúng tôi đã đề cập đến những điều cần thiết khi làm việc với các dự án AutoGPT. Chúng tôi bắt đầu bằng việc đặt ra nền tảng, đảm bảo bạn có sẵn tất cả các công cụ phù hợp. Từ đó, chúng tôi đi sâu vào chi tiết cụ thể để xây dựng một tác nhân AutoGPT hiệu quả. Hãy tin tôi đi, với những bước đi đúng đắn, nó sẽ trở thành một quá trình đơn giản.

Các bước tiếp theo: Xây dựng và nâng cao đại lý của bạn
=======================================================

Với bộ nền tảng, giờ đây bạn đã sẵn sàng xây dựng và nâng cao đại lý của mình, khám phá các chức năng khác nhau và cải thiện hiệu suất của nó. Hướng [dẫn tiếp theo](/autogpt-forge-the-blueprint-of-an-ai-agent-75cd72ffde6) sẽ xem xét cấu trúc của một tác nhân và cách thêm một số chức năng cơ bản.

<div style="text-align: right">Theo <a href="https://aiedge.medium.com/autogpt-forge-a-comprehensive-guide-to-your-first-steps-a1dfdf46e3b4">Craig Swift</a></div>
