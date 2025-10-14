---
product: campaign
title: 跟踪日志问题
description: 跟踪日志问题
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 14%

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
