---
title: 在 Twitter 上发布
seo-title: 在 Twitter 上发布
description: 在 Twitter 上发布
seo-description: null
page-status-flag: never-activated
uuid: 405bce50-a63c-4bd3-8f03-c71809bb1cfd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 2dc278ce-477c-493d-8abb-8bbdf2e988a5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 5%

---


# 在 Twitter 上发布{#publishing-on-twitter}

## 在您的Twitter帐户上发布 {#publishing-on-your-twitter-accounts}

配置完成后，Social Marketing允许您将帖子发送到Twitter帐户。

### 限制{#limitations}

以下限制是Twitter固有的限制。

* 邮件长度不得超过140个字符。
* 不支持HTML格式。

### 创建投放 {#creating-the-delivery}

根据投放创建新投放模板。 **[!UICONTROL Tweet (twitter)]**

![](assets/social_twitter_delivery_001.png)

### Selecting the main target {#selecting-the-main-target}

选择要将帖子发送到的帐户。

1. 单击链 **[!UICONTROL To]** 接。

   ![](assets/social_twitter_delivery_002.png)

1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/social_twitter_delivery_006.png)

1. 选择 **[!UICONTROL A Twitter account]**。

   ![](assets/social_twitter_delivery_007.png)

1. 在字段 **[!UICONTROL Folder]** 中，选择包含Twitter帐户的服务文件夹。 然后，选择要将您的推文发送到的Twitter帐户。

   ![](assets/social_twitter_delivery_011.png)

### 选择目标 {#selecting-the-target-of-the-proof}

通过 **[!UICONTROL Target of the proofs]** 该选项卡，您可以定义要在最终投放之前用于测试投放的Twitter帐户。 因此，我们建议您创建专用于发送验证的Twitter帐户。 有关如何创建私人Twitter帐户的详细信息，请参 [阅在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。 选择验证目标的步骤与选择主目标的步骤相同。 请参阅 [在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>如果对所有投放使用相同的Twitter测试帐户，则可以在通过节点访问的投放模板中 **[!UICONTROL Tweet]** 保存验证 **[!UICONTROL Resources > Templates > Delivery templates]** 目标。 然后，默认情况下将为每个新验证输入目标。

### 定义消息内容 {#defining-the-message-content}

在选项卡中键入您的帖子 **[!UICONTROL Content]** 内容。

![](assets/social_twitter_delivery_005.png)

### 查看预览 {#viewing-the-preview}

通 **[!UICONTROL Preview]** 过选项卡可视图帖子的呈现。

1. 单击选 **[!UICONTROL Preview]** 项卡。
1. 单击下 **[!UICONTROL Test personalization]** 拉菜单并选择 **[!UICONTROL Service]**。
1. 在字段 **[!UICONTROL Folder]** 中，选择包含您的Twitter帐户的服务文件夹。
1. 选择要测试预览的Twitter帐户。

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>预览可能与最终的推文略有不同。 我们强烈建议在最终验证之前发送投放，以视图帖子的确切呈现。 请参阅 [发送验证](#sending-the-proof)。

### 配置跟踪 {#configuring-tracking}

跟踪可在投放报告以及投放和服 **[!UICONTROL Edit > Tracking]** 务的选项卡中查看。

跟踪配置与电子邮件投放相同。 如需详细信息，请参阅[此部分](../../delivery/using/monitoring-a-delivery.md)。

>[!NOTE]
>
>在投放模板 **[!UICONTROL Tweet]** 中，默认情况下启用跟踪。

>[!IMPORTANT]
>
>我们无法分辨分析帖子的机器人和实际点击的用户之间的区别。

### 发送验证 {#sending-the-proof}

我们强烈建议在最终验证之前发送出版物的投放，以在专用Twitter测试页上获得出版物的精确呈现。 有关创建私人Twitter帐户的详细信息，请参 [阅在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。 选择验证目标的步骤详 [细介绍在选择验证](#selecting-the-target-of-the-proof)。

验证投放与电子邮件投放相同。 请参阅[此章节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) 。

### 发送消息 {#sending-the-message}

1. 批准内容后，单击按 **[!UICONTROL Send]** 钮。
1. 选 **[!UICONTROL Deliver as soon as possible]** 择并单击 **[!UICONTROL Analyze]** 按钮。

   >[!NOTE]
   >
   >通过 **[!UICONTROL Postpone the delivery]** 此选项，您可以延后投放到以后的日期。

   ![](assets/social_twitter_delivery_012.png)

1. 完成分析后，检查结果。
1. 单 **[!UICONTROL Confirm delivery]**&#x200B;击，然后单击 **[!UICONTROL Yes]**。

![](assets/social_facebook_delivery_016.png)

## 向订阅者发送直接消息 {#sending-direct-messages-to-subscribers}

### 工作原理 {#operating-principle}

该工 **[!UICONTROL Synchronize Twitter accounts]** 作流(请参 [阅同步Twitter帐户](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts))会恢复Twitter订阅者的列表，以便您能够向他们发送直接消息。 恢复的关注者存储在特定表中：访客表。 要显示Twitter关注者的列表，请转到该 **[!UICONTROL Profiles and Targets > Visitors]** 节点。

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>要使工作流恢复Twitter关注者的列表, **[!UICONTROL Synchronize Twitter accounts]** 必须在链接到帐户的服务的“编辑”屏幕中选中该框。 有关此内容的详细信息，请参阅： [将写权限委派给Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign)。

对于每位关注者，Adobe Campaign会恢复以下信息：

* **[!UICONTROL Origin]**:社交网络的名称(**本例中** 为Twitter)
* **[!UICONTROL External ID]**:用户标识符
* **[!UICONTROL User name]**:用户的帐户名
* **[!UICONTROL Full name]**:用户名
* **[!UICONTROL Language]**:用户语言
* **[!UICONTROL Number of friends]**:关注者数量
* **[!UICONTROL Time zone]**:用户时区
* **[!UICONTROL Verified]**:此字段指示用户是否具有经过验证的Twitter帐户

### 限制{#limitations-1}

以下限制是Twitter固有的限制。

* 邮件长度不得超过140个字符。
* 不支持HTML。
* 每天不能发送超过250条直接邮件。 要避免超出此阈值，您可以在多个批次中交付。 批次中的投放配置为与电子邮件投放类似。 如需详细信息，请参阅[此部分](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

### 创建投放 {#creating-the-delivery-}

根据投放创建新投放模板。 **[!UICONTROL Tweet (Direct Message)]**

![](assets/social_twitter_delivery_010.png)

### Selecting the main target {#selecting-the-main-target-1}

选择要将直接消息发送给的关注者。

1. 单击链 **[!UICONTROL To]** 接。

   ![](assets/social_twitter_delivery_016.png)

1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/social_twitter_delivery_006.png)

1. 选择定位类型。

   ![](assets/social_twitter_delivery_017.png)

   * 选择 **[!UICONTROL Twitter subscribers]** 以向所有帐户关注者发送直接消息。

      >[!IMPORTANT]
      >
      >每天不能发送250条以上的邮件。 如果您的Twitter帐户拥有超过250个关注者，我们强烈建议提供批次。 这涉及与电子邮件投放相同的流程。 请参阅[此章节](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) 。

   * 选 **[!UICONTROL Filter conditions]** 择以定义查询并视图其结果。 此选项与电子邮件投放相同。 Refer to [this section](../../platform/using/defining-filter-conditions.md) for more information.

      ![](assets/social_twitter_delivery_018.png)

### 选择目标 {#selecting-the-target-of-the-proof-1}

在选 **[!UICONTROL Target of the proofs]** 项卡中，您可以选择将接收您的直接消息验证的关注者。 选择过程与主目标相同。 请参阅 [选择主目标](#selecting-the-main-target)。

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>如果要将所有直接消息验证发送给同一Twitter关注者，可以将验证目标保存在 **[!UICONTROL Tweet (Direct Message)]** 投放模板中，通过节点 **[!UICONTROL Resources > Templates > Delivery templates]** 访问。 然后，默认情况下将为每个新验证输入目标。

### 定义消息内容 {#defining-message-content-}

在选项卡中输入帖子的 **[!UICONTROL Content]** 内容。

![](assets/social_twitter_delivery_015.png)

个性化字段的使用方式与电子邮件投放的使用方式相同，例如，在邮件正文中添加关注者的姓名。 内容个性化在本节 [中详细介绍](../../delivery/using/about-personalization.md)。

![](assets/social_twitter_delivery_021.png)

以下步骤与向Twitter帐户发送帖子的步骤相同。 请参阅 [在您的Twitter帐户上发布](#publishing-on-your-twitter-accounts)。
