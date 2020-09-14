---
layout: single
title:  "Sử dụng forEach trong JavaScript là phương sách cuối cùng"
desc: "Sử dụng forEach trong JavaScript là phương sách cuối cùng"
keywords: "loop, javascript"
categories: [javascript]
tag: [javascript]
---

Năm nay,  
tôi may mắn có cơ hội xem lại mã của nhiều thành viên với tư cách là một vị trí dẫn đầu những người mới bắt đầu và những người gia công có ít kinh nghiệm về JavaScript, nhưng vì có nhiều người sử dụng nó mọi lúc, nên điều `Array.prototype.forEach`này rất quan trọng đối với người mới bắt đầu. Tôi đã tổ chức nó.

Giả định rằng bạn đang sử dụng trình duyệt hỗ trợ ES2015 hoặc phiên bản mới hơn hoặc sử dụng polyfill.

Phần kết luận
====================================

Khi thực hiện bất kỳ hoạt động trên mảng, xem xét liệu các function có sẵn như `filter`, `find`, `map`, `reduce` có thể sử dụng được hay không, nếu không thể thì mới sử dụng tới `forEach`.

Dưới đây, tôi sẽ dùng một vài ví dụ để giải thích.

forEach ➔ filter
====================================

Ví dụ đầu tiên là `Array.prototype.filter`

```javascript
const pomeranians = [];

dogs.forEach(dog => {
  if (dog.type === 'pomeranian') {
    pomeranians.push(dog);
  }
});
```

Đoạn mã này `dogs`trích xuất tất cả các phần tử trong mảng phù hợp với một điều kiện nhất định.

Tất nhiên cách triển khai này cũng hoạt động tốt, nhưng trong  
trường hợp này, nó `filter`có thể được viết ngắn gọn hơn bằng cách sử dụng `filter`

```javascript
const pomeranians = dogs.filter(dog => {
  return dog.type === 'pomeranian';
});
```

Hơn nữa, nó thực sự nhỏ gọn hơn bằng cách sử dụng tốc ký mũi tên.  
(Trong các ví dụ sau, chỉ mã bằng tốc ký được giới thiệu.)

```javascript
const pomeranians = dogs.filter(dog => dog.type === 'pomeranian');
```

Bây giờ, bạn có thể thấy rằng mã đã được rút ngắn và đơn giản hóa bằng cách viết lại `forEach`từ `filter`,  
nhưng lợi thế quan trọng hơn đó là,

`filter`Thực tế được sử dụng để lặp qua mảng  
**ngay lập tức truyền đạt** cho người xem mã này **ý định rằng vòng lặp này đang trích xuất một tập hợp con của các con chó** .

`forEach`Chỉ có mục đích và ý nghĩa của việc lặp qua một mảng,  
vì vậy bạn cần làm theo các chi tiết triển khai để tìm ra những gì bạn đang thực hiện vòng lặp, nhưng nếu  
`filter`được sử dụng, thì chi tiết mã Ngay cả khi bạn không đọc, bạn sẽ có thể biết rằng bạn sẽ thực hiện quá trình trích xuất phần tử của điều kiện cụ thể như một quá trình.

Trong việc đọc mã, việc giải mã quá trình xử lý các vòng lặp  
có thể là một công việc nặng nề đối với não bộ, nhưng nếu bạn biết trước mục đích của toàn bộ quá trình xử lý, bạn có thể giảm đáng kể chi phí trong việc hiểu chi tiết.

Như `filter`đã giải thích trong ví dụ ở đây, mã khác, `find`và `map`, `reduce`có cùng ưu điểm, và  
điều quan trọng là mã phải dễ đọc bằng cách chọn phương pháp thích hợp.

forEach ➔ find
================================

Sau đó `Array.prototype.find`.

```javascript
let myDog;

dogs.forEach(dog => {
  if (dog.name === 'ポメラニアス3世') {
    myDog = dog;
  }
})
```

Mã này `dogs`trích xuất một phần tử cụ thể từ mảng .

Ngoài ra, tôi đã lo lắng rằng `forEach`vòng lặp `break`không thể được thực hiện với và  
tôi `for`thấy một số người viết nó đơn giản hơn, nhưng  
cả hai đều không phải là mã rất tốt.

```javascript
let myDog;

for (let i = 0; i < dogs.length; i++) {
  if (dog.name === 'ポメラニアス3世') {
    myDog = dog;
    break;
  }  
}
```

Trong trường hợp này, `find`mục đích có thể được làm rõ ràng hơn và mô tả có thể ngắn gọn bằng cách sử dụng.

```javascript
const myDog = dogs.find(dog => dog.name === 'ポメラニアス3世');
```
Tiện thể nếu bạn dùng `filter` thì có thể viết như sau.

```javascript
const myDog = dogs.filter(dog => dog.name === 'ポメラニアス3世')[0];
```

Từ số lượng triển khai mã, dường như không tạo ra nhiều khác biệt, nhưng như tôi  
đã giải thích trước đó, `find`việc sử dụng làm cho ý định tìm kiếm và trích xuất một phần tử cụ thể từ mảng trở nên rõ ràng. ,  
`filter`Tốt hơn `find`để sử dụng.

Đặc biệt, nếu `filter`giá trị trả về trong trường hợp này được nhận dưới dạng một biến dưới dạng mảng, bạn  
`myDogs[0]`sẽ chỉ định chỉ mục và chỉ tham chiếu đến phần tử đầu tiên, nhưng trong  
trường hợp này, phần đầu của mảng có nghĩa là gì? , Tại sao không tham chiếu đến các phần tử khác với phần tử đầu tiên? Nó sẽ gây nhiều nỗ lực cho người đọc và nên tránh.

forEach ➔ bản đồ
=================================

Thứ ba `Array.prototype.map`.

```javascript
const dogNames = [];

dogs.forEach(dog => {
  dogNames.push(dog.name);
});
```

Đoạn mã này là `dogs`một ví dụ về việc tham chiếu từng phần tử của một mảng để tạo một mảng khác.  
Nếu bạn muốn tạo một mảng với cấu hình khác, hãy `map`sử dụng để xóa nó.

```javascript
const dogNames = dogs.map(dog => dog.name);
```

Ví dụ này có thể quá đơn giản để truyền đạt những giá trị, nhưng  
khi xử lý JSX trong React, có rất nhiều nơi bạn có thể sử dụng nó mà không thất bại.

```javascript
render() {
  return (
    <ul>
      {this.props.dogs.map(dog => <li>{`${dog.name}: ${dog.description}`}</li>)}
    </ul>
  );
};
```

Ngoài ra, tôi nghĩ rằng có những trường hợp chỉ các phần tử cụ thể được xử lý thành một mảng như hình dưới đây,  
`map`nhưng nó sẽ được `filter`thực hiện kết hợp với thực tế là không thể tự chọn hoặc chọn phần tử .

```javascript
// forEach
const pomeranians = [];

dogs.forEach(dog => {
  if (dog.type === 'pomeranian') {
    pomeranians.push({
      id: uuid(),
      name: dog.name,
    });
  }
});
```

```javascript
// filter->map
const animals = dogs.filter(dog => dog.type === 'pomeranian')
  .map(dog => ({
    id: uuid(),
    name: dog.name,
  });
```

Trước khi xử lý với `map`, `filter`các trình tự đáp ứng các điều kiện được trích xuất.

```javascript
// map->filter
const animals = dogs.map(dog => {
  if (dog.type !== 'pomeranian') {
    return null;
  }
  return {
    id: uuid(),
    name: dog.name,
  };
}.filter(v => v);  
```

Trên đây là một ví dụ `map`về xử lý sau khi ngược lại `filter`.

Trong ví dụ này, ví dụ trước ngắn gọn hơn, nhưng `filter`nếu các điều kiện phức tạp, có thể viết hàm  
`map`trả về sớm thích hợp `null`cùng nhau sau này `filter`sẽ rõ ràng hơn.

Nhân tiện, cần nhớ rằng bạn có thể loại bỏ tất cả các giá trị sai `.filter(v => v)`trong một  
mảng bằng cách mô tả nó dưới dạng một mảng.

forEach ➔ giảm
==================================

Cuối cùng `Array.prototype.reduce`.

```javascript
// forEach
let total = 0;

dogs.forEach(dog => {
  total += dog.price;
});
```

Đoạn mã này là một `dogs`ví dụ về tính toán tổng giá trị bằng cách tham chiếu đến từng phần tử của mảng .

Trên thực tế `reduce`, nó là tốt hơn để sử dụng so với ba trước đó ! !! Mặc dù có một vài trường hợp mà tôi nhận xét, điều thuận tiện là khai báo biến có thể được viết lại từ  
khi thực hiện quá trình tính tổng giá trị của một mảng như vậy hoặc nối các chuỗi .  
`let``const`

```javascript
// reduce
const total = dogs.reduce((acc, dog) => acc + dog.price, 0);
```

Ngoài ra, như sẽ được giới thiệu trong mục tiếp theo, quá trình  
tạo một cá thể với trạng thái bên trong, gọi một phương thức cá thể trong một vòng lặp và  
cuối cùng trả về cá thể có trạng thái bên trong đã được thay đổi dưới dạng giá trị trả về là một lớp lót. Tôi có thể viết, vì vậy nó đôi khi rất vừa vặn.

Tuy nhiên, `reduce`ở một `forEach`mức độ thấp hơn, nó tương đối linh hoạt, vì vậy nếu bạn  
lạm dụng nó, bạn có xu hướng nhận được mã không rõ ràng.

Các trường hợp forEach thích hợp
============================================================================================================

Ngược lại `Array.prototype.forEach`, đây là một ví dụ mà tôi cảm thấy rằng mô tả trong là phù hợp.

cho mỗi

```javascript
// forEach
dogs.forEach(dog => {
  console.log(dog.name);
});
```

Nếu bạn không trực tiếp tham gia vào phạm vi bên ngoài, `forEach`có vẻ hợp lý khi viết vào.  
(Tôi không nghĩ ra ngay lập tức, nhưng có thể có ngoại lệ ...)

Cũng ở gần bạn, nhưng trong ví dụ trên `fetch`, chẳng hạn như hoặc thông báo, nếu bạn gọi xử lý không đồng bộ,  
`forEach`trong mỗi vòng lặp `await`và thực tế là không thể, `Promise.all`vì vậy tôi nghĩ trong nhiều trường hợp có thể được xử lý đồng thời bằng cách sử dụng,  
trong trường hợp này `map`Tôi nghĩ rằng bạn sẽ sử dụng để trả về một mảng các Lời hứa .

bản đồ

Copied!

Await  Promise . All ( Dogs . Map ( Async  Dog  \=>  Await  Dog . Eat ( ' phả hệ Chăm ' ));

Sau đây là một ví dụ về vận hành một phương thức instance với một instance có trạng thái bên trong nhất định.

cho mỗi

Copied!

const  pomeranian  \=  new  Pomeranian ();
thực phẩm . forEach ( food  \=>  { 
  an if  ( food . type  \===  ' beef ' )  { 
    pomeranian . the add ( food ); 
  } 
});

Nhân tiện, `reduce`nếu bạn viết với, bạn có thể viết như sau.

giảm

Copied!

const  pomeranian  \=  đồ ăn . Reduce (( pomeranian ,  food )  \=>  { 
  an if  ( food . type  \===  ' beef ' )  { 
    pomeranian . the add ( food ); 
  } 
  return  pomeranian ; 
},  new new  Pomeranian ());

Tuy nhiên, nó `forEach`đơn giản hơn thế một cách tinh tế và  
nếu bạn không muốn nhận một thể hiện làm giá trị trả về của một hàm, ngay cả khi nó được `forEach`mô tả trong, bạn  
cảm thấy rằng không có vấn đề gì trong danh mục yêu thích của mình.

Tóm lược
========================================

Vì vậy, tôi nghĩ rằng có một mẫu hơi tế nhị, nhưng `forEach`trong khi giới thiệu một ví dụ về việc viết lại,  
tại sao nó phải được viết lại? Tôi đã cố gắng nói chuyện.

`forEach`Vì tôi có thể làm bất cứ điều gì khi sử dụng , nên tôi đã thấy nhiều bài PR bị biến tấu, chẳng hạn như  
đóng gói nhiều ý định trong một vòng lặp, các  
`if`tuyên bố đáng kinh ngạc , `for`lồng vào nhau, v.v.

Ban đầu, nó `forEach`không có giá trị trả lại, vì vậy nếu bạn cố gắng nhận ra quá trình xử lý có ý nghĩa, nó sẽ được tạo tiền đề cho hoạt động ở phạm vi bên ngoài  
và tôi cảm thấy rằng đó sẽ là tất cả những gì bạn có thể làm.

Ngoài ra, khi thực sự triển khai một ứng dụng web,  
việc sử dụng thư viện vận hành bộ sưu tập như lodash, immutable.js, Rambda  
sẽ rất hiệu quả, nhưng nó cũng sẽ ảnh hưởng đến kích thước tệp đi kèm, vì vậy hợp lý Trong một số trường hợp, viết bằng vani sẽ dẫn đến trải nghiệm người dùng tốt.

Cuối cùng, tôi không nói nhiều về hiệu suất, nhưng tôi nghĩ cách  
đơn giản `for`nhất để viết nó có lẽ nhanh hơn (cần phải trưng bày) và đó là sự đánh đổi với khả năng đọc.

Tuy nhiên, mặc dù `for`nhanh nhưng tôi nghĩ rằng hiếm khi việc viết lại này tạo ra sự khác biệt lớn về hiệu suất, và trong  
giai đoạn điều chỉnh, chúng tôi đã thực sự đo lường và nhận thấy rằng đó là một nút thắt cổ chai, vì vậy hãy cân nhắc viết lại. Tôi nghĩ hướng làm là tốt.

(Bằng cách viết lại này, dường như có một vấn đề trong thiết kế của toàn bộ dịch vụ khi cần thực hiện xử lý vòng lặp trên JavaScript để có sự khác biệt lớn về hiệu suất ...)

<div style="text-align: right">Theo <a href="https://qiita.com/diescake/items/70d9b0cbd4e3d5cc6fce">qiita</a></div>