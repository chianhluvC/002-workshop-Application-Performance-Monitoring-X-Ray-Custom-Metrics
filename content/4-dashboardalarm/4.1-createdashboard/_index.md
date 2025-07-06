---
title: "Create a Dashboard"
date: 2025-07-06
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

In this step, we will create a **monitoring dashboard**, allowing us to observe key metrics at the time of creation.

1. Go to the **CloudWatch Console**  
   + Click on **Dashboards**  
   + Click on **Create dashboard**

![dash](/images/4-dashboardalarm/001-dash1.png)

2. The **Create new dashboard** screen will appear:  
+ Enter the dashboard name: **ProcessingTime**  
+ Click **Create dashboard**

![dash](/images/4-dashboardalarm/002-dash2.png)

3. The **Add widget** screen will appear:  
+ For **Data source type**, select **CloudWatch**  
+ For **Data type**, select **Metrics**  
+ For **Widget type**, choose **Line**  
+ Click **Next**

![dash](/images/4-dashboardalarm/003-dash3.png)

4. The **Add metric graph** dialog will appear:  
+ Select your desired service as shown  
+ Click **Create widget**

![dash](/images/4-dashboardalarm/004-dash4.png)

5. Once the dashboard is created, return to the **dashboard management** page to view the dashboards you've created:

![dash](/images/4-dashboardalarm/005-dash5.png)

![dash](/images/4-dashboardalarm/006-dash6.png)

That’s it! You’ve created a dashboard to monitor key metrics. Next, we’ll move on to setting up an alert system.
