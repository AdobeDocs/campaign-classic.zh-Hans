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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 668a0093616e1a2b49623b010ae5055f4d43d9b9

---


# 关于自定义收件人表{#about-custom-recipient-table}

本节详细介绍了使用非标准收件人表的原则。

默认情况下，Adobe Campaign提供一个标准收件人表，现成功能和流程均链接到该表。 标准收件人表具有许多预定义的字段和表，这些字段和表可以使用扩展表方便地扩展。

如果此扩展方法提供了很好的灵活性来扩展表，则不允许减少表中的字段或链接数。 使用非标准表（即“外部收件人表”）可以获得更大的灵活性，但在实施时需要一定的预防措施。

## 精确度 {#precisions}

此功能允许Adobe Campaign处理来自外部数据库的数据：此数据将用作一组提交配置文件。 实施此过程涉及根据客户需求可能相关的多个精确度。 例如：

* 没有Adobe Campaign数据库的更新流：此表中的数据可以直接通过承载该表的数据库引擎进行更新。
* 对现有数据库操作的进程没有更改。
* 使用非标准结构的配置文件数据库：使用单个实例，可能将保存在具有各种结构的各种表中的配置文件传送到。
* 更新Adobe Campaign数据库时，无需进行任何更改或维护。
* 如果您不需要大多数表字段或数据库模板不是位于收件人的中心，则标准收件人表是无用的。
* 为了提高效率，如果您有大量配置文件，则需要一个字段较少的表。 标准收件人表格包含的字段太多，以适合此特定情况。

本节介绍了用于映射Adobe Campaign中现有表的关键点，以及要应用于根据任何表执行分发的配置。 最后，介绍了如何向用户提供与标准收件人表一样实用的查询界面。 要了解本节介绍的材料，需要充分了解屏幕和模式设计的原则。

## 建议和限制 {#recommendations-and-limitations}

使用外部收件人表具有以下限制：

* Adobe Campaign不支持链接到相同广播和／或跟踪日志架构的多个收件人架构（称为定位架构）。 否则，这可能导致以后数据协调中的异常。

   下图详细描述了每个自定义收件人架构所需的关系结构：
   ![](assets/custom_recipient_limitation.png)

   我们建议：

   * 将 **[!UICONTROL nms:BroadLogRcp]** 和 **[!UICONTROL nms:TrackingLogRcp]** 架构专门用于开箱即用型 **[!UICONTROL nms:Recipientschema]**。 这两个日志表不应链接到任何其他自定义收件人表。
   * 为每个新的自定义收件人架构定义专用的自定义广播和跟踪日志架构。 在设置目标映射时可以自动完成此操作，请参阅 [Target映射](../../configuration/using/target-mapping.md)。

* 您不能使用产品 **[!UICONTROL Services and Subscriptions]** 中提供的标准。

   这意味着本节中详细介绍的 [整体操作](../../delivery/using/managing-subscriptions.md) 不适用。

* 与表的链接 **[!UICONTROL visitor]** 不起作用。

   因此，要使用 **[!UICONTROLSComial Marketing]** Module，您必须配置存储步骤以引用正确的表。

   同样，在使用转诊功能时，标准初始消息传输模板也必须进行调整。

* 不能在列表中手动添加配置文件。

   因此，如果没有其他配 [置](../../platform/using/creating-and-managing-lists.md) ，本节中详述的过程将不适用。

   >[!NOTE]
   >
   >您仍然可以使用工作流创建收件人列表。 有关详细信息，请参 [阅使用工作流创建配置文件列表](../../configuration/using/creating-a-profile-list-with-a-workflow.md)。

我们还建议检查不同现成配置中使用的默认值：根据所使用的功能，必须进行若干适应。

例如：

* 必须重新开发某些标准报告，特别是 **Interaction** 和 **Mobile Applications提供的报** 告。 请参阅管理 [报告部分](../../configuration/using/managing-reports.md) 。
* 某些工作流活动的默认配置引用标准收件人表(**[!UICONTROL nms:recipient]**):当用于外部收件人表时，必须更改这些配置。 请参阅管理工 [作流部分](../../configuration/using/managing-workflows.md) 。
* 必须调整 **[!UICONTROL Unsubscription link]** 标准个性化基块。
* 必须修改标准交付模板的目标映射。
* V4表单与外部收件人表格不兼容：必须使用Web应用程序。

