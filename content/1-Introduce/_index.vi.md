---
title : "Giới thiệu"
date: 2025-07-05 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

Trong workshop này, bạn sẽ khám phá hai công cụ chính là X-Ray và Custom Metrics. Các bước để giám sát, tối ưu, tự động hoá và hệ thống cảnh báo. 

Ưu điểm khi dùng AWS X-Ray & Custom Metrics:

-	🎯 Theo dõi toàn bộ luồng xử lý request đầu–cuối qua các service
-	🔍 Phát hiện nhanh điểm nghẽn (bottleneck) và độ trễ bất thường
-	📊 Ghi chỉ số tùy chỉnh như ProcessingTime, ErrorType, UserAction
-	📈 Dễ dàng tạo dashboard giám sát thời gian thực với CloudWatch
-	🚨 Tích hợp cảnh báo (alarm) khi hiệu năng vượt ngưỡng
-	🤖 Hỗ trợ tối ưu tự động: tăng RAM, bật cache, gửi cảnh báo
-	💡 Không cần thay đổi nhiều source code, bật tracing rất nhanh
-	💰 Giúp tối ưu chi phí vận hành qua phân tích sử dụng tài nguyên

Quy trình vận hành:

| 🧭 **Tình huống**                     | ⚙️ **Hành động chính**                                                                 |
|--------------------------------------|----------------------------------------------------------------------------------------|
| 🔔 Nhận cảnh báo CloudWatch Alarm    | Kiểm tra Alarm → Xem Logs bất thường → Dùng X-Ray để trace request chậm              |
| 🔍 Kiểm tra hiệu suất định kỳ        | Vào Dashboard → So sánh biểu đồ thời gian xử lý                                       |
| 🛠️ Latency tăng cao đột ngột        | Deploy lại Lambda → Kiểm tra memory/timeout → Giảm tải nếu cần                        |
| 🧪 Debug lỗi cụ thể                  | Dùng X-Ray → Tìm trace theo ID/thời gian → Phân tích breakdown                        |
| 📈 Tối ưu lâu dài                    | Ghi thêm metric vào EMF → Thiết lập thêm các Alarm nâng cao                          |
| 🧹 Dọn dẹp định kỳ                  | Xoá alarm/topic cũ → Kiểm tra chi phí Logs/X-Ray để tối ưu                           |
