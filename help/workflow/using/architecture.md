---
product: campaign
title: 架构
description: 工作流由特定模块处理，该模块可在多个服务器上启动以共享处理负载。
feature: Workflows
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# 架构 {#architecture}

![](../../assets/v7-only.svg)

工作流由特定模块处理。 为了共享处理负载，可以在多台服务器上启动此模块。

![](assets/architecture.png)

* “工作流实例运行器”(runwf)进程执行给定工作流实例的所有任务。 当当前没有要执行的任务时，它会变为“被动”，即将其状态保存在数据库中，然后停止。
* “工作流服务器”(wfserver)模块监视当前工作流实例。 当有要执行的任务时，此模块会创建一个进程以激活（或重新激活）相应的实例。
