---
product: campaign
title: 启动 Adobe Campaign
description: 启动 Adobe Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 51%

---

# 启动 Adobe Campaign{#launching-adobe-campaign}



Campaign客户端控制台是一个富客户端，可用于连接到Campaign应用程序服务器。 了解如何在中下载和配置客户端控制台 [此页面](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>在中检查您的系统和工具与Adobe Campaign客户端控制台的兼容性 [兼容性矩阵](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## 启动Adobe Campaign {#starting-adobe-campaign}

您可以通过选择启动Adobe Campaign **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

您可以利用客户端控制台连接窗口选择或配置现有数据库，并使用用户名和密码连接系统：

![](assets/acc-logon.png)

## 连接到Adobe Campaign {#connecting-to-adobe-campaign}

您可以使用 Adobe ID 连接到 Adobe Campaign。有关详细信息，请参见[此页面](../../integrations/using/about-adobe-id.md)。

您也可以使用专用的登录名/密码进行连接：

1. 在 **[!UICONTROL Login]** 字段中输入操作员帐户标识符。

   您的 Adobe Campaign 平台管理员会为您提供标识符。

1. 在 **[!UICONTROL Password]** 字段中输入您的密码。

   首次访问数据库时，您的密码是由管理员为您提供的。连接后，您可以通过 **[!UICONTROL Tools > Change password...]** 菜单。 有关运算符和连接的详细信息，请参阅 [访问管理](../../platform/using/access-management.md).

1. 单击 **[!UICONTROL LOG IN]** 确认。<!--You can also press the **Enter** key to launch connection.-->

现在可以访问 [Adobe Campaign 工作区](../../platform/using/adobe-campaign-workspace.md)了。

一些键盘快捷键可在 **[!UICONTROL Sign in screen]**：
* 所有可操作项目均可通过以下方式选择 **选项卡** 键（从上到下）或 **选项卡** + **Shift** 键（从下到上）。
* 要启动connection，您还可以按 **输入** 键。
* 您可以使用 **转义** 用于重置 **[!UICONTROL Login]** 和 **[!UICONTROL Password]** 字段到上一个成功连接值。

## 设置连接 {#setting-up-connections}

您可以通过输入区上方的链接来访问服务器连接设置。

![](assets/s_ncs_user_connections_management.png)

在 **[!UICONTROL Connections]** 窗口，单击 **[!UICONTROL Add > Connection]**.

然后您必须定义连接设置。操作步骤：

1. 输入 **[!UICONTROL Label]**，为数据库连接命名。

1. 在 **[!UICONTROL URL]** 字段中，添加应用程序服务器的地址。如果您不知道连接 URL，请联系管理员。

1. Check **[!UICONTROL Connect with an Adobe ID]** 运算符使用其Adobe ID连接到控制台。 有关详细信息，请参见[此页面](../../integrations/using/about-adobe-id.md)。

1. 单击 **[!UICONTROL OK]** 进行验证。

## 操作员和权限 {#operators-and-permissions}

具有软件访问权及其相关权限的操作员的标识符与密码是由 Adobe Campaign 系统管理员在 Adobe Campaign 树状结构的 **[!UICONTROL Administration > Access management > Operators]** 节点中定义的。

有关该功能的详情，请参见 [访问管理](../../platform/using/access-management.md) 部分。

## 断开与Adobe Campaign的连接 {#disconnecting-from-adobe-campaign}

要中断 Adobe Campaign 的连接，请使用图标栏中的第一个图标。

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>您也可以关闭应用程序，无需先行注销。

## 获取Adobe Campaign版本 {#getting-your-campaign-version}

此 **[!UICONTROL Help > About...]** 菜单可让您访问以下信息：

* **version** Campaign客户端控制台和应用程序服务器的编号
* **生成** Campaign客户端控制台和应用程序服务器的编号
* 用于联系 Adobe 客户关怀团队的链接
* 指向 Adobe 隐私政策、使用条款和 Cookie 政策的链接

![](assets/about-acc.png)

每当您联系Adobe客户关怀团队时，都需要提供Adobe Campaign客户端控制台和应用程序服务器的版本号和内部版本号。

**相关主题**：

* [Adobe Campaign帮助和支持选项](../../support.md)
* [Adobe Campaign Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)
* [Adobe Experience Cloud支持和专家讲座](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
