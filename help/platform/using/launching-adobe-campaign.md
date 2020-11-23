---
solution: Campaign Classic
product: campaign
title: 启动 Adobe Campaign
description: 启动 Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 50%

---


# 启动 Adobe Campaign{#launching-adobe-campaign}

活动客户端控制台是一个富客户端，它允许您连接到活动应用服务器。 了解如何在本页中下载和配置客户端 [控制台](../../installation/using/installing-the-client-console.md)。

## 打开 Adobe Campaign {#starting-adobe-campaign}

您可以通过选择来开始 **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]** Adobe Campaign。

您可以利用客户端控制台连接窗口选择或配置现有数据库，并使用用户名和密码连接系统：

![](assets/acc-logon.png)

## 连接 Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用 Adobe ID 连接到 Adobe Campaign。有关详细信息，请参见[此页面](../../integrations/using/about-adobe-id.md)。

您也可以使用专用的登录名/密码进行连接：

1. 在 **[!UICONTROL login]** 字段中输入操作员帐户标识符。

   您的 Adobe Campaign 平台管理员会为您提供标识符。

1. 在 **[!UICONTROL Password]** 字段中输入您的密码。

   首次访问数据库时，您的密码是由管理员为您提供的。Once you are connected, you can change your password via the **[!UICONTROL Tools > Change password...]** menu. Details on operators and connections are available in [Access management](../../platform/using/access-management.md).

1. Click **[!UICONTROL LOG IN]** to confirm.

现在可以访问 [Adobe Campaign 工作区](../../platform/using/adobe-campaign-workspace.md)了。

## 设置连接 {#setting-up-connections}

您可以通过输入区上方的链接来访问服务器连接设置。

![](assets/s_ncs_user_connections_management.png)

In the **[!UICONTROL Connections]** window, click **[!UICONTROL Add > Connection]**.

然后您必须定义连接设置。操作步骤：

1. 输入 **[!UICONTROL Label]**，为数据库连接命名。

1. 在 **[!UICONTROL URL]** 字段中，添加应用程序服务器的地址。如果您不知道连接 URL，请联系管理员。

1. Check **[!UICONTROL Connect with an Adobe ID]** for the operators to connect to the console using their Adobe ID. 有关详细信息，请参见[此页面](../../integrations/using/about-adobe-id.md)。

1. Click **[!UICONTROL OK]** to validate.

## 操作员和权限 {#operators-and-permissions}

具有软件访问权及其相关权限的操作员的标识符与密码是由 Adobe Campaign 系统管理员在 Adobe Campaign 树状结构的 **[!UICONTROL Administration > Access management > Operators]** 节点中定义的。

This functionality is detailed in the [Access management](../../platform/using/access-management.md) section.

## 中断 Adobe Campaign 连接 {#disconnecting-from-adobe-campaign}

要中断 Adobe Campaign 的连接，请使用图标栏中的第一个图标。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以关闭应用程序，无需先行注销。

## Getting your Adobe Campaign version {#getting-your-campaign-version}

The **[!UICONTROL Help > About...]** menu lets you access the following information:

* **活动** 客户端控制台和应用程序服务器的版本号
* **活动** 客户端控制台和应用程序服务器的内部版本号
* 联系Adobe客户关怀的链接
* adobe隐私政策、使用条款和Cookie政策的链接

![](assets/about-acc.png)

无论您何时联系Adobe客户关怀团队，您都需要提供Adobe Campaign客户控制台和应用程序服务器的版本号和内部版本号。

如果您运行的是 [活动金标版](../../rn/using/gold-standard.md)，则还需要共享框中显示的SHA/1字 **[!UICONTROL About]** 符。 例如，对于Gold Standard 10 **版本**，内部版本号将显 **示内部版本** 9032@efd8a94，如下所示：

![](assets/about-acc-gs.png)

在本文中进一步了 [解金本位](https://helpx.adobe.com/cn/campaign/kb/gold-standard.html)。

**相关主题**：

* [Adobe Campaign帮助和支持选项](https://helpx.adobe.com/cn/campaign/kb/ac-support.html#acc-support)
* [Adobe软件分发](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)
* [Adobe Experience Cloud支助和专家会议](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
