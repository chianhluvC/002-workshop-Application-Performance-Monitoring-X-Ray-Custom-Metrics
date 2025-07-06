---
title : "Phân tích chi phí và đề xuất tối ưu"
date: 2025-07-06 
weight : 5 
chapter : false
pre : " <b> 5. </b> "
---


#### Phân tích chi phí

1. Tổng quan các thành phần phát sinh chi phí

| **Dịch vụ**                  | **Tính phí theo**                                     | **Ước tính/tháng (ví dụ 100k requests)**     |
|-----------------------------|--------------------------------------------------------|-----------------------------------------------|
| **AWS Lambda**              | Số request + thời gian chạy (GB-seconds)              | ~ $2–$5                                       |
| **AWS X-Ray**               | Số trace segment (đo từng invoke)                     | ~ $2.50 / 1 triệu trace segment               |
| **CloudWatch Logs**         | GB log lưu trữ + log event ingest                     | ~ $0.50–$1 / GB                                |
| **CloudWatch Custom Metrics** | $0.30 / metric / tháng (sau 10 miễn phí)             | ~ $0.60 cho 2 metric                           |
| **CloudWatch Alarms**       | $0.10 / alarm / tháng                                 | ~ $0.10–$0.50                                 |
| **SNS (email alert)**       | Miễn phí với email (SMTP)                             | $0                                            |


2. Phân tích cụ thể theo giải pháp bạn triển khai

| **Thành phần**                | **Ghi chú**                                                              | **Chi phí**               |
|------------------------------|---------------------------------------------------------------------------|----------------------------|
| **Lambda MonitorFunction**   | Gọi 100,000 lần/tháng, thời gian trung bình 600ms, 128MB RAM             | ≈ $2.50                    |
| **X-Ray**                    | Ghi trace mỗi lần invoke (100k trace segment)                            | ≈ $2.50                    |
| **CloudWatch Logs**          | Log latency + custom metric EMF                                          | ≈ $1–$2 (tuỳ số lượng log/JSON size) |
| **Custom Metrics: ProcessingTime** | Ghi bằng EMF format → tính phí theo số lượng metric name           | ~$0.30–$0.60              |
| **Alarm CloudWatch + SNS**   | 1 alarm, 1 email topic                                                   | ~$0.10                    |
| **Tổng ước tính / tháng**    |                                                                           | **~ $6–$8.50 / tháng**     |


3. Giải pháp kiểm soát chi phí

| **Vấn đề**                              | **Cách tối ưu**                                                                 |
|----------------------------------------|----------------------------------------------------------------------------------|
| **X-Ray tốn nhiều**                    | Chỉ bật tracing cho các Lambda quan trọng (sampling 10–20%)                    |
| **Logs quá nhiều**                     | Dùng Filter log level (ví dụ: chỉ log latency khi > 500ms)                     |
| **Custom Metric tốn phí**              | Gộp nhiều metric vào 1 EMF log nếu được                                        |
| **Logs lưu quá lâu**                   | Đặt Log Group Retention = 7 hoặc 14 ngày                                       |
| **Truy vấn CloudWatch quá thường xuyên** | Tạo dashboard tổng hợp thay vì chạy truy vấn ad-hoc                            |
| **Lambda tốn GB-s quá nhiều**          | Giảm timeout, RAM khi không cần thiết                                          |

4. Dùng công cụ AWS để phân tích chi phí

- **AWS Cost Explorer:**
  - Lọc theo service: Lambda, CloudWatch, X-Ray
  - Xem theo thời gian hoặc tài nguyên cụ thể

- **AWS CloudWatch Billing Alerts:**
  - Tạo alarm khi tổng chi phí vượt ngưỡng

- **X-Ray + CloudWatch Metrics:**
  - Phân tích cụ thể request nào đang đắt (trace chậm → GB-seconds cao)

- **Tag các Lambda:**
  - Gắn tag theo `cost-center`, `env` để phân loại chi phí


Dựa trên các công cụ phân tích như AWS Cost Explorer và các metric từ X-Ray và CloudWatch, hệ thống hiện tiêu tốn khoảng $6–$9/tháng cho 100,000 lượt truy cập. Chi phí tập trung chủ yếu vào Lambda execution, X-Ray tracing và CloudWatch logs/metrics. Các phương án tối ưu đã được đề xuất gồm điều chỉnh sampling, giảm log size, đặt retention log ngắn và gom metric hợp lý.


#### Đề xuất tối ưu 


| **Quan sát từ X-Ray & CloudWatch**                      | **Khuyến nghị tối ưu**                                                                                   |
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| ⏱️ Latency trung bình > 600ms                            | 🔁 Sử dụng cache để giảm thời gian xử lý — ví dụ: cache kết quả DB/API bằng Redis hoặc S3                |
| 🚀 Lambda có spikes ngẫu nhiên 800–1000ms               | 📦 Tăng memory (CPU tăng theo RAM) — nâng từ 128MB → 256MB hoặc 512MB để cải thiện tốc độ                 |
| 📉 ProcessingTime dao động mạnh                          | 🔄 Tách các tác vụ nặng sang async — ví dụ: ghi log, gửi mail → SNS hoặc SQS + Lambda                    |
| 🔁 Lambda bị invoke nhiều lần lặp lại                    | ⛔ Thêm throttle / deduplication ở phía gọi API                                                           |
| 📊 Metric đều nhưng vẫn chậm                             | ⚙️ Kiểm tra external dependency — API bên ngoài, RDS chậm, mạng delay... trong trace                     |
| 📉 Thời gian "Initialization" lâu                        | 🛠️ Giảm cold start — giữ vùng nóng hoặc tránh khai báo biến lớn ở ngoài handler                         |

Có rất nhiều cách để tối ưu, một trong số cách rất hay là tối ưu khi gặp cảnh báo và chạy funtion để tăng tài nguyên của ứng dụng và từ đó giúp ứng dụng chạy tốt hơn.