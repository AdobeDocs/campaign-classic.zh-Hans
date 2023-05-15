---
product: campaign
title: 关于活动类型
description: 关于活动类型
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Typology Rules
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 19%

---

# 关于活动类型{#about-campaign-typologies}

Campaign Optimization是Adobe Campaign模块，可让您控制、过滤和监控投放的发送。 为了避免活动之间发生冲突，Adobe Campaign 可以应用特定的限制规则来测试各种活动组合。这可确保所发送的邮件符合客户的需求与期望以及公司的通信政策。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#typologies-video)

>[!NOTE]
>
>根据您的产品，可以包含促销活动优化或加载项。 请核实您的许可协议。

## 类型规则 {#typology-rules}

借助Adobe Campaign，您可以设计并应用四种类型的分类规则：

* **筛选** 规则来排除部分目标。 有关更多信息，请参阅 [筛选规则](filtering-rules.md).
* **压力** 用于控制营销疲劳度的规则。 有关更多信息，请参阅 [压力规则](pressure-rules.md).
* **容量** 用于限制加载以保证最佳处理条件的规则。 有关更多信息，请参阅 [控制容量](consistency-rules.md#controlling-capacity).
* **控制** 规则，用于在发送消息之前检查消息的有效性。 有关更多信息，请参阅 [控制规则](control-rules.md).

创建分类规则后，会将其分组到营销活动分类中，并在投放中引用这些分类。 请参阅 [应用分类](#applying-typologies).

## 类型 {#typologies}

营销活动分类可以包含 [类型规则](#typology-rules)，但投放只能引用一种分类。

的 **[!UICONTROL Rules]** 选项卡，可添加、删除或查看要应用的分类规则。

![](assets/campaign_opt_rules_tab.png)

## 应用分类 {#applying-typologies}

下面列出了创建分类并将其应用于投放的步骤：

1. 创建分类规则。

   在 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 节点。

   以下部分介绍了Campaign中可用的不同规则： [销售压力规则](pressure-rules.md), [容量规则](consistency-rules.md#controlling-capacity), [控制规则](control-rules.md) 和 [筛选规则](filtering-rules.md).

1. 创建分类并在其中引用您创建的规则。

   可通过 **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** 节点。

1. 配置投放以使用您创建的分类。 如需详细信息，请参阅[此部分](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 通过促销活动模拟测试和控制行为。 有关促销活动模拟的更多信息，请参阅 [此部分](campaign-simulations.md).

在投放准备期间，如果满足标准，则会排除收件人。 您可以检查日志以监视排除情况。有关压力分类规则的示例用例，请参阅 [本页](pressure-rules.md#use-cases-on-pressure-rules).

## 教程视频 {#typologies-video}

### 如何使用类型学规则设置疲劳管理

此视频介绍如何利用分类规则在Adobe Campaign中实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用预定义过滤器设置疲劳管理

疲劳管理控制消息传送的频度和数量，以避免过度招徕收件人。如果您的促销活动实例中没有促销活动优化模块，则可以配置一个预定义的过滤器，该过滤器将按收到的消息数过滤目标群体。此视频介绍如何使用过滤器在Adobe Campaign Classic中实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

还提供其他Campaign操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).

**相关主题**

* [分类和疲劳管理入门](pressure-rules.md)

