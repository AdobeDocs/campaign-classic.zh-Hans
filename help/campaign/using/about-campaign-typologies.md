---
solution: Campaign Classic
product: campaign
title: 关于活动类型
description: 关于活动类型
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 12%

---


# 关于活动类型{#about-campaign-typologies}

活动优化是Adobe Campaign模块，它允许您控制、过滤和监控投放的发送。 为了避免营销活动之间发生冲突，Adobe Campaign 可以应用特定的限制规则来测试各种活动组合。这保证所发送的消息满足客户的需求和期望以及公司通信策略。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#typologies-video)

>[!NOTE]
>
>根据您的产品，可以包含活动优化或加载项。 请核实您的许可协议。

## 分类规则 {#typology-rules}

利用Adobe Campaign，您可以设计并应用四种类型规则:

* **过** 滤规则，允许您根据条件排除部分目标。有关详细信息，请参阅[筛选规则](../../campaign/using/filtering-rules.md)。
* **压** 力规则，让您控制营销疲劳。有关详细信息，请参阅[压力规则](../../campaign/using/pressure-rules.md)。
* **允许** 您限制负载以确保最佳处理条件的能力规则。有关详细信息，请参阅[控制容量](../../campaign/using/consistency-rules.md#controlling-capacity)。
* **控** 制规则，允许您在发送邮件之前检查其有效性。有关详细信息，请参阅[控制规则](../../campaign/using/control-rules.md)。

创建类型规则后，活动类型将分组，这些在投放中引用。 请参阅[应用类型](#applying-typologies)。

## 分类 {#typologies}

活动类型可以包含多个[类型规则](#typology-rules)，但投放只能引用一个类型。

使用&#x200B;**[!UICONTROL Rules]**&#x200B;选项卡可以添加、删除或视图要应用的类型规则。

![](assets/campaign_opt_rules_tab.png)

## 应用类型{#applying-typologies}

创建字体并将其应用于投放的步骤如下：

1. 创建类型规则。

   类型规则位于&#x200B;**[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**&#x200B;节点中。

   以下各节介绍了活动中的不同规则：[销售压力规则](../../campaign/using/pressure-rules.md)、[容量规则](../../campaign/using/consistency-rules.md#controlling-capacity)、[控制规则](../../campaign/using/control-rules.md)和[过滤规则](../../campaign/using/filtering-rules.md)。

1. 创建类型学并引用您在其中创建的规则。

   通过&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;节点访问类型。

1. 配置投放以使用您创建的排版。 如需详细信息，请参阅[此部分](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)。
1. 通过活动模拟测试和控制行为。 有关活动模拟的详细信息，请参阅[此部分](../../campaign/using/campaign-simulations.md)。

在准备投放时，在满足标准时排除收件人。 您可以检查日志以监视排除情况。[本页](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules)中提供压力类型规则的示例用例。

## 教程视频 {#typologies-video}

### 如何使用类型规则建立疲劳管理

此视频介绍如何通过利用类型规则在Adobe Campaign Classic实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用预定义过滤器建立疲劳管理

疲劳管理控制消息传递的频率和数量，以避免收件人过度请求。 如果您的活动实例中没有活动优化模块，您可以配置一个预定义的筛选器，该筛选器将按收到的消息数来筛选目标群
此视频介绍如何使用过滤器在Adobe Campaign Classic实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

此处[提供其他Campaign Classic操作方法视频。](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)

**相关主题**

* [将自动业务规则应用于任何投放的渠道](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [关于活动类型](../../campaign/using/pressure-rules.md)

* [使用压力规则管理营销疲劳](https://docs.adobe.com/content/help/en/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html)