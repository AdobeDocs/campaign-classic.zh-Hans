---
title: 一般架构
seo-title: 一般架构
description: 一般架构
seo-description: null
page-status-flag: never-activated
uuid: a565a10c-cbef-455a-aa1d-9be9cd207c7a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: introduction
discoiquuid: f4879774-afe5-4556-ab60-9297cabbca2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 一般架构{#general-architecture}

## 最低架构 {#minimum-architecture}

在最低配置中，Adobe Campaign的运行方式如下：

* Adobe Campaign应用程序服务器、
* 数据库。

   ![](assets/formation_exploitation.png)

此示意图显示，最小架构上下文中涉及的唯一流量是：

1. 通过Internet连接到Adobe Campaign服务器的HTTP协议流量，
1. 通过Internet从Adobe Campaign服务器到Adobe Campaign服务器的SMTP协议通信。

## 分布式架构 {#distributed-architecture}

Adobe Campaign由多个模块组成，这些模块可以在多台计算机上划分。 此操作模式具有以下几个优点：

* 负载平衡，
* 建立模块冗余，
* 构建由多个服务提供商划分的架构（所提供服务的分段）。

![](assets/architecturerepartie.png)

多台机器上的模块分配提供了极大的使用灵活性，并提高了适应性。

>[!NOTE]
>
>有关各种架构的详细信息，请参 [阅本节](../../installation/using/general-architecture.md)。

## 打开的端口列表 {#list-of-open-ports}

| 端口号 | 关注的Adobe Campaign模块或应用程序 | 可配置 |
|---|---|---|
| 443/tcp或80/tcp | Web服务器(Apache/IIS) | 是 |
| 6666/udp（本地） | Adobe Campaign:Syslogd | 是 |
| 8005/tcp（本地） | Adobe Campaign:Web模块 | 是 |
| 8080/tcp | Adobe Campaign:Web模块(tomcat) | 是 |
| 7777 | 统计服务器（stat服务器） | 是 |

