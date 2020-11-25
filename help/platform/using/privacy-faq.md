---
solution: Campaign Classic
product: campaign
title: 隐私和同意
description: 进一步了解隐私和同意
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 9e31f69fde38dcdc7f4e6d3ba3fb17911f96ded8
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# 隐私常见问题解答 {#privacy-faq}

以下是使用Adobe Campaign时有关隐私和同意的常见问题。

## 主要条款 {#key-terms}

**隐私权的主要条款有哪些？**

以下所列项目链接到与Adobe Campaign中的隐私和同意相关的主要条款和概念：

* [隐私管理法规](../../platform/using/privacy-management.md#privacy-management-regulations)
* [个人数据和角色](../../platform/using/privacy-and-recommendations.md#personal-data)
* [访问权与被遗忘权](../../platform/using/privacy-management.md#right-access-forgotten)
* [同意、保留和角色](../../platform/using/privacy-management.md#consent-retention-roles)

## 隐私法规准备 {#privacy-regulations-readiness}

**Adobe Campaign关于遵守最新隐私法规的建议是什么？**

Adobe不提供法律建议。 您应与您自己的法律顾问合作，确保他们采取一切必要措施准备GDPR、CCPA、PDPA、LGPD或任何其他适用的法规。

**准备数据访问和删除请求**

* 确定接收／响应数据主体请求的流程，包括指定隐私联系人。

* 检查存储在Adobe Campaign中的各种客户数据并确定唯一标识符（可能有多个）。

* 确定确认数据主体身份的验证／身份验证策略和流程。

* 确保数据主体响应易于理解。

**考虑同意**

* 列表并根据需要更新GDPR数据捕获的所有接触点（即考虑语言、同意机制和同意日志）。

* 确保所有营销电子邮件都包含取消订阅链接。

* 评估电子邮件营销的全球战略，以确定特定于地理位置的实施。

**了解您的数据**

* 检查数据流入Adobe Campaign的所有数据导入和捕获源，并文档哪些字段用于您的营销工作。

* 从Adobe Campaign库中删除所有未使用的数据属性。

* 使用Adobe Campaign中可用的数据获取意图，为收件人提供更好的个性化体验。

* 检查和更新Adobe Campaign访问权限，以帮助确保活动用户能够完全利用运行数据所需的数据，但不能访问超出此范围的任何数据。

* 确保每个Adobe Campaign用户都有相应的访问权限来执行其所需的任务，但没有执行其他任务的任何其他权限。

## 保持用户参与度 {#preserve-user-engagement}

**数据管理者如何在获得同意的同时对用户参与度的影响最小？**

在需要特定营销活动同意的情况下，消费者同意必须是有效的（即，不要静默，如预设或预选框），取消捆绑，并且不得以提供服务为条件。

甚至有时，某些同意需要刷新才能继续使用数据。

营销人员不必将这些增强的同意要求视为市场空间的风险，而是将它们视为品牌参与度和忠诚度、客户满意度和信任的真正指标。

## 管理同意 {#manage-consent}

**Adobe Campaign管理者如何管理同意？**

Adobe Campaign已经提供了通过自定义数据字段或通过一个或多个服务在比大多数营销人员更高级别管理同意的功能。

营销人员应咨询其法律顾问，了解如何继续，然后利用已内置的Adobe Campaign功能。

例如，扩展Adobe Campaign中的数据模型，不仅跟踪用户已选择加入的情况，还跟踪选择加入的时间戳，以及捕获确切同意范围的某类指标。

## 数据删除 {#data-deletion}

**Adobe Campaign控制者可以根据数据主体的客户请求删除哪些数据？**

将删除与数据主体关联的所有数据，包括现成表格和自定义表格。

技术上，将删除与数据主体链接的所 `integrity="own"` 有数据。

作为数据控制者，您可以选择通过更改数据模式中定义的链接的完整性来自定义此数据（例如，如果您有业务理由不删除某些数据）。

**删除投放和跟踪日志时，报表受到什么影响？**

Adobe Campaign中的报告基于根据来自投放和跟踪日志的聚集数据计算的指标。 因此，删除单个日志不会影响报告中显示的度量。

## 重新导入数据 {#re-import-data}

**通常在Adobe Campaign中，记录从外部数据源上传。 我是否需要注意在以后某个日期可能重新导入数据？**

作为数据管理者，您需要确保在收到删除请求时，从所有系统中删除有关数据主体的所有必要数据。

## 选择加入 {#opt-in-again}

**数据主体(其数据已从Adobe Campaign中删除)是否可以稍后再次选择加入？**

数据主体可能再次选择加入，或在其收件人从Adobe Campaign中删除后作为新添加。

您可以使用审计跟踪，该跟踪跟踪在执行以前的删除操作以及创建新收件人时具有详细信息。