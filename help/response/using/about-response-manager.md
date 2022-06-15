---
product: campaign
title: 关于响应管理器
description: 关于响应管理器
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: d36e1881726af6238c4e0caecb7b299b594691f2
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 13%

---

# 营销活动响应管理器入门{#about-response-manager}

![](../../assets/common.svg)

Adobe Campaign 提供响应管理附加功能，可让您衡量营销活动的成功性和盈利能力，还可提供跨通信渠道（电子邮件、移动设备、直邮等）的优惠建议。

## 假设 {#hypothesis-concept}

可以在从联系日期开始的给定时间段内配置假设，以推断那些在接收投放后被定向的行为。 这些假设是基于 **交易** 表格，可保存购买情况及购买详情。

假设在时间上是有限的，并且可以应用于控制组以与目标群体进行比较。 假设结果由 **指标** 计算完成后会自动更新的受众区段。 营销活动报告中将考虑与假设相关的ROI。

此外， **报告** 响应管理器提供的信息让您能够汇总与营业额增加、利润计算以及投放或优惠的ROI相关的信息。

此外，由于购买详细信息行，您可以指定假设以仅关注一个特定产品。

例如，在促销项目的投放后，我们希望评估所产生的收入。 我们应用假设，即在触发投放后的一个月中购买了至少一个物品的任何收件人都已对此操作做出反应。 响应管理将根据此假设确定应将哪些采购请求行分配给该假设。 然后，根据此，可以确定所得收入作为这些行的总和。

>[!CAUTION]
>
>响应管理器是 **[!UICONTROL Campaign]** 选项。 请核实您的许可协议。

您还可以计算收到该投放或优惠的收件人整个家庭的所有反应。

每个假设都与单个事务表关联。 一个投放或选件可以链接到多个假设验证。

## 实施步骤 {#method}

在开始使用响应管理器之前，请参阅 [配置](configuration.md) 并进行必要的配置。

要在投放或选件上启动假设验证，您需要在模板中定义其上下文，该上下文将用于您创建的每个假设验证。

要定义和创建测量假设，请应用以下过程：

1. 定义假设模型。 [了解详情](hypothesis-templates.md#creating-a-hypothesis-model)
1. 对现有投放创建一个或多个假设验证。 [了解详情](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   或者

   对选件创建一个或多个假设验证。 [了解详情](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 检查假设结果。 [了解详情](hypothesis-tracking.md)
1. 如有必要，可重新启动假设验证。 [了解详情](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
