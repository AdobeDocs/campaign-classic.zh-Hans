---
title: 关于响应管理器
seo-title: 关于响应管理器
description: 关于响应管理器
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 关于响应管理器{#about-response-manager}

## 目标 {#objectives}

Adobe Campaign提供了响应管理应用程序（响应管理器），可让您衡量营销活动的成功和盈利能力，或为所有通信渠道（电子邮件、移动设备、电话、直邮、传真、代理等）提供建议。

## 假设概念 {#hypothesis-concept}

可以在从接触日期开始的给定时间段内配置假设，以推断在收到递送之后被定位的那些行为。 这些假设基于保存购 **买的事务** 表以及这些购买的详细信息。

假设在时间上是有限的，并且可以应用于控制组以与目标群体进行比较。 假设结果由一旦计 **算完成** ，就自动更新的指示器提供。 营销活动报告中将考虑与这些假设相关的投资回报率。

此外，随响 **应管理器提供的报表** ，使您能够汇总与营业额增加、利润计算以及交付或优惠的ROI相关的信息。

此外，由于购买详细信息行，您可以指定假设以仅关注一个特定产品。

例如，在提升物料的交付之后，我们希望评估生成的收入。 我们应用假设，即在触发交付后的一个月中购买了至少一件物品的任何接收者都对此行为做出反应。 响应管理将根据此假设确定应为其分配哪些采购请求行。 然后，根据这一点，可以确定这些行的总和作为最终收入。

>[!CAUTION]
>
>响应管理器是一个 **[!UICONTROL Campaign]** 选项。 请检查您的许可协议。

您还可以计算接收送货或优惠的整个接收者家庭的所有反应。

每个假设都与单个事务表相关联。 一个交付或报价可以链接到多个假设。

## 方法 {#method}

在开始使用Response Manager之前，请参阅 [配置](../../campaign/using/configuration.md) ，并执行必要的配置。

为了在交付或选件上启动假设，您需要在模板中定义其上下文，该上下文将用于您创建的每个假设。

要定义和创建测量假设，请应用以下过程：

1. 定义假设模型。 请参阅 [创建假设模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 在现有交付上创建一个或多个假设。 请参阅在 [营销活动交付中引用假设](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)。

   或

   创建关于选件的一个或多个假设。 请参阅 [创建选件假设](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer)。

1. 检查假设结果。 请参阅假 [说跟踪](../../campaign/using/hypothesis-tracking.md)。
1. 如有必要，重新发布假设。 请参阅 [在交货时即时创建假设](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)。

