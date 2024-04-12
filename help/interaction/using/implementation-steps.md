---
product: campaign
title: 实施步骤
description: Campaign交互模块的实施步骤
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 1%

---

# 实施步骤{#implementation-steps}



## 配置交互 {#configuring-interaction}

>[!NOTE]
>
>以下步骤应由用户执行 **管理员** 配置文件和仅在设计环境中。

1. 创建用户配置文件。 有关详细信息，请参见 [操作员用户档案](../../interaction/using/operator-profiles.md).
1. 通过定位维度创建选件环境。 有关详细信息，请参见 [创建优惠环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. 为每个环境创建分类规则。 有关详细信息，请参见 [创建和引用优惠呈现规则](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. 为每个环境创建选件空间并配置渲染函数。 有关详细信息，请参见 [创建优惠空间](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >如果空间由标识模式上的单一通道定义，则必须为此空间指定高级参数。

1. 为入站交互配置优惠引擎，以显示和更新一个或多个优惠。

   有关各种集成模式的详情，请参见 [关于入站渠道](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >在入站Web渠道上创建空间时，还需要在要显示优惠的网站上进行配置。

## 管理优惠目录 {#managing-the-offer-catalog-}

>[!NOTE]
>
>以下步骤应由用户执行 **选件管理器**.

1. 在设计环境中创建优惠类别。 有关详细信息，请参见 [创建优惠类别](../../interaction/using/creating-offer-categories.md).
1. 在设计环境中创建选件。 有关详细信息，请参见 [创建优惠](../../interaction/using/creating-an-offer.md).
1. 在一个或多个空间上批准和发布选件，以便在投放管理器的实时环境中可用。 有关详细信息，请参见 [批准和激活优惠](../../interaction/using/approving-and-activating-an-offer.md).

## 使用优惠目录 {#using-the-offer-catalog-}

>[!NOTE]
>
>以下步骤应由执行 **投放管理器** 个人资料。 他们只能在实时环境中编辑选件。

1. 创建活动。
1. 在营销活动或营销活动投放中引用优惠。 有关详细信息，请参见 [关于出站渠道](../../interaction/using/about-outbound-channels.md).
