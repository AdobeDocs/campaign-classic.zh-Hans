---
product: campaign
title: 配置
description: 配置
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

---

# 配置{#configuration}

## 更改syslogd侦听端口{#changing-the-syslogd-listening-port}

默认情况下，**syslogd**&#x200B;侦听端口为666(udp)。 您可以根据需要使用环境变量对其进行更改。

配置后，所有Adobe Campaign模块都会考虑此变量。

### 在Linux {#in-linux}中

编辑&#x200B;**customer.sh**&#x200B;文件并添加以下行：

```
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows {#in-windows}中

您需要使用&#x200B;**localhost**&#x200B;值创建&#x200B;**TRACEADDR.**&#x200B;环境变量：**`<listening port="" />`**。

>[!IMPORTANT]
>
>我们建议运行一些测试，以确保在创建此环境变量后，您的平台可以正常工作。

## 配置安全区{#configuring-security-zones}

每个操作员需要链接到区域才能登录到实例，并且操作员IP必须包含在安全区域中定义的地址或地址集中。 技术区域配置在Adobe Campaign服务器的配置文件中执行。 必须在控制台（**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点）中定义操作员与安全区域的链接。

>[!NOTE]
>
>有关配置安全区的更多信息，请参阅[此部分](../../installation/using/security-zones.md)。
