---
layout: single
title: "Những điều dễ nhầm lẫn trong javascript"
desc: "Ngôn ngữ lập trình chính mà tôi sử dụng là php, nhưng tôi cũng có dùng js trong một khoảng thời gian. Vì không có sử dụng bài bản và thường xuyên nên dạo này tôi có học lại javascript và thấy có rất nhiều thứ khiến mình dễ nhầm lẫn."
keywords: "javascript, js"
categories: [javascript]
tag: [javascript]
---

# Những điều dễ nhầm lẫn trong javascript

### this
 `this` là đại diện cho object gọi hàm. Tuy nhiên, với trường hơp không chỉ định object gọi hàm thì mặc định object này sẽ là window object. Nhưng mà trường hợp bạn bật mode `use strict` lên thì kết quả sẽ là `undefined`
```javascript
    const foo = {
      bar: function() {
        // caller is foo.bar()
        console.log(this); // foo object
          
        const baz = function() {
          // due to caller is baz(), so object wasn't set
          console.log(this); // window object
        }
        baz();
        
        const qux = function() {
          'use strict';
          // due to caller is qux(), so object wasn't set + strict mode on
          console.log(this); // undefined
        }
        qux();
      }
    }
    foo.bar();
```    


また、classの場合は`use strict`の指定なしでも厳格モードになる。以下は[引用](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Classes#%E3%83%97%E3%83%AD%E3%83%88%E3%82%BF%E3%82%A4%E3%83%97%E3%81%A8%E9%9D%99%E7%9A%84%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89%E3%81%AB%E5%AF%BE%E3%81%99%E3%82%8B_this_%E3%81%AE%E7%B5%90%E3%81%B3%E4%BB%98%E3%81%91)

> this に値が付けられずに静的メソッドまたはプロトタイプメソッドが呼ばれると、this の値はメソッド内で undefined になります。たとえ "use strict" ディレクティブがなくても同じふるまいになります。なぜなら、class 本体の中のコードは常に Strict モードで実行されるからです。
```javascript
    class Foo {
      bar() {
        // 呼び出し元はfoo.bar()
        console.log(this); // Foo object
        
        const baz = function() {
          // 呼び出し元はbaz()でオブジェクトの指定がないかつクラス内なので厳格モード
          console.log(this); // undefined
        }
        baz();
      }
    }
    const foo = new Foo();
    foo.bar();
```


call、apply、bindでthisを指定することができる
```javascript
    const foo = {
      bar: function() {
        const baz = function() {
          // 呼び出し元はbaz.apply(this)。
          // applyに指定しているthisの呼び出し元はfoo.bar()なのでfooとなる
          console.log(this) // foo object
        }
        baz.apply(this)
    
        const qux = function() {
          // 呼び出し元はqux()で、quxにはbind(this)が指定されている。
          // bindに指定されているthisの呼び出し元はfoo.bar()なのでfooとなる
          console.log(this) // foo object
        }.bind(this)
        qux();
      }
    }
    foo.bar();
```


また、アロー関数内のthisはアロー関数が定義されているスコープに基づく。以下は[引用](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/Arrow_functions#call%E3%80%81apply%E3%80%81bind)

> アロー関数は、そのアロー関数が定義されているスコープに基づいて "this" を確立する
```javascript
    const foo = {
      bar: function() {
        const baz = () => {
          // 呼び出し元はbaz()
          // bazが宣言されているbar()の呼び出し元はfoo.bar()なのでfooとなる
          console.log(this); // foo object
        }
        baz();
      }
    }
    foo.bar();
```

![](https://zenn.dev/images/copy-icon.svg)

[](#%E3%82%B7%E3%83%A3%E3%83%AD%E3%83%BC%E3%82%B3%E3%83%94%E3%83%BC)シャローコピー
---------------------------------------------------------------------------

以下は[引用](https://developer.mozilla.org/en-US/docs/Glossary/Shallow_copy)の翻訳。引用にあるコピー操作ではシャローコピー(浅いコピー)となることがあり、コピー先を変更することでコピー元に影響を与えることがある

> JavaScript では、標準的な組み込みのオブジェクトコピー操作 (スプレット構文, concat(), slice(), Array.from(), Object.assign(), Object.create()) はすべて、ディープコピーではなくシャローコピーを作成します。

以下の例では、nameは変わらないが、schoolは書きかわる
```javascript
    const user = {
      name: "user",
      school: { name: "school" }
    }
    
    const user2 = {...user}
    
    user2.name = "user2"
    user2.school.name = "school2"
    
    console.log(user); // {name: "user", school: {name: "school2"} }
    console.log(user2); // {name: "user2", school: {name: "shool2"} }
```


ディープコピー(深いコピー）を使用することで回避する。以下は[引用](https://developer.mozilla.org/ja/docs/Glossary/Deep_copy)

> Javascript のオブジェクトのディープコピーを作成する一つの方法は、そのオブジェクトが シリアライズ 可能であれば JSON.stringify() でオブジェクトを JSON 文字列に変換し、 JSON.parse() で文字列から（完全に新しい） Javascript のオブジェクトに変換することです。

[](#new%E6%BC%94%E7%AE%97%E5%AD%90)new演算子
-----------------------------------------

クラスでなく、関数に対しても使うことができる。関数がnew演算子で呼ばれるとき、コンストラクタ関数という。コンストラクタ関数として呼び出すとオブジェクトが生成される
```javascript
    const Foo = function() {
      this.foo = "bar"
      return 1;
    }
    
    // 通常の関数として呼び出す
    console.log(Foo()); // 1　
    
    // コンストラクタ関数として呼び出す
    console.log(new Foo()); // Foo{foo: "bar"}オブジェクト
```

以下はnew演算子のドキュメント

構文の[引用](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/new#%E6%A7%8B%E6%96%87)

> new constructor\[(\[arguments\])\]  
> 引数 constructor  
> オブジェクトインスタンスの型を指定するクラスまたは関数です。

解説の[引用](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/new#%E8%A7%A3%E8%AA%AC)

> 1.  空のプレーンな JavaScript オブジェクトを生成します。
> 2.  新しいオブジェクトにプロパティ (**proto**) を追加し、コンストラクター関数のプロトタイプオブジェクトに結びつけます。
> 3.  新しく生成されたオブジェクトインスタンスを this コンテキストとして結びつけます。 （すなわち、コンストラクター関数内の this へのすべての参照は、最初のステップで作成されたオブジェクトを参照するようになります。）
> 4.  関数がオブジェクトを返さない場合は this を返します。

コンストラクタ関数の戻り値として、オブジェクトを返す場合とそうでない場合で挙動が異なる

オブジェクトを返さない例
```javascript
    function Foo() {
      this.bar = 1;
    }
    
    const foo = new Foo();
    console.log(foo); // Foo { bar: 1 }
```

オブジェクトを返す例
```javascript
    function Foo() {
      this.bar = 1;
      return { baz: 1 };
    }
    
    const foo = new Foo();
    console.log(foo); // { baz: 1 }
    console.log(foo.bar) // undefined
```


[](#%E3%83%97%E3%83%AD%E3%83%88%E3%82%BF%E3%82%A4%E3%83%97%E3%83%99%E3%83%BC%E3%82%B9)プロトタイプベース
-----------------------------------------------------------------------------------------------

objectやarrayをconsole.logしたときに見かける`[[Prototype]]`や`__proto__`の正体。知らないと困るというケースがあるかどうかはわからないが、以下あたりを１度読んでおくと雰囲気がわかる

[図で理解するJavaScriptのプロトタイプチェーン - Qiita](https://qiita.com/howdy39/items/35729490b024ca295d6c)

[継承とプロトタイプチェーン - JavaScript | MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Inheritance_and_the_prototype_chain#inheritance_with_the_prototype_chain)

ただ、classから作ったオプジェクトもプロトタイプベースであることは変わらないので理解はしておくべき

[](#%E5%A4%89%E6%95%B0%E3%82%84%E9%96%A2%E6%95%B0%E3%81%AE%E5%B7%BB%E3%81%8D%E4%B8%8A%E3%81%92(hoisting))変数や関数の巻き上げ(Hoisting)
-----------------------------------------------------------------------------------------------------------------------------

以下はドキュメントの[引用](https://developer.mozilla.org/ja/docs/Glossary/Hoisting)

> 変数や関数の宣言が物理的にコードの先頭に移動されることを示唆していますが、実際にはそうではありません。変数や関数の宣言はコンパイル時にメモリに格納されますが、コード内で入力された場所は変わりません

ただし

> 定義のみが巻き上げられ、初期化はそうでありません。変数が使用された後に定義や初期化された場合、値は undefined になります

関数の場合、宣言の前に読んでもエラーにはならない
```javascript
    foo();
    
    function foo() {
      console.log("foo");
    }
```

変数の場合
```javascript
    foo(); // Uncaught TypeError: foo is not a function
    
    var foo = () => console.log("foo");
```

引用のとおり定義のみが巻き上げられるので、実行時は以下のイメージとなり、変数としては存在するが、関数として呼ぼうとするとエラーになる
```javascript
    var foo;
    
    foo(); // この時点でfoo は undefined
    
    foo = () => console.log("foo")
```

[](#%E3%81%9D%E3%81%AE%E4%BB%96)その他
-----------------------------------

オブジェクトを返すアロー関数の書き方。以下は[引用](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/Arrow_functions#%E9%AB%98%E5%BA%A6%E3%81%AA%E6%A7%8B%E6%96%87)

> オブジェクトリテラル式を返す場合は、式の周りに括弧が必要です。
```javascript
    // NG
    const foo = () => {bar: "baz"}
    
    // OK
    const foo = () => ({bar: "baz"})
```    


<div style="text-align: right">Theo <a href="https://zenn.dev/nrikiji/articles/b7bf2d1f527bff">zenn</a></div>
