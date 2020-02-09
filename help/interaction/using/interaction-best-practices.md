---
title: Adobe Campaign Classic Interaction最佳实践
description: 本节介绍了在Adobe Campaign Classic中管理“交互”模块的最佳实践方法。
page-status-flag: never-activated
uuid: 88bcc1d5-be8f-4a63-9b4a-3843b5751abe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: interaction-overview
discoiquuid: 85e8348f-d240-4a36-b7bd-645807dbc227
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 91f80adf0b84d45a71e07079d4e72fd7628b41c1

---


# 互动最佳实践{#interaction-best-practices}

## 一般性建议 {#general-recommendations}

本节介绍了在Adobe Campaign Classic中管理“交互”模块的最佳实践方法，包括资格规则、预定义的过滤器、工作流活动和数据库选项。

Adobe Campaign中的交互需要仔细的管理才能高效地运行。 您必须在联系人数和选件类别和选件数之间找到平衡点。 如果未仔细处理这些因素，您的Adobe Campaign实例可能会遇到问题。

### 实施 {#implementation}

下面列出了实施和配置交互时应牢记的重要元素。

* 对于批处理引擎（通常用于出站通信，如电子邮件），吞吐量是主要的问题，因为可以同时处理多个联系人。 典型的瓶颈是数据库性能。
* 统一引擎（通常用于入站通信，如网站上的横幅）的主要约束是延迟，因为有人期望得到答案。 典型的瓶颈是CPU性能。
* 优惠目录设计对Adobe Campaign Classic的性能产生了巨大影响。
* 当有许多选件时，将其拆分为多个选件目录。

### 资格规则 {#eligibility-rules}

下面列出了有关资格规则的一些最佳实践。

* 简化规则。 规则复杂性会影响性能，因为它扩展了查找范围。 复杂规则是任何具有5个以上条件的规则。
* 为了提高性能，可以在跨多个选件共享的不同预定义筛选器中划分规则。
* 将限制最严格的优惠类别规则放在树中最高的可能位置。 这样，他们会首先过滤掉大多数联系人，减少目标数量，并阻止他们被更多规则处理。
* 在树的底部放置时间或处理方面最昂贵的规则。 这样，这些规则将仅在其余目标受众上运行。
* 从特定类别开始，以避免扫描整个树。
* 要节省处理时间，请预计算聚合，而不是构建包含连接的复杂规则。 为此，请尝试将客户数据存储在可在资格规则中查找的参考表中。
* 使用最少的权重来限制查询的数量。
* 建议每个优惠空间提供有限数量的优惠。 这可确保在任何给定空间中更快地检索选件。
* 使用索引，尤其是常用查找列。

### 命题表 {#proposition-table}

下面列出了有关建议表的一些最佳实践。

* 使用最少的规则使处理尽可能快。
* 限制命题表中的记录数：只保留跟踪其状态更新所需的记录以及规则需要的记录，然后将其存档到另一个系统中。
* 对命题表执行密集的数据库维护，如重建索引或重新创建表。
* 限制每个目标提出的建议数。 请勿设置超出实际使用范围的设置。
* 尽可能避免在规则条件中加入。

## 有关管理优惠的提示与技巧 {#tips-managing-offers}

本节包含有关管理选件和使用Adobe Campaign Classic中的“交互”模块的更详细建议。

### 在电子邮件发送中使用多个选件空间 {#multiple-offer-spaces}

在分发中包含选件时，通常会通过丰富化活动（或其他类似活动）在营销活动工作流的上游选择选件。

在丰富化活动中选择选件时，您可以选择要使用的选件空间。 但是，无论选择的选件空间如何，交付自定义菜单都取决于在交付中设置的选件空间。

在以下示例中，在交付中选择的选件空间是 **[!UICONTROL Email (Environment - Recipient)]**:

![](assets/Interaction-best-practices-offer-space-selected.png)

如果您在分发中选择的选件空间未设置HTML渲染功能，则您将在分发菜单中看不到它，并且它将不可供选择。 同样，这与丰富化活动中选择的优惠空间无关。

在以下示例中，HTML渲染功能在下拉列表中可用，因为在交付中选择的选件空间具有渲染功能：

![](assets/Interaction-best-practices-HTML-rendering.png)

此函数插入代码，如： `<%@ include proposition="targetData.proposition" view="rendering/html" %>`.

选择命题时，属性的 **[!UICONTROL view]** 值如下：
* “rendering/html”:html渲染。 它使用HTML渲染功能。
* “offer/view/html”:html内容。 它不使用HTML渲染功能。 它只包括HTML字段。

当您在单个电子邮件发送中包含多个选件空间，并且其中某些具有渲染函数，而某些没有渲染函数时，您必须记住哪些选件使用了哪些选件提供了空间，哪些选件提供了具有渲染函数。

因此，为避免任何问题，建议所有选件空间都定义了HTML渲染函数，即使您的选件空间仅需要HTML内容也是如此。

### 在命题日志表中设置排名 {#rank-proposition-log-table}

当命题被生成或接受时，Offer空间能够将数据存储在命题表中：

![](assets/Interaction-best-practices-offer-space-storage.png)

但是，这仅适用于入站交互。

在使用出站交互时以及在不使用“交互”模块的情况下使用出站选件时，还可以在命题表中存储其他数据。

工作流临时表中的任何字段名称与命题表中的字段名称相匹配，这些字段将复制到命题表中的同一字段中。

例如，在富集中手动选择选件（不进行交互）时，标准字段的定义如下：

![](assets/Interaction-best-practices-manual-offer-std-fields.png)

可以添加其他字段，如@rank字段：

![](assets/Interaction-best-practices-manual-offer-add-fields.png)

由于命题表中有一个名为@rank的字段，因此将复制工作流临时表中的值。

有关将其他字段存储在命题表中的更多信息，请参 [阅通过工作流集成选件](../../interaction/using/integrating-an-offer-via-a-workflow.md#storing-offer-rankings-and-weights)。

对于具有交互的出站选件，当选择了多个选件并且您希望记录它们在电子邮件中的显示顺序时，此功能非常有用。

您还可以直接将其他元数据存储在建议表中，如当前支出水平，以保留在生成选件时有关支出的历史记录。

使用出站交互时，可以添加@rank字段（如上例所示），但其值会根据交互返回的顺序自动设置。 例如，如果您使用“交互”来选择三个选件，则@rank字段将返回值1、2和3。

在使用“交互”和手动选择选件时，用户可以组合这两种方法。 例如，用户可以手动将手动选择的选件的@rank字段设置为1，并对交互返回的选件使用“1 + @rank”等表达式。 如果“交互”选择三个选件，则两种方法返回的选件将排名为1-4:

![](assets/Interaction-best-practices-manual-offer-combined.png)

### 扩展nms:offer架构 {#extending-nms-offer-schema}

在扩展nms:offer架构时，请确保遵循现成的结构设置：
* 在下面为内容存储定义任何新字段 `<element name="view">`。
* 每个新字段需要定义两次。 一次是常规XML字段，一次是CDATA XML字段，名称后面附加“_jst”。 例如：

   ```
   <element label="Price" name="price" type="long" xml="true"/>
   <element advanced="true" label="Script price" name="price_jst" type="CDATA" xml="true"/>
   ```

* 包含要跟踪的URL的所有字段都必须放在 `<element name="trackedUrls">` 下方，该位置位于下方 `<element name="view" >`。