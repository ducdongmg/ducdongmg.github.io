---
layout: single
title:  "Tạo snippet như một template trong vs code"
desc: "Truy cập vào từ `File > Preferences > Configure User Snippets`, bạn sẽ thấy vscode cung cấp cho ta nhiều option khác nhau"
keywords: "vscode, tool"
categories: [tool]
tag: [vscode, tool]
---

Tạo snippet như một template trong vs code
=====================================================

Truy cập vào từ `File > Preferences > Configure User Snippets`, bạn sẽ thấy vscode cung cấp cho ta nhiều option khác nhau như: 
tạo Snippet cho 1 repository, cho một ngôn ngữ lập trình, hay dùng chung. Tùy vào lựa chọn của bạn mà Snippet này sẽ có phạm vi sử dụng tương ứng.

Tiếp theo bạn cần khai báo nội dung cho snippet này với format sau:
```
"Giới thiệu chung tại phần title này": {
    "scope": "javascript,markdown",
    "prefix": "outlog",
    "body": [
        "console.log('abc');",
        "//def"
    ],
    "description": "Giới thiệu chi tiết về snippet này"
}
```

 - `title`: Giới thiệu chung về snippet này
 - `scope`: phạm vi bạn muốn snippet này có hiệu lực, ví dụ: javascript
 - `prefix`: mã code mà khi gỗ nó thì vs code sẽ gợi ý cho bạn dùng snippet này
 - `body`: Là nội dung được hiển thị ra khi bạn gõ lệnh được khai báo ở `prefix`
 - `description`: Giới thiệu chi tiết về snippet này


Cách đơn giản để tạo khai báo cho snippet này là dùng tool của https://snippet-generator.app/. Bạn chỉ cần nhập các thông tin cần thiết vào là nó sẽ tự động generate ra nội dung cho bạn.
Sau đó copy vào fie khai báo là xong.
