---
product: campaign
title: 筛选规则
description: 了解如何使用Adobe Campaign中的筛选规则
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
TQID: https://experienceleague.adobe.com/4EMN3dCYWlCIIevYAbZsBxH1u2EaPl-izrzCKqyr1eA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2:
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 509
ht-degree: 2%

---

# 筛选规则{#filtering-rules}

过滤规则允许您根据查询中定义的条件定义要排除的消息。 这些规则链接到定向维度。

筛选规则可以链接到其他类型的规则（控制、压力等） 分类中进行分类，或分组到专用的&#x200B;**筛选**&#x200B;分类中。 有关详情，请参阅[创建和使用过滤类型](#creating-and-using-a-filtering-typology)。

## 创建筛选规则 {#creating-a-filtering-rule}

例如，您可以筛选新闻稿订阅者，以阻止将通信发送给未成年的收件人。

要定义此过滤器，请应用以下步骤：

1. 创建适用于所有通信渠道的&#x200B;**[!UICONTROL Filtering]**&#x200B;分类规则。

   ![](assets/campaign_opt_create_filter_01.png)

1. 更改默认定位维度并选择订阅(**nms:subscription**)。

   ![](assets/campaign_opt_create_filter_02.png)

1. 使用&#x200B;**[!UICONTROL Edit the query from the targeting dimension...]**&#x200B;链接创建筛选器。

   ![](assets/campaign_opt_create_filter_03.png)

1. 将此规则链接到营销活动类型并保存。

   ![](assets/campaign_opt_create_filter_04.png)

在投放中使用此规则时，将自动排除未成年订阅者。 特定消息指示规则应用：

![](assets/campaign_opt_create_filter_05.png)

## 为筛选规则设置条件 {#conditioning-a-filtering-rule}

您可以根据链接的投放或投放大纲限制筛选规则的应用程序字段。

为此，请转到分类规则的&#x200B;**[!UICONTROL General]**&#x200B;选项卡，选择要应用的限制类型并创建过滤器，如下所示：

![](assets/campaign_opt_create_filter_06.png)

在这种情况下，即使该规则链接到所有投放，它也只应用于与所定义过滤器的条件匹配的投放。

>[!NOTE]
>
>可在工作流的&#x200B;**[!UICONTROL Delivery outline]**&#x200B;活动中使用分类和筛选规则。 如需详细信息，请参阅[此小节](../../workflow/using/delivery-outline.md)。

## 创建和使用过滤类型 {#creating-and-using-a-filtering-typology}

您可以创建&#x200B;**[!UICONTROL Filtering]**&#x200B;分类：它们仅包含筛选规则。

![](assets/campaign_opt_create_typo_filtering.png)

选择目标后，这些特定分类可以链接到投放：在投放助手中，单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Exclusions]**&#x200B;选项卡。

![](assets/campaign_opt_apply_typo_filtering.png)

然后，选择要应用于投放的筛选类型。 为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并选择要应用的分类。

您还可以通过此选项卡直接链接筛选规则，而无需将它们分组到分类中。 要实现此目的，请使用窗口的下半部分。

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>只有类型和筛选规则在选择窗口中可用。
>
>这些配置可以在投放模板中定义，以自动应用于使用该模板创建的所有新投放。
>

## 默认可投放性排除规则 {#default-deliverability-exclusion-rules}

默认情况下，有两个筛选规则可用： **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** )和&#x200B;**[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** )。 在电子邮件分析期间，这些规则将收件人电子邮件地址与包含在可投放性实例中管理的加密全局禁止列表中的禁止地址或域名进行比较。 如果存在匹配项，则不会将该消息发送给该收件人。

这是为了避免由于恶意活动（特别是使用Spamtrap）而添加到。 例如，如果使用Spamtrap通过某个Web窗体进行订阅，则会自动向该Spamtrap发送确认电子邮件，这会导致您的地址自动添加到中。

>[!NOTE]
>
>全局隐藏列表中包含的地址和域名是隐藏的。 投放分析日志中仅指示排除的收件人的数量。
