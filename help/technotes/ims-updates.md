---
product: campaign
title: 更新您的环境以使用IMS连接到Adobe Campaign。
description: 营销活动 — IMS更新
hide: true
hidefromtoc: true
source-git-commit: 6a5253c1aa35e904635919f6c863930d376b473f
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 9%

---

# 如何更新环境以使用IMS连接到Adobe Campaign。 {#acc-ims-faq}

2021年6月30日，将对[AdobeIdentity Management系统](https://helpx.adobe.com/enterprise/using/identity.html)(IMS)登录功能进行更改，这可能会影响您继续使用Adobe Campaign的能力。 了解如何确保您继续使用Adobe Campaign Classic v7而不中断。

## 更改了哪些内容？

AdobeIdentity Management服务(IMS)将从2021年6月30日&#x200B;**开始停止支持旧的Internet Explorer版本**。 [了解详情](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

Adobe希望在2021年6月30日之前为所有客户保留IMS功能。 IMS是安全框架的一部分，该框架允许用户登录客户端控制台，从而登录Adobe Campaign。

要保留此功能，客户必须在每台用户的计算机上更新客户端控制台，并确保在每台用户的计算机上安装了内置&#x200B;**Internet Explorer 11**&#x200B;的[Windows版本](../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)的最新更新。

## 您是否受影响？

如果您通过Adobe ID](../integrations/using/about-adobe-id.md)、AdobeIdentity Management服务(IMS)连接到Campaign [，并运行比下面所列版本旧的Campaign版本，则会受到影响。

如果您已升级，但使用的是旧版Microsoft Internet Explorer，则必须升级到Internet Explorer 11。

## 如何更新？

* 作为托管客户，Adobe已将您的实例升级到新版本。

* 作为内部部署/混合型客户，您需要升级到上面列出的其中一个新版本，以便从新的客户端控制台中受益，并确保在2021年6月30日之前实现无缝过渡&#x200B;****。

   必须升级到下面列出的某个新版本：

   * Gold Standard 11。 [了解详情](../rn/using/gold-standard.md)
   * Campaign 21.1.3版本。 [了解详情](../rn/using/latest-release.md)
   * Campaign 20.2.5版本。 [了解详情](../rn/using/release--20-2.md)
   * Campaign 20.1.4版本。 [了解详情](../rn/using/release--20-1.md)
   * Campaign 19.2.4版本。 [了解详情](../rn/using/release--19-2.md)
   * Campaign 19.1.8版本。 [了解详情](../rn/using/release--19-1.md)

   这些版本随附了新的连接协议。 Campaign服务器和客户端控制台都必须进行升级：升级所有实例后，需要将客户端控制台升级到此版本，并能够在2021年6月30日&#x200B;****&#x200B;之后连接到Campaign。

此外，请确保在每台用户的计算机上安装了内置&#x200B;**Internet Explorer 11**&#x200B;的[Windows版本](../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)的最新更新。

## 常见问题解答

**如何检查Campaign版本？**

在此部分](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的版本[。


**如何检查我是否使用IMS?**

要检查连接模式，您可以：

* 启动Campaign客户端控制台并访问实例连接设置。 如果选中了&#x200B;**连接到Adobe ID**&#x200B;选项，则表明您使用的是AdobeIMS。

   ![](../integrations/using/assets/ims_1.png)

或者

* 启动Campaign客户端控制台，并检查连接窗口。 如果您连接的是Adobe ID（如下面的屏幕所示），则您使用的是IMS。

   ![](../integrations/using/assets/adobeID.png)

**连接警告消息**

如果用户需要更新其客户端控制台或使用旧版Microsoft Internet Explorer，则用户会看到以下警告消息：**您需要安装最新更新到Windows和/或您的Adobe应用程序。**

![](../integrations/using/assets/do-not-localize/errorMsg.png)

如果您看到此类警告，请确保安装所使用操作系统的最新更新。 [了解详情](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

**在2021年6月30日之后**，您将看到以下消息，并且将无法再连接到Adobe Campaign:

![](../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>有关这些更改的任何问题，请联系 [Adobe 客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。


## 有用链接

* [升级环境](../production/using/build-upgrade.md)
* [内部版本升级常见问题解答](../platform/using/faq-build-upgrade.md)
* [使新客户端控制台可供用户使用](../installation/using/client-console-availability-for-windows.md)
* [安装 Campaign Client Console](../installation/using/installing-the-client-console.md)
* [访问AdobeSoftware Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)
* [下载Campaign Classic内部版本](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)