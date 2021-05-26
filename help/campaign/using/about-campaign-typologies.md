---
solution: Campaign Classic
product: campaign
title: 关于活动类型
description: 关于活动类型
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 12%

---

# 关于活动类型{#about-campaign-typologies}

<!--
>[!AVAILABILITY]
>
>:warning: This capability is not available in Campaign v8. [Learn more](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaign-home.html)
-->

Campaign Optimization是Adobe Campaign模块，可让您控制、过滤和监控投放的发送。 为了避免营销活动之间发生冲突，Adobe Campaign 可以应用特定的限制规则来测试各种活动组合。这样可确保发送的消息符合客户的需求和期望以及公司通信政策。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#typologies-video)

>[!NOTE]
>
>根据您的产品，可以包含促销活动优化或加载项。 请核实您的许可协议。

## 分类规则 {#typology-rules}

借助Adobe Campaign，您可以设计并应用四种类型的分类规则：

* **** 过滤规则，以便您根据条件排除部分目标。有关更多信息，请参阅[筛选规则](../../campaign/using/filtering-rules.md)。
* **** 压力规则，可让您控制营销疲劳度。有关更多信息，请参阅[压力规则](../../campaign/using/pressure-rules.md)。
* **** 允许您限制加载以确保最佳处理条件的容量规则。有关更多信息，请参见[控制容量](../../campaign/using/consistency-rules.md#controlling-capacity)。
* **** 控制规则，用于在发送消息之前检查消息的有效性。有关更多信息，请参阅[控制规则](../../campaign/using/control-rules.md)。

创建分类规则后，会将其分组到营销活动分类中，并在投放中引用这些分类。 请参阅[应用分类](#applying-typologies)。

## 分类 {#typologies}

营销活动分类可以包含多个[分类规则](#typology-rules)，但投放只能引用一个分类。

通过&#x200B;**[!UICONTROL Rules]**&#x200B;选项卡，可添加、删除或查看要应用的分类规则。

![](assets/campaign_opt_rules_tab.png)

## 应用分类{#applying-typologies}

下面列出了创建分类并将其应用于投放的步骤：

1. 创建分类规则。

   在&#x200B;**[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**&#x200B;节点中找到分类规则。

   以下部分介绍了Campaign中可用的不同规则：[销售压力规则](../../campaign/using/pressure-rules.md)、[容量规则](../../campaign/using/consistency-rules.md#controlling-capacity)、[控制规则](../../campaign/using/control-rules.md)和[筛选规则](../../campaign/using/filtering-rules.md)。

1. 创建分类并在其中引用您创建的规则。

   可通过&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;节点访问分类。

1. 配置投放以使用您创建的分类。 如需详细信息，请参阅[此部分](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)。
1. 通过促销活动模拟测试和控制行为。 有关促销活动模拟的更多信息，请参阅[此部分](../../campaign/using/campaign-simulations.md)。

在投放准备期间，如果满足标准，则会排除收件人。 您可以检查日志以监视排除情况。[此页面](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules)中提供了压力分类规则的示例用例。

## 教程视频 {#typologies-video}

### 如何使用类型学规则设置疲劳管理

此视频介绍如何利用分类规则在Adobe Campaign中实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用预定义过滤器设置疲劳管理

疲劳管理控制报文传送的频率和数量，以避免收件人过度请求。 如果您的促销活动实例中没有促销活动优化模块，则可以配置一个预定义过滤器，该过滤器将按收到的消息数过滤目标群体
此视频介绍如何使用过滤器在Adobe Campaign Classic中实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign操作方法视频。

**相关主题**

* [将自动业务规则应用于任何渠道上的投放](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [分类和疲劳管理入门](../../campaign/using/pressure-rules.md)

