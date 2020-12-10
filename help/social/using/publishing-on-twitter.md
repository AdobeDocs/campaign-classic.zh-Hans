---
solution: Campaign Classic
product: campaign
title: 在 Twitter 上发布
description: 在 Twitter 上发布
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 5%

---


# 在 Twitter 上发布{#publishing-on-twitter}

## 发布到您的Twitter帐户{#publishing-on-your-twitter-accounts}

配置完成后，Social Marketing允许您将帖子发送到Twitter帐户。

### 限制{#limitations}

以下限制是Twitter固有的限制。

* 邮件长度不得超过140个字符。
* 不支持HTML格式。

### 创建投放 {#creating-the-delivery}

根据&#x200B;**[!UICONTROL Tweet (twitter)]**&#x200B;投放创建新投放模板。

![](assets/social_twitter_delivery_001.png)

### 选择主目标{#selecting-the-main-target}

选择要将帖子发送到的帐户。

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;链接。

   ![](assets/social_twitter_delivery_002.png)

1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/social_twitter_delivery_006.png)

1. 选择 **[!UICONTROL A Twitter account]**。

   ![](assets/social_twitter_delivery_007.png)

1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;字段中，选择包含Twitter帐户的服务文件夹。 然后，选择要将您的推文发送到的Twitter帐户。

   ![](assets/social_twitter_delivery_011.png)

### 选择验证{#selecting-the-target-of-the-proof}的目标

在&#x200B;**[!UICONTROL Target of the proofs]**&#x200B;选项卡中，您可以定义要在最终投放之前用于测试投放的Twitter帐户。 因此，我们建议您创建专用于发送验证的Twitter帐户。 有关如何创建专用Twitter帐户的详细信息，请参阅[在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。 选择验证目标的步骤与选择主目标的步骤相同。 请参阅[在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>如果对所有投放使用相同的Twitter测试帐户，则可以在&#x200B;**[!UICONTROL Tweet]**&#x200B;投放模板中保存验证目标，该通过&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点访问。 然后，默认情况下将为每个新验证输入目标。

### 定义消息内容{#defining-the-message-content}

在&#x200B;**[!UICONTROL Content]**&#x200B;选项卡中键入您的帖子内容。

![](assets/social_twitter_delivery_005.png)

### 查看预览{#viewing-the-preview}

使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡可视图帖子的呈现。

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡。
1. 单击&#x200B;**[!UICONTROL Test personalization]**&#x200B;下拉菜单并选择&#x200B;**[!UICONTROL Service]**。
1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;字段中，选择包含您的Twitter帐户的服务文件夹。
1. 选择要测试预览的Twitter帐户。

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>预览可能与最终的推文略有不同。 我们强烈建议在最终验证之前发送投放，以视图帖子的确切呈现。 请参阅[发送验证](#sending-the-proof)。

### 配置跟踪{#configuring-tracking}

跟踪可在投放报告和投放和服务的&#x200B;**[!UICONTROL Edit > Tracking]**&#x200B;选项卡中查看。

跟踪配置与电子邮件投放相同。 如需详细信息，请参阅[此部分](../../delivery/using/about-delivery-monitoring.md)。

>[!NOTE]
>
>在&#x200B;**[!UICONTROL Tweet]**&#x200B;投放模板中，默认情况下启用跟踪。

>[!IMPORTANT]
>
>我们无法分辨分析帖子的机器人和实际点击的用户之间的区别。

### 发送验证{#sending-the-proof}

我们强烈建议在最终验证之前发送出版物的投放，以在专用Twitter测试页上获得出版物的精确呈现。 有关创建专用Twitter帐户的详细信息，请参阅[在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。 选择验证目标的步骤详见[选择验证的目标](#selecting-the-target-of-the-proof)。

验证投放与电子邮件投放相同。 请参阅[此章节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) 。

### 发送消息{#sending-the-message}

1. 批准内容后，单击&#x200B;**[!UICONTROL Send]**&#x200B;按钮。
1. 选择&#x200B;**[!UICONTROL Deliver as soon as possible]**&#x200B;并单击&#x200B;**[!UICONTROL Analyze]**&#x200B;按钮。

   >[!NOTE]
   >
   >使用&#x200B;**[!UICONTROL Postpone the delivery]**&#x200B;选项可延后投放到以后的日期。

   ![](assets/social_twitter_delivery_012.png)

1. 完成分析后，检查结果。
1. 单击&#x200B;**[!UICONTROL Confirm delivery]**，然后单击&#x200B;**[!UICONTROL Yes]**。

![](assets/social_facebook_delivery_016.png)

## 向订阅者{#sending-direct-messages-to-subscribers}发送直接消息

### 工作原理 {#operating-principle}

**[!UICONTROL Synchronize Twitter accounts]**&#x200B;工作流程（请参阅[同步Twitter帐户](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts)）可恢复Twitter订阅者的列表，以便您能够向他们发送直接消息。 恢复的关注者存储在特定表中：访客表。 要显示Twitter关注者的列表，请转至&#x200B;**[!UICONTROL Profiles and Targets > Visitors]**&#x200B;节点。

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>要使工作流恢复Twitter关注者的列表，必须在链接到帐户的服务的“编辑”屏幕中选中&#x200B;**[!UICONTROL Synchronize Twitter accounts]**&#x200B;框。 有关此内容的详细信息，请参阅：[将写访问权委托给Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign)。

对于每位关注者，Adobe Campaign会恢复以下信息：

* **[!UICONTROL Origin]**:社交网络的名称(**** 本例中为Twitter)
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

根据&#x200B;**[!UICONTROL Tweet (Direct Message)]**&#x200B;投放创建新投放模板。

![](assets/social_twitter_delivery_010.png)

### 选择主目标{#selecting-the-main-target-1}

选择要将直接消息发送给的关注者。

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;链接。

   ![](assets/social_twitter_delivery_016.png)

1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/social_twitter_delivery_006.png)

1. 选择定位类型。

   ![](assets/social_twitter_delivery_017.png)

   * 选择&#x200B;**[!UICONTROL Twitter subscribers]**&#x200B;向所有帐户关注者发送直接消息。

      >[!IMPORTANT]
      >
      >每天不能发送250条以上的邮件。 如果您的Twitter帐户拥有超过250个关注者，我们强烈建议提供批次。 这涉及与电子邮件投放相同的流程。 请参阅[此章节](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves) 。

   * 选择&#x200B;**[!UICONTROL Filter conditions]**&#x200B;定义查询并视图其结果。 此选项与电子邮件投放相同。 有关详细信息，请参阅[本节](../../platform/using/defining-filter-conditions.md)。

      ![](assets/social_twitter_delivery_018.png)

### 选择验证{#selecting-the-target-of-the-proof-1}的目标

在&#x200B;**[!UICONTROL Target of the proofs]**&#x200B;选项卡中，您可以选择接收您的直接消息验证的关注者。 选择过程与主目标相同。 请参阅[选择主目标](#selecting-the-main-target)。

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>如果要将所有直接消息验证发送给同一Twitter关注者，可以在&#x200B;**[!UICONTROL Tweet (Direct Message)]**&#x200B;投放模板中保存验证目标，该通过&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点访问。 然后，默认情况下将为每个新验证输入目标。

### 定义消息内容{#defining-message-content-}

在&#x200B;**[!UICONTROL Content]**&#x200B;选项卡中输入帖子内容。

![](assets/social_twitter_delivery_015.png)

个性化字段的使用方式与电子邮件投放的使用方式相同，例如，在邮件正文中添加关注者的姓名。 内容个性化详见[本节](../../delivery/using/about-personalization.md)。

![](assets/social_twitter_delivery_021.png)

以下步骤与向Twitter帐户发送帖子的步骤相同。 请参阅[在您的Twitter帐户上发布](#publishing-on-your-twitter-accounts)。
