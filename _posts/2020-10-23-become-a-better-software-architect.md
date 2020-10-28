---
layout: single
title:  "Những điều cần thiết để trở thành một Software Architect"
desc: "Những điều cần thiết để trở thành một Software Architect"
keywords: "Architect"
categories: [Architect]
tag: [Architect]
---

Những điều cần thiết để trở thành một Software Architect
========================================================

### Software Architect là gì ?

Trước khi đi vào cụ thể SA là gì thì chúng ta cùng xem định nghĩa về SA:

> A software architect is a software expert who makes high-level design choices and dictates technical standards, including software coding standards, tools, and platforms. The leading expert is referred to as the chief architect. (Source: Wikipedia: Software Architect)

Có thể hiểu là Software Architect (SA) là một professor X, người chịu trách nhiệm thiết kế bộ khung cho hệ thống, cách phân chia và tương tác giữa các component, viết các tài liệu kiến trúc tổng quan, coding convention, và hướng dẫn các developer phát triển bản thiết kế chi tiết cho từng chức năng. Vì vậy nếu làm việc với 1 SA tốt, khi thêm các tính năng mới, độ phức tạp của phần mềm sẽ không bị tăng nhiều.

### Công việc của Software Architect là gì ?

![Pursuing a career as a Software Architect](http://www.varindersandhu.in/wp-content/uploads/2013/04/Software-Architect.png) Để những kỹ năng cần thiết của một SA, trước hết chúng ta phải hiểu được công việc của họ là gì ? Nó bao gồm những công việc sau:

*   quyết định công nghệ và platform phát triển
*   tạo tài liệu kiến trúc tổng quan (coding standards, tools, review processes,...)
*   hiểu được business requirements
*   thiết kế base hệ thống dựa trên requirements.
*   theo sát dev để check/review code và hệ thống.

### Những kỹ năng cần thiết của Software Architect là gì ?

#### **1\. Design**

*   _Có kiến thức về design patterns cơ bản_: design pattern là một trong những thứ quan trọng mà SA cần phải có để phát triển và maintain một hệ thống. Với design patterns bạn có thể reuse để giải quyết một số vấn đề hay gặp phải trước đó.
*   _Đi sâu vào pattern và anti-pattern_: Khi đã biết một vài pattern cơ bản rồi, bạn nên đào sâu/mở rộng kiến thức thêm về software design pattern. Tác giả có giới thiệu cuốn sách **Enterprise Integration Patterns: Designing, Building, and Deploying Messaging Solutions** mọi người có thể tham khảo qua.
*   _Biết đánh giá chất lượng_: Đó là lý do tài liệu hướng dẫn và coding standards được nêu ra phía trên để áp dụng. Làm vậy để hướng tới một hệ thống dễ maintain, bảo mật, tin cậy,...(điều mà ai cũng mong muốn).

Lý thuyết là vậy, còn thực tiễn thì sao ?

*   _Trải nghiệm và hiểu những stack công nghệ khác nhau_: Đây là hành động quan trọng nhất nếu bạn muốn trở thành một SA tốt. Hãy thử trải nghiệm công nghệ mới bởi mỗi công nghệ sẽ có những khía cạnh design khác nhau. Cũng không nhất thiết phải thực sự hiểu biết tất cả công nghệ nhưng phải có hiểu biết về những thứ quan trọng mà lĩnh vực của bạn.
*   _Phân tích và hiểu được pattern được áp dụng_: Cùng lấy một ví dụ đó là framework Angular. Khi bạn dùng nó bạn có thể học được khá nhiều patterns như Observables, Dependency Injection,... hãy cố tìm hiểu xem chúng được áp dụng trong framework đó như thế nào. Và nếu bạn đã hiểu thì có thể tìm hiểu sâu thêm là những đoạn code đó được thực thi như thế nào.

#### **2\. Decide**

Một SA cần phải có khả năng đưa ra quyết định và lead project hoặc team đi đúng hướng

*   **Biết điều gì là quan trọng/cần thiết**: Không nên lãng phí thời gian vào những việc không quan trọng. Hãy học cách đánh giá việc gì là quan trọng vì không có cuốn sách nào dạy bạn điều đó. Với cá nhân tôi thì tôi thường dùng 2 đặc tính để đánh giá điều đó:

_(1) Conceptional Integrity_: Nếu bạn quyết định làm việc gì theo 1 cách nào đó, hãy tập trung làm theo cách đó mặc dù có thể sẽ tốt hơn nếu làm việc đó theo cách khác. Thường thì điều đó dẫn đến một concept đơn giản, dễ hiểu và dễ bảo trì.

_(2) Uniformity (tính thống nhất)_: Nếu bạn định nghĩa và áp dụng một naming conventions, không đơn thuần chỉ là việc chữ hoa chữ thường, nhưng hãy áp dụng cùng cách đó ở bất kỳ đâu.

*   **Độ ưu tiên**: Một vài quyết định được đưa ra nhận định sớm. Nếu nó không được sớm đưa ra xem xét thì thường sẽ khó để tách nó ra sau đó và là một cơn ác mộng khi bảo trì hoặc tệ hơn là dev sẽ phải dừng công việc hiện tại cho đến khi quyết định trên được xem xét. Trong một số trường hợp thì việc đưa ra một quyết định tạm thời (có thể là không được tốt) còn hơn việc không làm gì cả. Nhưng trước hết hãy xem xét độ ưu tiên của những quyết định sắp tới. Có nhiều cách để làm điều này, tôi nghĩ các bạn nên xem qua [Weighted Shortest Job First (WSJF)](https://www.scaledagileframework.com/wsjf/) model, nó thường được sử dụng trong mô hình phát triển Agile.
*   **Biết được năng lực của mình**: Đừng nên đưa ra quyết định về những thứ không thuộc thẩm quyền của bạn. Điều này là rất quan trọng vì nó ảnh hưởng đến vị trí công việc của bạn nếu không được cân nhắc kỹ. Tốt hơn hết là hãy làm rõ với mọi người về trách nhiệm và vai trò của bạn. Nếu bạn tham gia một dự án có nhiều hơn 1 SA, bạn nên xem xét việc đưa ra một đề xuất ý tưởng hoặc ý kiến thay vì đưa ra luôn một quyết định.
*   **Xem xét nhiều sự lựa chọn**: Luôn liệt kê ra nhiều hơn một lựa chọn trước khi đưa ra quyết định. Trong hầu hết các trường hợp mà tôi đã tham gia thì có nhiều hơn một lựa chọn là khả thi (thực sự tốt).

#### **3\. Simplify**

Hãy luôn nhớ những nguyên lý giải quyết vấn đề Occam’s Razor (đề cao sự đơn giản). Có thể giải thích nguyên lý này như sau: Nếu bạn có quá nhiều giả định về một vấn đề cần giải quyết, để giải quyết vấn đề bạn có thể nghĩ sai hoặc dẫn tới những cách giải quyết phức tạp khác. Những giả định đó nên được tối giản nhất (nghĩ đơn giản) để có thể đưa ra cách giải quyết tốt.

*   **Shake the solution**: Để có thể đưa ra được những cách giải quyết đơn giản nhất, thường thì chúng ta sẽ móc nối các cách giải quyết lại với nhau và nhìn nhận vấn đề từ những vị trí khác nhau. Hãy cố gắng định hình cách giải quyết theo hướng là top-down hoặc bottom-up. Nếu bạn có data flow hoặc một quy trình, thì đầu tiên hay nghĩ theo hướng từ trái sang phải và ngược lại.
*   **Take a step back**: Sau những cuộc tranh luận dài thì thường hướng giải quyết phức tạp sẽ là kết quả còn lại. Nhưng chúng chưa phải là kết quả cuối cùng. Nên hãy dừng lại và nghĩ liệu nó có thực sự có ý nghĩa ? sau đó xem xét lại vấn đề và refactor. Cuộc tranh luận có thể sẽ diễn ra vào ngày tiếp theo, nhưng ít nhất chúng ta có thời gian để suy nghĩ về giải pháp tốt hơn và đơn giản hơn.
*   **Devide and conquer**: Đơn giản hóa vấn đề bằng cách chia để trị. Chia nhỏ vấn đề và giải quyết từng thằng đó một. sau khi validate thì match chúng lại và có cái nhìn tổng quan nhất
*   **Refactoring is not evil**: Chấp nhận việc giải quyết vấn đề theo hướng hơi phức tạp nếu hiện tại chưa có giải pháp nào tốt hơn. Chúng ta có thể suy nghĩ về điều đó sau này. Trước khi refactor thì chúng ta nên có: một automated tests để đảm bảo các function của hệ thống hoạt động chính xác và được sự đồng ý từ stackholders

#### **4\. Code**

Là một SA nên ít nhất bạn cũng cần phải biết dev của mình đang làm gì, có làm đúng không,... Nếu bạn không biết thì có thể dẫn đến 2 tình huống sau:

1.  Dev của bạn không tôn trọng những gì bạn nói
2.  Bạn không hiểu được những khó khăn hoặc những thứ dev đang cần hỗ trợ

*   **Have a side project**: Mục đích của side project chính là trải nghiệm công nghệ mới. Practice makes perfect. Việc đọc những tutorial hoặc những mặt tốt và chưa tốt của một công nghệ nào đó cũng chỉ đơn thuần là kiến thức trong sách vở.
*   **Find the right things to try out**: Như có nói qua ở phần trên, bạn không cần thiết phải biết mọi thứ (mọi công nghệ mới). Bởi vì điều đó khá tốn thời gian và dường như là nhiều vô kể. Một trang mà tôi thường xuyên ghé thăm đó là [Technology radar](https://www.thoughtworks.com/radar). Họ chia thành các category về công nghệ, công cụ, platforms, ngôn ngữ và frameworks thành 4 categories: `Adopt`, `Trial`, `Assess` và `Hold`. Với những category được chia như vậy thì sẽ dễ dàng để có được cái nhìn tổng quan nhất và người đọc dễ dàng đánh giá được xu hướng để tìm hiểu.

#### **5\. Document**

Architectural documentation thì đôi khi rất quan trọng ví dụ trong trường hợp như code guidelineds. Những tài liệu ban đầu thường sẽ là bắt buộc trước khi bắt đầu code và cần được điều chỉnh thường xuyên, liên tục. Một vài tài liệu khác được tự động tạo bằng code ví dụ như: UML class diagrams, API doc,...

*   **Clean Code**: Code có thể coi là tài liệu tốt nhất nếu nó được viết đúng cách. Một SA cần phải review và phân biệt được good/bad code. Tài liệu tham khảo đó chính là cuốn `Clean code`
*   **Generate documentation where possible**: Hệ thống có thể thay đổi liên tục (spec thay đổi là điều thường xuyên gặp ![😄](https://twemoji.maxcdn.com/2/72x72/1f604.png) ) và rất khó để update doc liên tục. Ví dụ API thì thường sẽ update thêm mới hoặc sửa thường xuyên nên việc update doc bằng sức cơm là hơi khó. Do đó một số tool như: Swagger hay RAML là một trong số tool giúp ích trong việc này.

#### **6\. Communicate**

Từ sự quan sát của tôi thì đây là một trong số những kỹ năng được đánh giá thấp nhất. Nếu bạn khá là giỏi/xuất sắc trong việc design nhưng lại không thể diễn đạt được ý tưởng đó của bạn, suy nghĩ của bạn dường như sẽ có ít ảnh hưởng hơn hoặc thậm chí có thể fail.

*   **Learn how to communicate your ideas**: Là một SA bạn sẽ không chỉ tham gia 1 cuộc họp mà bạn thường sẽ phải điều hành và moderate nó. Vì vậy học cách diễn đạt suy nghĩ và ý tưởng của mình rất quan trọng
*   **Give talks to large groups**: Diễn đạt ý tưởng ở một nhóm team nhỏ hoặc có thể là 1 group sẽ giúp bạn trau dồi điều này. Nếu bạn cảm thấy điều này hơi khó thì hãy bắt đầu bằng cách diễn đạt điều đó với bạn thân của mình. Điều này chỉ có thể thực hiện được khi bạn rời khỏi comfort zone của chính mình. Hãy kiên nhẫn, điều gì cũng cần có thời gian để trau dồi mà.
*   **Find the right level of communication**: Mỗi người sẽ có sự quan tâm và cái nhìn về một vấn đề khác nhau. vì vậy, bạn cần phải giải quyết được vấn đề của từng cá nhân đó. Ví dụ: Một dev thường sẽ quan tâm đến giải pháp cụ thể của một vấn đề, trong khi đó manager thì thường quan tâm tới giải pháp nào tiết kiệm nhất.
*   **Be always prepared to give a presentation**: Luôn có những câu hỏi từ những người xung quanh mà bạn cần trả lời ngay. Hãy thường xuyên tạo những slide tổng hợp lại những Q&A mà bạn có thể show và giải thích cho mọi người.

#### **7\. Estimate and Evaluate**

*   **Know basic project management principles**: Là một SA hoặc team leader bạn thường xuyên phải estimate time cho khối lượng công việc: trong bao lâu, cần bao nhiêu nhân lực, cần những skill nào,... Bất kể bạn dùng tool gì thì cũng cần phải trả lời những câu hỏi "quản lý" trên. Nhớ rằng nên estimate sơ bộ thời gian không chỉ phần implement mà còn bao gồm cả những hoạt động như test và fix bugs.
*   **Evaluate “unknown” architecture**: Bạn cần phải đánh giá được architecture nào là phù hợp với từng context cụ thể. Điều này không hề đơn giản nên bạn có thể chuẩn bị bằng cách tạo 1 set câu hỏi mà thường gặp cho mọi architecture. Một vài ý tưởng cho những câu hỏi đó:

(1) _Design practices_: hệ thống architecture này theo pattern nào? Chúng có thường được sử dụng và sử dụng đúng cách không? Design có follow theo 1 red line hoặc có sự phát triển nào không kiểm soát được không ? cấu trúc có rõ ràng và tách biệt không ?

(2) _Development practices_: Việc tuân theo Code guidelines như thế nào? Quản lý các version code như thế nào? Deployment practices?

### Conclusion

Nếu bạn có ý định trở thành Software Architect, con đường nghề nghiệp của bạn thường sẽ như thế này: `Junior Developer -> Developer -> Senior Developer -> Team Leader -> Software Architect`. Để trở thành một SA giỏi bạn cần phải trau dồi rất nhiều thứ như mình liệt kê ở trên. Hy vọng bài viết có thể giúp ích được cho mọi người có cái nhìn về vị trí SA (không phải nhàn hạ, đơn giản là vẽ đường cho hươu chạy như mọi người thường nghĩ đâu ![😄](https://twemoji.maxcdn.com/2/72x72/1f604.png) )

### Reference

[https://hackernoon.com/38-actions-and-insights-to-become-a-better-software-architect-f135e2de9a1b](https://hackernoon.com/38-actions-and-insights-to-become-a-better-software-architect-f135e2de9a1b)

<div style="text-align: right">Theo <a href="https://viblo.asia/p/nhung-dieu-can-thiet-de-tro-thanh-mot-software-architect-maGK7j6b5j2">Mr. Do Van Nam</a></div>