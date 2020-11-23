---
solution: Campaign Classic
product: campaign
title: 一般架构
description: 一般架构
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 3%

---


# 一般架构{#general-architecture}

## 最小架构 {#minimum-architecture}

在最低配置中，Adobe Campaign的操作包括：

* adobe campaign应用服务器、
* 数据库。

   ![](assets/formation_exploitation.png)

此图表显示，最小体系结构上下文中涉及的唯一流量是：

1. 通过Internet到Adobe Campaign服务器的HTTP协议流量，
1. 通过Internet从Adobe Campaign服务器传输和传输SMTP协议流量。

## 分布式架构 {#distributed-architecture}

Adobe Campaign由多个模块组成，这些模块可以在多台计算机上划分。 此操作模式具有以下几个优点：

* 负载平衡，
* 设置模块冗余，
* 构建一个按多个服务提供商划分的架构（所提供服务的细分）。

![](assets/architecturerepartie.png)

模块在多台机器上的分布提供了极大的使用灵活性，并增强了适应性。

>[!NOTE]
>
>For more on the various architectures, refer to [this section](../../installation/using/general-architecture.md).

## 开放端口列表 {#list-of-open-ports}

| 端口号 | 相关Adobe Campaign模块或应用程序 | 可配置 |
|---|---|---|
| 443/tcp或80/tcp | Web服务器(Apache/IIS) | 是 |
| 6666/udp（本地） | Adobe Campaign:塞斯洛格德 | 是 |
| 8005/tcp（本地） | Adobe Campaign:web模块 | 是 |
| 8080/tcp | Adobe Campaign:Web模块(tomcat) | 是 |
| 7777 | 统计服务器（统计服务器） | 是 |

