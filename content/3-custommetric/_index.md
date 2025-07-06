---
title: "Monitoring Performance with CloudWatch Custom Metrics"
date: 2025-07-06
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

In this section, we will monitor the application's performance using **CloudWatch Custom Metrics**. You'll view custom metric details and visualize the `ProcessingTime` as a line chart, among others.

1. Go to the [CloudWatch Console](https://console.aws.amazon.com/cloudwatch/home/)

![metric](/images/3-custommetric/001-metric1.png)

2. Under the **Metrics** section:  
+ Click on **All metrics**  
+ Then click on **MyApp**

![metric](/images/3-custommetric/002-metric2.png)

3. Next, click on **Service**

![metric](/images/3-custommetric/003-metric3.png)

4. Then select **CheckoutService** and choose the **Line** chart type

![metric](/images/3-custommetric/004-metric4.png)

5. The line chart of the custom metric will appear. Here, you can observe fluctuations in processing time over time. You can adjust the time range as needed. This helps identify periods where performance is suboptimal and allows you to prepare remediation strategies.

![metric](/images/3-custommetric/005-metric5.png)

You can also explore other chart types, such as the **Stacked area** chart:

![metric](/images/3-custommetric/006-metric6.png)

That concludes the section on **Monitoring Performance with CloudWatch Custom Metrics**. The insights from this part should give you a clearer picture of how Custom Metrics work. Through the data and visualizations, you'll be better equipped for the next steps.
