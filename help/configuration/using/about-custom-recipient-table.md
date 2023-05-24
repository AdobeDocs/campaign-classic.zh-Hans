---
product: campaign
title: 关于自定义收件人表
description: 关于自定义收件人表
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Custom Resources
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---

# 使用自定义收件人表格{#about-custom-recipient-table}



本节详细说明使用自定义（或外部）收件人表的原则。

默认情况下，Adobe Campaign提供了一个内置的收件人表，开箱即用的函数和进程将链接到该表。 内置的收件人表具有许多预定义字段和表，可使用扩展表轻松扩展这些字段和表。

如果此扩展方法为扩展表提供了良好的灵活性，则它不允许减少表中的字段或链接数。 使用非标准表或“外部收件人表”可提供更大的灵活性，但在实施时需要采取某些预防措施。

此功能允许Adobe Campaign处理来自外部数据库的数据：此数据将用作投放的一组用户档案。 实施此流程涉及多个可能根据客户需求而相关的精确度。 例如：

* 没有与Adobe Campaign数据库之间的更新流：可以通过承载此表的数据数据库引擎直接更新该表中的数据。
* 在现有数据库上运行的进程中没有更改。
* 使用具有非标准结构的用户档案数据库：可使用单个实例将内容交付给以各种结构保存在各种表中的用户档案。
* 更新Adobe Campaign数据库时不需要更改或维护。
* 如果您不需要大部分表字段或数据库模板未以收件人为中心，则内置的收件人表将毫无用处。
* 为了提高效率，如果您有大量用户档案，则需要具有少量字段的表。 对于此特定情况，内置收件人表的字段过多。

此部分介绍用于映射Adobe Campaign中现有表的关键点，以及根据任何表执行投放时应用的配置。 最后，还介绍了如何为用户提供与内置收件人表一样实用的查询接口。 要了解本节中介绍的材料，需要很好地了解屏幕和模式设计的原则。

## Recommendations和限制 {#recommendations-and-limitations}

使用自定义收件人表具有以下限制：

* Adobe Campaign不支持链接到同一broadlog和/或trackinglog架构的多个收件人架构（也称为定位架构）。 否则，这可能会导致以后数据协调出现异常。

   下图详细说明每个自定义收件人架构所需的关系结构：
   ![](assets/custom_recipient_limitation.png)

   我们建议：

   * 专注于 **[!UICONTROL nms:BroadLogRcp]** 和 **[!UICONTROL nms:TrackingLogRcp]** 开箱即用的架构 **[!UICONTROL nms:Recipientschema]**. 这两个日志表不应链接到任何其他自定义收件人表。
   * 为每个新的自定义收件人架构定义专用的自定义broadlog和trackinglog架构。 这在设置目标映射时可自动完成，请参阅 [目标映射](../../configuration/using/target-mapping.md).

* 不能使用标准 **[!UICONTROL Services and Subscriptions]** 在产品中提供。

   这意味着整个操作详见 [本节](../../delivery/using/managing-subscriptions.md) 不适用。

* 与的链接 **[!UICONTROL visitor]** 表格不起作用。

   因此，要使用 **[!UICONTROL Social Marketing]** 模块必须配置存储步骤以引用正确的表。

   同样，在使用反向链接功能时，必须采用标准的初始报文传输模板。

* 您不能在列表中手动添加用户档案。

   因此，中详述的程序 [本节](../../platform/using/creating-and-managing-lists.md) 不适用，因为没有其他配置。

   >[!NOTE]
   >
   >您仍然可以使用工作流创建收件人列表。 有关更多信息，请参阅 [使用工作流创建用户档案列表](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

我们还建议检查不同的现成配置中使用的默认值：根据使用的功能，必须执行若干调整。

例如：

* 某些标准报告，特别是由提供的报告 **互动** 和 **移动应用程序** 必须重新开发。 请参阅 [管理报告](../../configuration/using/managing-reports.md) 部分。
* 某些工作流活动的默认配置引用标准收件人表(**[!UICONTROL nms:recipient]**)：在用于外部收件人表时，必须更改这些配置。 请参阅 [管理工作流](../../configuration/using/managing-workflows.md) 部分。
* 标准 **[!UICONTROL Unsubscription link]** 必须调整个性化块。
* 必须修改标准投放模板的目标映射。
* V4表单与外部收件人表不兼容：您必须使用Web应用程序。
