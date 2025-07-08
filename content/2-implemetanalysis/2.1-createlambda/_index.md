---
title: "Create a Lambda Function with Tracing"
date: 2025-07-06
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

In this step, you will create a serverless application with tracing enabled to monitor the process when a user makes a request to the application.

1. Go to the [AWS Lambda Console](https://console.aws.amazon.com/lambda) and click **Create a function**

![lambda](/images/2-implemetanalysis/001-lambda1.png)

2. The Create function interface appears:

+ Select **Author from scratch**  
+ Enter **MonitorFunction** as the Function name  
+ For Runtime, choose the latest **Node.js** version  
+ For Architecture, select **x86_64**

![lambda](/images/2-implemetanalysis/002-lambda2.png)

3. Scroll down a bit further:  
+ Select **Create a new role with basic Lambda permissions**  
+ Click **Create function**

![lambda](/images/2-implemetanalysis/003-lambda3.png)

4. Once done, the newly created function will appear:

![lambda](/images/2-implemetanalysis/004-lambda4.png)

+ Click the **Code** tab  
+ Paste the following code and click **Deploy**

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

5. Click the **Configuration** tab and then go to **Monitoring and operations tools**

![lambda](/images/2-implemetanalysis/006-lambda6.png)

6. In the Monitoring and operations tools section, click **Edit**

![lambda](/images/2-implemetanalysis/007-lambda7.png)

7. The Edit monitoring tools interface appears. Under **Lambda service traces**, select **Enable**

![lambda](/images/2-implemetanalysis/008-lambda8.png)

8. Scroll to the bottom of the page and click **Save**

![lambda](/images/2-implemetanalysis/009-lambda9.png)

9. A success message will appear:

+ Under **Logs and metrics (default)**, you will see **Enabled**  
+ Under **Lambda service traces**, you will also see **Enabled**

![lambda](/images/2-implemetanalysis/010-lambda10.png)

10. Go back to **MonitorFunction** and click **Add trigger**

![lambda](/images/2-implemetanalysis/011-lambda11.png)

11. The Add trigger interface appears:

+ For Intent, select **Create a new API**  
+ For API type, select **HTTP API**  
+ For Security, choose **Open**  
+ Click **Add**

![lambda](/images/2-implemetanalysis/012-lambda12.png)

12. A confirmation will appear indicating the trigger was successfully created:

![lambda](/images/2-implemetanalysis/013-lambda13.png)
