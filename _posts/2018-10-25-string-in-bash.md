---
layout: single
title:  "Kinh nghiệm làm việc với string trong bash"
desc: "Kinh nghiệm làm việc với string trong bash"
keywords: "bash"
categories: [bash]
tag: [bash]
---


#### Replace character ở cuối string
 - Ta đặt dấu `?` đằng sau dấu `%` phía sau string
 ví dụ:  
```
 str="abc, xyz,"
 echo ${str1%?}
 → abc, xyz
```
　- Muốn xóa bao nhiêu kí tự, ta dùng bấy nhiêu dấu `?`
ví dụ:  
```
 str="abc, xyz, ;"
 echo ${str1%???}
 → abc, xyz
```

#### Lấy ra substring trong string
 - Cấu trúc là `${str:x:y}` với x là vị trí bắt đầu cắt và y là số lượng cần cắt
 ví dụ:  
```
 str="abc, xyz"
 echo ${str:1:2}
 → bc
```

#### Replace character có trong string
 - Cấu trúc là `${str/x/y}` với x là character bị replace và y là character sẽ dc thay vào
 ví dụ:  
```
 str="abc, xbz"
 echo ${str/b/y}
 → ayc, xyz
```

#### Convert string thành array
 - Ví dụ dưới đây sẽ là sflit string thành array dùng dấu `,` để phân tách
```
 str="abc, xbz"
 IFS=','; arrStr=($str); unset IFS;
 echo ${arrStr[0]};
 → abc
```

#### Xuất nội dung file vào variable
 - Ta dùng dấu ``` để phân tách, chú ý trách nhầm lẫn với dấu nháy đơn `'`
```
message=`cat $REPORT_FILE`
echo $message
```