---
product: campaign
title: 技术说明
description: 技术说明
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 28d60a02e3c94264c5ee311cf6ea2d21fd89bd4b
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 11%

---

# Adobe Campaign配置更新 — 2021年3月 {#acc-config-updates}

基础架构和设置应定期更新以包含最新内部版本和产品修复。 这些修复是确保服务和安全的连续性所必需的。 此外，需要升级才能与第三方更改保持一致。

作为&#x200B;**托管或Managed Services客户**,Adobe将定期通知您内部版本升级。 您将需要根据建议进行升级，以确保合规性。

作为&#x200B;**内部部署或混合客户**，您应当根据最新发布的内部版本定期升级您的实施。

出于安全考虑，您现在必须升级到下面列出的某个版本。 除了标准升级步骤之外，还必须执行一些手动任务，以确保您的环境安全，并且可以随时更改Adobe或第三方系统。

>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。


## 安全更新 {#acc-security-updates}

最新的Campaign版本随附了安全修复，该修复增强了针对服务器端请求伪造(SSRF)问题的保护。 请参阅[此页面](https://helpx.adobe.com/cn/security/products/campaign/apsb21-04.html)以了解详情。

**您是否受影响？**

如果您的环境的内部版本低于下面列出的环境，则您会受到影响：

* Gold Standard 11。 [了解详情](../rn/using/gold-standard.md)
* Campaign 21.1.1版本。 [了解详情](../rn/using/latest-release.md)
* Campaign 20.2.4版本。 [了解详情](../rn/using/release--20-2.md)
* Campaign 20.1.4版本。 [了解详情](../rn/using/release--20-1.md)
* Campaign 19.2.4版本。 [了解详情](../rn/using/release--19-2.md)
* Campaign 19.1.8版本。 [了解详情](../rn/using/release--19-1.md)

在此部分](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

**如何更新？**

您需要升级到上面列出的其中一个较新的内部版本。

* 作为混合客户，Adobe将通知您中间源实例的计划升级日期。 Adobe强烈建议您也升级营销实例。

   新内部版本向后兼容Campaign Classic17.9版本，但Adobe强烈建议在所有实例上升级以解决安全漏洞

* 作为内部部署客户，系统会要求您将营销和中间源实例升级为最新内部版本。

>[!CAUTION]
>
>如果无法在建议的时间范围内升级，**您应联系Adobe客户关怀团队，以对实例**&#x200B;应用短期手动安全修复。


## Campaign Classic客户端控制台更新  {#acc-cc-updates}

**现在可用的**&#x200B;控制台版本应该安装在下面，以解析最近识别的回归。 此回归会阻止在投放中使用客户端控制台的某些组件，例如日期选取器和图像管理。 **必须** 升级控制台。

* 最新Gold Standard 11内部版本9032@10c2709。 [了解详情](../rn/using/gold-standard.md)
* Campaign 20.1.4版本。 [了解详情](../rn/using/release--20-1.md)
* Campaign 19.2.4版本。 [了解详情](../rn/using/release--19-2.md)
* Campaign 19.1.8版本。 [了解详情](../rn/using/release--19-1.md)

## AdobeIdentity Management系统(IMS)更新

Adobe标识服务(IMS)将从2021年6月30日&#x200B;**开始停止支持旧的Internet Explorer版本。**[了解详情](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

需要升级Campaign客户端控制台，以确保与AdobeIMS兼容。

**您是否受影响？**

如果您通过Adobe ID](../integrations/using/about-adobe-id.md)连接到Campaign [，则必须通过AdobeIdentity Management服务(IMS)升级到下面列出的某个新版本：

* Gold Standard 11。 [了解详情](../rn/using/gold-standard.md)
* Campaign 21.1.1版本。 [了解详情](../rn/using/latest-release.md)
* Campaign 20.2.5版本。 [了解详情](../rn/using/release--20-2.md)
* Campaign 20.1.4版本。 [了解详情](../rn/using/release--20-1.md)
* Campaign 19.2.4版本。 [了解详情](../rn/using/release--19-2.md)
* Campaign 19.1.8版本。 [了解详情](../rn/using/release--19-1.md)

这些版本随附了新的连接协议：必须升级，Campaign服务器和客户端控制台才能在2021年6月30日&#x200B;**后连接到Campaign。**

在此部分](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

**如何更新？**

作为托管客户，Adobe将很快与您合作，将您的实例升级到新版本。

作为内部部署/混合型客户，您需要升级到其中一个较新版本，以便从新的客户端控制台中受益，并确保在2021年6月30日之前实现无缝过渡&#x200B;****。

升级所有实例后，还需要将客户端控制台升级到此版本。

* 了解如何访问[AdobeSoftware Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)。

* [了解如何安装Campaign客户端控制台](../installation/using/installing-the-client-console.md)。

## 与Experience Cloud触发器集成 {#acc-triggers-updates}

旧版oAuth身份验证服务已终止。 Triggers集成身份验证（最初基于用于访问管道的oAUTH身份验证设置）已移至Adobe I/O。Campaign [的旧版oAuth身份验证模式已在&#x200B;**2021年8月18日**&#x200B;停用](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。 托管环境将从扩展中受益，直到2021年11月30日&#x200B;**。**&#x200B;作为内部部署或混合型客户，请联系Adobe客户关怀团队，将支持延长至2021年11月30日。 您必须提供[OAuth应用程序](../integrations/using/configuring-pipeline.md?lang=en#step-optional)的AppID才能Adobe。

**您是否受影响？**

如果您的实例在低于Campaign 19.1.8、20.2.4、Gold Standard 11 **的**&#x200B;版本上运行，则表明您使用的是通过oAuth身份验证的旧版Triggers集成：**您需要升级到较新版本并移至Adobe I/O**。

必须升级到下面列出的某个新版本：

* Gold Standard 11。 [了解详情](../rn/using/gold-standard.md)
* Campaign 21.1.1版本。 [了解详情](../rn/using/latest-release.md)
* Campaign 20.2.5版本。 [了解详情](../rn/using/release--20-2.md)
* Campaign 19.1.8版本。 [了解详情](../rn/using/release--19-1.md)

在此部分](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

**如何更新？**

将实例升级到较新版本后，所有客户都需要按照[过程迁移到新的身份验证模式](../integrations/using/configuring-adobe-io.md)。 这要求您生成新的Adobe I/O令牌，并将其用在实施中。  

此外，对于混合环境，客户需要确保在中间源实例上配置管道。 [了解详情](../integrations/using/configuring-pipeline.md)。

[了解如何迁移到Adobe I/O](../integrations/using/configuring-adobe-io.md)。

## APNs更新 {#acc-apns-updates}

### 基于HTTP/2的APNs提供程序API

自2021年3月31日&#x200B;****&#x200B;起，Apple推送通知服务(APNs)不再支持旧版二进制协议。 [阅读更多](https://developer.apple.com/news/?id=c88acm2b)。

**您受影响吗？**

如果您的实例在低于Campaign 21.1、**的**&#x200B;版本上运行，并且您使用旧版Apple二进制协议发送推送通知，则需要更新到基于HTTP/2的APNs提供程序API。

在此部分](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

**如何更新？**

作为托管客户，如果您已升级到新内部版本，则Adobe已将您的实例更新为基于HTTP/2的API。

作为内部部署/混合客户，您需要更新配置。 [了解如何迁移到HTTP/2](https://helpx.adobe.com/cn/campaign/kb/migrate-to-apns-http2.html)

### APNs根证书更新

2021年3月29日，Apple推送通知服务(APNs)基础架构更新影响了Adobe Campaign Classic iOS渠道。 要避免iOS推送渠道中断，操作系统配置更改为&#x200B;**必需**。

在本页](https://developer.apple.com/news/?id=7gx0a2lp)中了解有关APNs更改[的更多信息。

**您是否受影响？**

如果您使用Campaign在iOS设备上发送推送通知，则会受到影响。

**如何更新？**

作为托管客户，无需执行任何操作：Adobe已将新的根证书纳入到您的环境中。

作为内部部署/混合型客户，您需要更新配置以确保在2021年3月29日之前实现无缝过渡&#x200B;****。

[了解如何合并新证书](ios-certificate-update.md)。

## 有用链接

* [升级环境](../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../platform/using/faq-build-upgrade.md)
* [下载Campaign Classic内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)
* [使新客户端控制台可供用户使用](../installation/using/client-console-availability-for-windows.md)
