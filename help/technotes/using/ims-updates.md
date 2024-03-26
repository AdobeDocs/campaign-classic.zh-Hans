---
product: campaign
title: 技术说明 — 更新您的环境以使用IMS连接到Adobe Campaign
description: Campaign - IMS更新
feature: Technote, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 6%

---

# 如何更新您的环境以使用IMS连接到Adobe Campaign {#acc-ims-faq}



2021年6月30日，已对 [AdobeIdentity Management System](https://helpx.adobe.com/cn/enterprise/using/identity.html) (IMS)登录功能，这可能会影响您继续使用Adobe Campaign的能力。 了解如何确保继续不间断地使用Adobe Campaign Classic v7。

## 更改了哪些内容？

AdobeIdentity Management服务(IMS)已停止支持上的旧Internet Explorer版本 **2021年6月30日**. [了解详情](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

Adobe希望在2021年6月30日之后为所有客户保留IMS功能。 IMS是安全框架的一部分，该框架允许用户登录到客户端控制台，即Adobe Campaign。

要保留此功能，客户必须更新每个用户计算机上的客户端控制台，并确保对您的进行最新更新 [Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)，替换为 **Internet Explorer 11** 内置，安装在每个用户的计算机上。

## 您是否受影响？

如果您要连接到Campaign [通过Adobe ID](../../integrations/using/about-adobe-id.md)，通过AdobeIdentity Management服务(IMS)并运行比下面列出的版本旧的Campaign版本，您会受到影响。

如果您已升级，但使用的是旧版本的Microsoft Internet Explorer，则必须升级到Internet Explorer 11。

## 如何更新？

* 作为托管客户，Adobe已将您的实例升级到较新版本。

* 作为内部部署/混合部署客户，您需要升级到上面列出的较新版本之一，以便从新的客户端控制台中受益并确保无缝过渡 **2021年6月30日之前**.

  必须升级到下列新版本之一：

   * Gold Standard 11。 [了解详情](../../rn/using/gold-standard.md)
   * Campaign 21.1.3版本。 [了解详情](../../rn/using/latest-release.md)
   * Campaign 20.2.5版本。
   * Campaign 20.1.4版本。
   * Campaign 19.2.4版本。

  这些版本随附新的连接协议。 Campaign服务器和客户端控制台都必须进行升级：一旦升级了所有实例，客户端控制台就需要升级到此版本，并且之后能够连接到Campaign **2021年6月30日**.

此外，请确保对您的 [Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)，替换为 **Internet Explorer 11** 内置，安装在每个用户的计算机上。

## 常见问题解答

**如何检查我的Campaign版本？**

了解如何检查您的版本 [在此部分中](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**如何检查我是否使用IMS？**

要检查连接模式，您可以：

* 启动Campaign客户端控制台并访问实例连接设置。 如果 **与Adobe ID连接** 选项，则表示您使用的是Adobe IMS。

  ![](../../integrations/using/assets/ims_1.png)

或者

* 启动Campaign客户端控制台，并检查您的连接窗口。 如果您正在与Adobe ID连接，如以下屏幕所示，则您使用的是IMS。

  ![](../../integrations/using/assets/adobeID.png)

**连接警告消息**

如果用户需要更新其客户端控制台或使用旧版本的Microsoft Internet Explorer，则以下警告消息对用户可见： **您需要安装更新到Windows和/或Adobe应用的最新版本。**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

如果看到此类警告，请确保安装正在使用的操作系统的最新更新。 [了解详情](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

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
* [下载Campaign Classic版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)
