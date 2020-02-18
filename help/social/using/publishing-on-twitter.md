---
title: 在Twitter上发布
seo-title: 在Twitter上发布
description: 在Twitter上发布
seo-description: null
page-status-flag: never-activated
uuid: 405bce50-a63c-4bd3-8f03-c71809bb1cfd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
discoiquuid: 2dc278ce-477c-493d-8abb-8bbdf2e988a5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2e18121e4094bc4cb215e5471091810df56b3ef5

---


# 在Twitter上发布{#publishing-on-twitter}

## 在您的Twitter帐户上发布 {#publishing-on-your-twitter-accounts}

配置完成后，Social Marketing允许您将帖子发送到您的Twitter帐户。

### 限制 {#limitations}

以下限制是Twitter固有的限制。

* 消息不能超过140个字符。
* 不支持HTML格式。

### 创建交付 {#creating-the-delivery}

根据分发模板创建新 **[!UICONTROL Tweet (twitter)]** 分发。

![](assets/social_twitter_delivery_001.png)

### 选择主目标 {#selecting-the-main-target}

选择要将帖子发送到的帐户。

1. 单击链 **[!UICONTROL To]** 接。

   ![](assets/social_twitter_delivery_002.png)

1. Click the **[!UICONTROL Add]** button.

   ![](assets/social_twitter_delivery_006.png)

1. Select **[!UICONTROL A Twitter account]**.

   ![](assets/social_twitter_delivery_007.png)

1. 在字段 **[!UICONTROL Folder]** 中，选择包含Twitter帐户的服务文件夹。 然后，选择要将您的推文发送到的Twitter帐户。

   ![](assets/social_twitter_delivery_011.png)

### 选择证明的目标 {#selecting-the-target-of-the-proof}

在选 **[!UICONTROL Target of the proofs]** 项卡中，您可以定义要在最终交付之前用于测试交付的Twitter帐户。 因此，我们建议您创建专用于发送校样的Twitter私人帐户。 有关如何创建私人Twitter帐户的详细信息，请参阅 [在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。 选择校样目标的步骤与选择主目标的步骤相同。 请参阅 [在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>如果您对所有分发使用相同的Twitter测试帐户，则可以在分发模板中保存证明目标，该模板可通 **[!UICONTROL Tweet]** 过节点访问 **[!UICONTROL Resources > Templates > Delivery templates]** 它。 然后，将默认为每个新交付输入证明目标。

### 定义消息内容 {#defining-the-message-content}

在选项卡中键入您的推文 **[!UICONTROL Content]** 内容。

![](assets/social_twitter_delivery_005.png)

### 查看预览 {#viewing-the-preview}

通过 **[!UICONTROL Preview]** 该选项卡可以查看帖子的呈现。

1. 单击选 **[!UICONTROL Preview]** 项卡。
1. 单击下 **[!UICONTROL Test personalization]** 拉菜单并选择 **[!UICONTROL Service]**。
1. 在字段 **[!UICONTROL Folder]** 中，选择包含您的Twitter帐户的服务文件夹。
1. 选择要测试预览的Twitter帐户。

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>预览可能与最终推文稍有不同。 我们强烈建议在最终交付前发送证据，以查看推文的确切呈现。 请参阅 [发送证明](#sending-the-proof)。

### 配置跟踪 {#configuring-tracking}

跟踪可在交付报告以及交付和服务 **[!UICONTROL Edit > Tracking]** 的选项卡中查看。

跟踪配置与电子邮件发送的跟踪配置相同。 如需详细信息，请参阅[此部分](../../delivery/using/monitoring-a-delivery.md)。

>[!NOTE]
>
>在交付模 **[!UICONTROL Tweet]** 板中，默认情况下启用跟踪。

>[!IMPORTANT]
>
>我们无法分辨分析帖子的机器人和实际点击的用户之间的区别。

### 发送证明 {#sending-the-proof}

我们强烈建议在最终交付之前发送出版物的证明，以在专用Twitter测试页面上获得出版物的精确呈现。 有关创建私人Twitter帐户的详细信息，请参阅 [在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。 选择校样目标的步骤在选 [择校样目标中有详细说明](#selecting-the-target-of-the-proof)。

证明交付与电子邮件发送相同。 Refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### 发送消息 {#sending-the-message}

1. 批准内容后，单击该按 **[!UICONTROL Send]** 钮。
1. 选 **[!UICONTROL Deliver as soon as possible]** 择并单击 **[!UICONTROL Analyze]** 按钮。

   >[!NOTE]
   >
   >该选 **[!UICONTROL Postpone the delivery]** 项允许您将交付推迟到以后的日期。

   ![](assets/social_twitter_delivery_012.png)

1. 分析完成后，检查结果。
1. 单 **[!UICONTROL Confirm delivery]**&#x200B;击，然后单击 **[!UICONTROL Yes]**。

![](assets/social_facebook_delivery_016.png)

## 向订阅者发送直接消息 {#sending-direct-messages-to-subscribers}

### 工作原理 {#operating-principle}

该工 **[!UICONTROL Synchronize Twitter accounts]** 作流(请参 [阅同步Twitter帐户](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts))会恢复Twitter订阅者列表，以便您能够向他们发送直接消息。 恢复的关注者存储在特定表中：访客表。 要显示Twitter关注者列表，请转到该节 **[!UICONTROL Profiles and Targets > Visitors]** 点。

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>要使工作流恢复Twitter关注者列表，必须在链 **[!UICONTROL Synchronize Twitter accounts]** 接到帐户的服务的“编辑”屏幕中选中该框。 有关详细信息，请参阅：委 [派对Adobe Campaign的写权限](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign)。

对于每个关注者，Adobe Campaign会恢复以下信息：

* **[!UICONTROL Origin]**:社交网络的名称(**Twitter** ，在此例中)
* **[!UICONTROL External ID]**:用户标识符
* **[!UICONTROL User name]**:用户的帐户名
* **[!UICONTROL Full name]**:用户名
* **[!UICONTROL Language]**:用户语言
* **[!UICONTROL Number of friends]**:关注者数
* **[!UICONTROL Time zone]**:用户时区
* **[!UICONTROL Verified]**:此字段指示用户是否具有经过验证的Twitter帐户

### 限制 {#limitations-1}

以下限制是Twitter固有的限制。

* 消息不能超过140个字符。
* 不支持HTML。
* 每天不能发送超过250条直接消息。 为避免超过此阈值，您可以以多个波形进行传送。 波形传送的配置类似于电子邮件传送。 如需详细信息，请参阅[此部分](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

### 创建交付 {#creating-the-delivery-}

根据分发模板创建新 **[!UICONTROL Tweet (Direct Message)]** 分发。

![](assets/social_twitter_delivery_010.png)

### 选择主目标 {#selecting-the-main-target-1}

选择要将直接消息发送到的关注者。

1. 单击链 **[!UICONTROL To]** 接。

   ![](assets/social_twitter_delivery_016.png)

1. Click the **[!UICONTROL Add]** button.

   ![](assets/social_twitter_delivery_006.png)

1. 选择定位类型。

   ![](assets/social_twitter_delivery_017.png)

   * 选择 **[!UICONTROL Twitter subscribers]** 以向所有帐户关注者发送直接消息。

      >[!IMPORTANT]
      >
      >每天不能发送超过250条消息。 如果您的Twitter帐户有超过250个关注者，我们强烈建议大量投递。 这与电子邮件发送过程相同。 Refer to [this section](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

   * 选择 **[!UICONTROL Filter conditions]** 以定义查询并查看其结果。 此选项与电子邮件发送的选项相同。 Refer to [this section](../../platform/using/defining-filter-conditions.md) for more information.

      ![](assets/social_twitter_delivery_018.png)

### 选择证明的目标 {#selecting-the-target-of-the-proof-1}

在选 **[!UICONTROL Target of the proofs]** 项卡中，您可以选择将收到您的直接消息证明的关注者。 选择过程与主目标的选择过程相同。 请参阅 [选择主目标](#selecting-the-main-target)。

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>如果要将所有直接消息校样发送给同一Twitter关注者，您可以将校样目标保存在通过节点访问 **[!UICONTROL Tweet (Direct Message)]** 的分发模板中， **[!UICONTROL Resources > Templates > Delivery templates]** 该模板。 然后，将默认为每个新交付输入证明目标。

### 定义消息内容 {#defining-message-content-}

在选项卡中输入推文的 **[!UICONTROL Content]** 内容。

![](assets/social_twitter_delivery_015.png)

个性化字段的使用方式与电子邮件发送相同，例如在邮件正文中添加关注者的姓名。 本节详细介绍了内 [容个性化](../../delivery/using/about-personalization.md)。

![](assets/social_twitter_delivery_021.png)

以下步骤与向Twitter帐户发送推文的步骤相同。 请参阅在 [您的Twitter帐户上发布](#publishing-on-your-twitter-accounts)。
