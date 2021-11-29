---
product: campaign
title: 在 Facebook 好友墙上发布
description: 在 Facebook 好友墙上发布
audience: social
content-type: reference
topic-tags: configuration
exl-id: 2135a836-245f-406e-b351-c27d38e0f9fd
source-git-commit: d11c918213e72fe4bf6adb464e516fac19b63d54
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 4%

---

# 在 Facebook 好友墙上发布{#publishing-on-facebook-walls}

![](../../assets/v7-only.svg)

为了使Adobe Campaign能够将出版物发送到Facebook墙，您需要将这些页面的写入权限委派给Adobe Campaign。 这涉及以下配置步骤：

1. 创建具有一个或多个页面的Facebook帐户。
1. 创建用于发送校样的测试Facebook页面。
1. 创建 Facebook 应用程序.
1. 在Adobe Campaign中输入Facebook应用程序设置，即 **[!UICONTROL Facebook routing]** 外部帐户。

## 先决条件 {#prerequisites}

首先，创建Facebook帐户和多个页面：这些将用于发送发布内容。

* 要创建Facebook帐户，请使用 [https://www.facebook.com](https://www.facebook.com) 链接。
* 要创建Facebook页面，请使用 [https://www.facebook.com/pages/create](https://www.facebook.com/pages/create) 链接。

   我们建议使用相同的Facebook帐户管理您的所有页面。 这样，您只需一个Facebook应用程序和一个外部帐户即可在该帐户的所有页面上写入内容。

   ![](assets/social_diagram_fb_external_account.png)

## 创建测试Facebook页面 {#creating-a-test-facebook-page}

我们建议创建用于传送发布校样的专用Facebook页面(有关更多信息，请参阅 [此部分](../../social/using/publishing-on-facebook.md#sending-the-proof).

1. 登录到用于管理页面的Facebook帐户。
1. 创建新的Facebook页面。
1. 单击 **[!UICONTROL Settings]** 按钮。
1. 在 **[!UICONTROL General]** 选项卡，修改页面的可见性参数：检查 **[!UICONTROL Page unpublished]** 框中。
1. 单击 **[!UICONTROL Save Changes]** 按钮。

![](assets/social_facebook_test_page.png)

## 创建 Facebook 应用程序 {#creating-a-facebook-application}

为了让Adobe Campaign能够在页面的壁上发布，您需要创建一个Facebook应用程序。 要执行此操作，请应用以下步骤：

1. 登录到用于管理页面的Facebook帐户。
1. 在浏览器中输入以下地址： [https://developers.facebook.com/apps](https://developers.facebook.com/apps).

   >[!CAUTION]
   >
   >根据您拥有的帐户类型，可能需要一个或多个授权。
   >
   >要创建Facebook应用程序，您需要 **已验证** Facebook帐户。

1. 单击 **[!UICONTROL Add a New App]** 按钮。 输入应用程序名称和联系人电子邮件，然后传递安全检查。

   ![](assets/social_create_facebook_app_002.png)

1. 在 **[!UICONTROL Settings > Basic]**，单击 **[!UICONTROL Add a platform]** ，然后选择 **[!UICONTROL Facebook Web Games]** 类型。

   ![](assets/social_create_facebook_app_003.png)

1. 在 **[!UICONTROL Products]** 部分，检查您是否看到 **[!UICONTROL Facebook Login]** 产品。 如果没有，请添加新产品并选择 **[!UICONTROL Facebook Login]**.

   ![](assets/social_create_facebook_app_003bis.png)

1. 创建应用程序后，选择 **[!UICONTROL App Review]** 选项卡，然后发布应用程序。

   ![](assets/social_create_facebook_app_004.png)

## 委派对Adobe Campaign的写入权限 {#delegating-write-access-to-adobe-campaign}

要委派对Adobe Campaign的写入权限以在页面的涂鸦墙上发布，您需要输入之前创建的Facebook应用程序的参数。

此步骤要求您同时访问Adobe Campaign控制台和登录到用于页面管理的Facebook帐户的Internet浏览器：

>[!CAUTION]
>
>Adobe Campaign运算符必须具有管理权限才能执行此配置。

* **Facebook**:选择之前创建的应用程序( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然后选择 **[!UICONTROL Settings > Basic]** 选项卡。

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Facebook Web Games]** 中，单击 **[!UICONTROL Add Platform]** 按钮，然后选择 **[!UICONTROL Facebook Web Games]**.

* **Adobe Campaign**:转到 **[!UICONTROL Administration > Platform > External Accounts]** 树的节点，选择 **[!UICONTROL Facebook routing]** 外部帐户，然后单击 **[!UICONTROL Connector]** 选项卡。

   ![](assets/social_facebook_external_account_001.png)

1. 在Adobe Campaign控制台中，复制 **[!UICONTROL Secure Canvas URL]** 字段，并将其粘贴到 **[!UICONTROL Secure Web Games URL (https)]** 字段(在 **[!UICONTROL Facebook Web Games]** )。

   ![](assets/social_facebook_external_account_006.png)

   >[!CAUTION]
   >
   >在任何情况下都不得使用不安全的URL。

   复制并粘贴此URL的位置也位于 **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** > **[!UICONTROL Valid OAuth Redirect URIs]**. 要检查URL的有效性，请保存应用程序，并将URL复制并粘贴到 **[!UICONTROL Redirect URI to Check]** 单击 **[!UICONTROL Check URI]**.

   ![](assets/social_facebook_external_account_007bis.png)

1. 在Facebook上，复制 **[!UICONTROL App ID]** 和 **[!UICONTROL App Secret]** 字段，并将其粘贴到控制台的匹配字段中。

   ![](assets/social_facebook_external_account_007.png)

1. 在Facebook上，单击 **[!UICONTROL Save Changes]** 按钮。
1. 转到Adobe Campaign控制台，保存外部帐户。

   >[!NOTE]
   >
   >的 **[!UICONTROL Marketing URL]** 字段，此为可选字段。

1. 在Adobe Campaign控制台中，单击 **[!UICONTROL Request the authorization from the application]** 链接 **[!UICONTROL Connector]** 选项卡。 的 **[!UICONTROL Synchronize Facebook pages]** 工作流会自动触发并收集由管理员管理的所有Facebook页面。 [了解详情](#synchronizing-facebook-pages)。

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >默认情况下，页面会添加到 **[!UICONTROL Facebook]** 服务文件夹，可通过 **[!UICONTROL Profiles and Targets > Services and Subscriptions]** 节点。 的 **[!UICONTROL Folder]** 字段 **[!UICONTROL Connector]** 选项卡，可更改同步后在其中创建Facebook页面的服务文件夹。 您还可以选择要在Adobe Campaign中同步的Facebook页面，这要归功于 **[!UICONTROL Filter]** 字段。 如果将此字段留空，则将同步管理员管理的所有Facebook页面。

1. 将显示一个具有各种Facebook权限设置的对话框。 这些功能可让Adobe Campaign将出版物发送到Facebook帐户页面。

   接受各种权限请求。

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign有权在Facebook帐户页面的涂鸦墙上发布内容。

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>如果Facebook帐户管理多个页面，则只需配置一个外部帐户以在Facebook帐户的任何页面上写入即可。 对于每个新的Facebook帐户，您将需要创建一个 **[!UICONTROL Routing]** 键入外部帐户。

的 **[!UICONTROL Synchronization of Facebook pages]** 工作流可同步由Facebook帐户管理的所有页面，以便您直接通过Adobe Campaign在其涂鸦墙上发布内容。 [了解详情](#synchronizing-facebook-pages)。

## 同步Facebook页面 {#synchronizing-facebook-pages}

的 **[!UICONTROL Synchronization of Facebook pages]** 工作流，通过 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 节点，用于同步(在Adobe Campaign中)先前配置的Facebook帐户页面。 默认情况下，此工作流配置为每天或每当管理员单击 **[!UICONTROL Request an authorization from the application]** 链接。 [了解详情](#delegating-write-access-to-adobe-campaign)。

同步完成后，收集的页面将显示在外部帐户中输入的服务文件夹中。 [了解详情](#delegating-write-access-to-adobe-campaign)).

默认情况下，页面会添加到的根 **[!UICONTROL Facebook]** 服务文件夹，可通过 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 菜单。

![](assets/social_facebook_service_002.png)

现在，您可以直接通过Adobe Campaign在Facebook页面的墙上发布内容。 [了解详情](#publishing-on-facebook-walls)。
