---
solution: Campaign Classic
product: campaign
title: 活动投放设置配置
description: 了解如何配置活动投放设置
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
translation-type: tm+mt
source-git-commit: 401e1be234d52f04cbdf8dfa97f51ac227836cd5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 1%

---

# 配置投放设置{#delivery-settings}

必须在&#x200B;**serverConf.xml**&#x200B;文件夹中配置投放参数。

* **DNS配置**:指定投放域和DNS服务器的IP地址（或主机），这些DNS服务器用于响应MTA模块从此开始创建的MX类型DNS **`<dnsconfig>`** 查询。

   >[!NOTE]
   >
   >**nameServers**&#x200B;参数对于在Windows中进行安装是必不可少的。 对于Linux中的安装，它必须留空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

您还可以根据您的需要和设置执行以下配置：配置[SMTP中继](#smtp-relay)，调整[MTA子进程](#mta-child-processes)的数量，[管理出站SMTP通信](#managing-outbound-smtp-traffic-with-affinities)。

## SMTP中继{#smtp-relay}

MTA模块充当SMTP广播（端口25）的本机邮件传输代理。

但是，如果您的安全策略需要，则可以用中继服务器替换它。 在这种情况下，全局吞吐量将是中继吞吐量(前提是中继服务器吞吐量低于Adobe Campaign吞吐量)。

在这种情况下，通过在&#x200B;**`<relay>`**&#x200B;部分配置SMTP服务器来设置这些参数。 必须指定用于传输邮件的SMTP服务器的IP地址（或主机）及其关联端口（默认为25）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>这种操作模式对投放造成了严重的限制，因为由于中继服务器的固有性能（延迟、带宽……），它可以大大降低吞吐量。 此外，限定同步投放错误（通过分析SMTP流量检测到）的容量将受到限制，并且如果中继服务器不可用，则发送将不可能。

## MTA子进程{#mta-child-processes}

可以根据服务器的CPU功率和可用网络资源控制子进程数（默认为2），以优化广播性能。 此配置将在每台计算机的MTA配置的&#x200B;**`<master>`**&#x200B;部分中进行。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另请参阅[电子邮件发送优化](../../installation/using/email-deliverability.md#email-sending-optimization)。

## 使用关联{#managing-outbound-smtp-traffic-with-affinities}管理出站SMTP通信

>[!IMPORTANT]
>
>关联配置需要从一台服务器到另一台服务器保持一致。 我们建议您与Adobe联系以进行关联配置，因为应在运行MTA的所有应用程序服务器上复制配置更改。

您可以通过具有IP地址的关联改善出站SMTP通信。

为此，请应用以下步骤：

1. 在&#x200B;**serverConf.xml**&#x200B;文件的&#x200B;**`<ipaffinity>`**&#x200B;部分输入关联。

   一个关联可以有多个不同的名称：要分离它们，请使用&#x200B;**;**&#x200B;字符。

   示例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   要视图相关参数，请参阅&#x200B;**serverConf.xml**&#x200B;文件。

1. 要在下拉列表中启用关联选择，您需要在&#x200B;**IPAffinity**&#x200B;明细列表中添加关联名称。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >明细列表详见[此文档](../../platform/using/managing-enumerations.md)。

   然后，您可以选择要使用的关联，如下所示，适用于类型：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您还可以引用[投放服务器配置](../../installation/using/email-deliverability.md#delivery-server-configuration)。

**相关主题**
* [技术电子邮件配置](email-deliverability.md)
* [将MX服务器与活动](using-mx-servers.md)
* [配置电子邮件密送](email-archiving.md)
