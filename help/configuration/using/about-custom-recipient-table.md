---
title: 关于自定义收件人表
seo-title: 关于自定义收件人表
description: 关于自定义收件人表
seo-description: null
page-status-flag: never-activated
uuid: 4b162da4-90d2-44ff-9f89-ff0275540359
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: c3ff8462-e47e-4637-8213-769fdeb86a57
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 2%

---


# 关于自定义收件人表{#about-custom-recipient-table}

本节详细介绍使用非标准收件人表的原则。

默认情况下，Adobe Campaign优惠标准收件人表，现成功能和进程链接到该表。 标准收件人表具有许多预定义的字段和表，这些字段和表可以使用扩展表轻松扩展。

如果此扩展方法优惠了扩展表的良好灵活性，则不允许减少表中的字段或链接数。 使用非标准表或“外部收件人表”可以获得更大的灵活性，但在实施时需要一定的预防措施。

## 精确度 {#precisions}

此功能允许Adobe Campaign处理来自外部数据库的数据：此用户档案将用作投放的一组数据。 实施此过程涉及一些可能与客户需求相关的精确度。 例如：

* 没有Adobe Campaign库的更新流：来自此表的数据可以直接通过承载该表的数据库引擎进行更新。
* 现有数据库上操作的进程中没有更改。
* 使用非标准结构的用户档案库：使用单个实例，可能将保存在具有各种结构的各种表中的用户档案传送到。
* 更新Adobe Campaign库时，无需更改或维护。
* 如果您不需要大多数表字段或收件人库模板不是位于收件人的中心，则标准表是无用的。
* 为了提高效率，如果您有大量用户档案，则需要具有少量字段的表。 标准收件人表包含的字段太多，以适合此特定情况。

本节介绍可以映射Adobe Campaign中现有表的关键点，以及要应用于根据任何表执行投放的配置。 最后，介绍了如何向用户提供与标准收件人表一样实用的查询界面。 要了解本节介绍的材料，需要充分了解屏幕和模式设计的原则。

## Recommendations和限制 {#recommendations-and-limitations}

使用外部收件人表具有以下限制：

* Adobe Campaign不支持链接到相同广播和／或跟踪日志模式的多个收件人模式(称为定位模式)。 否则，这可能导致之后的数据协调出现异常。

   下图详细描述了每个自定义收件人模式所需的关系结构：
   ![](assets/custom_recipient_limitation.png)

   我们建议：

   * 为开 **[!UICONTROL nms:BroadLogRcp]** 箱即 **[!UICONTROL nms:TrackingLogRcp]** 用的模式注入活力 **[!UICONTROL nms:Recipientschema]**。 这两个日志表不应链接到任何其他自定义收件人表。
   * 为每个新的自定义模式模式定义专用的自定义广告和跟踪日志收件人。 这可以在设置目标映射时自动完成，请参阅 [目标映射](../../configuration/using/target-mapping.md)。

* 您不能使用产品 **[!UICONTROL Services and Subscriptions]** 中提供的标准。

   这意味着本条所述的整 [体操作](../../delivery/using/managing-subscriptions.md) 不适用。

* 与表的链接 **[!UICONTROL visitor]** 不起作用。

   因此，要使用 **[!UICONTROL Social Marketing]** 模块，必须配置存储步骤以引用正确的表。

   同样，在使用引用功能时，必须调整标准初始消息传输模板。

* 不能手动在用户档案中添加列表。

   因此，如果没有其他配 [置](../../platform/using/creating-and-managing-lists.md) ，本节中详述的过程将不适用。

   >[!NOTE]
   >
   >您仍可以使用收件人创建列表。 有关此内容的详细信息，请 [参阅使用工作流创建用户档案列表](../../configuration/using/creating-a-profile-list-with-a-workflow.md)。

我们还建议检查不同现成配置中使用的默认值：根据所使用的功能，必须进行若干适应。

例如：

* 必须重新开发某些标准报告， **特别是** Interaction和 **Mobile Application** 提供的报告。 请参阅管理 [报告](../../configuration/using/managing-reports.md) 部分。
* 某些工作流活动的默认配置引用标准收件人表(**[!UICONTROL nms:recipient]**):当用于外部收件人表时，必须更改这些配置。 请参阅管理 [工作流](../../configuration/using/managing-workflows.md) 部分。
* 必须调整 **[!UICONTROL Unsubscription link]** 标准个性化基块。
* 必须修改标准投放模板的目标映射。
* V4表单与外部收件人表格不兼容：你必须使用Web 应用程序。

