---
solution: Campaign Classic
product: campaign
title: 跟踪日志问题
description: 跟踪日志问题
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# 跟踪日志问题{#tracking-logs-issues}

跟踪日志无法转发可能有多种原因。 我们建议您检查以下信息：

* 跟踪工 **作流** 是否有错误？

   请参阅监 [视技术工作流](../../workflow/using/monitoring-technical-workflows.md)。

   ![](assets/tracking_scheduled_task.png)

* 服务器上 **是否运行** module trackinglogd?

   请参阅 [日志文件](../../production/using/log-files.md)。

* 是否进行了更改？ 它们可以使用跟踪别名触发到服务器的连接丢失。

