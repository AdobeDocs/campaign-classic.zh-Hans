---
product: campaign
title: 关于响应管理器
description: 关于响应管理器
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 13%

---

# Campaign响应管理器入门{#about-response-manager}



Adobe Campaign 提供响应管理附加功能，可让您衡量营销活动的成功性和盈利能力，还可提供跨通信渠道（电子邮件、移动设备、直邮等）的优惠建议。

## 假设验证 {#hypothesis-concept}

可以配置假设在从联系日期开始的给定时间段内推断接收投放后目标受众的行为。 这些假设基于 **事务** 保存购买和这些购买详细信息的表。

假设在时间上是有限的，可以应用于控制组并与目标群体进行比较。 假设验证结果由提供 **指示器** 计算完成后会自动更新的属性。 与假设相关联的ROI将在营销活动报告中得到考虑。

此外， **报告** 通过响应管理器，您可以汇总与人员调整增长、利润计算以及投放或优惠的ROI相关的信息。

此外，借助采购详细信息行，您可以指定假设以仅关注一种特定产品，例如。

例如，在促销某个项目的投放之后，我们希望评估生成的收入。 我们应用以下假设：任何在触发投放后的一个月内购买至少一件物品的收件人已对此操作做出反应。 响应管理将根据此假设确定应将哪些采购请求行分配给它。 然后，基于此，将有可能确定所得的收入作为这些行的总和。

>[!CAUTION]
>
>响应管理器是 **[!UICONTROL Campaign]** 选项。 请核实您的许可协议。

您还可以计算接收投放或优惠的收件人的整个家庭的所有反应。

每个假设验证都链接到单个事务表。 一个投放或选件可以链接到多个假设验证。

## 实施步骤 {#method}

在开始使用响应管理器之前，请参阅 [配置](configuration.md) 并执行必要的配置。

为了针对投放或优惠启动假设验证，您需要在模板中定义其上下文，该模板将用于您创建的每个假设验证。

要定义和创建度量假设，请应用以下过程：

1. 定义假设验证模型。 [了解详情](hypothesis-templates.md#creating-a-hypothesis-model)
1. 在现有投放中创建一个或多个假设验证。 [了解详情](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   或者

   对优惠创建一个或多个假设验证。 [了解详情](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 检查假设验证结果。 [了解详情](hypothesis-tracking.md)
1. 如有必要，请重新启动假设验证。 [了解详情](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
