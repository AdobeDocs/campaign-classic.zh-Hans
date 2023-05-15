---
product: campaign
title: 筛选规则
description: 了解如何使用过滤规则
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Typology Rules
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 2%

---

# 筛选规则{#filtering-rules}

通过筛选规则，您可以根据查询中定义的条件定义要排除的消息。 这些规则已链接到定向维度。

筛选规则可以链接到其他类型的规则（控制、压力等） 分类，或分组到 **筛选** 分类。 有关更多信息，请参阅 [创建和使用过滤分类](#creating-and-using-a-filtering-typology).

## 创建筛选规则 {#creating-a-filtering-rule}

例如，您可以过滤新闻稿的订阅者，以防止将通信发送给未达到法定年龄的收件人。

要定义此过滤器，请应用以下步骤：

1. 创建 **[!UICONTROL Filtering]** 分类规则。

   ![](assets/campaign_opt_create_filter_01.png)

1. 更改默认定向维度并选择订阅(**nms:subscription**)。

   ![](assets/campaign_opt_create_filter_02.png)

1. 使用创建过滤器 **[!UICONTROL Edit the query from the targeting dimension...]** 链接。

   ![](assets/campaign_opt_create_filter_03.png)

1. 将此规则链接到营销活动分类并保存。

   ![](assets/campaign_opt_create_filter_04.png)

在投放中使用此规则时，会自动排除未成年订阅者。 特定消息指示规则应用程序：

![](assets/campaign_opt_create_filter_05.png)

## 筛选规则的条件 {#conditioning-a-filtering-rule}

您可以根据链接的投放大纲或投放大纲限制筛选规则的应用程序字段。

要执行此操作，请转到 **[!UICONTROL General]** ，选择要应用的限制类型并创建过滤器，如下所示：

![](assets/campaign_opt_create_filter_06.png)

在这种情况下，即使规则已链接到所有投放，它也将仅应用于符合所定义过滤器标准的投放。

>[!NOTE]
>
>分类和过滤规则可在工作流中的 **[!UICONTROL Delivery outline]** 活动。 如需详细信息，请参阅[此部分](../../workflow/using/delivery-outline.md)。

## 创建和使用过滤分类 {#creating-and-using-a-filtering-typology}

您可以创建 **[!UICONTROL Filtering]** 分类：它们只包含过滤规则。

![](assets/campaign_opt_create_typo_filtering.png)

选择目标后，这些特定分类可以链接到投放：在投放向导中，单击 **[!UICONTROL To]** 链接，然后单击 **[!UICONTROL Exclusions]** 选项卡。

![](assets/campaign_opt_apply_typo_filtering.png)

然后，选择要应用于投放的筛选分类。 为此，请单击 **[!UICONTROL Add]** 按钮，然后选择要应用的分类。

您还可以通过此选项卡直接链接过滤规则，而无需将规则分组到分类中。 要实现此目的，请使用窗口的下部。

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>只有分类和筛选规则在选择窗口中可用。
>
>这些配置可以在投放模板中定义，以自动应用于使用该模板创建的所有新投放。

## 默认的投放能力排除规则 {#default-deliverability-exclusion-rules}

默认情况下，可使用两个筛选规则： **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** )和 **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** )。 在电子邮件分析期间，这些规则将收件人电子邮件地址与可投放性实例中管理的加密全局抑制列表中包含的禁止地址或域名进行比较。 如果存在匹配项，则不会向该收件人发送消息。

这是为了避免由于恶意活动(阻止列表尤其是使用Spamtrap)而被添加到中。 例如，如果使用Spamtrap通过您的一个Web窗体订阅，则会自动向该Spamtrap发送确认电子邮件，这会导致您的地址被自动添加到该阻止列表页面。

>[!NOTE]
>
>全局禁止列表中包含的地址和域名将被隐藏。 投放分析日志中只显示被排除的收件人数。
