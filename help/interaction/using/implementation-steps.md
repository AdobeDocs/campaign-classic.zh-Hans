---
solution: Campaign Classic
product: campaign
title: 实施步骤
description: 实施步骤
audience: interaction
content-type: reference
topic-tags: general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 2%

---


# 实施步骤{#implementation-steps}

## 配置交互 {#configuring-interaction}

>[!NOTE]
>
>以下步骤应由管理员 **用户档案** (仅在设计环境)执行。

1. 创建用户用户档案。 For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).
1. 按优惠创建环境。 有关此内容的详细信息，请参 [阅创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。
1. 为每个类型规则创建环境。 有关此内容的详细信息，请 [参阅创建和引用优惠推荐规则](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)。
1. 为每个优惠空间创建环境并配置渲染功能。 有关此内容的详细信息，请参阅 [创建优惠空间](../../interaction/using/creating-offer-spaces.md)。

   >[!NOTE]
   >
   >如果空间由标识模式上的酉渠道定义，则必须指定此空间的高级参数。

1. 为入站交互配置优惠引擎，以展示和更新一个或多个优惠。

   有关入站渠道中详细介绍了 [各种集成模式](../../interaction/using/about-inbound-channels.md)。

   >[!NOTE]
   >
   >在入站Web渠道上创建空间时，在要显示优惠的站点上也需要配置。

## Managing the offer catalog {#managing-the-offer-catalog-}

>[!NOTE]
>
>优惠管理者应执行以下 **步骤**。

1. 在设计优惠中创建类别。 有关此内容的详细信息，请参阅 [创建优惠类别](../../interaction/using/creating-offer-categories.md)。
1. 在设计优惠中创建环境。 有关此内容的详细信息，请参 [阅创建优惠](../../interaction/using/creating-an-offer.md)。
1. 在一个或多个空间上批准和发布优惠，以便让投放管理者在实时环境上访问它们。 有关此内容的详细信息，请 [参阅批准和激活优惠](../../interaction/using/approving-and-activating-an-offer.md)。

## 使用优惠目录 {#using-the-offer-catalog-}

>[!NOTE]
>
>以下步骤应由投放管理 **器用户档案执行** 。 他们只能在实时优惠中编辑环境。

1. 创建活动。
1. 在活动或优惠投放中引用活动。 有关此内容的详细信息，请参 [阅关于出站渠道](../../interaction/using/about-outbound-channels.md)。

