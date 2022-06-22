---
layout: single
title:  "Memory leak trong javascript"
desc: "Một đề tài mà không phải ai cũng muốn quan tâm, và có muốn quan tâm thì cũng không dễ có thể hiểu được về bộ nhớ javascript"
keywords: "memory"
categories: [javascript]
tag: [javascript]
---

Memory leak trong javascript
=====================================================

Memory leak trong javascript. Một đề tài mà không phải ai cũng muốn quan tâm, và có muốn quan tâm thì cũng không dễ có thể hiểu được về bộ nhớ javascript. Nhưng nếu như bạn hay theo dõi những bài viết trước thì nó quả là dễ dàng. Học javascript là một quá trình, từ cơ bản đến nâng cao, từ [ES6 đến ES12](https://anonystick.com/blog-developer/tong-hop-tinh-nang-javascript-moi-nhat-ke-tu-es6-den-es11-2019120577967801), mỗi giai đoạn là một bản thảo của mỗi lập trình viên.

  
Việc bản thảo lỗi thời thì có thể nâng cấp, sửa chữa, và nâng cấp lên một bản thảo mới phù hợp với xu thế hơn. Và mỗi bài viết về công nghệ cũng mang lại cho chúng ta một kiến thức mới, hãy mỉm cười đón nhận dù bài viết có hữu ích hay là không.
  

Người trách nhiệm luôn quan tâm đến Memory leak
-----------------------------------------------

Nếu bạn để ý nếu bạn mở một web trong một thời gian thì có thể rơi vào những trạng thái như nhấp chuột không được, bị đóng băng, bị đơ, nói chung là không có một tý response nào hết. Sau đó, bạn mở task manage của Chrome lên và thấy rằng tỷ lệ chiếm dụng bộ nhớ đã rất cao, sơ bộ nhận định rằng có thể có bộ nhớ bị rò rỉ. Thật đáng buồn... 
  

Mỗi lập trình viên cần phải hiểu rằng Memory không còn được sử dụng bởi các quy trình hệ thống và không được giải phóng kịp thời được gọi là rò rỉ bộ nhớ. Khi việc sử dụng bộ nhớ ngày càng cao, hiệu suất hệ thống sẽ bị ảnh hưởng và quá trình sẽ bị lỗi. Có bạn nào biết rằng Chrome giới hạn giới hạn bộ nhớ mà trình duyệt có thể sử dụng (1,4GB cho 64 bit, 1,0GB cho 32 bit) 

  
Giờ thì chúng ta đã biết vì sao một số trang WEB bị như vậy, giờ nếu bạn là một người chịu trách nhiệm trước những nguyên nhân đó thì bạn phải tìm ra giải pháp như thế nào không? Bài viết hôm nay sẽ gợi ý cho bạn những nguyên nhân gây ra phổ biến nhất. Nhưng trước hết, bạn phải tìm hiểu lại kỹ hơn về một số khái niệm như ["Vòng đời bộ nhớ javascript như thế nào?"](https://anonystick.com/blog-developer/memory-leak-bo-nho-trong-javascript-2020122224602779) hay khi ta khai báo một biến hay một function thì việc phân bổ bộ nhớ diễn ra như thế nào. Tất cả có trong bài viết trước ["Memory leak - Bộ nhớ trong javascript".](https://anonystick.com/blog-developer/memory-leak-bo-nho-trong-javascript-2020122224602779)

  
Những nguyên nhân gây rò rỉ bộ nhớ phổ biến
-------------------------------------------
 

Để tìm ra nguyên nhân gây rò rỉ bộ nhớ không dễ dàng gì trong một mớ CODE lộn xộn. Nhất là khi những người chưa có kinh nghiệm, nhưng ở đây có những điểm chung mà hầu hết đều dính phải. Hãy tiếp tục theo dõi và tìm hiểu mình có dính vào những lỗi lầm này hay không? 

Một khi nắm được rồi thì cố gắng tránh càng xa càng tốt. Sẽ có nhiều luồng ý kiến khác nhau, chúng ta phải tôn trọng điều đó, và những kinh nghiệm trong bài viết này cũng là đúc kết trong quá trình làm việc.

  
Khai báo các biến toàn cục không mong muốn
------------------------------------------
  

Trước tiên hãy tìm hiểu những dòng code sau: 

  
**Biến không được khai báo**

function fn() {
  a = 'global variable'
}
fn()

**Sử dụng this**

function fn() {
  this.a = 'global variable'
}
fn()

  
Hai đoạn code trên là nguyên nhân phổ biến nhất bởi vì js xử lý các biến chưa được khai báo bằng cách tạo một tham chiếu đến biến trên đối tượng toàn cục. Nếu trong trình duyệt, đối tượng Global là đối tượng window. 

  
Các biến sẽ không được giải phóng cho đến khi cửa sổ của trình duyệt được đóng lại hoặc trang được làm mới. Nếu các biến chưa được khai báo sẽ lưu trữ một lượng lớn dữ liệu, nó sẽ gây ra rò rỉ bộ nhớ. 

  
Giải pháp: Tránh tạo các biến toàn cục càng ít càng tốt, bế tắc lắm mới khai báo mà thôi. Sử dụng chế độ nghiêm ngặt (use strict) và thêm nó vào đầu file hoặc hàm trong JavaScript.

  
Rò rỉ bộ nhớ do bao đóng (Closure)
----------------------------------

  
Việc dùng [closure(](https://anonystick.com/blog-developer/discuss-about-closures-in-javascript-2019051695927961)) thật là lợi hại thế những việc dùng và hiểu sai là một nguyên nhân chết người. Hay xem ví dụ dưới dây để hiểu
```javascript
function fn () {
  var a = "I'm a";
  return function () {
    console.log(a);
  };
}
```
  

Lý do: Sử dụng Closure có thể đọc các biến bên trong hàm và sau đó giữ các biến này trong bộ nhớ. Nếu biến cục bộ không được xóa sau khi kết thúc sử dụng, nó có thể gây rò rỉ bộ nhớ. 

  

Giải pháp: Xác định hàm xử lý sự kiện bên ngoài, loại bỏ bao đóng hoặc xác định chức năng bên ngoài của hàm xử lý sự kiện. Để hiểu rõ hơn thì hãy xem một đoạn code dưới này

  
```javascript
// bad
for (var k = 0; k < 10; k++) {
  var t = function (a) {
    // khởi tạo đến 10 lần
    console.log(a)
  }
  t(k)
}

// good
function t(a) {
  console.log(a)
}
for (var k = 0; k < 10; k++) {
  t(k)
}
t = null
```

Tham chiếu phần tử DOM không rõ ràng
------------------------------------

  

Hãy nhìn và chúng ta sẽ phân tích:
```javascript
var elements = {
  btn: document.getElementById('btn'),
}
function doSomeThing() {
  elements.btn.click()
}
function removeBtn() {
  // Remove 
  document.body.removeChild(document.getElementById('button'))
}
```
Nếu như bạn không theo dõi bài viết trước về Memory leak thì khó có thể hình dung được việc mặc dù chúng ta đã xoá .btn rồi nhưng bạn đâu biết rằng tại thời điểm xoá thì một tham chiếu vẫn còn lưu giữ những giá trị được khai báo trước đó. 


Cách giải quyết: Xóa thủ công [elements.btn](elements.btn) = null

  
Quên xoá bộ hẹn giờ
-------------------

  

[settimer javascript](https://anonystick.com/blog-developer/settimer-javascript-2020121811069708) là một kho tàng kiến thức, và nó cũng chính là tác nhận gây ra việc rò rỉ bộ nhớ, và đây cũng là một ví dụ cụ thể:
```javascript
var serverData = loadData()
setInterval(function () {
  var renderer = document.getElementById('renderer')
  if (renderer) {
    renderer.innerHTML = JSON.stringify(serverData)
  }
}, 5000)

var btn = document.getElementById('btn')
function onClick(element) {
  element.innerHTMl = "I'm innerHTML"
}
btn.addEventListener('click', onClick)
```

Việc khai báo một sự kiện sử dụng setTimeOut hay setInterval thì quá phổ biến những hãy nhớ rằng, đừng quên xoá nó sau khi sử dụng, chứ để vậy e rằng chạy mút mùa. 

  

Giải pháp: Xóa bộ hẹn giờ và dom theo cách thủ công. removeEventListener xóa trình nghe sự kiện

<div style="text-align: right">Theo <a href="https://anonystick.com/blog-developer/sau-khi-biet-anh-ca-phat-hien-memory-leak-trong-javascript-thi-giai-phap-la-gi-2021010891719380">anonystick</a></div>
