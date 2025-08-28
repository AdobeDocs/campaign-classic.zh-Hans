---
product: campaign
title: 技术说明 — 更新您的环境以使用IMS连接到Adobe Campaign
description: Campaign - IMS更新
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 62fc46e45078fce56eadda3518251e61244bf5d0
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 5%

---

# 如何更新您的环境以使用IMS连接到Adobe Campaign {#acc-ims-faq}



在2021年6月30日，已对[Adobe Identity Management System](https://helpx.adobe.com/cn/enterprise/using/identity.html) (IMS)登录功能进行了更改，这可能会影响您继续使用Adobe Campaign的能力。 了解如何确保继续不间断地使用Adobe Campaign Classic v7。

## 更改了哪些内容？

Adobe Identity Management服务(IMS)已于2021年6月30日&#x200B;**停止支持旧Internet Explorer版本**。 [了解详情](https://helpx.adobe.com/cn/x-productkb/global/update-operating-system-and-browser.html)。

Adobe希望在2021年6月30日之后为所有客户保留IMS功能。 IMS是安全框架的一部分，该框架允许用户登录到客户端控制台，即Adobe Campaign。

要保留此功能，客户必须在每个用户的计算机上更新客户端控制台，并确保在每个用户的计算机上安装了具有[Internet Explorer 11](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)内置的&#x200B;**Windows版本**&#x200B;的最新更新。

## 您是否受影响？

如果您通过Adobe ID[和Adobe Identity Management Service (IMS)连接到Campaign ](../../integrations/using/about-adobe-id.md)，并运行比下面列出的版本旧的Campaign，则您将受到影响。

如果您已升级，但使用的是旧版本的Microsoft Internet Explorer，则必须升级到Internet Explorer 11。

## 如何更新？

* 作为托管客户，Adobe已将您的实例升级到较新版本。

* 作为内部部署/混合部署客户，您需要升级到上面列出的较新版本之一，以便从新的客户端控制台中受益，并确保在2021年6月30日之前实现&#x200B;**的无缝过渡**。

  必须升级到下列新版本之一：

   * Gold Standard 11。 [了解详情](../../rn/using/gold-standard.md)
   * Campaign 21.1.3版本。 [了解详情](../../rn/using/latest-release.md)
   * Campaign 20.2.5版本。
   * Campaign 20.1.4版本。
   * Campaign 19.2.4版本。

  这些版本随附新的连接协议。 Campaign服务器和客户端控制台都必须升级：一旦升级了所有实例，客户端控制台就需要升级到此版本，并且在&#x200B;**2021年6月30日**&#x200B;之后能够连接到Campaign。

此外，请确保在每个用户的计算机上都安装了[Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)的最新更新，其中包含&#x200B;**Internet Explorer 11**&#x200B;内置。

## 常见问题解答

**如何检查我的Campaign版本？**

在本节[中了解如何检查您的版本](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。


**如何检查我是否使用IMS？**

要检查连接模式，您可以：

* 启动Campaign客户端控制台并访问实例连接设置。 如果选择了&#x200B;**Connect with an Adobe ID**&#x200B;选项，则表示您使用的是Adobe IMS。

  ![](../../integrations/using/assets/ims_1.png)

或者

* 启动Campaign客户端控制台，并检查您的连接窗口。 如果您正在与Adobe ID连接，如以下屏幕所示，则您使用的是IMS。

  ![](../../integrations/using/assets/adobeID.png)

**连接警告消息**

如果用户需要更新其客户端控制台或使用旧版本的Microsoft Internet Explorer，他们将会看到以下警告消息： **您需要安装更新到Windows和/或Adobe应用的最新版本。**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

如果看到此类警告，请确保安装正在使用的操作系统的最新更新。 [了解详情](https://helpx.adobe.com/cn/x-productkb/global/update-operating-system-and-browser.html)

如果未更新Internet Explorer版本，则会看到以下消息，并且无法再连接到Adobe Campaign：

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
>

## 有用的链接

* [升级环境](../../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../../platform/using/faq-build-upgrade.md)
* [使用户可以使用新的客户端控制台](../../installation/using/client-console-availability-for-windows.md)
* [安装 Campaign Client Console](../../installation/using/installing-the-client-console.md)
* [访问Adobe软件分发](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans)
* [下载Campaign Classic内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/zh-hans/campaign.html)
