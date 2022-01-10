---
product: campaign
title: 关于自定义收件人表
description: 关于自定义收件人表
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 2%

---

# 使用自定义收件人表格{#about-custom-recipient-table}

![](../../assets/common.svg)

本节详细介绍使用自定义（或外部）收件人表的原则。

默认情况下，Adobe Campaign提供了一个内置的收件人表，即装即用函数和进程都与之关联。 内置的收件人表具有许多预定义的字段和表，可以使用扩展表轻松扩展这些字段和表。

如果此扩展方法具有很好的扩展表的灵活性，则它不允许减少表中的字段或链接数。 使用非标准表（即“外部收件人表”）可以获得更大的灵活性，但在实施该表时需要采取某些预防措施。

此功能允许Adobe Campaign处理来自外部数据库的数据：此数据将用作投放的一组用户档案。 实施此过程涉及一些可能与客户需求相关的精确度。 例如：

* 没有进出Adobe Campaign数据库的更新流：此表中的数据可以直接通过托管该表的数据库引擎进行更新。
* 在现有数据库上运行的进程中没有更改。
* 使用具有非标准结构的用户档案数据库：可以使用单个实例将保存在具有各种结构的各种表中的用户档案传送到。
* 更新Adobe Campaign数据库时，无需进行任何更改或维护。
* 如果您不需要大多数表字段或数据库模板不是以收件人为中心，则内置的收件人表将无用。
* 为了提高效率，如果用户档案数量很大，则需要一个字段较少的表。 内置的收件人表具有太多字段用于此特定情况。

本节介绍用于映射Adobe Campaign中现有表的关键点以及用于根据任何表执行投放的配置。 最后，介绍了如何向用户提供与内置收件人表一样实用的查询界面。 要了解本节介绍的材料，需要充分了解屏幕和模式设计的原则。

## Recommendations和限制 {#recommendations-and-limitations}

使用自定义收件人表具有以下限制：

* Adobe Campaign不支持多个收件人模式（称为定位模式），这些模式链接到相同的broadlog和/或跟踪日志模式。 否则，这可能会导致以后的数据协调出现异常。

   下图详细列出了每个自定义收件人架构所需的关系结构：
   ![](assets/custom_recipient_limitation.png)

   我们建议：

   * 将 **[!UICONTROL nms:BroadLogRcp]** 和 **[!UICONTROL nms:TrackingLogRcp]** 模式到现成模式 **[!UICONTROL nms:Recipientschema]**. 这两个日志表不应链接到任何其他自定义收件人表。
   * 为每个新的自定义收件人模式定义专用的自定义broadlog和trackinglog模式。 设置目标映射时可以自动完成此操作，请参阅 [目标映射](../../configuration/using/target-mapping.md).

* 您不能使用标准 **[!UICONTROL Services and Subscriptions]** 提供。

   这表示 [此部分](../../delivery/using/managing-subscriptions.md) 不适用。

* 链接 **[!UICONTROL visitor]** 表不起作用。

   因此，要使用 **[!UICONTROL Social Marketing]** 模块必须配置存储步骤才能引用正确的表。

   同样，在使用反向链接功能时，必须修改标准的初始消息传输模板。

* 您无法在列表中手动添加用户档案。

   因此，详见 [此部分](../../platform/using/creating-and-managing-lists.md) 如果没有其他配置，则不适用。

   >[!NOTE]
   >
   >您仍可以使用工作流创建收件人列表。 有关更多信息，请参阅 [使用工作流创建用户档案列表](../../configuration/using/creating-a-profile-list-with-a-workflow.md).

我们还建议检查不同现成配置中使用的默认值：根据所使用的功能，必须进行若干适应。

例如：

* 某些标准报告，特别是 **互动** 和 **移动设备应用程序** 必须重新开发。 请参阅 [管理报告](../../configuration/using/managing-reports.md) 中。
* 某些工作流活动的默认配置引用标准收件人表(**[!UICONTROL nms:recipient]**):当用于外部收件人表时，必须更改这些配置。 请参阅 [管理工作流](../../configuration/using/managing-workflows.md) 中。
* 标准 **[!UICONTROL Unsubscription link]** 必须修改个性化块。
* 必须修改标准投放模板的目标映射。
* V4表单与外部收件人表不兼容：您必须使用web应用程序。
