---
layout: single
title:  "[git] diff 2 branch"
desc: ""
keywords: "git"
categories: [git]
tag: [git]
---

Khi có nhu cầu tìm hiểu xem branch hiện tại (`develop_branch`)  có những thay đổi gì so với branch gốc (`master_branch`) thì có thể làm như:

**Bước 1**: Chuẩn bị
 Tại folder của repository, mở git command (ở đây tôi dùng tool `git bash`)

**Bước 2**: Nguyên tắc
 Chúng ta cần tìm ra các file đã thay đổi. Và với các file này, chúng ta sẽ xem chúng đã được thay đổi như thế nào.

1. Show danh sách các file có thay đổi
    `git diff --name-only origin/master_branch..origin/develop_branch`

2. Hiển thị các thay đổi đối với 1 file cụ thể:
    ` git diff -w --ignore-blank-lines origin/master_branch..origin/develop_branch file_path`

    ví dụ: ` git diff -w --ignore-blank-lines origin/master_branch..origin/develop_branch app/file_name.php`

**Bước 3**: Tạo file bash 
Vì có rất nhiều file bị thay đổi nên ta sẽ tạo ra 1 file bash để check lần lượt từng file đã thay đổi với đầu vào là danh sách các file được tìm thấy ở bước 2.

1. Tạo file `diff_branch.sh` với nội dung như bên dưới

```
#!/bin/bash

file=(`cat "$1"`)
for line in "${file[@]}"; do	
	name="diff/${line}_diff.txt"
	mkdir -p "$(dirname "$name")" && touch  "$name"
	git diff -w --ignore-blank-lines origin/master_branch..origin/develop_branch $line | sed "s/+/'+/" | sed -e "s/  /\t/g" > $name
done
```

Giải thích:
 - file=(`cat "$1"`) : đưa danh sách các file thay đổi vào variable file
 - `mkdir -p` : tạo folder và các sub folder cũng như file tương ứng. 
  Ví dụ ta thay đổi 1 file tại path: `app/file_name.php` thì với command như trong bash thì nó sẽ tạo folder như sau `diff/app/file_name.php`
 - `git diff -w ...`: diff file lấy ra các line được thêm hoặc xóa 

 2. Tạo file `changed_file.txt` chứa danh sách các file bị thay đổi trong branch hiện tại
 `git diff --name-only origin/master_branch..origin/develop_branch > changed_file.txt`
  
 3. Run bash phía trên
 `sh diff_branch.sh changed_file.txt`

 Lưu ý: Đối với các file bị xóa đi ở branch hiện tại, khi diff sẽ xuất hiện error, bạn có thể bỏ qua nó và để bash tiếp tục chạy