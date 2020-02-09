---
title: 筛选规则
seo-title: 筛选规则
description: 筛选规则
seo-description: null
page-status-flag: never-activated
uuid: 24238a99-1f0f-4d04-9807-557ec2a5ba16
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 0d50826e-2211-4c3b-8413-ca1453bba6c4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 筛选规则{#filtering-rules}

过滤规则允许您根据在查询中定义的条件定义要排除的消息。 这些规则链接到定位维。

过滤规则可以链接到其他类型的规则（控制、压力等）或按专用的过滤类型 **分组** 。 有关此内容的详细信息，请参 [阅创建和使用筛选类型学](#creating-and-using-a-filtering-typology)。

## 创建筛选规则 {#creating-a-filtering-rule}

例如，您可以过滤新闻稿订阅者，以防止将通信发送给未达到年龄的收件人。

要定义此过滤器，请应用以下步骤：

1. 创建适用 **[!UICONTROL Filtering]** 于所有通信渠道的类型规则。

   ![](assets/campaign_opt_create_filter_01.png)

1. 更改默认定位维度并选择订阅(**nms:subscription**)。

   ![](assets/campaign_opt_create_filter_02.png)

1. 使用链接创建过 **[!UICONTROL Edit the query from the targeting dimension...]** 滤器。

   ![](assets/campaign_opt_create_filter_03.png)

1. 将此规则链接到营销活动类型学并保存它。

   ![](assets/campaign_opt_create_filter_04.png)

当此规则用于交付时，未成年订阅者将自动排除。 特定消息指示规则应用：

![](assets/campaign_opt_create_filter_05.png)

## 调整过滤规则 {#conditioning-a-filtering-rule}

您可以根据链接的交付或交付大纲限制筛选规则的应用程序字段。

为此，请转到排版规 **[!UICONTROL General]** 则的选项卡，选择要应用的限制类型并创建过滤器，如下所示：

![](assets/campaign_opt_create_filter_06.png)

在这种情况下，即使规则链接到所有提交，它也将仅应用于符合定义筛选器条件的规则。

>[!NOTE]
>
>可以在工作流中的活动中使用字体和过滤 **[!UICONTROL Delivery outline]** 规则。 如需详细信息，请参阅[此部分](../../workflow/using/delivery-outline.md)。

## 创建和使用过滤排版 {#creating-and-using-a-filtering-typology}

您可以创建 **[!UICONTROL Filtering]** 类型：它们只包含过滤规则。

![](assets/campaign_opt_create_typo_filtering.png)

选择目标时，这些特定类型可以链接到交付：在传送向导中，单击链 **[!UICONTROL To]** 接，然后单击选 **[!UICONTROL Exclusions]** 项卡。

![](assets/campaign_opt_apply_typo_filtering.png)

然后，选择要应用于分发的筛选类型。 为此，请单击按 **[!UICONTROL Add]** 钮并选择要应用的类型。

您还可以通过此选项卡直接链接筛选规则，而不将它们分组到类型学中。 为此，请使用窗口的下部。

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>* 只有类型和筛选规则在选择窗口中可用。
>* 这些配置可以在分发模板中定义，以自动应用于使用模板创建的所有新分发。
>



## 默认可交付性排除规则 {#default-deliverability-exclusion-rules}

默认情况下有两种筛选规则： **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** )和 **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** )。 在电子邮件分析过程中，这些规则将收件人电子邮件地址与包含在可交付性实例中管理的加密全局禁止列表中的禁止地址或域名进行比较。 如果存在匹配项，则不会向该收件人发送消息。

这可以避免由于恶意活动（特别是使用Spamtrap）而被列入黑名单。 例如，如果使用Spamtrap通过您的某个Web表单进行订阅，则会自动向该Spamtrap发送确认电子邮件，这会导致您的地址自动列入黑名单。

>[!NOTE]
>
>包含在全局隐藏列表中的地址和域名是隐藏的。 在分发分析日志中只显示被排除的收件人数。

