---
solution: Campaign Classic
product: campaign
title: 数据模型最佳实践
description: 了解如何使用Campaign Classic数据模型
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 9c59b89c-3542-4a17-a46f-3a1e58de0748
translation-type: tm+mt
source-git-commit: d5579fa1928888a088fe99b685f4d12bf2bde25b
workflow-type: tm+mt
source-wordcount: '4009'
ht-degree: 1%

---

# 数据模型最佳实践{#data-model-best-practices}

本文档概述设计Adobe Campaign数据模型时的主要建议。

要更好地了解活动内置表及其交互，请参阅[本节](../../configuration/using/about-data-model.md)部分。

阅读[本文档](../../configuration/using/about-schema-reference.md)，开始使用活动模式。 了解如何配置扩展模式，以扩展[此文档](../../configuration/using/about-schema-edition.md)中Adobe Campaign数据库的概念数据模型。

## 概述 {#overview}

Adobe Campaign系统极其灵活，可扩展到初始实现之外。 但是，尽管可能性是无限的，但做出明智决策并建立坚实的基础对于开始设计数据模型至关重要。

此文档提供了常见使用案例和最佳实践，以了解如何正确构建您的Adobe Campaign工具。

## 数据模型架构{#data-model-architecture}

Adobe Campaign是一个功能强大的跨渠道活动管理系统，可帮助您协调线上和线下战略以创建个性化的客户体验。

### 以客户为中心的方法{#customer-centric-approach}

虽然大多数电子邮件服务提供商都在通过以列表为中心的方法与客户进行通信，但Adobe Campaign依靠关系型数据库来充分利用客户及其属性的更广泛视图。

以客户为中心的方法如下图所示。 灰色的&#x200B;**收件人**&#x200B;表表示正在围绕其构建所有内容的主客户表：

![](assets/customer-centric-data-model.png)

要访问每个表的说明，请转到&#x200B;**[!UICONTROL Admin > Configuration > Data schemas]**，从列表中选择一个资源并单击&#x200B;**[!UICONTROL Documentation]**&#x200B;选项卡。

Adobe Campaign默认文档模型显示在[此数据](../../configuration/using/data-model-description.md)中。

>[!NOTE]
>
>Adobe Campaign Classic允许构建自定义客户表。 但是，在大多数情况下，建议使用标准[收件人表](../../configuration/using/about-data-model.md#default-recipient-table)，该表已经预建了其他表和功能。

### Adobe Campaign{#data-for-campaign}的数据

应将哪些数据发送给Adobe Campaign? 确定营销活动所需的数据至关重要。

>[!NOTE]
>
>Adobe Campaign既不是data warehouse，也不是报告工具。 因此，请勿尝试将所有可能的客户及其关联信息导入Adobe Campaign，或导入仅用于构建报表的数据。

要决定Adobe Campaign中是否需要某个属性，请扪心自问，该属性是否属于以下类别之一：

* 用于&#x200B;**segmentation**&#x200B;的属性
* 用于&#x200B;**数据管理进程**&#x200B;的属性(例如聚合计算)
* 用于&#x200B;**个性化**&#x200B;的属性

如果不掉入其中任何一个，您很可能不需要在Adobe Campaign中使用此属性。

### 数据类型{#data-types}的选择

为确保系统的良好架构和性能，请按照以下最佳做法设置Adobe Campaign中的数据。

* 大表应大多包含数字字段，并包含指向引用表的链接(当使用值列表时)。
* **expr**&#x200B;属性允许将模式属性定义为计算字段，而不是表中的物理集值。 这可以使用不同格式（例如，年龄和出生日期）访问信息，而无需存储这两个值。 这是避免重复字段的好方法。 例如，收件人表使用域的表达式，该域已在电子邮件字段中显示。
* 但是，当表达式计算复杂时，不建议使用&#x200B;**expr**&#x200B;属性作为即时计算，这可能会影响查询的性能。
* **XML**&#x200B;类型是避免创建过多字段的好方法。 但当它使用数据库中的CLOB列时，它也占用了磁盘空间。 它还可能导致复杂的SQL查询，并可能影响性能。
* **string**&#x200B;字段的长度应始终由列定义。 默认情况下，Adobe Campaign的最大长度为255，但如果您已经知道大小不会超过较短的长度，则Adobe建议将字段保持较短。
* 如果您确定源系统中的字段大小被高估，并且无法达到，则可以将Adobe Campaign比源系统中的字段短。 这可能意味着Adobe Campaign中的字符串更短或整数更小。

### 字段选择{#choice-of-fields}

如果字段具有定位或个性化目的，则需要将其存储在表中。 换句话说，如果字段不用于发送个性化电子邮件或用作查询中的标准，则会占用磁盘空间，而它是无用的。

对于混合型和预置型实例，联合数据访问(联合数据访问，允许访问外部数据的可选功能)涵盖在活动过程中“实时”添加字段的需要。 如果您有联合数据访问，则无需导入所有内容。 有关详细信息，请参阅[关于联合数据访问](../../installation/using/about-fda.md)。

### 键选择{#choice-of-keys}

除了大多数表中默认定义的&#x200B;**autopk**&#x200B;之外，您还应考虑添加一些逻辑或业务密钥（帐户号、客户端号等）。 它可以稍后用于导入/对帐或数据包。 有关详细信息，请参阅[Identifiers](#identifiers)。

高效的密钥对性能至关重要。 数字数据类型应始终作为表的键。

对于SQLServer数据库，如果需要性能，可以考虑使用&quot;clustered index&quot;。 由于Adobe不处理此问题，您需要在SQL中创建它。

### 专用表空间{#dedicated-tablespaces}

模式中的表空间属性允许您为表指定专用表空间。

安装向导允许您按类型（数据、临时和索引）存储对象。

专用表空间更适合于分区、安全规则，并允许流畅、灵活的管理、更好的优化和性能。

## 标识符{#identifiers}

Adobe Campaign资源具有三个标识符，并且可以添加附加标识符。

下表说明了这些标识符及其用途。

| 标识符 | 说明 | 最佳实践 |
|--- |--- |--- |
| ID | <ul><li>id是Adobe Campaign表的物理主键。 对于现成表，它是从序列中生成的32位数</li><li>此标识符通常对特定Adobe Campaign实例唯一。 </li><li>自动生成的ID可在模式定义中显示。 搜索&#x200B;*autopk=&quot;true&quot;*&#x200B;属性。</li></ul> | <ul><li>自动生成的标识符不应用作工作流或包定义中的引用。</li><li>不应假设id将始终为递增数。</li><li>现成表中的id是32位数，不应更改此类型。 此编号取自同名部分中所涵盖的“序列”。</li></ul> |
| 名称（或内部名称） | <ul><li>此信息是表中记录的唯一标识符。 此值可以手动更新，通常使用生成的名称。</li><li>此标识符在部署到其他Adobe Campaign实例时会保留其值，它不应为空。</li></ul> | <ul><li>如果要将对象从Adobe Campaign部署到另一个环境，请重命名由生成的记录名称。</li><li>当对象具有命名空间属性(例如&#x200B;*模式*)时，将在所有创建的自定义对象中利用此常用命名空间。 不应使用某些保留命名空间:*nms*、*xtk*。</li><li>当对象没有任何命名空间(例如&#x200B;*workflow*&#x200B;或&#x200B;*投放*)时，将添加此命名空间概念作为内部名称对象的前缀：*namespaceMyObjectName*。</li><li>请勿使用空格&quot; &quot;、半列&quot;:&quot;或连字符&quot;-&quot;等特殊字符。 所有这些字符将替换为下划线&quot;_&quot;（允许的字符）。 例如，“abc-def”和“abc:def”将存储为“abc_def”并互相覆盖。</li></ul> |
| 标签 | <ul><li>标签是Adobe Campaign中对象或记录的业务标识符。</li><li>此对象允许使用空格和特殊字符。</li><li>它不保证记录的唯一性。</li></ul> | <ul><li>建议确定对象标签的结构。</li><li>这是最易用的解决方案，用于为Adobe Campaign用户标识记录或对象。</li></ul> |

## 自定义内部键{#custom-internal-keys}

在Adobe Campaign中创建的每个表都需要主键。

大多数组织都从外部系统导入记录。 虽然收件人表的物理键是“id”属性，但也可以确定自定义键。

此自定义键是外部系统馈送Adobe Campaign中的实际记录主键。

当现成表同时具有autopk和内部密钥时，内部密钥将设置为物理数据库表中的唯一索引。

创建自定义表时，有两个选项：
* 自动生成的键(id)和内部键（自定义）的组合。 如果系统键是复合键或不是整数，则此选项很有意思。 整数在大表中提供更高的性能，并与其他表连接。
* 使用主键作为外部系统主键。 此解决方案通常是首选的，因为它通过不同系统之间的一致密钥简化了数据导入和导出的方法。 如果键名为“id”，并应使用外部值（而非自动生成）填充，则应禁用Autopk。

>[!IMPORTANT]
>
>在工作流中，不应将autopk用作引用。

## 序列{#sequences}

Adobe Campaign主键是所有现成表的自动生成id，对于自定义表可以是相同的。 有关更多信息，请参阅[此章节](#identifiers)。

该值取自称为&#x200B;**sequence**&#x200B;的数据库对象，该对象用于生成编号序列。

有两种序列类型：
* **共享**:多张表格会从同一序列中选取其ID。这意味着，如果一个表使用了id“X”，则共享同一序列的其他表将没有具有该id“X”的记录。 **XtkNewId** 是Adobe Campaign中可用的默认共享序列。
* **专用**:只有一个表从序列中选取其id。序列名称通常包含表名。

>[!IMPORTANT]
>
>序列是一个32位整数值，具有有限的最大可用值数：21.4亿。 达到最大值后，序列将返回0，以便循环使用id。
>
>如果未清除旧数据，则结果将是唯一键违规，这将成为平台运行状况和使用的阻止程序。 Adobe Campaign将无法发出通信(当它影响投放日志表时)，性能将受到严重影响。

因此，每年发送60亿封电子邮件，其日志的保留期为180天，客户在4个月内将会用完ID。 要防止出现此类问题，请确保根据卷设置清除设置。 有关更多信息，请参阅[此章节](#data-retention)。

当使用主键作为autoPK的Adobe Campaign创建自定义表时，应将自定义专用序列与该表系统地关联。

默认情况下，自定义序列的值将介于+1,000到+2.1BB之间。 从技术上讲，通过启用负ID，可获得全范围4BB。 这应当谨慎使用，当从负数到正数时，将丢失一个id:在生成的SQL查询中，记录0通常被Adobe Campaign忽略。

**相关主题：**
* 有关&#x200B;**序列自动生成**&#x200B;功能的详细信息，请参阅[此文档](https://helpx.adobe.com/cn/campaign/kb/sequence_auto_generation.html)。
* 有关序列耗尽的详细信息，请观看[此视频](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html)。

## 索引 {#indexes}

索引对于性能至关重要。 在模式中声明键时，Adobe将自动在键的字段上创建索引。 还可以为不使用该键的查询声明更多索引。

Adobe建议定义其他索引，因为它可以提高性能。

但是，请记住以下几点：

* 索引使用情况将绑定到您的访问模式。 优化索引往往是数据库设计中的关键部分，必须由专家处理。 添加索引通常是附加到数据库维护的迭代式工作流。 它会随着时间的推移逐步解决发生时的性能问题。
* 索引可增加表的整体大小（以存储索引本身）。
* 在列上添加索引可以提高数据读取访问(SELECT)的性能，但会降低数据写入访问(UPDATE)的性能。
* 由于这会影响插入数据时的性能，索引的大小和数量应受到限制。
* 不必添加索引。 确保它是必需的，并且它提高了查询的整体性能（测试和学习）。
* 通常来说，如果您知道您的查询不会带回超过10%的记录，则索引是有效的。
* 仔细选择需要定义的索引。
* 请勿从现成表中删除本机索引。

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### 示例

管理索引可能会变得非常复杂，因此了解索引的工作方式非常重要。 为了说明这种复杂性，我们举一个基本示例，例如，通过筛选名字和姓氏来搜索收件人。 操作步骤：
1. 转到列表数据库中所有收件人的文件夹。 有关详细信息，请参阅[管理用户档案](../../platform/using/managing-profiles.md)。
1. 右键单击&#x200B;**[!UICONTROL First name]**&#x200B;字段。
1. 选择 **[!UICONTROL Filter on this field]**。

   ![](assets/data-model-index-example.png)

1. 对&#x200B;**[!UICONTROL Last name]**&#x200B;字段重复此操作。

两个对应的过滤器将添加到屏幕顶部。

![](assets/data-model-index-search.png)

您现在可以根据各种筛选条件对&#x200B;**[!UICONTROL First name]**&#x200B;和&#x200B;**[!UICONTROL Last name]**&#x200B;字段执行搜索筛选。

现在，您可以添加索引以加快对这些过滤器的搜索。 但应该使用哪些索引？

>[!NOTE]
>
>此示例适用于使用PostgreSQL数据库的托管客户。

下表显示了在哪些情况下，根据第一列中显示的访问模式使用或不使用下面描述的三个索引。

| 搜索条件 | 索引1（名+姓） | 索引2（仅名） | 索引3（仅姓氏） | 评论 |
|--- |--- |--- |--- |--- |
| 名字等于&quot;强尼&quot; | 已使用 | 已使用 | 未使用 | 由于名在索引1上处于第一位置，因此仍将使用它：无需在姓氏上添加标准。 |
| 名字等于&quot;Johnny&quot;，姓氏等于&quot;Smith&quot; | 已使用 | 未使用 | 未使用 | 由于两个属性都以同一查询搜索，因此将只使用组合这两个属性的索引。 |
| 姓氏等于“史密斯” | 未使用 | 未使用 | 已使用 | 索引中属性的顺序被考虑在内。 如果与此顺序不匹配，则可能无法使用索引。 |
| 带有“Joh”的名开始 | 已使用 | 已使用 | 未使用 | “左搜索”将启用索引。 |
| 名以“ny”结尾 | 未使用 | 未使用 | 未使用 | “右搜索”将禁用索引，并执行完整扫描。 某些特定索引类型可以处理此用例，但默认情况下在Adobe Campaign中不可用。 |
| 名字包含&quot;John&quot; | 未使用 | 未使用 | 未使用 | 这是“left”和“right”搜索的组合。 由于后者，它将禁用索引，并将执行完全扫描。 |
| 名字等于“john” | 未使用 | 未使用 | 未使用 | 索引区分大小写。 要使其不区分大小写，应创建包含SQL函数(如“upper(firstname)”)的特定索引。 您应该对其他数据转换(如“unaccent(firstname)”)执行同样的操作。 |

## 链接和基数{#links-and-cardinality}

### 链接 {#links}

谨防大桌上的“自身”诚信。 删除具有“自有”完整性的宽表的记录可以停止实例。 表已锁定，删除操作逐个完成。 因此，最好在具有大卷的子表上使用“中立”完整性。

声明链接为外部连接不利于性能。 零ID记录模拟外部连接功能。 如果链接使用autopk，则无需声明外部连接。

虽然可以在工作流中加入任何表，但Adobe建议直接在数据结构定义中定义资源之间的公用链接。

链接的定义应与表中的实际数据保持一致。 错误的定义可能会影响通过链接检索到的数据，例如意外重复记录。

使用表名一致地命名链接：链接名称应有助于了解远程表的内容。

请勿将链接命名为后缀为“id”。 例如，将其命名为“transaction”而不是“transactionId”。

默认情况下，Adobe Campaign将使用外部表的主键创建链接。 更清楚地说，最好在链接定义中显式定义连接。

索引将添加到链接中使用的属性。

The   “创建者”和“上次修改者”链接在许多表中都存在。 如果业务未使用此信息，则可以通过在链接上使用属性noDbIndex来禁用索引。

### 基数{#cardinality}

在设计链接时，请确保声明1-1关系时目标记录是唯一的。 否则，当仅需要一条记录时，连接可能会返回多个记录。 这会在准备投放时导致“查询返回的行数比预期的多”出现错误。 将链接名称设置为与目标模式相同的名称。

在(1)侧的模式中定义带基数(1-N)的链接。 例如，应在事务处理收件人中定义关系模式(1)-(N)事务处理。

请注意，默认情况下，链接的反向基数为(N)。 可以通过向链接定义中添加属性revCardinality=&#39;single&#39;来定义链接(1-1)。

如果用户不能看到反向链接，则可以使用链接定义revLink=&#39;_NONE_&#39;隐藏它。 这的一个好用例是定义从收件人到最后完成的事务的链接。 您只需查看从收件人到最后一个事务的链接，无需从事务表中看到任何反向链接。

执行外部连接(1-0.1)的链接应谨慎使用，因为它将影响系统性能。

## 数据保留 — 清除和清除{#data-retention}

Adobe Campaign既不是data warehouse，也不是报告工具。 因此，为确保Adobe Campaign解决方案的良好性能，数据库增长应保持可控。 为此，遵循以下一些最佳实践可能会有所帮助。

默认情况下，Adobe Campaign投放和跟踪日志的保留期为180天。 运行清除进程以删除任何早于该进程的日志。

* 如果希望保留日志的时间更长，应根据数据库大小和发送的消息量仔细作出此决定。 作为提醒，Adobe Campaign序列是32位整数。
* 建议在这些表中一次不要有超过10亿个记录（在21.4亿个可用ID中约有50%），以限制使用所有可用ID的风险。 这将要求某些客户将保留期限降低到180天以下。

了解有关[活动隐私和安全准则](https://helpx.adobe.com/cn/campaign/kb/campaign-privacy-overview.html#consent)中数据保留的更多信息。

在本节](../../production/using/database-cleanup-workflow.md)中了解有关活动数据库清理工作流[的更多信息。

>[!IMPORTANT]
>
>自定义表不会使用标准清除过程进行清除。 尽管在第一天可能不需要执行此操作，但不要忘记为自定义表构建清除流程，因为这可能会导致性能挑战。

有几种解决方案可以最大限度地减少对Adobe Campaign记录的需求：
* 将data warehouse导出到Adobe Campaign之外。
* 生成汇总值，这些值在满足您的营销实践需求的同时占用较少空间。 例如，您不需要Adobe Campaign中完整的客户交易记录历史记录来跟踪上次购买。

您可以在模式中声明“deleteStatus”属性。 将记录标记为已删除，然后在清除任务中延迟删除更为有效。

## 性能{#performance}

为确保在任何时间都能获得更好的性能，请遵循以下最佳实践。

### 一般建议 {#general-recommendations}

* 避免在查询中使用“CONTAINS”等操作。 如果您知道需要什么并希望筛选对象，请对“EQUAL TO”或其他特定筛选器运算符应用相同的条件。
* 在工作流中构建数据时，避免与非索引字段连接。
* 尝试确保诸如导入和导出等流程在工作时间外完成。
* 确保每日所有活动都有计划，并坚持计划。
* 如果每天有一个或几个进程失败，并且如果强制要求在同一天运行该进程，请确保在启动手动进程时没有运行冲突进程，因为这可能会影响系统性能。
* 确保在导入过程中或执行任何手动过程时，不运行任何每日活动。
* 使用一个或多个引用表，而不是在每行中复制字段。 使用键/值对时，最好选择数字键。
* 短字符串仍可接受。 如果外部系统中已有引用表，则重用引用表将有助于数据与Adobe Campaign的集成。

### 一对多关系{#one-to-many-relationships}

* 数据设计会影响可用性和功能。 如果您设计的数据模型具有许多一对多关系，则用户在应用程序中构建有意义的逻辑将更加困难。 对于非技术营销人员而言，一对多过滤逻辑可能难以正确构建和理解。
* 将所有基本字段放在一个表中是件好事，因为它使用户更容易构建查询。 有时，如果可以避免连接，则在表中重复某些字段也会对性能有好处。
* 某些内置功能将不能引用一对多关系，例如优惠加权公式和投放。

## 大表{#large-tables}

Adobe Campaign依赖第三方数据库引擎。 根据提供程序的不同，为较大的表优化性能可能需要特定的设计。

以下是在使用大表和复杂连接设计数据模型时应遵循的一些常见最佳实践。

* 使用其他自定义收件人表时，请确保每个投放映射都有专用的日志表。
* 减少列数，特别是通过识别未使用的列数。
* 通过避免复杂连接（如多个条件和/或多个列上的连接）来优化数据模型关系。
* 对于联接键，请始终使用数字数据而不是字符串。
* 尽可能减少日志保留深度。 如果需要更深入的历史记录，您可以聚合计算和/或处理自定义日志表以存储更大的历史记录。

### 表{#size-of-tables}的大小

表大小是记录数和每个记录的列数的组合。 两者都会影响查询的性能。

* **小型**&#x200B;表与投放表类似。
* **中等大小**&#x200B;表与收件人表的大小相同。 每位客户只有一份记录。
* **large-size**表与“广泛”日志表类似。 每位客户都有许多记录。
例如，如果您的收件人库包含1000万个投放，则Broad日志表包含约1亿到2亿条消息，而表包含几千条记录。

在PostgreSQL上，行不应超过8KB以避免[TOAST](https://wiki.postgresql.org/wiki/TOAST)机制。 因此，请尽量减少列数和每行的大小，以保持系统（内存和CPU）的最佳性能。

行数也会影响性能。 Adobe Campaign数据库并非设计用于存储不主动用于定位或个性化目的的历史数据 — 这是一个操作数据库。

要防止与高行数相关的任何性能问题，请仅在数据库中保留必要记录。 任何其他记录应导出到第三方data warehouse并从Adobe Campaign操作数据库中删除。

以下是有关表大小的一些最佳实践：

* 设计字段更少、数字数据更多的大型表。
* 请勿使用大数量的列类型(例如：Int64)存储布尔值等小数字。
* 从表定义中删除未使用的列。
* 请勿将历史或非活动数据保留在Adobe Campaign数据库中（导出和清理）。

以下是一个示例：

![](assets/transaction-table-example.png)

在此示例中：
* *事务*&#x200B;和&#x200B;*事务项*&#x200B;表较大：超过1000万。
* *Product*&#x200B;和&#x200B;*Store*&#x200B;表较小：不到一万。
* 产品标签和引用已放在&#x200B;*产品*&#x200B;表中。
* *事务项*&#x200B;表仅具有指向&#x200B;*产品*&#x200B;表的链接，该表是数字表。

<!--For more detailed best practices on how to optimize the database design for larger volumes, see [Campaign Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).-->
