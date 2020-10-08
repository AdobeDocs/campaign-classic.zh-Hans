---
title: 在 Facebook 好友墙上发布
seo-title: 在 Facebook 好友墙上发布
description: 在 Facebook 好友墙上发布
seo-description: null
page-status-flag: never-activated
uuid: 02288473-a0d7-42b5-9f86-3c96550ab1a8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 8577db0b-f1fc-41af-aa0f-ec4d02dac376
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 2%

---


# 在 Facebook 好友墙上发布{#publishing-on-facebook-walls}

为了Adobe Campaign能够将出版物发送到Facebook墙，您需要将这些页面的写入权限委托给Adobe Campaign。 这涉及以下配置步骤：

1. 使用一个或多个页面创建Facebook帐户。
1. 创建用于发送验证的测试Facebook页面。
1. 创建Facebook应用程序。
1. 在Adobe Campaign中，将Facebook应用程序设置输入 **[!UICONTROL Facebook routing]** 外部帐户。

## 先决条件{#prerequisites}

开始方式：创建Facebook帐户和多个页面：这些将用于发送发布。

* 要创建Facebook帐户，请使用https://www.facebook.com [链接](https://www.facebook.com) 。
* 要创建Facebook页面，请使用https://www.facebook.com/pages/create [链接](https://www.facebook.com/pages/create) 。

   我们建议使用相同的Facebook帐户管理您的所有页面。 这样，您只需要一个Facebook应用程序和一个外部帐户即可在帐户的所有页面上写入内容。

   ![](assets/social_diagram_fb_external_account.png)

## 创建测试Facebook页面 {#creating-a-test-facebook-page}

我们建议创建专用Facebook页面以传送发布验证(有关详细信息，请参 [阅发送验证](../../social/using/publishing-on-facebook.md#sending-the-proof)。

1. 登录到用于管理页面的Facebook帐户。
1. 创建新Facebook页面。
1. 单击 **[!UICONTROL Settings]** 右上角的按钮。
1. 在选项卡 **[!UICONTROL General]** 中，修改页面的可见性参数：复选 **[!UICONTROL Page unpublished]** 框。
1. 单击 **[!UICONTROL Save Changes]** 按钮。

![](assets/social_facebook_test_page.png)

## 创建 Facebook 应用程序 {#creating-a-facebook-application}

为了让Adobe Campaign能够在页面的墙上发布，您需要创建一个Facebook应用程序。 为此，请应用以下步骤：

1. 登录到用于管理页面的Facebook帐户。
1. 在浏览器中输入以下地址： [https://developers.facebook.com/apps](https://developers.facebook.com/apps)。

   >[!IMPORTANT]
   >
   >根据您拥有的帐户类型，可能需要一个或多个授权。
   >
   >要创建Facebook应用程序，您需要一个经过验 **证的** Facebook帐户。

1. 单击 **[!UICONTROL Add a New App]** 页面右上角的按钮。 输入应用程序名称和联系人电子邮件，然后通过安全检查。

   ![](assets/social_create_facebook_app_002.png)

1. 在下 **[!UICONTROL Settings > Basic]**&#x200B;面，单 **[!UICONTROL Add a platform]** 击并选择 **[!UICONTROL Facebook Web Games]** 类型。

   ![](assets/social_create_facebook_app_003.png)

1. 在左 **[!UICONTROL Products]** 侧菜单中，检查您是否看到该产 **[!UICONTROL Facebook Login]** 品。 否则，添加新产品并选择 **[!UICONTROL Facebook Login]**。

   ![](assets/social_create_facebook_app_003bis.png)

1. 创建应用程序后，选择选项卡 **[!UICONTROL App Review]** 并发布该应用程序。

   ![](assets/social_create_facebook_app_004.png)

## 将写权限委派给Adobe Campaign {#delegating-write-access-to-adobe-campaign}

要授予Adobe Campaign在页面壁上发布的写入权限，您需要输入之前创建的Facebook应用程序的参数。

此步骤要求访问您的Adobe Campaign控制台和登录到用于页面管理的Facebook帐户的Internet浏览器：

>[!IMPORTANT]
>
>Adobe Campaign操作员必须具有管理权限才能执行此配置。

* **Facebook**:选择之前创建的应用程序( [https://developers.facebook.com/apps](https://developers.facebook.com/apps))，然后选择选 **[!UICONTROL Settings > Basic]** 项卡。

   ![](assets/social_facebook_external_account_002.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Facebook Web Games]** 未显示章节，请单 **[!UICONTROL Add Platform]** 击页面底部的按钮，然后选择 **[!UICONTROL Facebook Web Games]**。

* **Adobe Campaign**:转到树 **[!UICONTROL Administration > Platform > External Accounts]** 的节点，选择外部帐户 **[!UICONTROL Facebook routing]** 并单击选 **[!UICONTROL Connector]** 项卡。

   ![](assets/social_facebook_external_account_001.png)

1. 在Adobe Campaign控制台中，复制字段中包含的地 **[!UICONTROL Secure Canvas URL]** 址，并将其粘贴 **[!UICONTROL Secure Web Games URL (https)]** 到Facebook上的字段(在 **[!UICONTROL Facebook Web Games]** 部分)。

   ![](assets/social_facebook_external_account_006.png)

   >[!IMPORTANT]
   >
   >在任何情况下均不得使用不安全的URL。

   复制并粘贴此URL也位于 **[!UICONTROL Products]** > **[!UICONTROL Facebook Login]** > **[!UICONTROL Settings]** >下 **[!UICONTROL Valid OAuth Redirect URIs]**。 要检查URL的有效性，请保存应用程序，在字段中复制并粘 **[!UICONTROL Redirect URI to Check]** 贴URL并单击 **[!UICONTROL Check URI]**。

   ![](assets/social_facebook_external_account_007bis.png)

1. 在Facebook上，复制和字段的 **[!UICONTROL App ID]** 内 **[!UICONTROL App Secret]** 容，并将其粘贴到控制台的匹配字段中。

   ![](assets/social_facebook_external_account_007.png)

1. 在Facebook上，单 **[!UICONTROL Save Changes]** 击页面底部的按钮。
1. 转到Adobe Campaign控制台，保存外部帐户。

   >[!NOTE]
   >
   >The **[!UICONTROL Marketing URL]** field is optional.

1. 在Adobe Campaign控制台中，单 **[!UICONTROL Request the authorization from the application]** 击选项卡底部的链 **[!UICONTROL Connector]** 接。 该工 **[!UICONTROL Synchronize Facebook pages]** 作流会自动触发并收集管理员管理的所有Facebook页面。 有关此方面的详细信息，请参 [阅同步Facebook页面](#synchronizing-facebook-pages)。

   ![](assets/social_facebook_external_account_004.png)

   >[!NOTE]
   >
   >默认情况下，页面会添加到服 **[!UICONTROL Facebook]** 务文件夹，可通过节点 **[!UICONTROL Profiles and Targets > Services and Subscriptions]** 访问。 通过 **[!UICONTROL Folder]** 选项卡的字 **[!UICONTROL Connector]** 段，可以更改同步后创建Facebook页面的服务文件夹。 您还可以选择要以Adobe Campaign同步的Facebook页面，这要归功于该 **[!UICONTROL Filter]** 字段。 如果将此字段留空，将同步管理员管理的所有Facebook页面。

1. 将显示一个包含各种Facebook权限设置的对话框。 这些选项使Adobe Campaign能够将出版物发送到Facebook帐户页面。

   接受各种权限请求。

   ![](assets/social_facebook_external_account_003.png)

1. Adobe Campaign被授予在Facebook帐户页面的墙上发布的权利。

   ![](assets/social_facebook_external_account_011.png)

>[!NOTE]
>
>如果Facebook帐户管理多个页面，只需配置一个外部帐户以在Facebook帐户的任何页面上写入。 对于每个新的Facebook帐户，您需要创建新的类型 **[!UICONTROL Routing]** 外部帐户。

该工 **[!UICONTROL Synchronization of Facebook pages]** 作流将同步Facebook帐户管理的所有页面，以便您通过Adobe Campaign直接在其墙上发布内容。 有关此方面的详细信息，请参 [阅同步Facebook页面](#synchronizing-facebook-pages)。

## 同步Facebook页面 {#synchronizing-facebook-pages}

通 **[!UICONTROL Synchronization of Facebook pages]** 过节点访问的工作流 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 允许您以Adobe Campaign同步之前配置的Facebook帐户的页面。 默认情况下，此工作流配置为每天或每当管理员单击服务配置屏幕中的链 **[!UICONTROL Request an authorization from the application]** 接时运行一次(请参阅将写 [权限委派给Adobe Campaign](#delegating-write-access-to-adobe-campaign))。

同步完成后，收集的页面会显示在外部帐户中输入的服务文件夹中(请参 [阅将写权限委派给Adobe Campaign](#delegating-write-access-to-adobe-campaign))。 默认情况下，页面会添加到服务文件 **[!UICONTROL Facebook]** 夹的根目录中，该根目录可通过菜 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 单访问。

![](assets/social_facebook_service_002.png)

您现在可以直接通过Adobe Campaign在Facebook页面的墙上发布。 有关此内容的详细信息，请参 [阅Facebook上发布](#publishing-on-facebook-walls)。
