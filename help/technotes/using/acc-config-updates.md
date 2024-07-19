---
product: campaign
title: 技术说明 — Adobe Campaign配置更新
description: Adobe Campaign配置更新
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 8%

---

# 2021年Adobe Campaign配置更新 {#acc-config-updates}



基础架构和设置应定期更新为最新的内部版本和产品修复。 为确保服务的连续性和安全性，这些修复是必需的。 此外，还需要升级以符合第三方更改。

作为&#x200B;**托管客户或Managed Services客户**，Adobe将定期通知您版本升级。 您将需要根据建议进行升级以确保遵循相关建议。

作为&#x200B;**内部部署或混合型客户**，您应该按照最新发布的内部版本，定期升级实施。

出于安全原因，您现在必须升级到下面列出的版本之一。 除了标准升级步骤外，还必须执行一些手动任务，以确保您的环境安全并准备好迎接即将从Adobe或第三方系统进行的更改。

>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
>

## 安全更新 {#acc-security-updates}

最新Campaign版本附带安全修复，可加强针对服务器端请求伪造(SSRF)问题的保护。 请参阅[此页面](https://helpx.adobe.com/cn/security/products/campaign/apsb21-04.html)以了解详情。

**您是否受影响？**

如果您的环境所在的内部版本低于下面列出的内部版本，则您将受到影响：

* Gold Standard 11。 [了解详情](../../rn/using/gold-standard.md)
* Campaign 21.1.1版本。 [了解详情](../../rn/using/latest-release.md)
* Campaign 20.2.5版本。
* Campaign 20.1.4版本。
* Campaign 19.2.4版本。
* Campaign 19.1.8版本。

在本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

**如何更新？**

您需要升级到上面列出的较新内部版本之一。

* 作为混合型客户，Adobe将通知您中间源实例的计划升级日期。 Adobe强烈建议您也升级营销实例。

  新版本向后兼容Campaign Classic17.9版本，但Adobe强烈建议升级所有实例以解决安全漏洞

* 作为内部部署客户，您需要将营销和中间源实例升级到最新内部版本。

>[!CAUTION]
>
>如果在建议的时间范围内无法升级，则应联系Adobe客户关怀团队，为您的实例应用短期手动安全修补程序&#x200B;**。**
>

## Campaign Classic客户端控制台更新  {#acc-cc-updates}

应安装下面的&#x200B;**当前可用**&#x200B;控制台版本以解决最近识别的回归。 这种回归方法禁止使用客户端控制台的某些组件，如投放中的日期选取器和图像管理。 必须升级&#x200B;**控制台**。

* 最新的Gold Standard 11内部版本9032@10c2709。 [了解详情](../../rn/using/gold-standard.md)
* Campaign 20.1.4版本。
* Campaign 19.2.4版本。
* Campaign 19.1.8版本。

## AdobeIdentity Management System (IMS)更新

Adobe标识服务(IMS)将从2021年6月30日&#x200B;**起停止支持旧Internet Explorer版本**。 [了解详情](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

需要升级Campaign客户端控制台，以确保与Adobe IMS兼容。

**您是否受影响？**

如果您要通过Adobe ID](../../integrations/using/about-adobe-id.md)和AdobeIdentity Management服务(IMS)连接到Campaign [，则必须升级到以下列出的新版本之一：

* Gold Standard 11。 [了解详情](../../rn/using/gold-standard.md)
* Campaign 21.1.1版本。 [了解详情](../../rn/using/latest-release.md)
* Campaign 20.2.5版本。
* Campaign 20.1.4版本。
* Campaign 19.2.4版本。
* Campaign 19.1.8版本。

这些版本附带新的连接协议：Campaign服务器和客户端控制台都必须升级，才能在&#x200B;**2021年6月30日**&#x200B;后连接到Campaign。

在本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

**如何更新？**

作为托管客户，Adobe将很快协助您将实例升级到新版本。

作为内部部署/混合部署客户，您需要升级到较新版本之一，以便从新的客户端控制台中受益，并确保在2021年6月30日之前&#x200B;**无缝过渡**。

升级所有实例后，客户端控制台也需要升级到此版本。

* 了解如何访问[Adobe软件分发](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans)。

* [了解如何安装Campaign客户端控制台](../../installation/using/installing-the-client-console.md)。

## 与Experience Cloud触发器集成 {#acc-triggers-updates}

旧版oAuth身份验证服务的生命周期已终止。 最初基于oAUTH身份验证设置来访问管道的Triggers集成身份验证已移至Adobe I/O。营销活动[的旧版oAuth身份验证模式已于&#x200B;**2021年9月**&#x200B;停用](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。 托管环境的支持时间可延长至 **2022 年 2 月 23 日**。作为内部部署或混合型部署客户，请联系Adobe客户关怀团队，将支持延长至2022年2月。 您必须向 Adobe 提供 [OAuth 应用程序的 AppID](../../integrations/using/configuring-pipeline.md#step-optional)。

**您是否受影响？**

如果您的实例在低于Campaign 19.1.8、20.2.4、Gold Standard 11 **的**&#x200B;版本上运行，则您正在通过oAuth身份验证使用旧版本的Triggers集成： **您需要升级到较新版本并移至Adobe I/O**。

必须升级到下列新版本之一：

* Gold Standard 11。 [了解详情](../../rn/using/gold-standard.md)
* Campaign 21.1.1版本。 [了解详情](../../rn/using/latest-release.md)
* Campaign 20.2.5版本。
* Campaign 19.1.8版本。

在本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

**如何更新？**

实例升级到较新版本后，所有客户需要按照[过程移动到新身份验证模式](../../integrations/using/about-triggers.md#implement)。 这需要您生成新的Adobe I/O令牌并在实施中使用它。  

此外，对于混合环境，客户需要确保在中间源实例上配置管道。 [了解详情](../../integrations/using/configuring-pipeline.md)。

[了解如何迁移到Adobe I/O](../../integrations/using/about-triggers.md#implement)。

## APNs更新 {#acc-apns-updates}

### 基于HTTP/2的APNs提供程序API

自2021年3月31日&#x200B;**起**，Apple推送通知服务(APN)不再支持旧版二进制协议。 [了解更多信息](https://developer.apple.com/news/?id=c88acm2b)。

**您是否受影响？**

如果您的实例在低于Campaign 21.1，**的**&#x200B;版本上运行，并且您使用旧版Apple二进制协议发送推送通知，则需要更新为基于HTTP/2的APNs提供程序API。

在本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。

**如何更新？**

作为托管客户，如果您已升级到新内部版本，则Adobe已将您的实例更新为基于HTTP/2的API。

作为内部部署/混合部署客户，您需要更新配置。

### APNs根证书更新

2021年3月29日，Apple推送通知服务(APN)基础设施更新影响Adobe Campaign Classic iOS渠道。 操作系统配置更改是&#x200B;**必需的**，这样可避免iOS推送渠道中断。

在此页面](https://developer.apple.com/news/?id=7gx0a2lp)中了解有关APN更改[的更多信息。

**您是否受影响？**

如果您使用Campaign在iOS设备上发送推送通知，则会受到影响。

**如何更新？**

作为托管客户，无需执行任何操作：Adobe已将新的根证书并入您的环境。

作为内部部署/混合部署客户，您需要更新配置以确保在2021年3月29日之前实现无缝过渡&#x200B;****。

[了解如何合并新证书](ios-certificate-update.md)。

## 有用的链接

* [升级环境](../../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [下载Campaign Classic内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)
* [使用户可以使用新的客户端控制台](../../installation/using/client-console-availability-for-windows.md)
