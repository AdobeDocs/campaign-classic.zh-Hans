---
title: 架构
description: 工作流由特定模块处理，该模块可在多个服务器上启动，以共享处理负载。
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---


# 架构 {#architecture}

工作流由特定模块处理。 此模块可以在多台服务器上启动，以共享处理负载。

![](assets/architecture.png)

* “工作流实例运行器”(runwf)进程执行给定工作流实例的所有任务。 当暂时没有任务需要执行时，它会变为“被动”，即它保存在数据库中的状态，然后停止。
* “工作流服务器”(wfserver)模块监视当前工作流实例。 当存在要执行的任务时，此模块会创建一个过程以激活（或重新激活）相应实例。

