---
title : "Tạo hệ thống cảnh báo"
date: 2025-07-06
weight : 2 
chapter : false
pre : " <b> 4.2 </b> "
---


Trong bước này, chúng ta sẽ thực hiện tạo hệ thống cảnh báo. Dịch vụ giúp chúng ta thực hiện Cloudwatch Alarm.

1. Truy cập vào trang quản lý cloud watch
+ Phần Alarms click chọn vào **In alarm**
+ Click chọn vào **Create alarm**

![alarm](/images/4-dashboardalarm/007-alarm1.png)

2. Ở giao diện step 1, chúng ta chọn vào **Select metrics**

![alarm](/images/4-dashboardalarm/008-alarm2.png)

3. Trong giao diện Select metric
+ Chọn vào mục Browse
+ Click chọn vào dịch vụ đã tạo trước đó
+ Click chọn vào Select metric

![alarm](/images/4-dashboardalarm/009-alarm3.png)

4. Sau khi chọn xong, metric đã chọn sẽ xuất hiện và bên cạnh đó là các thông số

![alarm](/images/4-dashboardalarm/010-alarm4.png)

5. Chỉnh các thông số như hình bên dưới

![alarm](/images/4-dashboardalarm/011-alarm5.png)

6. Kéo xuống them một đoạn
+ Phần Threshold type click chọn vào **Static**
+ Phần Whenever ProcessingTime is… click chọn vào **Greater**
+ Phần than… điền vào 350
+ Phần Datapoints to alarm: điền từ **3** đến hết **3**

![alarm](/images/4-dashboardalarm/012-alarm6.png)

7. Kéo xuống đoạn cuối, sau đó click chọn **Next**

![alarm](/images/4-dashboardalarm/013-alarm7.png)

8. Giao diện Step 2 sẽ xuất hiện
+ Phần Alarm state trigger chọn **In alarm**
+ Phần Send a notification to the following SNS topic click chọn **Create new topic**
+ Phần Create new topic… điền tên của topic 
+ Phần Email endpoints that will receive the notification… chọn email của bạn (nhớ xác thực khi AWS gửi mail)
+ Click chọn vào Create topic

![alarm](/images/4-dashboardalarm/014-alarm8.png)

9. Kéo xuống đoạn cuối và click chọn **Next**

![alarm](/images/4-dashboardalarm/015-alarm9.png)

10.	Giao diện Step 3 sẽ xuất hiện

+ Phần Alarm name điền **HighProcessingLatency**
+ Phần Edit điền mô tả là **Alert when Lambda ProcessingTime > 350ms avg in 1 mins**
+ Click chọn **Next**

![alarm](/images/4-dashboardalarm/016-alarm10.png)

11.	Giao diện phần overview xuất hiện, xem lại các thông số đã tạo và click vào **Create alarm**

![alarm](/images/4-dashboardalarm/017-alarm11.png)

12.	Trang quản lý Alarms sẽ xuất hiện, click chọn vào alarm vừa tạo

![alarm](/images/4-dashboardalarm/018-alarm12.png)

13.	Xem chi tiết alarm, các thông số quan trọng

![alarm](/images/4-dashboardalarm/019-alarm13.png)

14.	Dùng postman test với một lượng request lớn

![alarm](/images/4-dashboardalarm/020-alarm14.png)

15.	Quay lại trang alarm và xem chi tiết alarm đã tạo

![alarm](/images/4-dashboardalarm/021-alarm15.png)

16.	Đợi mail cảnh báo hệ thống từ AWS

![alarm](/images/4-dashboardalarm/022-alarm16.png)

Vậy là chúng ta đã hoàn thành tạo hệ thống cảnh báo, ở phần sau chúng ta sẽ đi tìm hiểu cách phân tích chi phí và tối ưu hệ thống.