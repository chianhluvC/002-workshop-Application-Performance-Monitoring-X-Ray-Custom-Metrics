---
title: "Create an Alert System"
date: 2025-07-06
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

In this step, we will create an alert system using **CloudWatch Alarm**, a service that helps us detect and notify when metrics exceed thresholds.

1. Go to the **CloudWatch Console**  
+ Under the **Alarms** section, click on **In alarm**  
+ Then click **Create alarm**

![alarm](/images/4-dashboardalarm/007-alarm1.png)

2. In **Step 1**, click **Select metric**

![alarm](/images/4-dashboardalarm/008-alarm2.png)

3. In the **Select metric** interface:  
+ Choose **Browse**  
+ Click on the previously created service  
+ Then click **Select metric**

![alarm](/images/4-dashboardalarm/009-alarm3.png)

4. After selection, your chosen metric will appear along with related details

![alarm](/images/4-dashboardalarm/010-alarm4.png)

5. Configure the metric settings as shown:

![alarm](/images/4-dashboardalarm/011-alarm5.png)

6. Scroll down a bit:  
+ For **Threshold type**, select **Static**  
+ Under **Whenever ProcessingTime is...**, choose **Greater**  
+ Set the value to **350**  
+ For **Datapoints to alarm**, set both min and max to **3**

![alarm](/images/4-dashboardalarm/012-alarm6.png)

7. Scroll to the bottom and click **Next**

![alarm](/images/4-dashboardalarm/013-alarm7.png)

8. In **Step 2** interface:  
+ Under **Alarm state trigger**, select **In alarm**  
+ Under **Send a notification to the following SNS topic**, choose **Create new topic**  
+ Name the new topic  
+ Enter your email under **Email endpoints that will receive the notification** (make sure to confirm when AWS sends the verification email)  
+ Click **Create topic**

![alarm](/images/4-dashboardalarm/014-alarm8.png)

9. Scroll down and click **Next**

![alarm](/images/4-dashboardalarm/015-alarm9.png)

10. In **Step 3**:  
+ Set **Alarm name** to `HighProcessingLatency`  
+ In **Description**, enter: `Alert when Lambda ProcessingTime > 350ms avg in 1 min`  
+ Click **Next**

![alarm](/images/4-dashboardalarm/016-alarm10.png)

11. The **Overview** screen will appear. Review your settings and click **Create alarm**

![alarm](/images/4-dashboardalarm/017-alarm11.png)

12. You will be redirected to the **Alarms Management** screen — click on the alarm you just created

![alarm](/images/4-dashboardalarm/018-alarm12.png)

13. Review the alarm details and important configuration metrics

![alarm](/images/4-dashboardalarm/019-alarm13.png)

14. Use **Postman** to send a high volume of test requests

![alarm](/images/4-dashboardalarm/020-alarm14.png)

15. Go back to the Alarms page and check the alarm status and metrics

![alarm](/images/4-dashboardalarm/021-alarm15.png)

16. Wait for an alert email from AWS

![alarm](/images/4-dashboardalarm/022-alarm16.png)

And that’s it — we’ve successfully created an alert system. In the next section, we’ll explore **cost analysis and system optimization**.
