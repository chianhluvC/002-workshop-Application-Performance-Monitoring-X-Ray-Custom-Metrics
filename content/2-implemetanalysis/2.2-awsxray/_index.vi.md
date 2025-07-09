---
title : "Phân tích và kiểm tra bằng AWS X-Ray"
date: 2025-07-06 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

### Phân tích và kiểm tra bằng AWS X-Ray

Trong bước này chúng ta sẽ tiến hành phân tích kiểm tra ứng dụng serverless bằng AWS X-Ray. Từ các thông số quan trọng và đặc biệt là latency để đưa ra các giải pháp phù hợp làm tăng hiệu suất.

1. Truy cập vào trigger vừa tạo và copy API endpoint

![xray](/images/2-implemetanalysis/014-xray1.png)

2. Dùng postman test API endpoint vừa tạo (test khoảng 5 đến 7 lần)

![xray](/images/2-implemetanalysis/015-xray2.png)

3. Truy cập vào trang quản lý [trace map](https://console.aws.amazon.com/console/home/)

+ Quan sát biểu đồ gồm 3 thành phần chính: Client, Lambda Context và Lambda Function
+ Click vào Lambda Function

![xray](/images/2-implemetanalysis/016-xray3.png)

4. Xuất hiện các thông số của Lambda Funtion vừa chọn, gồm các lựa chọn về Metrics, Alerts, Response time distribution và click chọn vào Metrics

+ Xem các thông số Latency (avg), Request, Faults
+ Xem các biểu đồ Latency (avg), Request, Faults

![xray](/images/2-implemetanalysis/017-xray4.png)

5. Click chọn vào mục Response time distribution, nhận thấy response time trung bình ở đây là 4%

![xray](/images/2-implemetanalysis/018-xray5.png)

6. Click chọn vào View traces để xem chi tiết các traces

![xray](/images/2-implemetanalysis/019-xray6.png)

7. Giao diện Traces xuất hiện, quan sát các traces và xem các thông số quan trọng

![xray](/images/2-implemetanalysis/020-xray7.png)


8. Click chọn vào trace bất kì để xem chi tiết 

![xray](/images/2-implemetanalysis/021-xray8.png)


9. Quay lại giao diện traces và click chọn vào Refine query by

![xray](/images/2-implemetanalysis/022-xray9.png)

10. Phần User annotations chọn vào aws:responseLatency. Đây là một thông số rất quan trọng quyết định request trung bình mất bao lâu để xử lý. Từ đó chúng ta sẽ đánh giá được hiệu năng của ứng dụng

![xray](/images/2-implemetanalysis/023-xray10.png)

11. Bảng thông số các traces được sắp xếp theo chỉ số Latency giảm dần. Quan sát bảng này nhận thấy ứng dụng đang chạy có latency cao nhất là 312.446. Từ đó có thể chuẩn bị cho các trường hợp, quá tải của ứng dụng. Khi mà các traces dần có latency vượt ngưỡng

![xray](/images/2-implemetanalysis/024-xray11.png)

Vậy là phần triển khai theo dõi và phân tích này đã kết thúc, phần sau chúng ta sẽ tới phần theo dõi hiệu năng với CloudWatch Custom Metrics.