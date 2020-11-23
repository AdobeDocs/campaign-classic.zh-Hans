---
solution: Campaign Classic
product: campaign
title: 筛选规则
description: 筛选规则
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---


# 筛选规则{#filtering-rules}

筛选规则允许您根据在查询中定义的条件定义要排除的消息。 这些规则与定位维度相关。

过滤规则可以链接到其他类型的规则（控制、压力等） 或按专用的过滤排 **版** 。 有关此方面的详细信息，请 [参阅创建和使用过滤排版](#creating-and-using-a-filtering-typology)。

## Creating a filtering rule {#creating-a-filtering-rule}

例如，您可以过滤新闻稿订阅者，以防止将通信发送给未满收件人。

要定义此筛选器，请应用以下步骤：

1. 创建适 **[!UICONTROL Filtering]** 用于所有通信渠道的类型规则。

   ![](assets/campaign_opt_create_filter_01.png)

1. 更改默认定位维度并选择订阅&#x200B;**(nms:订阅**)。

   ![](assets/campaign_opt_create_filter_02.png)

1. 使用链接创建筛 **[!UICONTROL Edit the query from the targeting dimension...]** 选器。

   ![](assets/campaign_opt_create_filter_03.png)

1. 将此规则链接到活动类型并保存它。

   ![](assets/campaign_opt_create_filter_04.png)

在投放中使用此规则时，将自动排除未成年订阅者。 特定消息指示规则应用程序：

![](assets/campaign_opt_create_filter_05.png)

## 调整过滤规则 {#conditioning-a-filtering-rule}

您可以根据链接的投放或投放概要限制筛选规则的应用程序字段。

为此，请转到类型规则 **[!UICONTROL General]** 的选项卡，选择要应用的限制类型并创建过滤器，如下所示：

![](assets/campaign_opt_create_filter_06.png)

在这种情况下，即使规则链接到所有投放，它也将仅应用于那些符合已定义筛选器条件的规则。

>[!NOTE]
>
>类型和过滤规则可在工作流中、在活动中使 **[!UICONTROL Delivery outline]** 用。 如需详细信息，请参阅[此部分](../../workflow/using/delivery-outline.md)。

## 创建和使用过滤排版 {#creating-and-using-a-filtering-typology}

您可以创建 **[!UICONTROL Filtering]** 类型：它们只包含过滤规则。

![](assets/campaign_opt_create_typo_filtering.png)

选择投放后，这些特定类型可以链接到目标:在投放向导中，单击链 **[!UICONTROL To]** 接，然后单击选 **[!UICONTROL Exclusions]** 项卡。

![](assets/campaign_opt_apply_typo_filtering.png)

然后，选择要应用于投放的筛选类型。 为此，请单击按 **[!UICONTROL Add]** 钮并选择要应用的类型。

您还可以通过此选项卡直接链接过滤规则，而不将它们分组到类型学中。 为此，请使用窗口的下部。

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>只有类型和筛选规则在选择窗口中可用。
>
>这些配置可以在投放模板中定义，以自动应用于使用模板创建的所有新投放。


## 默认可交付性排除规则 {#default-deliverability-exclusion-rules}

默认情况下有两种筛选规则： **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) **[!UICONTROL Exclude domains]** 和( **[!UICONTROL domainExclusions]** )。 在电子邮件分析期间，这些规则将收件人电子邮件地址与在可交付性实例中管理的加密全局禁止列表中包含的禁止地址或域名进行比较。 如果存在匹配项，则消息不会发送到该收件人。

这可以避免由于恶意活动阻止列表（特别是使用垃圾邮件陷阱）而添加到该。 例如，如果使用垃圾邮件陷阱通过您的某个Web表单进行订阅，则会自动向该垃圾邮件陷阱发送确认电子邮件，这会导致您的地址被自动添加到该阻止列表垃圾邮件。

>[!NOTE]
>
>全局禁止列表中包含的地址和域名将被隐藏。 在收件人分析日志中只指示被排除的投放数。

