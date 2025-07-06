---
title: "Introduction"
date: 2025-07-05
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

In this workshop, you will explore two main tools: **X-Ray** and **Custom Metrics**. The steps include monitoring, optimization, automation, and alerting systems.

### Advantages of using AWS X-Ray & Custom Metrics:

- 🎯 Monitor the entire end-to-end request flow across services  
- 🔍 Quickly detect bottlenecks and abnormal latencies  
- 📊 Record custom metrics such as `ProcessingTime`, `ErrorType`, `UserAction`  
- 📈 Easily create real-time monitoring dashboards using CloudWatch  
- 🚨 Integrate alerts (alarms) when performance thresholds are breached  
- 🤖 Support automatic optimization: increase memory, enable caching, send alerts  
- 💡 Minimal source code changes needed — tracing can be enabled quickly  
- 💰 Optimize operational costs through resource usage analysis  

### Operation Workflow:

| 🧭 **Scenario**                        | ⚙️ **Main Action**                                                                 |
|--------------------------------------|-------------------------------------------------------------------------------------|
| 🔔 Receive CloudWatch Alarm          | Check the Alarm → Review unusual Logs → Use X-Ray to trace slow requests           |
| 🔍 Perform routine performance check | Go to Dashboard → Compare request processing time charts                          |
| 🛠️ Sudden latency spike              | Redeploy Lambda → Check memory/timeout → Apply load reduction if needed           |
| 🧪 Debug specific error               | Use X-Ray → Find trace by ID/time → Analyze breakdown                             |
| 📈 Long-term optimization             | Add more metrics to EMF → Set up advanced alarms                                  |
| 🧹 Periodic cleanup                  | Remove old alarms/topics → Review Logs/X-Ray cost for optimization                |
