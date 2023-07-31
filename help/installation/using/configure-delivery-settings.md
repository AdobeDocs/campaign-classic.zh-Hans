---
product: campaign
title: Campaign投放设置配置
description: 了解如何配置Campaign投放设置
feature: Installation, Channel Configuration
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 6%

---

# 配置投放设置 {#delivery-settings}



投放参数必须在中配置 **serverConf.xml** 文件夹。

* **DNS配置**：指定用于响应MTA模块从发出的MX类型DNS查询的DNS服务器的投放域和IP地址（或主机）。 **`<dnsconfig>`** 从上往下。

  >[!NOTE]
  >
  >此 **名称服务器** 参数对于Windows中的安装至关重要。 对于Linux中的安装，必须将其留空。

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

您还可以根据需求和设置执行以下配置：配置 [SMTP中继](#smtp-relay)，调整数量 [MTA子进程](#mta-child-processes)， [管理出站SMTP流量](#managing-outbound-smtp-traffic-with-affinities).

## SMTP中继 {#smtp-relay}

MTA模块充当用于SMTP广播（端口25）的本机邮件传输代理。

但是，如果您的安全策略要求使用中继服务器，则可以将其替换。 在这种情况下，全局吞吐量将是中继服务器吞吐量(前提是中继服务器吞吐量低于Adobe Campaign吞吐量)。

在本例中，这些参数的设置是通过在 **`<relay>`** 部分。 必须指定用于传输邮件及其关联端口（默认为25）的SMTP服务器的IP地址（或主机）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>这种操作模式意味着严重限制投放，因为它会因为中继服务器固有的性能（延迟、带宽……）而大大降低吞吐量。 此外，限定同步投放错误（通过分析SMTP流量检测）的容量将受限，并且如果中继服务器不可用，将无法进行发送。

## MTA子进程 {#mta-child-processes}

可以控制子进程（默认为2）的数量，以便根据服务器的CPU功率和可用的网络资源优化广播性能。 此配置将在 **`<master>`** 每台计算机上MTA配置的部分。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另请参阅 [电子邮件发送优化](../../installation/using/email-deliverability.md#email-sending-optimization).

## 使用相关性管理出站SMTP流量 {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>关联配置需要从一台服务器到另一台服务器保持一致。 我们建议您联系Adobe以进行关联配置，因为应在运行MTA的所有应用程序服务器上复制配置更改。

您可以通过与IP地址的相关性改善出站SMTP流量。

要执行此操作，请应用以下步骤：

1. 输入以下各项的亲和度： **`<ipaffinity>`** 的部分 **serverConf.xml** 文件。

   一个关联可以有多个不同的名称：要分隔它们，请使用 **；** 字符。

   示例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   要查看相关参数，请参阅 **serverConf.xml** 文件。

1. 要在下拉列表中启用关联选择，您需要将关联名称添加到 **IPAffinity** 明细列表。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >有关详细的明细列表，请参见 [本文档](../../platform/using/managing-enumerations.md).

   然后，您可以选择要使用的关联，如下面的分类所示：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您还可以参阅 [投放服务器配置](../../installation/using/email-deliverability.md#delivery-server-configuration).

**相关主题**
* [技术电子邮件配置](email-deliverability.md)
* [在 Campaign 中使用 MX 服务器](using-mx-servers.md)
* [配置电子邮件密送](email-archiving.md)
