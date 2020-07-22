---
title: 每季度列表更新(使用增量查询)
description: 在此用例中，使用增量查询自动更新收件人列表。
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aa192d975a08246ba684940fff3d33853d7d9345
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# 每季度列表更新(使用增量查询) {#quarterly-list-update}

在以下示例中，使用 [增量查询](../../workflow/using/incremental-query.md) ，以自动更新收件人列表。 这些收件人作为季节性营销活动的一部分而定。

由于每季开始推出这些活动以优惠相关的体育活动，因此每季更新这些列表。 但是，此收件人必须每9个月针对一次此活动。 这样，您就可以避开收件人的资格频率，并在多年内优惠活动不同季节。

![](assets/incremental_query_example.png)

1. 将增量查询和列表更新活动添加到新工作流中。
1. 按照创 **[!UICONTROL Incremental query]** 建活动中的指定配置查询 [的选项卡](../../workflow/using/query.md#creating-a-query)。
1. 选择选 **[!UICONTROL Scheduling & History]** 项卡，然后指定270天历史记录。 已被攻击的收件人在270天或大约9个月内不再被攻击。

   Then click the **[!UICONTROL Change...]** button.

1. 要确保在每个季节的列表之前更新开始，请选择 **[!UICONTROL Monthly]**。
1. 在下一个屏幕上，选择3月、6月、9月和12月。 选择月的20号，然后选择要启动该工作流的时间。
1. 接下来，选择查询的有效期。 例如，如果希望此活动永久处于活动状态，请选择 **[!UICONTROL Permanent validity]**。

   ![](assets/incremental_query_example_2.png)

1. 批准增量查询后，请配置列表更新活动，如 [列表更新](../../workflow/using/list-update.md)。

因此，该工作流将在每个季节的开始之前自动启动。 列表将更新为新的合格收件人以接收优惠。
