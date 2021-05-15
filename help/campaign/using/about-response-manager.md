---
solution: Campaign Classic
product: campaign
title: 关于响应管理器
description: 关于响应管理器
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: dc3151a77350aa2b2acd989a57f5b489c1a98962
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 3%

---

# 开始使用活动 响应管理器{#about-response-manager}

Adobe Campaign优惠Response Management附加组件，可让您跨通信渠道衡量营销活动或优惠建议的成功和盈利能力：电子邮件、移动设备、直邮等

## 假设验证{#hypothesis-concept}

假设验证可以在从联系日期开始的给定时间段内配置，以推断在接收投放之后目标的行为。 这些假设验证基于&#x200B;**transaction**&#x200B;表，该表保存了购买情况和这些购买的详细信息。

假设验证时间有限，可应用于要与目标人口比较的对照组。 假设验证结果由&#x200B;**指示器**&#x200B;提供，这些指示器在计算完成后自动更新。 与假设验证相关的ROI将在活动报告中予以考虑。

此外，随响应管理器提供的&#x200B;**报表**&#x200B;使您能够汇总与营业额增加、利润计算以及投放或优惠的ROI相关的信息。

此外，由于购买详细信息行，您可以指定假设验证仅关注一个特定产品。

例如，在提升物料的投放之后，我们希望评估生成的收入。 我们应用假设验证，即在触发投放后的一个月中购买了至少一个物品的任何收件人都对此操作作出了反应。 响应管理将根据此假设验证确定应将哪些采购请求行分配给它。 然后，根据此，可以确定生成的收入作为这些行的总和。

>[!CAUTION]
>
>响应管理器是&#x200B;**[!UICONTROL Campaign]**&#x200B;选项。 请核实您的许可协议。

您还可以计算接收投放或优惠的整个收件人家庭的所有反应。

每个假设验证都链接到单个事务表。 一个投放或优惠可以链接到多个假设验证。

## 实施步骤 {#method}

在使用响应管理器进行开始之前，请参阅[Configuration](../../campaign/using/configuration.md)并执行必要的配置。

要在投放或优惠上启动假设验证，您需要在模板中定义其上下文，该上下文将用于您创建的每个假设验证。

要定义和创建测量假设验证，请应用以下流程：

1. 定义假设验证模型。 请参阅[创建假设验证模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 在现有假设验证上创建一个或多个投放。 请参阅[在活动投放中引用假设验证](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)。

   或者

   在优惠上创建一个或多个假设验证。 请参阅[在优惠](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer)上创建假设验证。

1. 检查假设验证结果。 请参阅[假设验证跟踪](../../campaign/using/hypothesis-tracking.md)。
1. 如有必要，重新启动假设验证。 请参阅[在投放上快速创建假设验证](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)。
