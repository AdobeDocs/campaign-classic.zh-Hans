---
title: 关于活动类型
seo-title: 关于活动类型
description: 关于活动类型
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
source-git-commit: e97183256ef6d3f2068dd0fbc8eb3c3f32e0bae0
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 6%

---


# 关于活动类型{#about-campaign-typologies}

活动优化是Adobe Campaign模块，它允许您控制、过滤和监控投放的发送。 为了避免营销活动之间发生冲突，Adobe Campaign 可以应用特定的限制规则来测试各种活动组合。这保证所发送的消息满足客户的需求和期望以及公司通信策略。

>[!NOTE]
>
>根据您的产品，可以包含活动优化或加载项。 请检查您的许可协议。

## 类型规则 {#typology-rules}

利用Adobe Campaign，您可以设计并应用四种类型规则:

* **筛选规则** ，允许您根据条件排除部分目标。 For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
* **压力规则** ，让您能够控制营销疲劳。 For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
* **容量规则** ，允许您通过限制负载来保证最佳处理条件。 For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
* **控制规则** ，允许您在发送邮件之前检查邮件的有效性。 For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

创建类型规则后，活动类型将分组，这些在投放中引用。 请参 [阅应用排版](#applying-typologies)。

## 类型 {#typologies}

活动类型可以包含多 [个类型规则](#typology-rules)，但投放只能引用一种类型。

在选 **[!UICONTROL Rules]** 项卡中可以添加、删除或视图要应用的类型规则。

![](assets/campaign_opt_rules_tab.png)

## 应用类型 {#applying-typologies}

创建字体并将其应用于投放的步骤如下：

1. 创建类型规则。

   类型规则在节点中 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 找到。

   以下各节介绍了活动中的不同规则： [销售压力规则](../../campaign/using/pressure-rules.md)、 [容量规则](../../campaign/using/consistency-rules.md#controlling-capacity)、 [控制规则](../../campaign/using/control-rules.md)[和过](../../campaign/using/filtering-rules.md)滤规则。

1. 创建类型学并引用您在其中创建的规则。

   通过>节点访 **[!UICONTROL Administration > Campaign Management > Typology management]** 问 **[!UICONTROL Typologies]** 字体。

1. 配置投放以使用您创建的排版。 如需详细信息，请参阅[此部分](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)。
1. 通过活动模拟测试和控制行为。 For more on campaign simulations, refer to [this section](../../campaign/using/campaign-simulations.md).

在准备投放时，在满足标准时排除收件人。 您可以检查日志以监视排除。 本页提供压力类型规则的示 [例用例](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules)。

**相关主题**

* [将自动业务规则应用于任何投放的渠道](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)