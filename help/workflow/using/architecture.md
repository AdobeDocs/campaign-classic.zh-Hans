---
product: campaign
title: 架构
description: 工作流由特定模块处理，可以在多个服务器上启动该模块以共享处理负载
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# 架构 {#architecture}



工作流由特定模块处理。 此模块可以在多个服务器上启动，以共享处理负载。

![](assets/architecture.png)

* “工作流实例运行器”(runwf)进程执行给定工作流实例的所有任务。 如果当前没有要执行的任务，则它会变为“被动”，即将其状态保存在数据库中，然后停止。
* “工作流服务器”(wfserver)模块监视当前工作流实例。 当有任务要执行时，此模块会创建一个流程来激活（或重新激活）相应的实例。
