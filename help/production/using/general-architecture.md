---
product: campaign
title: 一般架构
description: 一般架构
feature: Monitoring, Architecture
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
audience: production
content-type: reference
topic-tags: introduction
exl-id: 3bfb5448-6996-4080-bf9a-434f1207637e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 4%

---

# 一般架构{#general-architecture}



## 最低架构 {#minimum-architecture}

在最低配置下，Adobe Campaign通过以下方式运行：

* Adobe Campaign应用程序服务器，
* 数据库。

  ![](assets/formation_exploitation.png)

此图显示最低架构上下文中涉及的唯一流量是：

1. 通过Internet发送到Adobe Campaign服务器的HTTP协议流量，
1. 通过Internet与Adobe Campaign服务器之间的SMTP协议流量。

## 分布式架构 {#distributed-architecture}

Adobe Campaign由多个模块组成，这些模块可以在多台计算机上进行划分。 这种工作模式具有以下几个优点：

* 负载平衡，
* 设置模块冗余，
* 构建按多个服务提供商划分的架构（提供的服务细分）。

![](assets/architecturerepartie.png)

模块分布在多台机器上，提供了很大的使用灵活性和改进的适应性。

>[!NOTE]
>
>有关各种体系结构的更多信息，请参阅 [本节](../../installation/using/general-architecture.md).

## 打开的端口列表 {#list-of-open-ports}

| 端口号 | 涉及Adobe Campaign模块或应用程序 | 可配置 |
|---|---|---|
| 443/tcp或80/tcp | Web服务器(Apache/IIS) | 是 |
| 6666/udp（本地） | Adobe Campaign： Syslogd | 是 |
| 8005/tcp（本地） | Adobe Campaign： web模块 | 是 |
| 8080/tcp | Adobe Campaign： web module (tomcat) | 是 |
| 7777 | 统计服务器（stat服务器） | 是 |
