---
product: campaign
title: 跟踪日志问题
description: 跟踪日志问题
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# 跟踪日志问题{#tracking-logs-issues}



跟踪日志未转发可能有多种原因。 我们建议您检查以下信息：

* **&#x200B;**&#x200B;跟踪&#x200B;**工作流是否有错误？**

  请参阅[监控技术工作流](../../workflow/using/monitoring-technical-workflows.md)。

  ![](assets/tracking_scheduled_task.png)

* **模块** trackinglogd **是否在服务器上运行？**

  请参阅[日志文件](../../production/using/log-files.md)。

* **是否进行了更改？**

  它们可能会触发使用跟踪别名断开与服务器的连接。
