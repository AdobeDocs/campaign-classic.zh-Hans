---
title: 简介
seo-title: 简介
description: 简介
seo-description: null
page-status-flag: never-activated
uuid: 4192a74e-1d4f-4784-80e3-53aaefa9141e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 772992bf-588f-42bd-a72a-986a88815264
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 2%

---


# 简介{#introduction}

本节介绍将应用于升级Adobe Campaign、客户端和服务器端的过程，并描述将现有实例切换为Unicode的过程。

>[!NOTE]
>
>对于托管实例，必须与Adobe管理员协作。\
>对于预置型实例，您可以从Adobe顾问处获得帮助。

升级必须应用于安装Adobe Campaign的所有服务器。

1. 迁移重定向和跟踪服务器(Apache/IIS)。
1. 迁移Power Booster/群集服务器。
1. 迁移营销服务器。

Adobe Campaign基于在更新过程中需要处理的服务器端执行的多个进程，特别是：

* 应用程序服务器(nlserver web)
* 投放服务器(nlserver mta)
* 重定向服务器(webmdl)

>[!NOTE]
>
>有关各种Adobe Campaign流程的详细信息，请参 [阅本节](../../installation/using/general-architecture.md#logical-application-layer)。\
>当使用Power Booster或Power Cluster类型体系结构时，必须将此过程应用于所有Power Booster/Cluster服务器。

如果新版本涉及数据库结构的更改，建议按以下顺序重新启动服务器：

1. 应用程序服务器(nlserver web)、
1. 重定向服务器(webmdl),
1. 投放服务器(nlserver mta)。

