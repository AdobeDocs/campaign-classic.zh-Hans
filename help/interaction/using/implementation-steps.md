---
product: campaign
title: 实施步骤
description: 实施步骤
audience: interaction
content-type: reference
topic-tags: general-operation
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 2%

---

# 实施步骤{#implementation-steps}

![](../../assets/v7-only.svg)

## 配置交互 {#configuring-interaction}

>[!NOTE]
>
>以下步骤应由&#x200B;**Administrator**&#x200B;配置文件执行，并且只应在设计环境中执行。

1. 创建用户配置文件。 有关更多信息，请参阅[运算符配置文件](../../interaction/using/operator-profiles.md)。
1. 通过定向维度创建选件环境。 有关更多信息，请参阅[创建选件环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。
1. 为每个环境创建分类规则。 有关更多信息，请参阅[创建和引用选件演示规则](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)。
1. 为每个环境创建选件空间并配置渲染功能。 有关更多信息，请参阅[创建选件空间](../../interaction/using/creating-offer-spaces.md)。

   >[!NOTE]
   >
   >如果空间由标识模式上的单一渠道定义，则必须为此空间指定高级参数。

1. 为集客交互配置选件引擎，以便显示和更新一个或多个选件。

   [关于入站渠道](../../interaction/using/about-inbound-channels.md)中详细介绍了各种集成模式。

   >[!NOTE]
   >
   >在集客Web渠道上创建空间后，还需要在要显示选件的网站上进行配置。

## 管理优惠目录 {#managing-the-offer-catalog-}

>[!NOTE]
>
>**选件管理器**&#x200B;应执行以下步骤。

1. 在设计环境中创建选件类别。 有关更多信息，请参阅[创建选件类别](../../interaction/using/creating-offer-categories.md)。
1. 在设计环境中创建选件。 有关更多信息，请参阅[创建选件](../../interaction/using/creating-an-offer.md)。
1. 在一个或多个空间上批准和发布选件，以便它们在实时环境中可供投放管理器使用。 有关更多信息，请参阅[批准和激活选件](../../interaction/using/approving-and-activating-an-offer.md)。

## 使用优惠目录 {#using-the-offer-catalog-}

>[!NOTE]
>
>**投放管理器**&#x200B;配置文件应执行以下步骤。 他们只能在实时环境中编辑选件。

1. 创建营销活动。
1. 在营销活动或营销活动投放中引用选件。 有关更多信息，请参阅[关于出站渠道](../../interaction/using/about-outbound-channels.md)。
