---
solution: Campaign Classic
product: campaign
title: 关于响应管理器
description: 关于响应管理器
audience: campaign
content-type: reference
topic-tags: response-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---


# 关于响应管理器{#about-response-manager}

## 目标 {#objectives}

Adobe Campaign优惠一个响应管理应用程序(响应管理器)，它允许您衡量所有通信渠道（电子邮件、移动设备、电话、直邮、传真、代理等）的营销活动或优惠建议的成功和盈利能力。

## 假设验证概念 {#hypothesis-concept}

假设验证可以在从联系日期开始的给定时间段内进行配置，以推断在收到投放后目标用户的行为。 这些假设验证基于保存 **购买** 的事务表以及这些购买的详细信息。

假设验证时间有限，可应用于对照组以与目标人口进行比较。 假设验证结果由一 **旦计算** 完成，将自动更新的指示器提供。 与假设验证相关的ROI将在活动报告中予以考虑。

此外，通 **过响应管理器** 提供的报表，您可以汇总与营业额增加、利润计算以及投放或优惠的ROI相关的信息。

此外，由于有了购买详细信息行，您可以指定假设验证只关注一个特定产品。

例如，在投放提升项目后，我们希望评估生成的收入。 我们应用假设验证，在触发投放后的一个月内购买了至少一件物品的任何收件人都对此操作作出了反应。 响应管理将根据此假设验证确定应为其分配哪些采购请求行。 然后，根据这一点，可以确定生成的收入作为这些行的总和。

>[!CAUTION]
>
>响应管理器是一个 **[!UICONTROL Campaign]** 选项。 请核实您的许可协议。

您还可以计算整个收件人家庭收到投放或优惠的所有反应。

每个假设验证都链接到单个事务表。 一个投放或优惠可以链接到多个假设验证。

## Method {#method}

在使用开始之前，请参 [阅](../../campaign/using/configuration.md) “配置”并执行必要的配置。

要在投放或优惠上启动假设验证，您需要在模板中定义其上下文，该上下文将用于您创建的每个假设验证。

要定义和创建度量假设验证，请应用以下流程：

1. 定义假设验证模型。 请参阅 [创建假设验证模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 在现有假设验证上创建一个或多个投放。 请参阅 [在假设验证投放中引用活动](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)。

   或者

   在优惠上创建一个或多个假设验证。 请参阅 [在优惠上创建假设验证](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer)。

1. 检查假设验证结果。 请参阅 [假设验证跟踪](../../campaign/using/hypothesis-tracking.md)。
1. 如有必要，重新启动假设验证。 请参 [阅在假设验证上动态创建投放](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)。

