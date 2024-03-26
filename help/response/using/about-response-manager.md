---
product: campaign
title: 关于响应管理器
description: 关于响应管理器
feature: Campaigns
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 4%

---

# Campaign响应管理器入门{#about-response-manager}



Adobe Campaign提供了响应管理附加功能，可让您衡量营销活动的成功性和盈利能力，还可提供跨通信渠道（电子邮件、移动设备、直邮等）的优惠建议。

## 假设验证 {#hypothesis-concept}

可以配置假设在从联系日期开始的给定时间段内推算接收投放后定向用户的行为。 这些假设基于 **交易** 保存购买和这些购买详细信息的表。

假设在时间上是有限的，并且可以应用于对照组以与目标群体进行比较。 假设验证结果由提供 **指示器** 计算完成后会自动更新的。 与假设相关的ROI将在营销活动报告中得到考虑。

此外， **报表** 通过响应管理器，您可以汇总与人员流动增长、利润率计算以及投放或优惠的ROI相关的信息。

此外，借助采购详细信息行，您可以将假设指定为仅关注一种特定产品（例如）。

例如，在投放促销项目后，我们希望评估生成的收入。 我们应用了一个假设，即任何在触发投放后的一个月内至少购买了一个项目的收件人已对此操作做出反应。 响应管理将根据此假设确定应将哪些采购请求行分配给它。 然后，基于此，将有可能确定所得的收入作为这些行的总和。

>[!CAUTION]
>
>响应管理器是 **[!UICONTROL Campaign]** 选项。 请核实您的许可协议。

您还可以计算收到投放或优惠的收件人的整个家庭的所有反应。

每个假设都与单个交易表相关联。 一个投放或选件可以链接到多个假设。

## 实施步骤 {#method}

在开始使用响应管理器之前，请参阅 [配置](configuration.md) 并执行必要的配置。

为了针对投放或优惠启动假设验证，您需要在模板中定义其上下文，该模板将用于您创建的每个假设验证。

要定义和创建衡量假设，请应用以下过程：

1. 定义假设验证模型。 [了解详情](hypothesis-templates.md#creating-a-hypothesis-model)
1. 对现有投放创建一个或多个假设验证。 [了解详情](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   或者

   对优惠创建一个或多个假设验证。 [了解详情](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 检查假设验证结果。 [了解详情](hypothesis-tracking.md)
1. 如有必要，重新启动假设验证。 [了解详情](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
