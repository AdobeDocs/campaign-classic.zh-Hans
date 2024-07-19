---
product: campaign
title: 关于自定义收件人表
description: 关于自定义收件人表
feature: Configuration, Custom Resources
role: User, Data Engineer, Developer
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: d8cea496-b3f3-420a-bf6e-b7cbb321b30d
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%

---

# 使用自定义收件人表格{#about-custom-recipient-table}

本节详细说明使用自定义（或外部）收件人表的原则。

默认情况下，Adobe Campaign提供了一个内置的收件人表，开箱即用的函数和进程将链接到此表中。 内置的收件人表具有许多预定义字段和表，这些字段和表可以使用扩展表轻松扩展。

如果此扩展方法为扩展表提供了良好的灵活性，则不允许减少表中的字段或链接数。 使用非标准表（或“外部收件人表”）可以具有更大的灵活性，但在实施时需要特别注意。

此功能允许Adobe Campaign处理来自外部数据库的数据：此数据将用作投放的一组用户档案。 根据客户的需求，实施此流程涉及多个可能相关的精确度。 例如：

* 没有与Adobe Campaign数据库之间的更新流：此表中的数据可以直接通过承载它的数据库引擎进行更新。
* 在现有数据库上运行的进程中没有更改。
* 使用具有非标准结构的用户档案数据库：可使用单个实例将内容传送到保存在具有各种结构的各种表中的用户档案。
* 更新Adobe Campaign数据库时不需要更改或维护。
* 如果您不需要大部分表字段或数据库模板不在收件人中心，则内置的收件人表将毫无用处。
* 为了提高效率，如果您有大量用户档案，则需要具有很少字段的表。 对于此特定情况，内置收件人表的字段过多。

本节介绍可让您映射Adobe Campaign中现有表的关键点，以及根据任何表执行投放时要应用的配置。 最后，还介绍了如何为用户提供与内置收件人表一样实用的查询接口。 要了解本节中介绍的材料，需要很好地了解屏幕和模式设计的原则。

## Recommendations和限制 {#recommendations-and-limitations}

使用自定义收件人表具有以下限制：

* Adobe Campaign不支持链接到同一broadlog和/或trackinglog架构的多个收件人架构（也称为定位架构）。 否则，这可能会导致以后数据协调出现异常。

  下图详细说明每个自定义收件人模式所需的关系结构：
  ![](assets/custom_recipient_limitation.png)

  我们建议：

   * 将&#x200B;**[!UICONTROL nms:BroadLogRcp]**&#x200B;和&#x200B;**[!UICONTROL nms:TrackingLogRcp]**&#x200B;架构专用于现成的&#x200B;**[!UICONTROL nms:Recipientschema]**。 这两个日志表不应链接到任何其他自定义收件人表。
   * 为每个新的自定义收件人模式定义专用的自定义broadlog和trackinglog模式。 在设置目标映射时，可以自动完成此操作，请参阅[目标映射](../../configuration/using/target-mapping.md)。

* 您无法使用产品中提供的标准&#x200B;**[!UICONTROL Services and Subscriptions]**。

  这意味着[此部分](../../delivery/using/managing-subscriptions.md)中详述的总体操作不适用。

* 与&#x200B;**[!UICONTROL visitor]**&#x200B;表的链接不起作用。

  因此，要使用&#x200B;**[!UICONTROL Social Marketing]**&#x200B;模块，您必须配置存储步骤以引用正确的表。

  同样，在使用反向链接功能时，必须采用标准的初始报文传输模板。

* 您不能在列表中手动添加用户档案。

  因此，如果没有其他配置，[此部分](../../platform/using/creating-and-managing-lists.md)中详述的过程将不适用。

  >[!NOTE]
  >
  >您仍然可以使用工作流创建收件人列表。 有关详情，请参阅[使用工作流创建用户档案列表](../../configuration/using/creating-a-profile-list-with-a-workflow.md)。

我们还建议检查不同的现成配置中使用的默认值：根据使用的功能，必须执行若干调整。

例如：

* 必须重新开发某些标准报告，特别是&#x200B;**交互**&#x200B;和&#x200B;**移动设备应用程序**&#x200B;提供的报告。 请参阅[管理报表](../../configuration/using/managing-reports.md)部分。
* 某些工作流活动的默认配置引用了标准收件人表(**[!UICONTROL nms:recipient]**)：这些配置在用于外部收件人表时必须更改。 请参阅[管理工作流](../../configuration/using/managing-workflows.md)部分。
* 必须调整标准&#x200B;**[!UICONTROL Unsubscription link]**&#x200B;个性化块。
* 必须修改标准投放模板的目标映射。
* V4表单与外部收件人表不兼容：您必须使用Web应用程序。
