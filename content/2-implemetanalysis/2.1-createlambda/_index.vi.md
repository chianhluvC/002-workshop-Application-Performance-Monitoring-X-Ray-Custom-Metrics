---
title : "Tạo Lambda Function có Tracing"
date: 2025-07-06 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

Trong bước này bạn sẽ tiến hành tạo một ứng dụng serverless có tracing, để theo dõi quá trình khi người dùng thực hiện truy vấn tới ứng dụng đó.

1. Truy cập vào [giao diện quản trị](https://console.aws.amazon.com/lambda) của AWS Lambda Console và click chọn vào **Create a funtion**

![lambda](/images/2-implemetanalysis/001-lambda1.png)

2. Giao diện create function xuất hiện

+ Click chọn Author from scratch
+ Funtion name điền MonitorFuction
+ Runtime click chọn vào phiên bản Node.js mới nhất
+ Architecture click chọn vào x86_64

![lambda](/images/2-implemetanalysis/002-lambda2.png)

3. Kéo xuống thêm một đoạn
+ Click chọn vào Create a new role with basic Lambda permission
+ Click vào Create function

![lambda](/images/2-implemetanalysis/003-lambda3.png)

4. Sau khi hoàn tất thao tác trước đó, function vừa tạo sẽ xuất hiện

![lambda](/images/2-implemetanalysis/004-lambda4.png)

+ Click chọn vào mục Code:
+ Paste đoạn code sau vào và ấn deploy

```js

  export async function handler(event) {
      const start = Date.now();
	
  	  await new Promise((r) => setTimeout(r, Math.random() * 300 + 300));
  	  const latency = Date.now() - start;
	
  	  console.log("Request processed in:", latency, "ms");
	
  	  console.log(JSON.stringify({
  	    "_aws": {
  	      "Timestamp": Date.now(),
  	      "CloudWatchMetrics": [
  	        {
            "Namespace": "MyApp",
	          "Dimensions": [["Service"]],
	          "Metrics": [{ "Name": "ProcessingTime", "Unit": "Milliseconds" }]
	        }
	      ]
	    },
	    "Service": "CheckoutService",
	    "ProcessingTime": latency
	  }));
	
	  return {
	    statusCode: 200,
	    body: JSON.stringify({
	      message: "Hello! Tracing + metrics working.",
	      latency
	    })
	  };	
  }

```

![lambda](/images/2-implemetanalysis/005-lambda5.png)

5. Click chọn vào mục Configuration và chọn vào Monitoring and operations tools

![lambda](/images/2-implemetanalysis/006-lambda6.png)

6. Trong mục Monitoring and operations tools click chọn vào Edit

![lambda](/images/2-implemetanalysis/007-lambda7.png)

7. Giao diện Edit monitoring tools sẽ xuất hiện, phần Lambda service traces click chọn vào Enable

![lambda](/images/2-implemetanalysis/008-lambda8.png)

8. Kéo xuống cuối trang và click chọn vào Save

![lambda](/images/2-implemetanalysis/009-lambda9.png)

9. Xuất hiện thông báo đã thay đổi thành công

+ Quan sát Logs and metrics (default) hiện **Enabled**
+ Quan sát Lambda service traces hiện **Enabled**

![lambda](/images/2-implemetanalysis/010-lambda10.png)

10. Quay lại MonitorFuntion và click chọn vào Add trigger

![lambda](/images/2-implemetanalysis/011-lambda11.png)

11. Giao diện add triggers sẽ xuất hiện

+ Phần Intent click chọn vào **Create a new API**
+ Phần API type click chọn vào **HTTP API**
+ Phần Security click chọn vào **Open**
+ Click chọn vào **Add**

![lambda](/images/2-implemetanalysis/012-lambda12.png)

12. Xuất hiện thông báo và trigger đã được tạo thành công

![lambda](/images/2-implemetanalysis/013-lambda13.png)

