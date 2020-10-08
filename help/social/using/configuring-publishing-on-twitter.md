---
title: 在 Twitter 上配置发布
seo-title: 在 Twitter 上配置发布
description: 在 Twitter 上配置发布
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 3%

---


# 在 Twitter 上配置发布{#configuring-publishing-on-twitter}

为了Adobe Campaign能够将帖子发送到您的Twitter帐户，您需要为这些帐户委派写权限以访问Adobe Campaign。 为此，请应用以下配置步骤：

* 创建Twitter帐户。
* 创建用于发送验证的测试Twitter帐户。
* 为每个Twitter帐户创建一个Twitter应用程序。
* 对于每个Twitter应用程序，创建新的 **[!UICONTROL Twitter]** 类型服务。

![](assets/social_diagram_twitter_service.png)

## 先决条件{#prerequisites}

开始，方法是创建一个或多个Twitter帐户，将您的帖子发送到。

要创建Twitter帐户，请转 [到https://twitter.com](https://twitter.com)。

## 在Twitter上创建测试帐户 {#creating-a-test-account-on-twitter}

我们还建议创建可用于发送推文验证的专用Twitter帐户(有关详细信息，请参阅 [发送验证](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* 创建新的Twitter帐户。
* 单击右上角的菜单，然后选择 **[!UICONTROL Settings]**。
* 选择选 **[!UICONTROL Security and privacy]** 项卡，然后选中 **[!UICONTROL Protect my Tweets]** 该框。
* 单击页 **[!UICONTROL Save Changes]** 面底部的按钮。

![](assets/social_twitter_test_page.png)

## 在Twitter上创建应用程序 {#creating-an-application-on-twitter}

为了Adobe Campaign能够向您的Twitter帐户发送帖子，您需要为每个Twitter帐户创建一个Twitter应用程序。 为此，请应用以下步骤：

1. 登录您的Twitter帐户。
1. 在Internet浏览器中输入以下地址： [https://apps.twitter.com/](https://apps.twitter.com/)。
1. 然后单击 **[!UICONTROL Create New App]** 右侧的按钮。

   ![](assets/social_create_twitter_app_001.png)

1. 让向导指导您完成整个过程。

   为了使此应用程序允许Adobe Campaign向您的帐户发送帖子，请转 **[!UICONTROL Permissions]** 到该应用程序的选项卡并选 **[!UICONTROL Read and Write]** 择相应 **[!UICONTROL Access]** 部分。 在选 **[!UICONTROL Settings]** 项卡中，您还需要将字段留 **[!UICONTROL Callback URL]** 空。

   ![](assets/social_create_twitter_app_002.png)

## 将写权限委派给Adobe Campaign {#delegating-write-access-to-adobe-campaign}

对于每个Twitter应用程序，您需要创建一个不同 **[!UICONTROL Twitter]** 的类型服务，其中将包括应用程序设置。

此步骤要求同时访问您的Adobe Campaign控制台和登录到您的Twitter帐户的Internet浏览器：

* **Twitter**:选择之前创建的应用程[序(](https://dev.twitter.com/apps)https://dev.twitter.com/apps)，然后单击选 **[!UICONTROL Keys and Access Tokens]** 项卡。

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**:转到“ **[!UICONTROL Profiles and targets]** universe”，单击 **[!UICONTROL Services and Subscriptions]** 链接并单击按 **[!UICONTROL Create]** 钮。

   ![](assets/social_twitter_service_007.png)

1. Select the **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >The **[!UICONTROL Synchronize subscriptions]** option is enabled by default. 选中该框后，Twitter帐户同步工作流(请参 [阅同步Twitter帐户](#synchronizing-twitter-accounts))会恢复Twitter关注者的列表，以便您可以向他们发送直接消息(请参 [阅向订阅者发送直接消息](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers))。 如果您不想恢复关注者的列表，请取消选中此框。

1. 输入服务的标签和内部名称。

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >服 **[!UICONTROL Internal name]** 务的名称必须与Twitter帐户的名称相同。 要确保没有输入错误，请应用以下步骤。

   * 单击 **[!UICONTROL Save]** 按钮。
   * 在服务概述中，单击您刚刚创建的Twitter类型服务。
   * 选择 **[!UICONTROL Twitter page]** 选项卡。应显示Twitter帐户。

      ![](assets/social_twitter_service_010.png)

1. 在字 **[!UICONTROL Visitor folder]** 段中，选择将在其中创建关注者的访客文件夹。 For more on this, refer to [Operating principle](../../social/using/publishing-on-twitter.md#operating-principle). 默认情况下，将在文件夹的根中创建关 **[!UICONTROL Visitors]** 注者。

   ![](assets/social_twitter_service_010_b.png)

1. 在Twitter上，复制和字段 **[!UICONTROL Consumer Key (API Key)]** 的内 **[!UICONTROL Consumer Secret (API Secret)]** 容并将其粘贴 **[!UICONTROL Consumer key]** 到控制台 **[!UICONTROL Consumer secret]** 的和字段中。

   ![](assets/social_twitter_service_012.png)

1. 在Twitter上，复制和字段 **[!UICONTROL Access Token]** 的内 **[!UICONTROL Access Token Secret]** 容并将其粘贴 **[!UICONTROL Access token]** 到控制台 **[!UICONTROL Access token secret]** 的和字段中。

   ![](assets/social_twitter_service_013.png)

1. 在Adobe Campaign控制台中，单击 **[!UICONTROL Save]**。 现已完成对Adobe Campaign的写权限委派。

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>必须为每个Twitter应 **[!UICONTROL Twitter]** 用程序创建一个类型服务。

该工 **[!UICONTROL Twitter account Synchronization]** 作流以Adobe Campaign同步Twitter帐户。 有关此方面的详细信息，请参 [阅同步Facebook页面](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)。

## 同步Twitter帐户 {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>要使工作流恢复Twitter订阅者的列表，必 **[!UICONTROL Twitter account synchronization]** 须在链接到帐户的服务的编辑部分选中该框。 有关详细信息，请参 [阅委派写入权限Adobe Campaign](#delegating-write-access-to-adobe-campaign)。

通过 **[!UICONTROL Twitter account synchronization]** 该节点访问的工作流 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 允许您同步以前配置的Twitter帐户和Adobe Campaign。 默认情况下，此工作流每周四早7点30分触发。

>[!NOTE]
>
>可以通过运行预期的开始处理随时任务工作流。 您还可以编辑调度程序以更改工作流触发频率。 For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

您现在可以将帖子发送到您的Twitter帐户，并将消息直接发送给您的关注者。 有关此内容的详细信息，请参阅： [在Twitter上发布](../../social/using/publishing-on-twitter.md)。
