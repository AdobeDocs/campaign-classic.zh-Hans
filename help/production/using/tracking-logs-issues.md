---
product: campaign
title: 跟踪日志问题
description: 跟踪日志问题
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 81
ht-degree: 24%

---

# 跟踪日志问题{#tracking-logs-issues}



跟踪日志未转发可能有多种原因。 我们建议您检查以下信息：

* **&#x200B;**&#x200B;跟踪&#x200B;**工作流是否有错误？**

请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=zh-Hans){target="_blank"}。

![](assets/tracking_scheduled_task.png)

* **模块** trackinglogd **是否在服务器上运行？**

  请参阅[日志文件](../../production/using/log-files.md)。

* **是否进行了更改？**

  它们可能会触发使用跟踪别名断开与服务器的连接。
