---
product: campaign
title: 关于活动类型
description: 关于活动类型
role: User, Data Engineer
feature: Typology Rules, Campaigns
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 16%

---

# 关于活动类型{#about-campaign-typologies}

Campaign Optimization是一个Adobe Campaign模块，可让您控制、过滤和监控投放的发送。 为了避免活动之间发生冲突，Adobe Campaign 可以应用特定的限制规则来测试各种活动组合。这可确保所发送的邮件符合客户的需求与期望以及公司的通信政策。

![](assets/do-not-localize/how-to-video.png) [通过观看视频了解此功能](#typologies-video)

>[!NOTE]
>
>根据您的产品/服务，可包含Campaign Optimization或附加组件。 请核实您的许可协议。

## 类型规则 {#typology-rules}

通过Adobe Campaign，您可以设计和应用四种类型的分类规则：

* **正在筛选**&#x200B;规则，该规则允许您根据条件排除部分目标。 有关详细信息，请参阅[筛选规则](filtering-rules.md)。
* 允许您控制营销疲劳的&#x200B;**压力**&#x200B;规则。 有关详细信息，请参阅[压力规则](pressure-rules.md)。
* **容量**&#x200B;规则，允许您限制负载以确保最佳处理条件。 有关详情，请参阅[控制容量](consistency-rules.md#controlling-capacity)。
* **控制**&#x200B;规则，允许您在发送消息之前检查消息的有效性。 有关详细信息，请参阅[控制规则](control-rules.md)。

创建后，分类规则将分组到在投放中引用的活动分类。 请参阅[应用分类](#applying-typologies)。

## 类型 {#typologies}

活动类型可以包含多个[类型规则](#typology-rules)，但投放只能引用一个类型。

**[!UICONTROL Rules]**&#x200B;选项卡允许您添加、删除或查看要应用的分类规则。

![](assets/campaign_opt_rules_tab.png)

## 应用分类 {#applying-typologies}

下面列出了创建分类并将其应用于投放的步骤：

1. 创建分类规则。

   在&#x200B;**[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**&#x200B;节点中找到分类规则。

   以下各节介绍了Campaign中可用的不同规则：[销售压力规则](pressure-rules.md)、[容量规则](consistency-rules.md#controlling-capacity)、[控制规则](control-rules.md)和[筛选规则](filtering-rules.md)。

1. 创建分类并在其中引用之前创建的规则。

   可通过&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;节点访问分类。

1. 配置投放以使用创建的分类。 如需详细信息，请参阅[此小节](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 通过活动模拟测试和控制行为。 有关活动模拟的详细信息，请参阅[此部分](campaign-simulations.md)。

在投放准备期间，当满足条件时，将排除收件人。 您可以检查日志以监控排除情况。 [此页面](pressure-rules.md#use-cases-on-pressure-rules)中提供了有关压力类型规则的示例用例。

## 教程视频 {#typologies-video}

### 如何使用类型规则设置疲劳管理

此视频介绍如何在Adobe Campaign中利用类型规则实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用预定义过滤器设置疲劳管理

疲劳管理控制消息传送的频度和数量，以避免过度招徕收件人。如果您的活动实例中没有活动优化模块，则可以配置一个预定义过滤器，以收到的消息数过滤目标群体
此视频介绍如何使用过滤器在Adobe Campaign Classic中实施疲劳管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign操作方法视频。

**相关主题**

* [类型和疲劳管理入门](pressure-rules.md)

