---
title : "Tạo bảng điều khiển"
date: 2025-07-06
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---

Trong bước này chúng ta sẽ tiến hành tạo bảng điều khiển, từ đó quan sát các thông số quan trọng tại thời điểm tạo bảng.

1. Truy cập vào giao diện của Cloud Watch
	+ Click chọn vào Dashboards
	+ Click chọn vào Create dashboard

![dash](/images/4-dashboardalarm/001-dash1.png)

2. Giao diện Create new dashboards sẽ xuất hiện
+ Nhập tên dashboards là **ProcessingTime**
+ Click chọn vào Create dashboard

![dash](/images/4-dashboardalarm/002-dash2.png)

3. Giao diện Add widget sẽ xuất hiện
+ Phần Data source types chọn **Cloudwatch**
+ Phần Data type chọn ** Metrics**
+ Phần Widget type chọn **Line**
+ Click chọn vào Next

![dash](/images/4-dashboardalarm/003-dash3.png)

4. Hộp thoại Add metric graph sẽ xuất hiện 
+ Chọn service như hình 
+ Click chọn vào Create widget

![dash](/images/4-dashboardalarm/004-dash4.png)

5. Sau khi tạo xong dashboard, truy cập lại trang quản lý dashboard và xem các dashboards đã tạo

![dash](/images/4-dashboardalarm/005-dash5.png)

![dash](/images/4-dashboardalarm/006-dash6.png)

Vậy là chúng ta đã tạo và theo dõi các thông số qua dashboard, tiếp theo chúng ta sẽ đến với các bước tạo hệ thống cảnh báo.