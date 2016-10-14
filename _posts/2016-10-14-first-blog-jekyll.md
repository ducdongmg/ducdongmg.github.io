---
layout: single
title:  "Dùng Jekyll làm blog"
desc: "jekyll using"
keywords: "jekyll,blog,first"
---

# Cài đặt
- Bạn nào muốn cài đặt từ đầu thì có thể tham khảo các bước trên trang chủ của [Jekyll](https://jekyllrb.com/docs/home/)
- Ngoài ra cũng có rất nhiều bài viết bằng tiếng việt như [Tự tạo một Blog Lập trình với Jekyll & Github Pages](http://dev.ethanify.me/misc/create-blog-with-jekyll) các bạn cũng có thể search ra rất nhiều.

# Theme
 - Hiện tại có rất nhiều theme có thể sử dụng, các bạn có thể tham khảo tại
 - Blog này mình dùng theme [Minimal Mistakes Jekyll Theme](https://github.com/mmistakes/minimal-mistakes/). Các bạn có thể nhanh chóng tạo blog này bằng [Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) có trên trang chủ.



# Fix Bug
 Trong quá trình sử dụng Jekyll có thể các bạn sẽ gặp rất nhiều lỗi nên có thể tham khảo một vài lỗi sau:

 1. GitHub Metadata

  Tại Terminal, nếu chỉ gọi jekyll serve thì có thể gặp lỗi `GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.`. Lỗi này xảy ra do server tại local của ta không có biến môi trường `$JEKYLL_GITHUB_TOKEN`. Để không gặp lỗi này nữa, ta chạy lệnh sau:

  ```javascript
  $ JEKYLL_GITHUB_TOKEN=jkghtoken jekyll serve
```

  Trong đó `jkghtoken` là 1 chuỗi bất kỳ, thế nào cũng được.

 2. Https
