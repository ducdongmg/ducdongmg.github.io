---
layout: single
title:  "Bản ghi Quyết định Kiến trúc (ADR) là gì?"
desc: ""
keywords: "development"
categories: [development]
tag: [development]
---

Bản ghi Quyết định Kiến trúc (ADR) là gì?
=====================================================

Lần đầu tiên tôi nghe đến thuật ngữ bản ghi quyết định kiến ​​trúc (Architecture Decision Record; ADR) khi tôi đọc '' [What an Engineering Manager Does](https://www.oreilly.co.jp/books/9784873119946/) ''. Gần đây, số lượng thành viên trong nhóm đã tăng lên và có nhiều cuộc thảo luận về việc giao việc thiết kế cơ sở hạ tầng dữ liệu cho ADR, vì vậy tôi quyết định thực hiện một số nghiên cứu để hiểu ADR theo cách riêng của mình.

ADR là gì?
----------

Bản ghi Quyết định Kiến trúc (ADR) là tài liệu ghi lại các quyết định quan trọng được đưa ra trong kiến ​​trúc phần mềm. ADR ghi lại lịch sử, cơ sở lý luận và kết quả của các quyết định về kiến ​​trúc phần mềm và chia sẻ chúng với toàn bộ nhóm dự án. Điều quan trọng là không chỉ ghi lại những gì đã được quyết định mà còn bao gồm các cuộc thảo luận, bối cảnh và những ràng buộc dẫn đến quyết định.

Mục tiêu chính của ADR là:

1.  Giảm hiểu lầm trong nhóm của bạn bằng cách làm rõ các quyết định về kiến ​​trúc.
2.  Giúp các thành viên mới hiểu các quyết định kiến ​​trúc trong quá khứ.
3.  Bằng cách học hỏi từ các quyết định trong quá khứ, toàn bộ nhóm có thể tích lũy kiến ​​thức và kinh nghiệm kiến ​​trúc, giảm bớt các cuộc thảo luận không cần thiết và tăng hiệu quả ra quyết định cho các dự án trong tương lai.

Nếu một thành viên mới muốn biết ý đồ của thiết kế kiến ​​trúc hiện tại, họ có thể hỏi người thiết kế kiến ​​trúc xem người đó có còn ở trong nhóm không, nhưng nếu người đó đã nghỉ hưu hoặc người đó đã quên thì bạn đã thắng. không thể biết được ý định của bạn là gì.

Nếu bạn không biết mục đích, khi xem xét kiến ​​trúc trong tương lai, bạn có thể sẽ sử dụng những lập luận tương tự như khi bạn thiết kế nó lần đầu tiên hoặc cuối cùng bạn có thể đưa ra quyết định sai lầm.

Giả sử thiết kế hiện tại là A, nhưng có ý kiến ​​cho rằng thiết kế B có thể tốt hơn. Tuy nhiên, trên thực tế, B không thể được chấp nhận vì điều kiện ràng buộc C, và A có thể phải được chấp nhận. Nếu bạn không biết về các ràng buộc đó, một dự án thay đổi thành B sẽ được khởi chạy, nhưng các ràng buộc sẽ được phát hiện trong quá trình thiết kế hoặc triển khai và bạn sẽ không có lựa chọn nào khác ngoài việc hủy bỏ nó. Tất cả thời gian và tiền bạc bạn đã bỏ ra cho đến thời điểm đó sẽ bị lãng phí. Thông tin như ý định, lịch sử, cơ sở và ràng buộc của việc ra quyết định trong thiết kế kiến ​​trúc là cần thiết.

mẫu ADR
-------

Khi tạo ADR, nó thường bao gồm các yếu tố sau:

1.  Tiêu đề: Một biểu thức ngắn gọn cung cấp cái nhìn tổng quan về quyết định.
2.  Trạng thái: Trạng thái hiện tại của quyết định
    *   Bản nháp: Những gì chúng tôi sẽ đề xuất
    *   Đề xuất: Đề xuất
    *   Đã chấp nhận: Đề xuất đã được chấp nhận.
    *   Bị từ chối: Đề xuất đã bị từ chối
    *   Không dùng nữa: Không dùng nữa
    *   Đã thay thế: được thay thế bởi một ADR khác
3.  Quyết định: Chi tiết về kiến ​​trúc và quyết định giải pháp
4.  Bối cảnh (thông tin cơ bản): Bối cảnh, vấn đề, mục đích, v.v. cho việc ra quyết định này.
5.  Xem xét (nội dung so sánh/xem xét): Các phương án khác được xem xét và các nội dung được xem xét.
6.  Hậu quả: Kết quả mong đợi. Tác động của các quyết định đối với hệ thống và dự án, tác động đến các bên liên quan, v.v.
7.  Tài liệu tham khảo: Các liên kết liên quan

Quy trình vận hành ADR
----------------------

1.  Thực hiện: Giải thích mục đích và lợi ích của ADR cho tất cả các thành viên trong nhóm và đạt được sự đồng thuận để thực hiện nó.
2.  Tạo mẫu: Tạo mẫu trong Notion, v.v. Quản lý danh sách ADR của bạn bằng chức năng cơ sở dữ liệu của Notion.
3.  Định nghĩa quá trình tạo/cập nhật ADR (được mô tả sau)
4.  Quyết định thời điểm tạo và xem xét ADR
5.  Chia sẻ với toàn bộ nhóm: Chia sẻ các ADR và ​​​​cập nhật mới trong các cuộc họp định kỳ, v.v.

Quy trình tạo ADR
-----------------

Sơ đồ quy trình được xuất bản trong tài liệu AWS chính thức được sao chép bên dưới.

![tạo quảng cáo](https://contents.blog.jicoman.info/2023/05/adr-creation.png)

Tham khảo: [https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html#adoption](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html#adoption)

*   ADR có thể được tạo bởi tất cả các thành viên trong nhóm
*   Người tạo ADR cần duy trì nội dung ADR, cập nhật trạng thái, liên lạc với các thành viên và yêu cầu đánh giá.
*   Sau khi ADR được tạo và sẵn sàng để xem xét, hãy đặt trạng thái thành **Đề xuất .**
*   Người tạo ra ADR sẽ tổ chức một cuộc họp đánh giá hoặc xem xét nó tại một cuộc họp thường kỳ.
    *   Thời gian trung bình khoảng 10-15 phút
    *   Mỗi thành viên trong nhóm đọc ADR, đưa ra nhận xét và câu hỏi cũng như thảo luận về nội dung đó trong nhóm.
*   Nếu tìm thấy các điểm hành động để cải thiện ADR, hãy cùng nhau làm việc theo nhóm để giải quyết các điểm hành động.
*   Nếu nhóm phê duyệt ADR, hãy đặt trạng thái thành **Đã chấp nhận**
*   Nếu nhóm từ chối ADR, hãy thêm lý do từ chối và đặt trạng thái thành **Bị từ chối.**
*   Khóa tài liệu ADR khỏi sửa đổi (phụ thuộc vào các công cụ tài liệu như Notion)

Quy trình gia hạn ADR
---------------------

Hãy coi các ADR đã được phê duyệt hoặc bị từ chối là tài liệu bất biến. Nếu bạn muốn sửa đổi ADR hiện tại, ADR mới phải được tạo và phê duyệt thông qua quy trình xem xét. Khi ADR mới được thông qua, người tạo ADR sẽ thay đổi trạng thái của ADR cũ thành **Đã thay thế .**

Sơ đồ quy trình được xuất bản trong tài liệu AWS chính thức được sao chép bên dưới.

![kiểm tra adr](https://contents.blog.jicoman.info/2023/05/adr-inspection.png)

Tham khảo: [https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html#review](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/adr-process.html#review)

URL tham chiếu
--------------

*   [https://adr.github.io](https://adr.github.io/)
*   [Sử dụng bản ghi quyết định kiến ​​trúc để hợp lý hóa việc ra quyết định kỹ thuật cho dự án phát triển phần mềm - Hướng dẫn quy định của AWS](https://docs.aws.amazon.com/prescriptive-guidance/latest/architectural-decision-records/welcome.html)
*   [Tổng quan về hồ sơ quyết định kiến ​​trúc | Trung tâm kiến ​​trúc đám mây | Google Cloud](https://cloud.google.com/architecture/architecture-decision-records)
*   [Ghi lại thiết kế bằng cách sử dụng "Bản ghi quyết định kiến ​​trúc (ADR)" - Blog của nhóm sản phẩm StudySapuri](https://blog.studysapuri.jp/entry/architecture_decision_records)
*   [Tôi quyết định dùng thử ODDR để đưa ra quyết định minh bạch trong phát triển tổ chức | DevelopersIO](https://dev.classmethod.jp/articles/oddr/)

<div style="text-align: right">Theo <a href="https://blog.jicoman.info/2023/05/6-understanding-architecture-decision-record">jicoman</a></div>