---
product: campaign
title: 推荐类别
description: 推荐类别
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cb062cb2-dfea-46aa-8d9e-580e4dc7bb25
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 5%

---

# 推荐类别{#recommending-a-category}



这可能是因为收件人被认为不符合所有优惠的资格。 为确保所有接收者都收到优惠建议，可以在建议中系统地添加一个或多个优惠类别。 与主要选件不同，这些“备用”选件必须具有低权重（但不为零），因此只有在没有高权重选件符合条件时，才会考虑它们。 此外，不得对这些选件应用演示规则，以确保始终将这些选件包含在推荐中。 这意味着，在建议期间，如果没有可用的高权重优惠，则收件人将至少收到此类别的一个优惠。

要始终在推荐中包含类别，请应用以下步骤：

1. 打开资源管理器，然后单击树结构中的选件目录。
1. 单击 **[!UICONTROL Eligibility]** 按Tab键并勾选 **[!UICONTROL Always include this category in the recommendations]** 盒子。
1. 通过单击完成并批准 **[!UICONTROL Save]**.

   ![](assets/offer_cat_default_001.png)
