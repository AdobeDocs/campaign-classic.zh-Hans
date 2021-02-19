---
solution: Campaign Classic
product: campaign
title: 简介
description: 简介
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 5639f08ad709597d5f5c9e6bbd6932cffcbde40f
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---


# 简介{#introduction}

本节介绍将应用于升级Adobe Campaign、客户端和服务器端的过程，并描述将现有实例切换为Unicode的过程。

>[!NOTE]
>
>对于托管实例，您必须与Adobe管理员协调。\
>对于预置型实例，您可以从Adobe顾问处获得帮助。

必须将升级应用到安装了Adobe Campaign的所有服务器。

1. 迁移重定向和跟踪服务器(Apache/IIS)。
1. 迁移Power Booster/群集服务器。
1. 迁移营销服务器。

Adobe Campaign基于在更新期间需要处理的服务器端执行的多个进程，特别是：

* 应用程序服务器(nlserver web)
* 投放服务器(nlserver mta)
* 重定向服务器(webmdl)

>[!CAUTION]
>
>客户端控制台应与服务器实例位于同一版本上。

>[!NOTE]
>
>有关各种Adobe Campaign进程的详细信息，请参阅[本节](../../installation/using/general-architecture.md#logical-application-layer)。\
>当使用Power Booster或Power Cluster类型体系结构时，必须将此过程应用于所有Power Booster/Cluster服务器。

如果新版本涉及更改数据库结构，建议按以下顺序重新启动服务器：

1. 应用程序服务器(nlserver web)、
1. 重定向服务器(webmdl),
1. 投放服务器(nlserver mta)。

