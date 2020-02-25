---
title: 使用Adobe Campaign Classic收件人表
description: 了解如何在设计数据模型时使用Adobe Campaign Classic中开箱即用的收件人表。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a8bfeaecc8a4832cac96f479ea1a0b11cd73c1e8

---


# 数据模型最佳实践{#data-model-best-practices}

本文档概述了设计Adobe Campaign数据模型时的主要建议。

要更好地了解Campaign内置表及其交互，请参阅 [Campaign Classic数据模型部分](../../configuration/using/about-data-model.md) 。

阅读此文 [档](../../configuration/using/about-schema-reference.md) ，开始使用营销活动架构。 了解如何配置扩展架构以扩展本文档中Adobe Campaign数据库的概念数据模型 [](../../configuration/using/about-schema-edition.md)。

## 概述 {#overview}

Adobe Campaign系统极其灵活，可扩展至初始实施之外。 但是，尽管可能性是无限的，但开始设计数据模型至关重要，必须做出明智的决策并打牢基础。

本文档提供了常见使用案例和最佳实践，以了解如何正确构建您的Adobe Campaign工具。

## 数据模型架构 {#data-model-architecture}

Adobe Campaign standard是一款功能强大的跨渠道营销活动管理系统，可帮助您整合线上和线下策略，创造个性化的客户体验。

### 以客户为中心的方法 {#customer-centric-approach}

虽然大多数电子邮件服务提供商都在通过以列表为中心的方式与客户进行通信，但Adobe Campaign依靠关系数据库来利用更广泛的客户视图及其属性。

以客户为中心的方法如下图所示。 灰 **色的Recipient** （收件人）表代表构建所有内容的主客户表：

![](assets/customer-centric-data-model.png)

要访问每个表的说明，请转到 **[!UICONTROL Admin > Configuration > Data schemas]**，从列表中选择一个资源，然后单击选 **[!UICONTROL Documentation]** 项卡。

Adobe Campaign默认数据模型在此文档中 [显示](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html)。

>[!NOTE]
>
>Adobe Campaign Classic允许构建自定义客户表。 但是，在大多数情况下，建议使用标准的“收件人 [表”](../../configuration/using/default-recipient-table.md) ，该表已预建了其他表和功能。

### Adobe Campaign的数据 {#data-for-campaign}

应将哪些数据发送到Adobe Campaign? 确定营销活动所需的数据至关重要。

>[!NOTE]
>
>Adobe Campaign既不是数据仓库也不是报表工具。 因此，请勿尝试将所有可能的客户及其关联信息导入Adobe Campaign，或导入仅用于构建报告的数据。

要决定Adobe Campaign中是否需要某个属性，请自问该属性是否属于以下类别之一：

* 用于分段的属 **性**
* 用于数据管 **理进程的属性** （例如聚合计算）
* 用于个性化的属 **性**

如果不属于上述任何一种情况，您很可能不需要Adobe Campaign中的此属性。

## 数据类型选择 {#data-types}

要确保系统的良好架构和性能，请按照以下最佳做法在Adobe Campaign中设置数据。

* 大表应大部分包含数字字段并包含引用表的链接（在使用值列表时）。
* expr **属性** 允许将架构属性定义为计算字段，而不是表中的物理集值。 这可以访问不同格式（例如年龄和出生日期）的信息，而无需存储这两个值。 这是避免重复字段的好方法。 例如，“收件人”表使用域的表达式，该表达式已在电子邮件字段中显示。
* 但是，当表达式计算复杂时，建议不要使用 **expr** 属性，因为即时计算可能会影响查询的性能。
* XML **类型** ，是避免创建过多字段的好方法。 但是，当它使用数据库中的CLOB列时，它也占用了磁盘空间。 它还可能导致复杂的SQL查询，并可能影响性能。
* 字符串字段 **的长度** ，应始终用列进行定义。 默认情况下，Adobe Campaign中的最大长度为255，但如果您已经知道字段的大小不会超过较短的长度，Adobe建议将字段缩短。
* 如果您确定源系统中的字段大小被高估且无法达到，则可以在Adobe Campaign中将字段缩短到源系统中的字段。 这可能意味着Adobe Campaign中的字符串更短或更小的整数。

## 标识符 {#identifiers}

Adobe Campaign资源具有三个标识符，并且可以添加其他标识符。

下表描述了这些标识符及其用途。

| 标识符 | 说明 | 最佳实践 |
|--- |--- |--- |
| Id | <ul><li>id是Adobe Campaign表的物理主键。 对于现成表，它是从序列生成的32位数</li><li>此标识符通常对特定Adobe Campaign实例是唯一的。 </li><li>自动生成的ID可在架构定义中显示。 搜索 *autopk=&quot;true&quot;属性* 。</li></ul> | <ul><li>自动生成的标识符不应用作工作流或包定义中的引用。</li><li>不应假定id将始终为递增数。</li><li>现成表中的id是32位数，不应更改此类型。 此编号取自同一名称的章节中涵盖的“序列”。</li></ul> |
| 名称（或内部名称） | <ul><li>此信息是表中记录的唯一标识符。 此值可以手动更新，通常使用生成的名称。</li><li>此标识符在部署到Adobe Campaign的其他实例时保留其值，且不应为空。</li></ul> | <ul><li>如果对象要从环境部署到另一个环境，请重命名Adobe Campaign生成的记录名称。</li><li>当对象具有namespace属性(例&#x200B;*如架构* )时，将在所有创建的自定义对象中利用此通用命名空间。 不应使用某些保留的命名空间： *nms*、 *xtk*。</li><li>当对象没有任何命名空间(例&#x200B;*如*** 工作流或交付)时，此命名空间概念将添加为内部名称对象的前缀：namespaceMyObjectName **。</li><li>请勿使用空格“”、半列“:”或连字符“-”等特殊字符。 所有这些字符将替换为下划线“_”（允许的字符）。 例如，“abc-def”和“abc:def”将存储为“abc_def”并相互覆盖。</li></ul> |
| 标签 | <ul><li>标签是Adobe Campaign中对象或记录的业务标识符。</li><li>此对象允许空格和特殊字符。</li><li>它不保证记录的唯一性。</li></ul> | <ul><li>建议确定对象标签的结构。</li><li>这是用于为Adobe Campaign用户识别记录或对象的最易用的解决方案。</li></ul> |

## 自定义内部密钥 {#custom-internal-keys}

在Adobe Campaign中创建的每个表都需要主键。

大多数组织都从外部系统导入记录。 虽然“收件人”表的物理密钥是“id”属性，但也可以另外确定自定义密钥。

此自定义密钥是提供Adobe Campaign的外部系统中的实际记录主键。

当现成表同时具有自动键和内部键时，内部键将在物理数据库表中设置为唯一的索引。

创建自定义表时，有两个选项：
* 自动生成的键(id)和内部键（自定义）的组合。 如果系统密钥是复合密钥或不是整数，则此选项很有趣。 整数在大表中提供更高的性能，并与其他表连接。
* 使用主键作为外部系统主键。 此解决方案通常是首选的，因为它简化了导入和导出数据的方法，并且在不同系统之间使用一致的键。 如果键名为“id”，并且应使用外部值（而非自动生成）填充，则应禁用Autopk。

>[!IMPORTANT]
>
>在工作流中，不应将作品用作引用。

## 序列 {#sequences}

Adobe Campaign主键是自动生成的用于所有现成表的ID，对于自定义表也可以相同。 For more on this, see [this section](#identifiers).

此值取自称为序列的内 **容**，该序列是用于生成数字序列的数据库对象。

有两种类型的序列：
* **共享**:多张桌子会从同一序列中挑出他们的id。 这意味着，如果一个表使用id &#39;X&#39;，则共享同一序列的其他表将没有具有id &#39;X&#39;的记录。 **XtkNewId是Adobe Campaign中提供的默认共享序列** 。
* **专用**:只有一个表从序列中选取其id。 序列名称通常包含表名。

序列是一个32位的整数值，其可用值的最大有限数：21.4亿。 达到最大值后，序列将返回0，以便循环使用id。 如果未清除旧数据，则结果将是唯一键违规，这将成为平台运行状况和使用的阻止程序。 Adobe Campaign将无法发送通信（当它影响交付日志表时），并且性能将受到严重影响。

因此，每年发送60亿封电子邮件，其日志的保留期为180天，客户在4个月后将用完ID。 要防止出现此类问题，请确保根据卷设置清除设置。 For more on this, see [this section](#data-retention).

当在Adobe Campaign中使用主键作为autoPK创建自定义表时，应将自定义专用序列与该表系统关联。

默认情况下，自定义序列的值将介于+1,000到+2.1BB之间。 从技术上讲，通过启用负ID，可以获得4BB的全范围。 这应当谨慎使用，当从负数到正数时，将丢失一个id:在生成的SQL查询中，记录0通常被Adobe Campaign Classic忽略。

**相关主题：**
* 有关序列自动 **生成功能的更多** ，请参阅此 [文档](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)。
* 有关序列耗尽的更多信息，请观看此 [视频](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html)。

## 索引 {#indexes}

索引对于性能至关重要。 当您在架构中声明密钥时，Adobe将自动在密钥的字段上创建索引。 您还可以为不使用该键的查询声明更多索引。

Adobe建议定义其他索引，因为这可能会提高性能。

但是，请牢记以下几点：

* 索引使用与访问模式相关。 优化索引通常是数据库设计中的关键部分，必须由专家处理。 添加索引通常是附加到数据库维护的迭代式工作流。 它可以随时间逐步解决发生的性能问题。
* 索引可增加表的整体大小（以存储索引本身）。
* 在列上添加索引可以提高数据读访问(SELECT)的性能，但会降低数据写访问(UPDATE)的性能。
* 由于这会影响插入数据时的性能，因此索引的大小和数量应受到限制。
* 不必添加索引。 确保这是必需的，并且它提高了查询的整体性能（测试和学习）。
* 通常，如果您知道查询不会返回超过10%的记录，则索引是有效的。
* 仔细选择需要定义的索引。
* 请勿从现成表中删除本机索引。

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

## 链接和基数 {#links-and-cardinality}

### 链接 {#links}

谨防大桌上的“自身”诚信。 删除具有“自有”完整性宽表的记录可以停止实例。 表被锁定，删除操作逐个完成。 因此，最好在具有大卷的子表上使用“中性”完整性。

声明链接为外部连接不利于性能。 零id记录模拟外部连接功能。 如果链接使用autopk，则无需声明外部连接。

虽然可以在工作流中加入任何表，但Adobe建议直接在数据结构定义中定义资源之间的公用链接。

链接的定义应与表中的实际数据保持一致。 错误的定义可能会影响通过链接检索到的数据，例如意外重复记录。

使用表名称一致命名链接：链接名称应有助于了解远程表是什么。

请勿以“id”作为后缀命名链接。 例如，将其命名为“transaction”而不是“transactionId”。

默认情况下，Adobe Campaign将使用外部表的主键创建一个链接。 更清晰地说，最好在链接定义中显式定义连接。

索引将添加到链接中使用的属性。

创建者链接和上次修改者链接在许多表中显示。 如果企业未使用此信息，则可以使用链接上的属性noDbIndex禁用索引。

### 基数 {#cardinality}

设计链接时，请确保在声明1-1关系时目标记录是唯一的。 否则，当仅需要一条记录时，连接可能会返回多个记录。 当“查询返回的行数超出预期”时，这会导致在准备交付时出错。 将链接名称设置为与目标架构相同的名称。

在(1)侧的架构中定义一个基数(1-N)的链接。 例如，应在事务架构中定义关系收件人(1)-(N)事务。

请注意，链接的反向基数在默认情况下为(N)。 可以通过向链接定义添加属性revCardinality=&#39;single&#39;来定义链接(1-1)。

如果用户不能看到反向链接，则可以使用链接定义revLink=&#39;_NONE_&#39;隐藏它。 这的一个好用例是定义从收件人到最后完成事务的链接。 您只需查看从收件人到最后一个事务的链接，无需从事务表中看到反向链接。

执行外部连接(1-0..1)的链接应谨慎使用，因为这将影响系统性能。

## 数据保留——清理和清除 {#data-retention}

Adobe Campaign既不是数据仓库也不是报表工具。 因此，为确保Adobe Campaign解决方案的良好性能，数据库增长应保持可控。 为此，遵循以下一些最佳实践可能会有所帮助。

默认情况下，Adobe Campaign交付和跟踪日志的保留期为180天。 运行清除进程以删除任何早于该进程的日志。

* 如果您希望保留日志更长，应根据数据库大小和发送的消息量仔细作出此决定。 作为提醒，Adobe Campaign序列是一个32位整数。
* 建议在这些表中一次不要有超过10亿个记录（21.4亿个ID中的50%），以限制使用所有可用ID的风险。 这将要求一些客户将保留期限降低到180天以下。

>[!IMPORTANT]
>
>自定义表不会使用标准清除过程进行清除。 虽然这在第一天可能不是必需的，但不要忘记为自定义表构建清除流程，因为这可能会导致性能挑战。

在Adobe Campaign中，有几个解决方案可以最大限度地减少对记录的需求：
* 在Adobe Campaign外的数据仓库中导出数据。
* 生成汇总值，这些值在满足您的营销实践需求的同时占用较少的空间。 例如，您无需在Adobe Campaign中拥有完整的客户交易历史记录即可跟踪上次购买。

## 性能 {#performance}

为了确保在任何时间获得更好的性能，请遵循以下最佳实践。

### 一般性建议 {#general-recommendations}

* 避免在查询中使用“CONTAINS”等操作。 如果您知道需要什么并希望筛选什么，请使用“EQUAL TO”或其他特定筛选器运算符应用相同的条件。
* 在工作流中构建数据时，避免加入非索引字段。
* 尝试确保像导入和导出这样的流程在工作时间之外完成。
* 确保所有日常活动都有预定，并按预定计划进行。
* 如果一个或几个日常进程失败，并且如果强制要求在同一天运行该进程，请确保启动手动进程时没有运行冲突的进程，因为这可能会影响系统性能。
* 确保在导入过程中或执行任何手动过程时，没有运行任何每日营销活动。
* 使用一个或多个引用表，而不是复制每行中的字段。 使用键／值对时，最好选择数字键。
* 短字符串仍可接受。 如果引用表已在外部系统中就位，重复使用引用表将有助于与Adobe Campaign的数据集成。

### 一对多关系 {#one-to-many-relationships}

* 数据设计会影响可用性和功能性。 如果您设计的数据模型具有许多一对多关系，则用户在应用程序中构建有意义的逻辑会更加困难。 对于非技术营销人员来说，一对多过滤逻辑可能难以正确构建和理解。
* 将所有基本字段放在一个表中是件好事，因为这使用户更容易构建查询。 有时，如果可以避免连接，则跨表复制某些字段也会有好的性能。
* 某些内置功能将不能引用一对多关系，例如“优惠加权公式”和“交付”。

### 大表 {#large-tables}

以下是使用大表和复杂连接设计数据模型时应遵循的一些最佳实践。

* 使用其他自定义收件人表时，请确保每个传送映射都有一个专用的日志表。
* 减少列数，特别是通过识别未使用的列数。
* 通过避免复杂连接（例如在多个条件和／或多个列上的连接）来优化数据模型关系。
* 对于连接键，请始终使用数字数据而不是字符串。
* 尽可能减少日志保留深度。 如果需要更深入的历史记录，您可以聚合计算和／或处理自定义日志表以存储更大的历史记录。

有关如何为较大的卷优化数据库设计的更多详细信息，请参阅 [Campaign Classic数据模型最佳实践](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html)。