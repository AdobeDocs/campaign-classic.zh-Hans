---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 96f5709b4c67d1979286cc1f71069a64435c5c70
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 7%

---


# Adobe Campaign配置更新 — 2021年3月{#acc-config-updates}

您必须使用最新的构建和产品修复来更新您的基础架构和设置。 这些修复是确保服务连续性和安全性的必修程序。 此外，您需要调整实施以与第三方更改保持一致。

作为托管客户，Adobe将定期通知您所需的构建升级。 您需要根据建议进行升级，以确保合规性。

作为内部部署/混合客户，出于安全考虑，您必须升级到本页中列出的某个版本。 此外，还必须执行一些手动任务，以确保您的环境是安全的，并且准备好随时从Adobe或第三方系统进行更改。

>[!NOTE]
>
>有关这些更改的任何问题，请联系[Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。


## 安全更新

最新的活动版本附带一个安全修复，可增强针对服务器端请求伪造(SSRF)问题的保护。 请阅读本页](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)了解更多信息。[

**您是否受影响？**

如果您的环境的内部版本低于下面列出的版本，则您会受到影响：

* 金标11。 [了解详情](../rn/using/gold-standard.md)
* 活动 21.1.1版。 [了解详情](../rn/using/latest-release.md)
* 活动 20.3.3版。 [了解详情](../rn/using/release--20-3.md)
* 活动 20.2.4版。 [了解详情](../rn/using/release--20-2.md)
* 活动 20.1.4版。 [了解详情](../rn/using/release--20-1.md)
* 活动 19.2.4版。 [了解详情](../rn/using/release--19-2.md)
* 活动 19.1.8版。 [了解详情](../rn/using/release--19-1.md)

**如何更新？**

您需要升级到上面列出的某个较新版本。

* 作为混合型客户，Adobe会将营销实例升级到新版本，并且强烈建议您也升级其营销实例。

   新版本至少与Campaign Classic 17.9版本兼容，但为防止任何安全漏洞，Adobe强烈建议将所有实例升级到新版本。 

* 作为内部部署客户，系统会要求您将营销和中间源实例升级到较新的版本。

>[!CAUTION]
>
>如果暂时无法升级，则&#x200B;**必须联系Adobe客户关怀团队以手动对实例**&#x200B;应用安全修复。


## 活动客户端控制台更新

最新的Gold Standard 11版本修复了一个回归问题，该问题会阻止使用客户端控制台的某些组件，如投放中的日期选择器和图像管理。 Console升级是必需的。

[了解详情](../rn/using/gold-standard.md)。

>[!NOTE]
>
>此修复也位于最新的[19.1.8](../rn/using/release--19-1.md#release-19-1-8-build-9039)、[19.2.4](../rn/using/release--19-2.md#release-19-2-4-build-9082)和[20.1.4](../rn/using/release--20-1.md#release-20-1-4-build-9126)中。 适用于其他版本的新客户端控制台即将推出。

## Adobe Identity Management系统(IMS)更新

Adobe标识服务(IMS)将停止支持从2021年6月30日&#x200B;**开始的旧版Internet Explorer**。 [了解详情](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

活动客户端控制台已更新，以确保与Adobe IMS兼容。

**您是否受影响？**

如果您通过Adobe ID](../integrations/using/about-adobe-id.md)通过活动 Identity Management服务(IMS)连接到Adobe [，则必须升级到以下列出的某个新版本：

* 金标11。 [了解详情](../rn/using/gold-standard.md)
* 活动 21.1.1版。 [了解详情](../rn/using/latest-release.md)
* 活动 20.3.3版。 [了解详情](../rn/using/release--20-3.md)
* 活动 20.2.4版。 [了解详情](../rn/using/release--20-2.md)
* 活动 20.1.4版。 [了解详情](../rn/using/release--20-1.md)
* 活动 19.2.4版。 [了解详情](../rn/using/release--19-2.md)
* 活动 19.1.8版。 [了解详情](../rn/using/release--19-1.md)

这些版本附带新的连接协议：升级是必需的，因为活动 server和Client Console都必须在2021年6月30日&#x200B;**之后才能连接到活动**。

**如何更新？**

作为托管客户，无需执行任何操作：Adobe已将您的实例升级到较新版本。

作为内部部署/混合型客户，您需要升级到某个较新版本，以从新的客户端控制台中受益，并确保在2021年6月30日之前实现&#x200B;**的无缝过渡。**

升级所有实例后，客户端控制台也需要升级到此版本。

* 了解如何访问[Adobe软件分发](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)。

* [了解如何安装活动 Client Console](../installation/using/installing-the-client-console.md)。

## 与Experience Cloud触发器集成

旧版身份验证服务已到期。 触发集成身份验证（最初基于oAUTH身份验证设置以访问管道）已移至Adobe I/O。它将于2021年11月30日&#x200B;****&#x200B;退休。 [了解详情](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email)。

**您是否受影响？**

如果您的实例运行于&#x200B;**较早版本(活动 19.1.8、20.2.4、Gold Standard 11**)上，则您使用的是通过身份验证实现触发器集成的较早版本：**您需要升级到较新版本并移至Adobe I/O**。

必须升级到以下列出的某个新版本：

* 金标11。 [了解详情](../rn/using/gold-standard.md)
* 活动 21.1.1版。 [了解详情](../rn/using/latest-release.md)
* 活动 20.3.3版。 [了解详情](../rn/using/release--20-3.md)
* 活动 20.2.4版。 [了解详情](../rn/using/release--20-2.md)
* 活动 19.1.8版。 [了解详情](../rn/using/release--19-1.md)

**如何更新？**

实例升级到较新版本后，所有客户都需要按照[过程移动到新的身份验证模式](../integrations/using/configuring-adobe-io.md)。 这需要生成新的Adobe I/O令牌并在实现中使用它。  

此外，对于混合环境，客户需要确保在中间源实例上配置管道。 [了解详情](../integrations/using/configuring-pipeline.md)。

[了解如何迁移到Adobe I/O](../integrations/using/configuring-adobe-io.md)。

## APNs更新

### 基于HTTP/2的APNs提供程序API

自2021年3月31日&#x200B;****&#x200B;起，Apple推送通知服务(APNs)将不再支持旧版二进制协议。 [阅读更多](https://developer.apple.com/news/?id=c88acm2b)。

**您是否受影响？**

如果您的实例运行于比活动 21.1、**更早的**&#x200B;版本上，并使用旧版Apple二进制协议发送推送通知，则需要更新到基于HTTP/2的APNs提供程序API。

**如何更新？**

作为托管客户，无需执行任何操作：Adobe已将您的实例更新为基于HTTP/2的API。

作为内部部署/托管客户，您需要更新配置。 [了解如何迁移到HTTP/2](https://helpx.adobe.com/cn/campaign/kb/migrate-to-apns-http2.html)

### APNs根证书更新

2021年3月29日，Apple推送通知服务(APNs)基础架构更新将影响Adobe Campaign Classic iOS渠道。 操作系统配置更改为&#x200B;**mandatory**&#x200B;以避免iOS推送渠道中断。

了解有关APNs更改[的更多信息，请参阅本页](https://developer.apple.com/news/?id=7gx0a2lp)。

**您是否受影响？**

如果您使用活动在iOS设备上发送推送通知，则会受到影响。

**如何更新？**

作为托管客户，无需执行任何操作：Adobe已将新根证书并入您的环境。

作为内部部署/混合型客户，您需要更新配置以确保在2021年3月29日之前实现&#x200B;**的无缝过渡。**

[了解如何合并新证书](ios-certificate-update.md)。


## 有用的链接

* [升级您的环境](../production/using/build-upgrade.md)
* [构建升级常见问题解答](../platform/using/faq-build-upgrade.md)
* [下载Campaign Classic构建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [使新客户端控制台可供用户使用](../installation/using/client-console-availability-for-windows.md)
