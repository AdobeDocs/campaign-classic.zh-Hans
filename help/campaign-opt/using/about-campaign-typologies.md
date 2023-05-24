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

Campaign Optimization是一个Adobe Campaign模块，您可以通过它控制、过滤和监控投放的发送。 为了避免活动之间发生冲突，Adobe Campaign 可以应用特定的限制规则来测试各种活动组合。这可确保所发送的邮件符合客户的需求与期望以及公司的通信政策。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#typologies-video)

>[!NOTE]
>
>根据您的产品/服务，可包含Campaign Optimization或附加组件。 请核实您的许可协议。

## 类型规则 {#typology-rules}

借助Adobe Campaign，您可以设计和应用四种类型的分类规则：

* **正在筛选** 允许您根据条件排除部分目标的规则。 有关更多信息，请参阅 [筛选规则](filtering-rules.md).
* **压力** 可让您控制营销疲劳的规则。 有关更多信息，请参阅 [压力规则](pressure-rules.md).
* **容量** 允许您限制负载以确保最佳处理条件的规则。 有关更多信息，请参阅 [控制容量](consistency-rules.md#controlling-capacity).
* **控制** 允许您在发送消息之前检查消息有效性的规则。 有关更多信息，请参阅 [控制规则](control-rules.md).

创建分类规则后，这些规则会按投放中引用的活动分类进行分组。 参见 [应用分类](#applying-typologies).

## 类型 {#typologies}

活动类型可以包含多个 [类型规则](#typology-rules)，但投放只能引用一种分类。

此 **[!UICONTROL Rules]** 选项卡允许您添加、删除或查看要应用的分类规则。

![](assets/campaign_opt_rules_tab.png)

## 应用分类 {#applying-typologies}

下面列出了创建分类并将其应用于投放的步骤：

1. 创建分类规则。

   分类规则可在 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 节点。

   以下各节介绍了Campaign中可用的不同规则： [销售压力规则](pressure-rules.md)， [容量规则](consistency-rules.md#controlling-capacity)， [控制规则](control-rules.md) 和 [筛选规则](filtering-rules.md).

1. 创建分类并在其中引用之前创建的规则。

   可通过访问分类 **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** 节点。

1. 配置投放以使用创建的分类。 如需详细信息，请参阅[此部分](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 通过活动模拟测试和控制行为。 有关促销活动模拟的详细信息，请参阅 [本节](campaign-simulations.md).

在投放准备期间，如果满足标准，则会排除收件人。 您可以检查日志以监视排除情况。有关压力类型规则的示例用例，请参见 [此页面](pressure-rules.md#use-cases-on-pressure-rules).

## 教程视频 {#typologies-video}

### 如何使用类型规则设置疲劳管理

此视频介绍如何在Adobe Campaign中利用类型规则实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用预定义过滤器设置疲劳管理

疲劳管理控制消息传送的频度和数量，以避免过度招徕收件人。如果您的营销活动实例中没有营销活动优化模块，则可以配置一个预定义过滤器，该过滤器将根据收到的消息数过滤目标群体。本视频介绍如何使用过滤器在Adobe Campaign Classic中实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

提供了其他Campaign操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).

**相关主题**

* [类型和疲劳管理入门](pressure-rules.md)

