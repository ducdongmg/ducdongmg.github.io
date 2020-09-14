---
layout: single
title:  "So sánh tốc ký trong PHP"
desc: "So sánh tốc ký trong PHP"
keywords: "shorthand, php"
categories: [php]
tag: [php]
---

So sánh tốc ký trong PHP
========================

Có thể bạn đã biết một số toán tử so sánh trong PHP. Những thứ như ternary `?:`, the null coalescing `??` và the spaceship `<=>` . Nhưng bạn có thực sự biết chúng hoạt động như thế nào không? Việc hiểu các toán tử này giúp bạn sử dụng chúng nhiều hơn, dẫn đến codebase sạch hơn.

Trước khi tìm hiểu sâu về từng toán tử, đây là tóm tắt về những gì mỗi toán tử làm:

*   Các [toán tử  ternary](#ternary-operator) được sử dụng để rút ngắn nếu / cấu trúc khác
*   Các [toán tử  coalescing rỗng](#null-coalescing-operator) được sử dụng để cung cấp các giá trị mặc định thay vì null
*   Các [toán tử  tàu vũ trụ](#spaceship-operator) được sử dụng để so sánh hai giá trị

[#](#ternary-operator) Toán tử  ternary
-------------------------------------

Toán tử ternary là cách viết tắt của cấu trúc `if {} else {}`. Thay vì viết thế này:

    if ($condition) {
        $result = 'foo' 
    } else {
        $result = 'bar'
    }

Bạn có thể viết thế này:

    $result = $condition ? 'foo' : 'bar';

Nếu giá trị `$condition` là `true`, thì toán hạng bên trái sẽ được gán cho `$result`. Nếu là `false`, thì toán hạng bên phải sẽ được sử dụng.

Thực tế thú vị: tên _toán tử bậc ba_ thực sự có nghĩa là "một toán tử hoạt động trên ba toán hạng". Một _toán hạng_ là một thuật ngữ dùng để chỉ các bộ phận cần thiết của một biểu thức. Toán tử bậc ba là toán tử duy nhất trong PHP yêu cầu ba toán hạng: điều kiện, `true`và `false`kết quả. Tương tự, cũng có các toán tử nhị phân và đơn phân. Bạn có thể đọc thêm về nó [ở đây](http://php.net/manual/en/language.operators.php) .

Quay lại toán tử bậc ba: bạn có biết biểu thức nào đánh giá và biểu thức `true`nào không? Hãy nhìn vào `boolean`cột của [bảng này](http://php.net/manual/en/types.comparisons.php) .

Toán tử bậc ba sẽ sử dụng toán hạng bên trái của nó khi điều kiện đánh giá là `true`. Đây có thể là một chuỗi, một số nguyên, một boolean, v.v. Toán hạng bên phải sẽ được sử dụng cho cái gọi là "giá trị sai".

Các ví dụ sẽ là `0`hoặc `'0'`, một mảng hoặc chuỗi trống `null`, một biến không xác định hoặc chưa được gán và tất nhiên là `false`chính nó. Tất cả các giá trị này sẽ làm cho toán tử bậc ba sử dụng toán hạng bên phải của nó.

### [#](#shorthand-ternary-operator) Toán tử bậc ba viết tắt

Kể từ PHP 5.3, có thể bỏ đi toán hạng bên trái, cho phép các biểu thức thậm chí còn ngắn hơn:

    $result = $initial ?: 'default';

Trong trường hợp này, giá trị của `$result`sẽ là giá trị của `$initial`, trừ khi được `$initial`đánh giá là `false`, trong trường hợp đó chuỗi `'default'`được sử dụng.

Bạn có thể viết biểu thức này theo cách tương tự bằng cách sử dụng toán tử bậc ba thông thường:

    $result = $condition ? $condition : 'default';

Trớ trêu thay, bằng cách bỏ đi toán hạng thứ hai của toán tử bậc ba, nó thực sự trở thành một **toán tử nhị phân** .

### [#](#chaining-ternary-operators) Chuỗi toán tử bậc ba

Sau đây, mặc dù nó có vẻ logic; không hoạt động trong PHP:

    $result = $firstCondition
        ? 'truth'
        : $elseCondition
            ? 'elseTrue'
            : 'elseFalse';

Lý do là vì toán tử bậc ba trong PHP là phép liên kết trái và do đó được phân tích cú pháp theo một cách rất lạ. Ví dụ trên luôn đánh giá `$elseCondition`phần đầu tiên, vì vậy ngay cả khi `$firstCondition`có `true`, bạn sẽ không bao giờ nhìn thấy đầu ra của nó.

Tôi tin rằng điều đúng đắn cần làm là tránh tất cả các toán tử bậc ba lồng nhau. Bạn có thể đọc thêm về hành vi kỳ lạ này trong [câu trả lời Stack Overflow này](https://stackoverflow.com/questions/20559150/ternary-operator-left-associativity/38231137#38231137) .

Hơn nữa, như PHP 7.4, việc sử dụng các cụm từ có chuỗi không có dấu ngoặc sẽ [không được dùng nữa](/blog/new-in-php-74#left-associative-ternary-operator-deprecation-rfc) .

[#](#null-coalescing-operator) toán tử  liên kết Null
----------------------------------------------------------

Bạn đã xem qua [bảng so sánh các loại](http://php.net/manual/en/types.comparisons.php) trước đó chưa? Toán tử liên kết null có sẵn kể từ PHP 7.0. Nó tương tự như toán tử bậc ba, nhưng sẽ hoạt động giống như `isset`trên toán hạng bên trái thay vì chỉ sử dụng giá trị boolean của nó. Điều này làm cho toán tử này đặc biệt hữu ích cho mảng và gán giá trị mặc định khi một biến không được đặt.

    $undefined ?? 'fallback'; // 'fallback'
    
    $unassigned;
    $unassigned ?? 'fallback'; // 'fallback'
    
    $assigned = 'foo';
    $assigned ?? 'fallback'; // 'foo'
    
    '' ?? 'fallback'; // ''
    'foo' ?? 'fallback'; // 'foo'
    '0' ?? 'fallback'; // '0'
    0 ?? 'fallback'; // 0
    false ?? 'fallback'; // false

Toán tử kết hợp null nhận hai toán hạng, làm cho nó trở thành toán tử _nhị phân_ . Nhân tiện, "kết hợp" có nghĩa là "kết hợp với nhau để tạo thành một khối hoặc toàn bộ". Sẽ cần đến hai toán hạng và quyết định sử dụng toán hạng nào dựa trên giá trị của toán hạng bên trái.

### [#](#null-coalescing-on-arrays) Null liên kết trên các mảng

Toán tử này đặc biệt hữu ích khi kết hợp với các mảng, vì nó hoạt động như thế nào `isset`. Điều này có nghĩa là bạn có thể nhanh chóng kiểm tra sự tồn tại của các khóa, thậm chí cả các khóa lồng nhau, mà không cần viết các biểu thức dài dòng.

    $input = [
        'key' => 'key',
        'nested' => [
            'key' => true
        ]
    ];
    
    $input['key'] ?? 'fallback'; // 'key'
    $input['nested']['key'] ?? 'fallback'; // true
    $input['undefined'] ?? 'fallback'; // 'fallback'
    $input['nested']['undefined'] ?? 'fallback'; // 'fallback'
    
    null ?? 'fallback'; // 'fallback'

Ví dụ đầu tiên cũng có thể được viết bằng toán tử bậc ba:

    $output = isset($input['key']) ? $input['key'] : 'fallback';

Lưu ý rằng không thể sử dụng toán tử bậc ba viết tắt khi kiểm tra sự tồn tại của các khóa mảng. Nó sẽ kích hoạt lỗi hoặc trả về boolean, thay vì giá trị của toán hạng bên trái thực.

    // Returns `true` instead of the value of `$input['key']`
    $output = isset($input['key']) ?: 'fallback' 
    
    // The following will trigger an 'undefined index' notice 
    // when $output is no array or has no 'key'.
    //
    // It will trigger an 'undefined variable' notice 
    // when $output doesn't exist.
    $output = $input['key'] ?: 'fallback';

### [#](#null-coalesce-chaining) Null kết hợp chuỗi

Toán tử liên kết null có thể dễ dàng được xâu chuỗi:

    $input = [
        'key' => 'key',
    ];
    
    $input['undefined'] ?? $input['key'] ?? 'fallback'; // 'key'

### [#](#nested-coalescing) Liên kết lồng nhau

Có thể sử dụng toán tử liên kết null trên các thuộc tính đối tượng lồng nhau, ngay cả khi một thuộc tính trong chuỗi là `null`.

    $a = (object) [
        'prop' => null,
    ];
    
    var_dump($a->prop->b ?? 'empty');
    
    // 'empty'

### [#](#null-coalescing-assignment-operator) Toán tử gán liên kết rỗng

Trong PHP 7,4, chúng ta có thể mong đợi một cú pháp thậm chí còn ngắn hơn được gọi là ["toán tử gán liên kết null"](https://wiki.php.net/rfc/null_coalesce_equal_operator) .

    // This operator will be available in PHP 7.4
    
    function (array $parameters = []) {
        $parameters['property'] ??= 'default';
    }

Trong ví dụ này, `$parameters['property']`sẽ được đặt thành `'default'`, trừ khi nó được đặt trong mảng được truyền cho hàm. Điều này sẽ tương đương với điều sau, sử dụng toán tử kết hợp null hiện tại:

    function (array $parameters = []) {
        $parameters['property'] = $parameters['property'] ?? 'default';
    }

[#](#spaceship-operator) toán tử  tàu vũ trụ
-------------------------------------------------

toán tử  tàu vũ trụ, trong khi có một cái tên khá kỳ lạ, có thể rất hữu ích. Đó là một toán tử được sử dụng để so sánh. Nó sẽ luôn luôn trở lại một trong ba giá trị: `0`, `-1`hoặc `1`.

`0`sẽ được trả về khi cả hai toán hạng bằng nhau, `1`khi toán hạng bên trái lớn hơn và `-1`khi toán hạng bên phải lớn hơn. Hãy xem một ví dụ đơn giản:

    1 <=> 2; // Will return -1, as 2 is larger than 1.

Ví dụ đơn giản này không phải là tất cả những gì thoát, phải không? Tuy nhiên, toán tử tàu vũ trụ có thể so sánh nhiều hơn các giá trị đơn giản!

    // It can compare strings,
    'a' <=> 'z'; // -1
    
    // and arrays,
    [2, 1] <=> [2, 1]; // 0
    
    // nested arrays,
    [[1, 2], [2, 2]] <=> [[1, 2], [1, 2]]; // 1
    
    // and even casing.
    'Z' <=> 'z'; // -1

Thật kỳ lạ, khi so sánh cách viết hoa của chữ cái, chữ cái viết thường được coi là cao nhất. Có một lời giải thích đơn giản. So sánh chuỗi được thực hiện bằng cách so sánh từng ký tự. Ngay sau khi một ký tự khác nhau, giá trị ASCII của chúng sẽ được so sánh. Vì các chữ cái thường đứng sau các chữ cái viết hoa trong bảng ASCII nên chúng có giá trị cao hơn.

### [#](#comparing-objects) So sánh các đối tượng

Người điều khiển tàu vũ trụ gần như có thể so sánh bất cứ thứ gì, thậm chí cả các vật thể. Cách các đối tượng được so sánh dựa trên loại đối tượng. Các lớp PHP dựng sẵn có thể xác định phép so sánh của riêng chúng, trong khi các đối tượng vùng người dùng được so sánh dựa trên các thuộc tính và giá trị của chúng.

Khi nào bạn muốn so sánh các đối tượng mà bạn yêu cầu? Thực ra có một ví dụ rất rõ ràng: ngày tháng.

    $dateA = DateTime::createFromFormat('Y-m-d', '2000-02-01');
    
    $dateB = DateTime::createFromFormat('Y-m-d', '2000-01-01');
    
    $dateA <=> $dateB; // Returns 1

Tất nhiên, so sánh ngày tháng chỉ là một ví dụ, nhưng là một ví dụ rất hữu ích.

### [#](#sort-functions) Sắp xếp các chức năng

Một công dụng tuyệt vời cho toán tử này là sắp xếp các mảng. Có khá [nhiều cách](http://php.net/manual/en/array.sorting.php) để sắp xếp một mảng trong PHP và một số phương pháp này cho phép một hàm sắp xếp do người dùng xác định. Chức năng này có để so sánh hai yếu tố, và trở lại `1`, `0` hoặc `-1` dựa trên vị trí của họ.

Một trường hợp sử dụng tuyệt vời cho người điều hành tàu vũ trụ!

    $array = [5, 1, 6, 3];
    
    usort($array, function ($a, $b) {
        return $a <=> $b;
    });
    
    // $array = [1, 3, 5, 6];

Để sắp xếp giảm dần, bạn chỉ cần đảo ngược kết quả so sánh:

    usort($array, function ($a, $b) {
        return -($a <=> $b);
    });
    
    // $array = [6, 5, 3, 1];

### Other
 - [What's the Difference Between ?? and ?: in PHP?](https://www.designcise.com/web/tutorial/whats-the-difference-between-null-coalescing-operator-and-ternary-operator-in-php)


<div style="text-align: right">Theo <a href="https://stitcher.io/blog/shorthand-comparisons-in-php">stitcher.io</a></div>