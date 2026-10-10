---
product: campaign
title: 架构
description: 工作流由特定模块处理，可以在多个服务器上启动该模块以共享处理负载
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: 'https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%
---
# 架构 {#architecture}



工作流由特定模块处理。 此模块可以在多个服务器上启动，以共享处理负载。

![](assets/architecture.png)

* “工作流实例运行器”(runwf)进程执行给定工作流实例的所有任务。 如果当前没有要执行的任务，则它会变为“被动”，即将其状态保存在数据库中，然后停止。
* “工作流服务器”(wfserver)模块监视当前工作流实例。 当有任务要执行时，此模块会创建一个流程来激活（或重新激活）相应的实例。
