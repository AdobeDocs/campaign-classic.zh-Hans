---
title: 关于营销活动类型
seo-title: 关于营销活动类型
description: 关于营销活动类型
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 关于营销活动类型{#about-campaign-typologies}

营销活动优化是Adobe Campaign模块，可让您控制、过滤和监控分发的发送。 为了避免营销活动之间发生冲突，Adobe Campaign 可以应用特定的限制规则来测试各种活动组合。这可确保在遵守公司通信政策的同时，发送最符合客户需求及期望的邮件。

>[!NOTE]
>
>根据您的产品，可以包含营销活动优化或附加项。 请检查您的许可协议。

## 排版规则 {#typology-rules}

借助Adobe Campaign，您可以设计并应用四种类型的排版规则：

1. **筛选规则** ，允许您根据条件排除部分目标。 For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
1. **压力规则** ，让您能够控制营销疲劳。 For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
1. **容量规则** ，允许您限制负载以确保最佳处理条件。 For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
1. **控制规则** ，允许您在发送消息之前检查消息的有效性。 For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

一旦创建了这些规则，类型学规则就会按营销活动类型进行分组，这些类型在分发中引用。 请参 [阅应用类型](#applying-typologies)。

## 类型 {#typologies}

营销活动类型学可以包含多 [个类型学规则](#typology-rules)，但交付只能引用一个类型学。

通过 **[!UICONTROL Rules]** 该选项卡可以添加、删除或查看要应用的排版规则。

![](assets/campaign_opt_rules_tab.png)

## 应用类型 {#applying-typologies}

创建字体并将其应用到交付的步骤如下：

1. 创建排版规则。

   在节点中可找到排版 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 规则。

   以下部分介绍了营销活动中可用的不同规则：销售 [压力规则](../../campaign/using/pressure-rules.md)，容 [量规则](../../campaign/using/consistency-rules.md#controlling-capacity), [控制规则](../../campaign/using/control-rules.md) , [过](../../campaign/using/filtering-rules.md)滤规则

1. 创建一种类型学，并参考您在其中创建的规则。

   可通过 **[!UICONTROL Administration > Campaign Management > Typology management]** >节点访 **[!UICONTROL Typologies]** 问类型。

1. 配置您的交付以使用您创建的排版。 如需详细信息，请参阅[此部分](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)。
1. 通过营销活动模拟测试和控制行为。 For more on campaign simulations, refer to [this section](../../campaign/using/campaign-simulations.md).

在交付准备过程中，当满足标准时，收件人将被排除。 您可以检查日志以监视排除。 本页提供了有关压力类型规则的示 [例用例](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules)。

**相关主题**

* [将自动业务规则应用于任何渠道上的分发](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)