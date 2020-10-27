---
title: 配置
seo-title: 配置
description: 配置
seo-description: null
page-status-flag: never-activated
uuid: 4316d4b2-0964-4e25-9e4f-f2378f044c85
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 12f13b8d-afc3-4b55-a31b-080d31f84fc9
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 2%

---


# 配置{#configuration}

## 更改syslogd监听端口 {#changing-the-syslogd-listening-port}

默认情况下， **syslogd** 监听端口为666(udp)。 如有必要，可以使用环境变量更改它。

配置此变量后，所有Adobe Campaign模块都会考虑此变量。

### 在Linux中 {#in-linux}

编辑 **customer.sh** 文件并添加以下行：

```
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows中 {#in-windows}

您需要使用 **localhost值创建** TRACE **_ADDR.** 环境变量： **`<listening port="" />`**.

>[!IMPORTANT]
>
>我们建议运行一些测试，以确保在创建此环境变量后您的平台能正常工作。

## 配置安全区域 {#configuring-security-zones}

每个操作员需要链接到一个区域才能登录到实例，并且操作员IP必须包含在安全区域中定义的地址或地址集中。 技术区配置在Adobe Campaign服务器的配置文件中执行。 必须在控制台（节点）中定义操作员与安全区 **[!UICONTROL Administration > Access management > Operators]** 域的链接。

>[!NOTE]
>
>有关配置安全区域的详细信息，请参 [阅此部分](../../installation/using/configuring-campaign-server.md#defining-security-zones)。
