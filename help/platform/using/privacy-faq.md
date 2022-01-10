---
product: campaign
title: 隐私和同意
description: 进一步了解隐私和同意
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: ce2c90cd-46d9-4365-8013-5c1273b6c176
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 100%

---

# 隐私常见问题解答 {#privacy-faq}

![](../../assets/common.svg)

以下是使用 Adobe Campaign 时有关隐私和同意的一些常见问题解答。

## 关键术语 {#key-terms}

### 有关隐私的关键术语有哪些？

以下所列项目链接到与 Adobe Campaign 中的隐私和同意相关的关键术语和概念：

* [隐私管理法规](../../platform/using/privacy-management.md#privacy-management-regulations)
* [个人数据和角色](../../platform/using/privacy-and-recommendations.md#personal-data)
* [访问权与被遗忘权](../../platform/using/privacy-management.md#right-access-forgotten)
* [同意、保留和角色](../../platform/using/privacy-management.md#consent-retention-roles)

## 隐私法规就绪性 {#privacy-regulations-readiness}

### Adobe Campaign 关于遵守最新隐私法规的建议是什么？

Adobe 不提供法律建议。您应与您自己的法律顾问合作，以确保其采取所有必要措施为 GDPR、CCPA、PDPA、LGPD 或任何其他适用法规做准备。

**准备数据访问和删除请求**

* 确定接收/响应数据主体请求的流程，包括指定隐私联系人。

* 审查存储在 Adobe Campaign 中的各种客户数据并确定唯一标识符（可能有多个）。

* 确定确认数据主体身份的验证/身份验证策略和流程。

* 确保数据主体响应易于理解。

**考虑同意**

* 列出并根据需要更新 GDPR 数据捕获的所有接触点（即，考虑语言、同意机制和同意日志）。

* 确保所有营销电子邮件都包含取消订阅链接。

* 评估电子邮件营销的全球战略，以确定特定于地理位置的实施。

**了解数据**

* 审查数据流入 Adobe Campaign 的所有数据导入和捕获源，并记录哪些字段用于您的营销工作。

* 从 Adobe Campaign 数据库中删除任何未使用的数据属性。

* 使用 Adobe Campaign 中可用的数据获取捕获该数据的意图，并为收件人提供更好的个性化体验。

* 审查和更新数据访问权限，以帮助确保 Adobe Campaign 用户只能充分利用运行其营销活动所需的数据，但不能访问超出此范围的任何数据。

* 确保每个 Adobe Campaign 用户都具有相应的访问权限来执行其所需的任务，但没有用于执行其他任务的任何其他权限。

## 保持用户参与度 {#preserve-user-engagement}

### 数据控制者如何在对用户参与度影响最小的情况下获取同意？

在需要针对特定营销活动获得同意的情况下，消费者同意需要有效（即，无“沉默即同意”框或预选框）、未捆绑，并且不能有条件地提供服务。

甚至可能存在需要刷新某些同意才能继续使用数据的情况。

营销人员应该接受这些加强的同意要求，作为品牌互动和忠诚度以及客户满意度和信任度的真实指标。

## 管理同意 {#manage-consent}

### 数据控制者如何能够在 Adobe Campaign 中管理同意？

Adobe Campaign 已经提供通过自定义数据字段或通过一个或多个服务在比大多数营销人员所使用更多的级别管理同意的功能。

营销人员应咨询其法律顾问以获取有关如何继续的指导，然后利用已内置到 Adobe Campaign 的功能。

例如，扩展 Adobe Campaign 中的数据模型，从而不仅跟踪用户已选择加入的情况，还跟踪选择加入的时间戳，以及用于捕获确切同意范围的某类指标。

## 数据删除 {#data-deletion}

### 数据控制者可以删除 Adobe Campaign 中的哪些数据来响应数据主体的客户请求？

与数据主体关联的所有数据都将删除，包括现成表格和自定义表格。

技术上，链接到 `integrity="own"` 的数据主体的所有数据都将删除。

作为数据控制者，您可以选择通过更改数据模式中定义的链接的完整性来自定义此数据（例如，如果您有业务理由不删除某些数据）。

### 删除投放和跟踪日志后报告会受到什么影响？

Adobe Campaign 中的报告基于根据投放和跟踪日志中的汇总数据计算所得的指标。因此，删除个别日志应当不会影响报告中显示的指标。

## 重新导入数据 {#re-import-data}

### 我是否需要注意在以后某个日期可能重新导入数据？

在 Adobe Campaign 中，通常从外部数据源上传记录。

作为数据控制者，您将需要确保在收到删除请求时，从所有系统中删除有关数据主体的所有必要数据。

## 再次选择加入 {#opt-in-again}

### 其数据已从 Adobe Campaign 中清除的数据主体是否可以稍后再次选择加入？

数据主体可能再次选择加入，或者在从 Adobe Campaign 中删除其数据后添加为新收件人。

您可以使用审计跟踪，其中详细说明了上次删除的执行时间和新收件人的创建时间。
