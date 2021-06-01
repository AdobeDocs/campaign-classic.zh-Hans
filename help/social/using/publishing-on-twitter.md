---
product: campaign
title: 在 Twitter 上发布
description: 在 Twitter 上发布
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: e030c029-d1ee-4749-94e3-6bdfc8d89a34
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 5%

---

# 在 Twitter 上发布{#publishing-on-twitter}

## 在Twitter帐户上发布{#publishing-on-your-twitter-accounts}

配置完成后， Social Marketing允许您将推文发送到Twitter帐户。

### 限制 {#limitations}

以下限制是Twitter固有的限制。

* 消息长度不能超过140个字符。
* 不支持HTML格式。

### 创建投放 {#creating-the-delivery}

根据&#x200B;**[!UICONTROL Tweet (twitter)]**&#x200B;投放模板创建新投放。

![](assets/social_twitter_delivery_001.png)

### 选择主目标{#selecting-the-main-target}

选择要将推文发送到的帐户。

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;链接。

   ![](assets/social_twitter_delivery_002.png)

1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/social_twitter_delivery_006.png)

1. 选择 **[!UICONTROL A Twitter account]**。

   ![](assets/social_twitter_delivery_007.png)

1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;字段中，选择包含Twitter帐户的服务文件夹。 然后，选择要将推文发送到的Twitter帐户。

   ![](assets/social_twitter_delivery_011.png)

### 选择校样{#selecting-the-target-of-the-proof}的目标

利用&#x200B;**[!UICONTROL Target of the proofs]**&#x200B;选项卡，可定义在最终投放之前用于测试投放的Twitter帐户。 因此，我们建议您创建一个专用于发送校样的Twitter帐户。 有关如何创建专用Twitter帐户的更多信息，请参阅[在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。 选择校样目标的步骤与选择主目标的步骤相同。 请参阅[在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。

![](assets/social_twitter_delivery_004.png)

>[!NOTE]
>
>如果您对所有投放使用相同的Twitter测试帐户，则可以在&#x200B;**[!UICONTROL Tweet]**&#x200B;投放模板中保存校样目标，该模板可通过&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点访问。 然后，将默认为每个新投放输入校样目标。

### 定义消息内容{#defining-the-message-content}

在&#x200B;**[!UICONTROL Content]**&#x200B;选项卡中键入推文内容。

![](assets/social_twitter_delivery_005.png)

### 查看预览{#viewing-the-preview}

使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡可以查看推文的呈现。

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡。
1. 单击&#x200B;**[!UICONTROL Test personalization]**&#x200B;下拉菜单并选择&#x200B;**[!UICONTROL Service]**。
1. 在&#x200B;**[!UICONTROL Folder]**&#x200B;字段中，选择包含您的Twitter帐户的服务文件夹。
1. 选择要用于测试预览的Twitter帐户。

![](assets/social_twitter_delivery_008.png)

>[!NOTE]
>
>预览可能与最终推文略有不同。 我们强烈建议在最终投放之前发送校样，以查看推文的确切呈现。 请参阅[发送校样](#sending-the-proof)。

### 配置跟踪{#configuring-tracking}

可以在投放报告和投放和服务的&#x200B;**[!UICONTROL Edit > Tracking]**&#x200B;选项卡中查看跟踪。

跟踪配置与电子邮件投放的相同。 如需详细信息，请参阅[此部分](../../delivery/using/about-delivery-monitoring.md)。

>[!NOTE]
>
>在&#x200B;**[!UICONTROL Tweet]**&#x200B;投放模板中，默认启用跟踪。

>[!IMPORTANT]
>
>我们无法区分分析推文的机器人和实际点击的用户。

### 发送校样{#sending-the-proof}

我们强烈建议在最终交付之前发送发布校样，以在专用Twitter测试页面上获取发布的确切呈现。 有关创建专用Twitter帐户的更多信息，请参阅[在Twitter上创建测试帐户](../../social/using/configuring-publishing-on-twitter.md#creating-a-test-account-on-twitter)。 [选择校样的目标](#selecting-the-target-of-the-proof)中详细介绍了选择校样目标的步骤。

校样投放与电子邮件投放相同。 请参阅[此小节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 发送消息{#sending-the-message}

1. 批准内容后，单击&#x200B;**[!UICONTROL Send]**&#x200B;按钮。
1. 选择&#x200B;**[!UICONTROL Deliver as soon as possible]**&#x200B;并单击&#x200B;**[!UICONTROL Analyze]**&#x200B;按钮。

   >[!NOTE]
   >
   >使用&#x200B;**[!UICONTROL Postpone the delivery]**&#x200B;选项可将投放推迟到以后的日期。

   ![](assets/social_twitter_delivery_012.png)

1. 分析完成后，检查结果。
1. 单击&#x200B;**[!UICONTROL Confirm delivery]**，然后单击&#x200B;**[!UICONTROL Yes]**。

![](assets/social_facebook_delivery_016.png)

## 向订阅者发送私信{#sending-direct-messages-to-subscribers}

### 操作原则 {#operating-principle}

**[!UICONTROL Synchronize Twitter accounts]**&#x200B;工作流(请参阅[同步Twitter帐户](../../social/using/configuring-publishing-on-twitter.md#synchronizing-twitter-accounts))取回了Twitter订阅者列表，以便您能够向他们发送私信。 恢复的关注者存储在特定表中：访客表。 要显示Twitter关注者列表，请转到&#x200B;**[!UICONTROL Profiles and Targets > Visitors]**&#x200B;节点。

![](assets/social_twitter_visitors_001.png)

>[!IMPORTANT]
>
>为了工作流恢复Twitter关注者列表，必须在链接到帐户的服务的编辑屏幕中选中&#x200B;**[!UICONTROL Synchronize Twitter accounts]**&#x200B;框。 有关更多信息，请参阅：[委派对Adobe Campaign](../../social/using/configuring-publishing-on-twitter.md#delegating-write-access-to-adobe-campaign)的写入权限。

对于每个关注者，Adobe Campaign会恢复以下信息：

* **[!UICONTROL Origin]**:社交网络的名称(**** 在本例中为Twitter)
* **[!UICONTROL External ID]**:用户标识符
* **[!UICONTROL User name]**:用户的帐户名称
* **[!UICONTROL Full name]**:用户名称
* **[!UICONTROL Language]**:用户语言
* **[!UICONTROL Number of friends]**:关注者数量
* **[!UICONTROL Time zone]**:用户时区
* **[!UICONTROL Verified]**:此字段指示用户是否具有已验证的Twitter帐户

### 限制{#limitations-1}

以下限制是Twitter固有的限制。

* 消息长度不能超过140个字符。
* 不支持HTML。
* 您每天不能发送超过250条私信。 为避免超过此阈值，您可以分几批投放内容。 分批投放的配置方式与电子邮件投放类似。 如需详细信息，请参阅[此部分](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

### 创建投放 {#creating-the-delivery-}

根据&#x200B;**[!UICONTROL Tweet (Direct Message)]**&#x200B;投放模板创建新投放。

![](assets/social_twitter_delivery_010.png)

### 选择主目标{#selecting-the-main-target-1}

选择要将私信发送给的关注者。

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;链接。

   ![](assets/social_twitter_delivery_016.png)

1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/social_twitter_delivery_006.png)

1. 选择定位类型。

   ![](assets/social_twitter_delivery_017.png)

   * 选择&#x200B;**[!UICONTROL Twitter subscribers]**&#x200B;以向所有帐户关注者发送私信。

      >[!IMPORTANT]
      >
      >每天不能发送超过250条消息。 如果您的Twitter帐户有250多个关注者，我们强烈建议分批投放。 这涉及与电子邮件投放相同的流程。 请参阅[此小节](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

   * 选择&#x200B;**[!UICONTROL Filter conditions]**&#x200B;以定义查询并查看其结果。 此选项与电子邮件投放的选项相同。 有关详细信息，请参阅[此部分](../../platform/using/defining-filter-conditions.md)。

      ![](assets/social_twitter_delivery_018.png)

### 选择校样{#selecting-the-target-of-the-proof-1}的目标

**[!UICONTROL Target of the proofs]**&#x200B;选项卡允许您选择接收您私信校样的关注者。 选择过程与主目标的选择过程相同。 请参阅[选择主目标](#selecting-the-main-target)。

![](assets/social_twitter_delivery_020.png)

>[!NOTE]
>
>如果要将所有直接消息校样发送到同一Twitter关注者，可以在&#x200B;**[!UICONTROL Tweet (Direct Message)]**&#x200B;投放模板中保存校样目标，该模板可通过&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点访问。 然后，将默认为每个新投放输入校样目标。

### 定义消息内容{#defining-message-content-}

在&#x200B;**[!UICONTROL Content]**&#x200B;选项卡中输入推文的内容。

![](assets/social_twitter_delivery_015.png)

个性化字段的使用方式与电子邮件投放相同，例如，在消息正文中添加关注者的名称。 有关内容个性化的详细信息，请参见[此部分](../../delivery/using/about-personalization.md)。

![](assets/social_twitter_delivery_021.png)

以下步骤与向Twitter帐户发送推文的步骤相同。 请参阅[在Twitter帐户上发布](#publishing-on-your-twitter-accounts)。
