---
layout: single
title:  "Dùng Jekyll làm blog"
desc: "jekyll using"
excerpt: "Jekyll là một phần mềm được viết trên Ruby giúp tạo ra các website tĩnh"
keywords: "jekyll, blog"
categories: [blog]
tags: [jekyll]
---

Jekyll là một phần mềm được viết trên Ruby giúp tạo ra các website tĩnh từ các file Markdown hoặc html. Nó hơi khó sử dụng với người mới nhưng với việc tạo các website cá nhân, blog, trang tài liệu thì khả năng sinh web tĩnh cho phép nó đạt hiệu suất vượt trội. Bạn có thể tùy biến đủ kiểu với website của mình và lưu trữ nó trên chính Github - dịch vụ lưu trữ mã nguồn một cách hoàn toàn miễn phí. Một ưu điểm nữa là web tĩnh sẽ cho phép website của bạn miễn nhiễm với các mã độc, sự tấn công của hacker.

# Cài đặt
- Bạn nào muốn cài đặt từ đầu thì có thể tham khảo các bước trên trang chủ của [Jekyll](https://jekyllrb.com/docs/home/).
Môi trường cần thiết là phải có cài đặt Ruby (vì Jekyll được viết bằng Ruby). Trên windows bạn có thể tham khảo theo các bước tại [jekyll-windows](http://jekyll-windows.juthilo.com/)
Trong quá trình cài đặt nhiều khả năng bạn sẽ gặp phải nhiều lỗi khác nhau, các bạn có thể tham khảo một vài lỗi mình ghi phía dưới và cách khắc phục.
- Ngoài ra cũng có rất nhiều bài viết bằng tiếng việt như [Tự tạo một Blog Lập trình với Jekyll & Github Pages](http://dev.ethanify.me/misc/create-blog-with-jekyll) các bạn cũng có thể search ra rất nhiều.

# Theme
 - Hiện tại có rất nhiều theme có thể sử dụng, các bạn có thể tham khảo tại [Jekyll Themes](https://github.com/jekyll/jekyll/wiki/Themes) hay trực quan hơn tại [jekyllthemes](http://jekyllthemes.org/) hoặc [themes jekyllrc](http://themes.jekyllrc.org/)
 - Blog này mình dùng theme [Minimal Mistakes Jekyll Theme](https://github.com/mmistakes/minimal-mistakes/). Các bạn có thể nhanh chóng tạo blog này bằng [Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) có trên trang chủ.

# Fix Bug
 Trong quá trình sử dụng Jekyll có thể các bạn sẽ gặp rất nhiều lỗi nên có thể tham khảo một vài lỗi sau:

 1. GitHub Metadata

  Tại Terminal, nếu chỉ gọi jekyll serve thì có thể gặp lỗi `GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.`. Lỗi này xảy ra do server tại local của ta không có biến môi trường `$JEKYLL_GITHUB_TOKEN` cũng như là tính bảo mật.
  Tham khảo tại link sau để  [fix-github-metadata-error](http://knightcodes.com/miscellaneous/2016/09/13/fix-github-metadata-error.html)

 2. Https
  Khi cài đặt 1 package nào đó, bạn sẽ dễ gặp lỗi đại loại `Unable to download data from https://rubygems.org/ - SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (https://api.rubygems.org/specs.4.8.gz)`.
  Bạn có thể làm theo cách được ghi tại [stackoverflow](http://stackoverflow.com/a/27641786)

 3. Devkit
  Error khi bạn chưa install devkit và gặp lỗi `Please update your PATH to include build tools or download the DevKit` . Tham khảo tại [stackoverflow](http://stackoverflow.com/a/10695190)


<!-- reference -->
[trucnt]: https://trucnt.com/jekyll/cai-dat-jekyll-windows/
[trucnt jekyll]: https://trucnt.com/jekyll/tao-blog-jekyll/
[goyllo]: https://www.goyllo.com/