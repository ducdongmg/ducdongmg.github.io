---
layout: single
title:  "LÀM SAO ĐỂ SỬ DỤNG NHIỀU TÀI KHOẢN GITHUB TRÊN CÙNG MỘT MÁY TÍNH?"
desc: "LÀM SAO ĐỂ SỬ DỤNG NHIỀU TÀI KHOẢN GITHUB TRÊN CÙNG MỘT MÁY TÍNH?"
keywords: "git"
categories: [git]
tag: [git]
---

LÀM SAO ĐỂ SỬ DỤNG NHIỀU TÀI KHOẢN GITHUB TRÊN CÙNG MỘT MÁY TÍNH?

[Tham khảo bài viết từ 2kvn](https://2kvn.com/lam-sao-de-su-dung-nhieu-tai-khoan-github-tren-cung-mot-may-tinh-p5f32333531)


ping đến từng tài khoản xem đã connect được chưa

`$ ssh -vT git@github.com`

`$ ssh -vT git@gitlab.com`

 Sau khi sepup trong thì khi commit, git sẽ dùng email và user name được thiết lập ở global. Nếu cần dùng thông tin riêng cho từng repository thì cần thiết lập lại user name và email cho local project. 

```
git config --local user.name "My Name"

git config --local user.email "myemail@example.com"
```

 Link tham khảo từ [stackoverflow](https://stackoverflow.com/questions/46941346/how-to-know-the-git-username-and-email-saved-during-configuration)


 Nếu gặp lỗi `Permission denied` thì tham khảo bài này từ [github docs](https://docs.github.com/en/enterprise-server@3.3/authentication/troubleshooting-ssh/error-permission-denied-publickey)