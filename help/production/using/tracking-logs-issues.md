---
title: 跟踪日志问题
seo-title: 跟踪日志问题
description: 跟踪日志问题
seo-description: null
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 16%

---


# 跟踪日志问题{#tracking-logs-issues}

跟踪日志无法转发可能有多种原因。 我们建议您检查以下信息：

* 跟踪工 **作流** 是否有错误？

   请参阅监 [视技术工作流](../../workflow/using/monitoring-technical-workflows.md)。

   ![](assets/tracking_scheduled_task.png)

* 服务器上 **是否运行** module trackinglogd?

   请参阅 [日志文件](../../production/using/log-files.md)。

* 是否进行了更改？ 它们可以使用跟踪别名触发到服务器的连接丢失。

