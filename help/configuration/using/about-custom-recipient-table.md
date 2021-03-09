---
solution: Campaign Classic
product: campaign
title: 关于自定义收件人表
description: 关于自定义收件人表
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 5871674ee26766cf08439768df3fb07ea0f99e7b
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---


# 使用自定义收件人表{#about-custom-recipient-table}

本节详细介绍了使用非标准收件人表的原则。

默认情况下，Adobe Campaign优惠一个标准收件人表，现成功能和进程链接到该表。 标准收件人表具有许多预定义的字段和表，可以使用扩展表轻松扩展这些字段和表。

如果此扩展方法优惠了扩展表的良好灵活性，则不允许减少表中字段或链接的数量。 使用非标准表(或“外部收件人表”)可以获得更大的灵活性，但在实施时需要一定的预防措施。

## 精度{#precisions}

此功能允许Adobe Campaign处理来自外部数据库的数据：此用户档案将用作一组投放。 实施此过程涉及根据客户需求可能相关的几个精确度。 例如：

* 没有与Adobe Campaign数据库之间的更新流：此表中的数据可以直接通过承载该表的数据库引擎进行更新。
* 在现有数据库上操作的进程中没有更改。
* 使用非标准结构的用户档案数据库：可能使用单个实例将保存在具有各种结构的各种表中的用户档案传送到。
* 更新Adobe Campaign数据库时，不需要进行任何更改或维护。
* 如果不需要大多数表字段，或者收件人库模板不以收件人居中，则标准表是无用的。
* 为了提高效率，如果您具有大量用户档案，则需要具有少量字段的表。 标准收件人表中包含的字段太多，无法用于此特定情况。

本节介绍了用于映射Adobe Campaign中现有表的要点，以及应用于基于任何表执行投放的配置。 最后，介绍了如何向用户提供与标准收件人表一样实用的查询接口。 要了解本节介绍的材料，需要充分了解屏幕和模式设计的原则。

## Recommendations和限制{#recommendations-and-limitations}

使用外部收件人表具有以下限制：

* Adobe Campaign不支持链接到相同广播和/或跟踪日志模式的多个收件人模式(称为定位模式)。 否则，这可能导致之后数据协调出现异常。

   下图详细说明了每个自定义收件人模式所需的关系结构：
   ![](assets/custom_recipient_limitation.png)

   我们建议：

   * 将&#x200B;**[!UICONTROL nms:BroadLogRcp]**&#x200B;和&#x200B;**[!UICONTROL nms:TrackingLogRcp]**&#x200B;模式指定到现成的&#x200B;**[!UICONTROL nms:Recipientschema]**。 这两个日志表不应链接到任何其他自定义收件人表。
   * 为每个新的自定义模式模式定义专用的自定义广播和跟踪日志收件人。 在设置目标映射时，可以自动完成此操作，请参阅[目标映射](../../configuration/using/target-mapping.md)。

* 不能使用产品中提供的标准&#x200B;**[!UICONTROL Services and Subscriptions]**。

   这意味着，[本节](../../delivery/using/managing-subscriptions.md)中详述的整体操作不适用。

* 与&#x200B;**[!UICONTROL visitor]**&#x200B;表的链接不起作用。

   因此，要使用&#x200B;**[!UICONTROL Social Marketing]**&#x200B;模块，必须配置存储步骤以引用正确的表。

   同样，在使用引用功能时，必须调整标准初始消息传输模板。

* 不能在列表中手动添加用户档案。

   因此，如果没有其他配置，则不适用[本节](../../platform/using/creating-and-managing-lists.md)中详细介绍的过程。

   >[!NOTE]
   >
   >您仍可以使用收件人创建列表。 有关详细信息，请参阅[使用工作流](../../configuration/using/creating-a-profile-list-with-a-workflow.md)创建用户档案列表。

我们还建议检查不同现成配置中使用的默认值：根据所使用的功能，必须进行若干适应。

例如：

* 必须重新开发某些标准报告，特别是由&#x200B;**Interaction**&#x200B;和&#x200B;**Mobile Applications**&#x200B;提供的报告。 请参阅[管理报告](../../configuration/using/managing-reports.md)部分。
* 某些工作流活动的默认配置引用标准收件人表(**[!UICONTROL nms:recipient]**):当用于外部收件人表时，必须更改这些配置。 请参阅[管理工作流](../../configuration/using/managing-workflows.md)部分。
* 必须调整标准&#x200B;**[!UICONTROL Unsubscription link]**&#x200B;个性化基块。
* 必须修改标准投放模板的目标映射。
* V4表单与外部收件人表格不兼容：您必须使用web应用程序。

