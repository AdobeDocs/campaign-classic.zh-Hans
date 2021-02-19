---
solution: Campaign Classic
product: campaign
title: 架构
description: 工作流由特定模块处理，该模块可以在多个服务器上启动，以共享处理负载。
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---


# 架构 {#architecture}

工作流由特定模块处理。 此模块可以在多台服务器上启动，以共享处理负载。

![](assets/architecture.png)

* “工作流实例运行程序”(runwf)进程执行给定工作流实例的所有任务。 当目前没有任务需要执行时，它会变为“被动”，即它保存在数据库中的状态，然后停止。
* “工作流服务器”(wfserver)模块监视当前工作流实例。 当存在要执行的任务时，此模块会创建一个过程以激活（或重新激活）相应实例。

