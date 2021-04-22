---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 65ff09dd8ded029178c4c85489bf01ef80d16e8d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 6%

---

# 跟踪的URL签名问题{#tracked-urls}

在最近的更改后，当URL签名在活动中处于活动状态时，跟踪的URL可能会失败。 某些邮箱可能比其他邮箱受到的影响更大，因为某些公司具有特定的安全工具，这些工具可能会影响链接并更改URL签名机制。

因此，Adobe建议您禁用跟踪链接的签名机制。 此过程修复了旧的跟踪链接，但接收到的多次转义链接除外。

请注意，退订链路可能会像任何其他链接一样失败，其频率从主机到主机是可变的，但小于1%。

**您是否受影响？**

为了提高安全性，[活动 Gold Standard 8](../rn/using/gold-standard.md#gs8) - 2020年4月引入了用于跟踪电子邮件中链接的签名机制，默认情况下，启动内部版本19.1.4(9032@3a9dc9c)和活动 20.2的所有客户都将启用该机制。

如果您的环境运行在以下列出的某个版本上，您可能会受到影响：

* 金标7至11。 [了解详情](../rn/using/gold-standard.md)
* 活动 21.1.1到21.1.2版本。 [了解详情](../rn/using/latest-release.md)
* 活动 20.3.1到20.3.3版本。 [了解详情](../rn/using/release--20-3.md)
* 活动 20.2.1到20.2.3版本。 [了解详情](../rn/using/release--20-2.md)
* 活动 20.1.1到21.1.3版本。 [了解详情](../rn/using/release--20-1.md)
* 活动 19.2.2到19.2.3版本。 [了解详情](../rn/using/release--19-2.md)
* 活动 19.1.5到19.1.7版本。 [了解详情](../rn/using/release--19-1.md)

了解如何在本节](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中检查您的版本[。

**如何更新？**

作为&#x200B;**托管客户**,Adobe将与您合作，在不久后更新您的配置。

作为&#x200B;**内部部署/混合客户**，您需要更新配置。

按照以下步骤操作：

1. 在[服务器配置文件](../installation/using/the-server-configuration-file.md)(serverConf.xml)中，将&#x200B;**signEmailLinks**&#x200B;更改为&#x200B;**false**。
1. 重新启动&#x200B;**nlserver**&#x200B;服务。
1. 在跟踪服务器上，重新启动Web服务器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>**config-`<instance>`.xml**&#x200B;文件将覆盖&#x200B;**serverConf.xml**&#x200B;设置。 如果&#x200B;**signEmailLinks**&#x200B;在&#x200B;**config-`<instance>`.xml**&#x200B;中存在（其中&#x200B;**instance**&#x200B;是实例的名称），则还必须将其转换为&#x200B;**false**。


**影响是什么？**

维护最长需要25分钟的停机时间，在此期间，所有投放、跟踪链接和API调用都将无效。

完成更新后，所有链接都会按预期工作。

>[!NOTE]
>
>有关这些更改的任何问题，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

