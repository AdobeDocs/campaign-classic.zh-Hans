---
product: campaign
title: 跟踪日志问题
description: 跟踪日志问题
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# 跟踪日志问题{#tracking-logs-issues}

![](../../assets/v7-only.svg)

跟踪日志无法转发的原因有多种。 我们建议您查看以下信息：

* **是否**&#x200B;跟踪&#x200B;**工作流有错误？**

   请参阅 [监控技术工作流](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **是模块** trackinglogd **服务器上运行？**

   请参阅 [日志文件](../../production/using/log-files.md).

* **是否进行了更改？**

   它们可能会使用跟踪别名触发与服务器的连接丢失。
