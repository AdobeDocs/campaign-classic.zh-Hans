---
title: 配置在Twitter上发布
seo-title: 配置在Twitter上发布
description: 配置在Twitter上发布
seo-description: null
page-status-flag: never-activated
uuid: 88867881-fb59-4f0d-862e-537d498e9aef
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: configuration
discoiquuid: 9d74ed9c-0055-4556-a205-6e5fea11816b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# 配置在Twitter上发布{#configuring-publishing-on-twitter}

为了使Adobe Campaign能够将帖子发送到您的Twitter帐户，您需要为这些帐户授予对Adobe Campaign的写权限。 为此，请应用以下配置步骤：

* 创建Twitter帐户。
* 创建用于发送校样的测试Twitter帐户。
* 每个Twitter帐户创建一个Twitter应用程序。
* 对于每个Twitter应用程序，创建新的类 **[!UICONTROL Twitter]** 型服务。

![](assets/social_diagram_twitter_service.png)

## 先决条件 {#prerequisites}

首先，创建一个或多个Twitter帐户，将您的帖子发送到。

要创建Twitter帐户，请转到 [https://twitter.com](https://twitter.com)。

## 在Twitter上创建测试帐户 {#creating-a-test-account-on-twitter}

我们还建议创建可用于发送推文证明的专用Twitter帐户(有关详细信息，请参阅 [发送证明](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* 创建新的Twitter帐户。
* 单击右上角的菜单，然后选择 **[!UICONTROL Settings]**。
* 选择选 **[!UICONTROL Security and privacy]** 项卡，然后选中该 **[!UICONTROL Protect my Tweets]** 框。
* 单击 **[!UICONTROL Save Changes]** 页面底部的按钮。

![](assets/social_twitter_test_page.png)

## 在Twitter上创建应用程序 {#creating-an-application-on-twitter}

为了使Adobe Campaign能够向您的Twitter帐户发送帖子，您需要为每个Twitter帐户创建一个Twitter应用程序。 为此，请应用以下步骤：

1. 登录您的Twitter帐户。
1. 在Internet浏览器中输入以下地址： [https://apps.twitter.com/](https://apps.twitter.com/)。
1. 然后单击 **[!UICONTROL Create New App]** 右侧的按钮。

   ![](assets/social_create_twitter_app_001.png)

1. 让向导指导您完成整个过程。

   为了使此应用程序允许Adobe Campaign将帖子发送到您的帐户，请转到该应用程序的选 **[!UICONTROL Permissions]** 项卡，然后选择 **[!UICONTROL Read and Write]** 相应的 **[!UICONTROL Access]** 部分。 在选 **[!UICONTROL Settings]** 项卡中，您还需要将字段留空 **[!UICONTROL Callback URL]** 。

   ![](assets/social_create_twitter_app_002.png)

## 委派对Adobe Campaign的写权限 {#delegating-write-access-to-adobe-campaign}

对于每个Twitter应用程序，您需要创建一个不同的类 **[!UICONTROL Twitter]** 型服务，其中将包括应用程序设置。

此步骤需要同时访问您的Adobe Campaign控制台和登录到您的Twitter帐户的Internet浏览器：

* **Twitter**:选择之前创建的应用程序([https://dev.twitter.com/apps](https://dev.twitter.com/apps))，然后单击选 **[!UICONTROL Keys and Access Tokens]** 项卡。

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**:转到“ **[!UICONTROL Profiles and targets]** universe”（宇宙），单击 **[!UICONTROL Services and Subscriptions]** 链接并单击 **[!UICONTROL Create]** 按钮。

   ![](assets/social_twitter_service_007.png)

1. Select the **[!UICONTROL Twitter]** type.

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >默 **[!UICONTROL Synchronize subscriptions]** 认情况下会启用此选项。 选中该框后，Twitter帐户同步工作流(请参阅同步 [Twitter帐户](#synchronizing-twitter-accounts))将恢复Twitter关注者列表，以便您可以向他们发送直接消息(请参阅向订阅者 [发送直接消息](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers))。 如果不想恢复关注者列表，请取消选中此框。

1. 输入服务的标签和内部名称。

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >服 **[!UICONTROL Internal name]** 务的名称必须与Twitter帐户的名称相同。 要确保没有输入错误，请应用以下步骤。

   * Click the **[!UICONTROL Save]** button.
   * 在服务概述中，单击您刚刚创建的Twitter类型服务。
   * 选择选 **[!UICONTROL Twitter page]** 项卡。 应显示Twitter帐户。

      ![](assets/social_twitter_service_010.png)

1. 在字段 **[!UICONTROL Visitor folder]** 中，选择将在其中创建关注者的访客文件夹。 For more on this, refer to [Operating principle](../../social/using/publishing-on-twitter.md#operating-principle). 默认情况下，关注者将创建在文件夹的根 **[!UICONTROL Visitors]** 位置。

   ![](assets/social_twitter_service_010_b.png)

1. 在Twitter上，复制和字段的 **[!UICONTROL Consumer Key (API Key)]** 内容 **[!UICONTROL Consumer Secret (API Secret)]** 并将其粘贴到控制台 **[!UICONTROL Consumer key]** 的和 **[!UICONTROL Consumer secret]** 字段中。

   ![](assets/social_twitter_service_012.png)

1. 在Twitter上，复制和字段的 **[!UICONTROL Access Token]** 内容 **[!UICONTROL Access Token Secret]** 并将其粘贴到控制台 **[!UICONTROL Access token]** 的和 **[!UICONTROL Access token secret]** 字段中。

   ![](assets/social_twitter_service_013.png)

1. 在Adobe Campaign控制台中，单击 **[!UICONTROL Save]**。 现在，对Adobe Campaign的写权限委托已完成。

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>必须为每个Twitter应用 **[!UICONTROL Twitter]** 程序创建一个类型服务。

该工 **[!UICONTROL Twitter account Synchronization]** 作流将同步Adobe Campaign中的Twitter帐户。 有关详细信息，请参阅同 [步Facebook页面](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)。

## 同步Twitter帐户 {#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>要使工作流恢复Twitter订阅者列表，必须在链 **[!UICONTROL Twitter account synchronization]** 接到帐户的服务的编辑部分选中该框。 有关详细信息，请参 [阅委派对Adobe Campaign的写权限](#delegating-write-access-to-adobe-campaign)。

通过 **[!UICONTROL Twitter account synchronization]** 通过节点访问的工作 **[!UICONTROL Administration > Production > Technical workflows > Managing social networks]** 流，您可以同步之前与Adobe Campaign配置的Twitter帐户。 默认情况下，此工作流每周四上午7:30触发。

>[!NOTE]
>
>可以通过运行预期的任务处理随时启动工作流。 您还可以编辑调度程序以更改工作流触发频率。 For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

您现在可以将帖子发送到您的Twitter帐户，并将消息定向到您的关注者。 有关详细信息，请参阅：在 [Twitter上发布](../../social/using/publishing-on-twitter.md)。
