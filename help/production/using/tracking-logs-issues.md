---
product: campaign
title: 跟踪日志问题
description: 跟踪日志问题
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 21%

---

# 跟踪日志问题{#tracking-logs-issues}



跟踪日志未转发可能有多种原因。 我们建议您检查以下信息：

* **是否**&#x200B;跟踪&#x200B;**工作流有错误？**

  请参阅 [监控技术工作流](../../workflow/using/monitoring-technical-workflows.md).

  ![](assets/tracking_scheduled_task.png)

* **是模块** trackinglogd **在服务器上运行？**

  请参阅 [日志文件](../../production/using/log-files.md).

* **是否进行了更改？**

  它们可能会触发使用跟踪别名断开与服务器的连接。
