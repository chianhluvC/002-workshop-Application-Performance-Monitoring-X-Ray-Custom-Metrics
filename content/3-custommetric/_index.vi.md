---
title : "Theo dõi hiệu năng với CloudWatch Custom Metrics"
date: 2025-07-06 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

Trong phần này chúng ta sẽ theo dõi hiệu năng của ứng dụng bằng CloudWatch Custom Metrics. Xem thông tin của custom metric và vẽ biểu đồ ProcessingTime dạng line,…

1. Truy cập vào [trang quản lý CloudWatch](https://console.aws.amazon.com/cloudwatch/home/)

![metric](/images/3-custommetric/001-metric1.png)

2. Phần Metrics 
+ Click chọn vào All metrics 
+ Sau đó click chọn vào MyApp

![metric](/images/3-custommetric/002-metric2.png)

3. Tiếp tục click chọn vào Service

![metric](/images/3-custommetric/003-metric3.png)

4. Tiếp tục click chọn vào CheckoutService và sau đó chọn Line

![metric](/images/3-custommetric/004-metric4.png)

5. Biểu đồ dạng line của custom metric sẽ xuất hiện. Ở đây chúng ta sẽ quan sát thấy sự lên xuống theo thời gian của processing time. Có thể tuỳ chỉnh theo các khoảng thời gian khác nhau. Từ đó xác định các vùng thời gian có thời gian xử lý chưa tối ưu và lên các phương án khắc phục.

![metric](/images/3-custommetric/005-metric5.png)

Chọn vào các biểu đồ khác, ví dụ ở đây là Stacked area

![metric](/images/3-custommetric/006-metric6.png)

Như vậy là chúng ta đã kết thúc phần theo dõi hiệu năng với CloudWatch Custom Metrics. Từ các kiến thức phần này, phần nào đó sẽ giúp bạn có cái nhìn trực quan về Custom Metrics. Qua các thông số cũng như biểu đồ, giúp chúng ta thực hiện phần tiếp theo tốt hơn.