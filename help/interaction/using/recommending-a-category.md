---
product: campaign
title: 推荐类别
description: 推荐类别
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cb062cb2-dfea-46aa-8d9e-580e4dc7bb25
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 5%

---

# 推荐类别{#recommending-a-category}

![](../../assets/v7-only.svg)

收件人可能被认为不符合所有选件的条件。 为了确保所有收件人都收到优惠建议，可以在推荐中系统地添加一个或多个优惠类别。 与主选件不同，这些“备用”选件的权重必须较低（但不为零），因此只有在没有高权重选件符合条件时，才会考虑这些选件。 此外，不得对这些选件应用任何展示规则，以确保始终将它们包含在推荐中。 这意味着，在提出建议期间，如果没有高权重选件可用，则收件人将至少收到此类别中的一个选件。

要在推荐中始终包含类别，请应用以下步骤：

1. 打开资源管理器，然后单击树结构中的选件目录。
1. 单击 **[!UICONTROL Eligibility]** 勾选 **[!UICONTROL Always include this category in the recommendations]** 框中。
1. 通过单击完成和批准 **[!UICONTROL Save]**.

   ![](assets/offer_cat_default_001.png)
