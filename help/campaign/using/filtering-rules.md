---
product: campaign
title: 筛选规则
description: 筛选规则
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---

# 筛选规则{#filtering-rules}

通过筛选规则，您可以根据查询中定义的条件定义要排除的消息。 这些规则已链接到定向维度。

筛选规则可以链接到其他类型的规则（控制、压力等） ，或分组到专用&#x200B;**筛选**&#x200B;分类中。 有关更多信息，请参阅[创建和使用过滤分类](#creating-and-using-a-filtering-typology)。

## 创建筛选规则{#creating-a-filtering-rule}

例如，您可以过滤新闻稿的订阅者，以防止将通信发送给未达到法定年龄的收件人。

要定义此过滤器，请应用以下步骤：

1. 创建适用于所有通信渠道的&#x200B;**[!UICONTROL Filtering]**&#x200B;分类规则。

   ![](assets/campaign_opt_create_filter_01.png)

1. 更改默认定向维度并选择订阅(**nms:subscription**)。

   ![](assets/campaign_opt_create_filter_02.png)

1. 使用&#x200B;**[!UICONTROL Edit the query from the targeting dimension...]**&#x200B;链接创建过滤器。

   ![](assets/campaign_opt_create_filter_03.png)

1. 将此规则链接到营销活动分类并保存。

   ![](assets/campaign_opt_create_filter_04.png)

在投放中使用此规则时，会自动排除未成年订阅者。 特定消息指示规则应用程序：

![](assets/campaign_opt_create_filter_05.png)

## 调整筛选规则{#conditioning-a-filtering-rule}

您可以根据链接的投放大纲或投放大纲限制筛选规则的应用程序字段。

要实现此目的，请转到分类规则的&#x200B;**[!UICONTROL General]**&#x200B;选项卡，选择要应用的限制类型并创建过滤器，如下所示：

![](assets/campaign_opt_create_filter_06.png)

在这种情况下，即使规则已链接到所有投放，它也将仅应用于符合所定义过滤器标准的投放。

>[!NOTE]
>
>分类和筛选规则可在工作流的&#x200B;**[!UICONTROL Delivery outline]**&#x200B;活动中使用。 如需详细信息，请参阅[此部分](../../workflow/using/delivery-outline.md)。

## 创建和使用过滤分类{#creating-and-using-a-filtering-typology}

您可以创建&#x200B;**[!UICONTROL Filtering]**&#x200B;分类：它们只包含过滤规则。

![](assets/campaign_opt_create_typo_filtering.png)

选择目标后，这些特定分类可以链接到投放：在投放向导中，单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Exclusions]**&#x200B;选项卡。

![](assets/campaign_opt_apply_typo_filtering.png)

然后，选择要应用于投放的筛选分类。 为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并选择要应用的分类。

您还可以通过此选项卡直接链接过滤规则，而无需将规则分组到分类中。 要实现此目的，请使用窗口的下部。

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>只有分类和筛选规则在选择窗口中可用。
>
>这些配置可以在投放模板中定义，以自动应用于使用该模板创建的所有新投放。


## 默认可投放性排除规则{#default-deliverability-exclusion-rules}

默认情况下，可使用两个筛选规则：**[!UICONTROL Exclude addresses]**(**[!UICONTROL addressExclusions]**)和&#x200B;**[!UICONTROL Exclude domains]**(**[!UICONTROL domainExclusions]**)。 在电子邮件分析期间，这些规则将收件人电子邮件地址与可投放性实例中管理的加密全局抑制列表中包含的禁止地址或域名进行比较。 如果存在匹配项，则不会向该收件人发送消息。

这是为了避免由于恶意活动(阻止列表尤其是使用Spamtrap)而被添加到中。 例如，如果使用Spamtrap通过您的一个Web窗体订阅，则会自动向该Spamtrap发送确认电子邮件，这会导致您的地址被自动添加到该阻止列表页面。

>[!NOTE]
>
>全局禁止列表中包含的地址和域名将被隐藏。 投放分析日志中只显示被排除的收件人数。
