---
title: 实施步骤
seo-title: 实施步骤
description: 实施步骤
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 实施步骤{#implementation-steps}

## 配置交互 {#configuring-interaction}

>[!NOTE]
>
>以下步骤应由管理员配置文件 **执行** ，并且仅在设计环境中执行。

1. 创建用户配置文件。 For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).
1. 通过定位维度创建选件环境。 有关详细信息，请参阅 [创建选件环境](../../interaction/using/live-design-environments.md#creating-an-offer-environment)。
1. 为每个环境创建排版规则。 有关详细信息，请参阅创 [建和引用选件演示规则](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)。
1. 为每个环境创建选件空间并配置渲染功能。 有关此内容的详细信息，请参阅 [创建选件空间](../../interaction/using/creating-offer-spaces.md)。

   >[!NOTE]
   >
   >如果空间由标识模式上的酉通道定义，则必须为此空间指定高级参数。

1. 为入站交互配置选件引擎，以展示和更新一个或多个选件。

   关于入站渠道中详细介绍了各 [种集成模式](../../interaction/using/about-inbound-channels.md)。

   >[!NOTE]
   >
   >在入站Web渠道上创建空间后，还需要在要显示选件的站点上进行配置。

## 管理选件目录 {#managing-the-offer-catalog-}

>[!NOTE]
>
>选件管理者应执行以下 **步骤**。

1. 在设计环境中创建选件类别。 有关此信息的详细信息，请参阅创 [建选件类别](../../interaction/using/creating-offer-categories.md)。
1. 在设计环境中创建选件。 有关详细信息，请参阅 [创建选件](../../interaction/using/creating-an-offer.md)。
1. 在一个或多个空间上批准和发布选件，以便在实时环境中为交付管理器提供。 有关详细信息，请参 [阅批准和激活选件](../../interaction/using/approving-and-activating-an-offer.md)。

## 使用选件目录 {#using-the-offer-catalog-}

>[!NOTE]
>
>以下步骤应由交付管理器配置 **文件执行** 。 他们只能在实时环境中编辑选件。

1. 创建营销活动。
1. 在营销活动或营销活动分发中引用选件。 有关详细信息，请参阅关于 [出站渠道](../../interaction/using/about-outbound-channels.md)。

