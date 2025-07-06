---
title: "Analyzing and Inspecting with AWS X-Ray"
date: 2025-07-06
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

### Analyzing and Inspecting with AWS X-Ray

In this step, we will analyze and inspect the serverless application using **AWS X-Ray**. From important metrics — especially latency — we can derive optimization strategies to improve performance.

1. Access the previously created trigger and copy the **API endpoint**:

![xray](/images/2-implemetanalysis/014-xray1.png)

2. Use **Postman** to test the API endpoint (send about 5 to 7 requests):

![xray](/images/2-implemetanalysis/015-xray2.png)

3. Go to the [Trace Map Console](https://console.aws.amazon.com/console/home/)

+ Observe the diagram with 3 main components: **Client**, **Lambda Context**, and **Lambda Function**  
+ Click on **Lambda Function**

![xray](/images/2-implemetanalysis/016-xray3.png)

4. The details of the selected Lambda Function will appear, including options for **Metrics**, **Alerts**, **Response time distribution** — click on **Metrics**

+ View metrics such as **Latency (avg)**, **Requests**, **Faults**  
+ Check the graphs for **Latency (avg)**, **Requests**, **Faults**

![xray](/images/2-implemetanalysis/017-xray4.png)

5. Click on **Response time distribution**, and note that the average response time is around 4%

![xray](/images/2-implemetanalysis/018-xray5.png)

6. Click **View traces** to see detailed trace data

![xray](/images/2-implemetanalysis/019-xray6.png)

7. The **Traces** interface appears. Browse through the traces and review important metrics.

![xray](/images/2-implemetanalysis/020-xray7.png)

8. Click on any trace to view the detailed breakdown:

![xray](/images/2-implemetanalysis/021-xray8.png)

9. Return to the **Traces** interface and click **Refine query by**

![xray](/images/2-implemetanalysis/022-xray9.png)

10. In the **User annotations** section, choose `aws:responseLatency`. This is a key metric showing how long a request takes to process. Based on this, you can evaluate the application’s performance.

![xray](/images/2-implemetanalysis/023-xray10.png)

11. A table of traces will appear, sorted by descending latency. From this, you can see that the application has a peak latency of **312.446 ms**, which helps prepare for potential overload situations — when traces gradually exceed latency thresholds.

![xray](/images/2-implemetanalysis/024-xray11.png)

That concludes the **Monitoring and Analysis** section. In the next part, we’ll move on to monitoring performance with **CloudWatch Custom Metrics**.
