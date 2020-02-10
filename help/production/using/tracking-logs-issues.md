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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# 跟踪日志问题{#tracking-logs-issues}

跟踪日志未转发的原因可能有多种。 我们建议您检查以下信息：

* 跟踪工 **作流** 是否有错误？

   请参阅监 [控技术工作流程](../../workflow/using/monitoring-technical-workflows.md)。

   ![](assets/tracking_scheduled_task.png)

* 服务器上 **是否运行** module trackinglogd?

   请参阅 [日志文件](../../production/using/log-files.md)。

* 是否进行了更改？ 它们可以触发与使用跟踪别名的服务器的连接断开。

