---
product: campaign
title: 技术说明
description: 技术说明
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: ed9e76495efb0cb49e248a7d38417642c5094a11
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 35%

---

# 跟踪的 URL 签名问题 {#tracked-urls}

![](../../assets/v7-only.svg)

在进行最近的更改后，当Campaign中的URL签名处于活动状态时，跟踪的URL可能会失败。 某些邮箱可能比其他邮箱受到的影响更大，因为某些公司具有特定的安全工具，这些工具可能会影响链接并更改 URL 签名机制。

因此，Adobe建议您禁用跟踪链接的签名机制。 此过程修复了旧的跟踪链接，但收到的双重转义链接除外。

请注意，退订链接可能会像任何其他链接一样失效，其频率在不同主机上是可变的，但小于 1%。

**您是否受影响？**

为了提高安全性，在 [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - 2020年4月 — 从版本19.1.4(9032@3a9dc9c)和促销活动20.2开始，默认为所有客户启用。

如果您的环境在下面列出的某个版本上运行，则可能会受到影响：

* Gold Standard 8 - 11。 [了解详情](../../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1（版本9277）到21.1.2（版本9282）版本。 [了解详情](../../rn/using/latest-release.md)
* Campaign 20.3.1（版本9228）到20.3.3（版本9234）版本。 [了解详情](../../rn/using/release--20-3.md)
* Campaign 20.2.1（版本9178）到20.2.4（版本9187）版本。 [了解详情](../../rn/using/release--20-2.md)
* Campaign 20.1.1（版本9122）到21.1.3（版本9124）版本。 [了解详情](../../rn/using/release--20-1.md)
* Campaign 19.2.2（版本9080）到19.2.3（版本9081）版本。 [了解详情](../../rn/using/release--19-2.md)
* Campaign 19.1.5（版本9033）到19.1.7（版本9036）版本。 [了解详情](../../rn/using/release--19-1.md)

了解如何检查您的版本 [在此部分中](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**如何更新？**

As a **托管客户**,Adobe将尽快与您合作更新配置。

作为 **内部部署/混合客户**，则需要更新配置。

按照以下步骤操作：

1. 在 [服务器配置文件](../../installation/using/the-server-configuration-file.md) (serverConf.xml)，更改 **signEmailLinks** to **false**.
1. 重新启动 **nlserver** 服务。
1. 在跟踪服务器上，重新启动Web服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>的 **配置 — `<instance>`.xml** 文件覆盖 **serverConf.xml** 设置。 如果 **signEmailLinks** 在  **配置 — `<instance>`.xml** (其中 **实例** 是实例的名称)，则还必须将其设置为 **false**.

**会有什么影响？**

维护工作最长需要 25 分钟的停机时间，在此期间，所有投放、跟踪链接和 API 调用都无法工作。

完成更新后，所有链接都会按预期工作。

>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
