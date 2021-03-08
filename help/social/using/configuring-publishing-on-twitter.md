---
solution: Campaign Classic
product: campaign
title: 在 Twitter 上配置发布
description: 在 Twitter 上配置发布
audience: social
content-type: reference
topic-tags: configuration
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 2%

---


# 在 Twitter 上配置发布{#configuring-publishing-on-twitter}

为了让Adobe Campaign能够向您的Twitter帐户发送帖子，您需要将这些帐户的写权限委托给Adobe Campaign。 为此，请应用以下配置步骤：

* 创建Twitter帐户。
* 创建用于发送验证的测试Twitter帐户。
* 每个Twitter帐户创建一个Twitter应用程序。
* 对于每个Twitter应用程序，创建新的&#x200B;**[!UICONTROL Twitter]**&#x200B;类型服务。

![](assets/social_diagram_twitter_service.png)

## 先决条件{#prerequisites}

开始，方法是创建一个或多个Twitter帐户，以将您的推文发送到。

要创建Twitter帐户，请转至[https://twitter.com](https://twitter.com)。

## 在Twitter上创建测试帐户{#creating-a-test-account-on-twitter}

我们还建议创建可用于发送推文验证的专用Twitter帐户(有关详细信息，请参阅[发送验证](../../social/using/publishing-on-twitter.md#sending-the-proof)):

* 创建新Twitter帐户。
* 单击右上角的菜单，然后选择&#x200B;**[!UICONTROL Settings]**。
* 选择&#x200B;**[!UICONTROL Security and privacy]**&#x200B;选项卡，然后选中&#x200B;**[!UICONTROL Protect my Tweets]**&#x200B;框。
* 单击页面底部的&#x200B;**[!UICONTROL Save Changes]**&#x200B;按钮。

![](assets/social_twitter_test_page.png)

## 在Twitter上创建应用程序{#creating-an-application-on-twitter}

为了让Adobe Campaign能够向您的Twitter帐户发送推文，您需要为每个Twitter帐户创建一个Twitter应用程序。 为此，请应用以下步骤：

1. 登录您的Twitter帐户。
1. 在Internet浏览器中输入以下地址：[https://apps.twitter.com/](https://apps.twitter.com/)。
1. 然后单击右侧的&#x200B;**[!UICONTROL Create New App]**&#x200B;按钮。

   ![](assets/social_create_twitter_app_001.png)

1. 让向导指导您完成整个过程。

   为了使此应用程序允许Adobe Campaign向您的帐户发送推文，请转至应用程序的&#x200B;**[!UICONTROL Permissions]**&#x200B;选项卡，然后为&#x200B;**[!UICONTROL Access]**&#x200B;部分选择&#x200B;**[!UICONTROL Read and Write]**。 在&#x200B;**[!UICONTROL Settings]**&#x200B;选项卡中，您还需要将&#x200B;**[!UICONTROL Callback URL]**&#x200B;字段留空。

   ![](assets/social_create_twitter_app_002.png)

## 委派对Adobe Campaign{#delegating-write-access-to-adobe-campaign}的写访问

对于每个Twitter应用程序，您需要创建一个不同的&#x200B;**[!UICONTROL Twitter]**&#x200B;类型服务，其中将包括应用程序设置。

此步骤要求同时访问您的Adobe Campaign控制台和登录到Twitter帐户的Internet浏览器：

* **Twitter**:选择之前创建的应用程序([https://dev.twitter.com/apps](https://dev.twitter.com/apps))，然后单击选 **[!UICONTROL Keys and Access Tokens]** 项卡。

   ![](assets/social_twitter_service_002.png)

* **Adobe Campaign**:转到选 **[!UICONTROL Profiles and targets]** 项卡，单击 **[!UICONTROL Services and Subscriptions]** 链接并单击按 **[!UICONTROL Create]** 钮。

   ![](assets/social_twitter_service_007.png)

1. 选择&#x200B;**[!UICONTROL Twitter]**&#x200B;类型。

   ![](assets/social_twitter_service_008.png)

   >[!NOTE]
   >
   >默认情况下，**[!UICONTROL Synchronize subscriptions]**&#x200B;选项处于启用状态。 选中该框后，Twitter帐户同步工作流（请参阅[同步Twitter帐户](#synchronizing-twitter-accounts)）会恢复Twitter关注者的列表，以便您可以向他们发送直接消息（请参阅[向订阅者](../../social/using/publishing-on-twitter.md#sending-direct-messages-to-subscribers)发送直接消息）。 如果您不想恢复关注者的列表，请取消选中此框。

1. 输入服务的标签和内部名称。

   ![](assets/social_twitter_service_009.png)

   >[!IMPORTANT]
   >
   >服务的&#x200B;**[!UICONTROL Internal name]**&#x200B;必须与Twitter帐户的名称相同。 要确保没有输入错误，请应用以下步骤。

   * 单击 **[!UICONTROL Save]** 按钮。
   * 在服务概述中，单击您刚刚创建的Twitter类型服务。
   * 选择 **[!UICONTROL Twitter page]** 选项卡。应显示Twitter帐户。

      ![](assets/social_twitter_service_010.png)

1. 在&#x200B;**[!UICONTROL Visitor folder]**&#x200B;字段中，选择将在其中创建关注者的访客文件夹。 有关详细信息，请参阅[操作原则](../../social/using/publishing-on-twitter.md#operating-principle)。 默认情况下，将在&#x200B;**[!UICONTROL Visitors]**&#x200B;文件夹的根位置创建关注者。

   ![](assets/social_twitter_service_010_b.png)

1. 在Twitter上，复制&#x200B;**[!UICONTROL Consumer Key (API Key)]**&#x200B;和&#x200B;**[!UICONTROL Consumer Secret (API Secret)]**&#x200B;字段的内容，并将其粘贴到控制台的&#x200B;**[!UICONTROL Consumer key]**&#x200B;和&#x200B;**[!UICONTROL Consumer secret]**&#x200B;字段中。

   ![](assets/social_twitter_service_012.png)

1. 在Twitter上，复制&#x200B;**[!UICONTROL Access Token]**&#x200B;和&#x200B;**[!UICONTROL Access Token Secret]**&#x200B;字段的内容，并将其粘贴到控制台的&#x200B;**[!UICONTROL Access token]**&#x200B;和&#x200B;**[!UICONTROL Access token secret]**&#x200B;字段中。

   ![](assets/social_twitter_service_013.png)

1. 在Adobe Campaign控制台中，单击&#x200B;**[!UICONTROL Save]**。 现在已完成对Adobe Campaign的写权限委派。

   ![](assets/social_twitter_service_014.png)

>[!NOTE]
>
>必须为每个Twitter应用程序创建一个&#x200B;**[!UICONTROL Twitter]**&#x200B;类型服务。

**[!UICONTROL Twitter account Synchronization]**&#x200B;工作流将Twitter帐户同步到Adobe Campaign。 有关详细信息，请参阅[同步Facebook页面](../../social/using/publishing-on-facebook-walls.md#synchronizing-facebook-pages)。

## 正在同步Twitter帐户{#synchronizing-twitter-accounts}

>[!IMPORTANT]
>
>要恢复Twitter订阅者的列表，必须在链接到帐户的服务的编辑部分选中&#x200B;**[!UICONTROL Twitter account synchronization]**&#x200B;框。 有关详细信息，请参阅[将写访问权限委派给Adobe Campaign](#delegating-write-access-to-adobe-campaign)。

通过&#x200B;**[!UICONTROL Administration > Production > Technical workflows > Managing social networks]**&#x200B;节点访问的&#x200B;**[!UICONTROL Twitter account synchronization]**&#x200B;工作流允许您同步之前配置的Twitter帐户和Adobe Campaign。 默认情况下，此工作流会在每星期四的早7:30触发。

>[!NOTE]
>
>可以通过运行预期的开始处理随时任务工作流。 您还可以编辑调度程序以更改工作流触发频率。 有关调度程序的详细信息，请参阅[此部分](../../workflow/using/scheduler.md)。

您现在可以将推文发送到您的Twitter帐户，并将消息直接发送给您的关注者。 有关详细信息，请参阅：[在Twitter上发布。](../../social/using/publishing-on-twitter.md)
