---
product: campaign
title: 简介
description: 简介
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 5%

---

# 简介{#introduction}



本节介绍升级Adobe Campaign、客户端和服务器端时应用的过程，并介绍如何切换到现有实例的Unicode。

>[!NOTE]
>
>对于托管/托管服务实例，您必须与Adobe管理员进行协调。\
>对于内部部署实例，您可以从Adobe顾问那里获得帮助。

升级必须应用于安装了Adobe Campaign的所有服务器。

1. 迁移重定向和跟踪服务器(Apache/IIS)。
1. 迁移Power Booster/Cluster服务器
1. 迁移营销服务器。

Adobe Campaign基于在服务器端执行的多个进程，在更新期间您需要处理这些进程，特别是：

* 应用程序服务器(nlserver web)
* 投放服务器(nlserver mta)
* 重定向服务器(webmdl)

>[!CAUTION]
>
>客户端控制台应与服务器实例位于同一内部版本上。

>[!NOTE]
>
>有关各种Adobe Campaign过程的更多信息，请参阅 [本节](../../installation/using/general-architecture.md#logical-application-layer).\
>使用Power Booster或Power Cluster类型体系结构时，必须将此过程应用于所有Power Booster/Cluster服务器。

如果新版本涉及更改数据库结构，我们建议按以下顺序重新启动服务器：

1. 应用程序服务器(nlserver web)、
1. 重定向服务器(webmdl)、
1. 投放服务器(nlserver mta)。
