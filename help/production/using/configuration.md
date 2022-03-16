---
product: campaign
title: 其他配置
description: 配置
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# 配置{#configuration}

![](../../assets/v7-only.svg)

## 更改syslogd侦听端口 {#changing-the-syslogd-listening-port}

默认情况下， **syslogd** 侦听端口为666(udp)。 您可以根据需要使用环境变量对其进行更改。

配置后，所有Adobe Campaign模块都会考虑此变量。

### 在Linux中 {#in-linux}

编辑 **customer.sh** 并添加以下行：

```
export TRACE_ADDR=localhost:<listening port>
```

### 在Windows中 {#in-windows}

您需要创建 **TRACE_ADDR。** 环境变量 **localhost** 值： **`<listening port="" />`**.

>[!IMPORTANT]
>
>我们建议运行一些测试，以确保在创建此环境变量后，您的平台可以正常工作。

## 配置安全区 {#configuring-security-zones}

每个操作员需要链接到区域才能登录到实例，并且操作员IP必须包含在安全区域中定义的地址或地址集中。 技术区域配置在Adobe Campaign服务器的配置文件中执行。 必须在控制台中定义操作员与安全区域的链接( **[!UICONTROL Administration > Access management > Operators]** 节点)。

>[!NOTE]
>
>有关配置安全区的更多信息，请参阅 [此部分](../../installation/using/security-zones.md).
