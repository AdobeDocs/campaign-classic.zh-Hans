---
product: campaign
title: 配置事件
description: 了解如何为自定义实施配置事件
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 0%

---

# 为自定义实施配置事件 {#events}

此配置的部分内容是自定义开发，需要满足以下条件：

* 在Adobe Campaign中解析JSON、XML和Javascript的工作知识。
* QueryDef和Writer API的工作知识。
* 使用私钥进行加密和身份验证的工作概念。

由于编辑Javascript代码需要技术技能，因此在没有适当了解的情况下，请勿尝试编辑代码。

## 在JavaScript中处理事件{#events-javascript}

### JavaScript文件{#file-js}

管道使用JavaScript函数处理每条消息。 此函数是用户定义的。

它在&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;选项中“JSConnector”属性下进行配置。 每次收到事件时都会调用此javascript。 它由[!DNL pipelined]进程运行。

示例Javascript文件为cus:triggers.js。

### JavaScript函数{#function-js}

[!DNL pipelined] Javascript必须以特定函数开头。

对每个事件调用一次此函数：

```
function processPipelineMessage(xmlTrigger) {}
```

它应返回为

```
<undefined/>
```

应在编辑Javascript后重新启动[!DNL pipelined]。

### 触发数据格式{#trigger-format}

[!DNL trigger]数据以XML格式传递到JS函数。

* **[!UICONTROL @triggerId]**&#x200B;属性包含[!DNL trigger]的名称。
* JSON格式的&#x200B;**enrichments**&#x200B;元素包含由Adobe Analytics生成的数据，并附加到触发器。
* **[!UICONTROL @offset]** 是消息的“指针”。它指示消息在队列中的顺序。
* **[!UICONTROL @partition]** 是队列中的消息容器。偏移相对于分区。 <br>队列中大约有15个分区。

示例:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### 数据格式扩充{#enrichment-format}

>[!NOTE]
>
>它是各种可能实施中的一个特定示例。

在Adobe Analytics中，对于每个触发器，内容都以JSON格式定义。
例如，在触发器LogoUpload_uploading_Visits中：

* **[!UICONTROL eVar01]** 可以包含字符串格式的购物者ID，该格式用于与Adobe Campaign收件人进行协调。<br>必须协调以找到购物者ID，该ID是主键。

* **[!UICONTROL timeGMT]** 可以包含Adobe Analytics端触发器的时间（以UTC Epoc格式表示）(自UTC 01/01/1970以来的秒数)。

示例:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### 事件处理顺序{#order-events}

事件按偏移的顺序一次处理一次。 [!DNL pipelined]的每个线程都处理不同的分区。

检索到的最后一个事件的“offset”存储在数据库中。 因此，如果进程停止，则从最后一条消息重新启动。 此数据存储在内置模式xtk:pipelineOffset中。

此指针专用于每个实例和每个用户。 因此，当多个实例通过不同的用户访问同一管道时，它们会以相同的顺序获取所有消息。

管道选项的&#x200B;**consumer**&#x200B;参数标识调用实例。

目前，无法为不同的环境（如“暂存”或“开发”）设置不同的队列。

### 日志记录和错误处理{#logging-error-handling}

日志(如logInfo())会定向到[!DNL pipelined]日志。 将logError()等错误写入[!DNL pipelined]日志，并导致该事件被置于重试队列中。 在这种情况下，应检查管道日志。
错误消息在[!DNL pipelined]选项中设置的持续时间内重试多次。

出于调试和监控目的，完整的触发器数据将以XML格式写入触发器表的“data”字段中。 或者，包含触发器数据的logInfo()也具有相同的用途。

### 解析数据{#data-parsing}

此示例Javascript代码解析扩充中的eVar01。

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

在解析时要谨慎，以避免出现错误。
由于此代码用于所有触发器，因此大多数数据都不是必需的。 因此，当不存在时，可将其留空。

### 存储触发器{#storing-triggers-js}

>[!NOTE]
>
>它是各种可能实施中的一个特定示例。

此示例JS代码会将触发器保存到数据库。

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>;
 }
```

### 约束 {#constraints}

此代码的性能必须是最佳的，因为它以高频率运行，并且可能会对其他营销活动产生潜在的负面影响。 特别是当在营销服务器上每小时处理超过100万个触发事件，或者未正确调整时。

此Javascript的上下文受限。 并非API的所有函数都可用。 例如，getOption()或getCurrentdate()不起作用。

为了加快处理速度，将同时执行此脚本的多个线程。 代码必须是线程安全的。

## 存储事件{#store-events}

>[!NOTE]
>
>它是各种可能实施中的一个特定示例。

### 管道事件架构{#pipeline-event-schema}

事件存储在数据库表中。 营销活动使用它来定位客户，并使用触发器扩充电子邮件。
尽管每个触发器可以具有不同的数据结构，但所有触发器都可以放在一个表格中。
triggerType字段标识数据源自哪个触发器。

下面是此表的模式代码示例：

| 属性 | 类型 | 标签 | 说明 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | 长 | 主键 | 触发器的内部主键。 |
| 数据 | 备忘录 | 触发数据 | 以XML格式触发数据的完整内容。 用于调试和审核。 |
| triggerType | 字符串50 | TriggerType | 触发器的名称。 标识客户在网站上的行为。 |
| shopper_id | 字符串32 | shopper_id | 购物者的内部标识符。 由协调工作流设置。 如果为零，则表示客户在Campaign中为未知。 |
| shopper_key | 长 | shopper_key | 由Analytics捕获的购物者外部标识符。 |
| 已创建 | 日期时间 | 已创建 | 在Campaign中创建事件的时间。 |
| lastModified | 日期时间 | 上次修改时间 | 上次在Adobe中修改事件的时间。 |
| timeGMT | 日期时间 | 时间戳 | 在Analytics中生成事件的时间。 |

### 显示事件{#display-events}

事件可以基于事件架构以简单的形式显示。

>[!NOTE]
>
>管道事件节点未内置，需要添加，并且需要在Campaign中创建相关表单。 这些操作仅限专家用户。 有关更多信息，请参阅以下章节：[导航层次结构](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)。 和[编辑表单](../../configuration/using/editing-forms.md)。

![](assets/triggers_7.png)

## 处理事件{#processing-the-events}

### 协调工作流{#reconciliation-workflow}

协调是将客户从Adobe Analytics匹配到Adobe Campaign数据库的过程。 例如，匹配的标准可以是shopper_id。

出于性能原因，匹配必须由工作流在批处理模式下完成。
必须将频率设置为15分钟才能优化工作负载。 因此，Adobe Campaign中的事件接收与营销工作流处理事件之间的延迟最长为15分钟。

### JavaScript中用于单元协调的选项{#options-unit-reconciliation}

可以在JavaScript中为每个触发器运行协调查询。 它对性能的影响更大，并且提供更快的结果。 当需要反应性时，可要求对特定用例进行反应。

如果未对shopper_id设置索引，则可能很难实施。 如果标准位于与营销服务器不同的单独数据库服务器上，则它使用数据库链接，因为该链接的性能不佳。

### 清除工作流{#purge-workflow}

触发器将在一小时内得到处理。 该卷的触发次数可以是每小时100万次。 它解释了为什么必须实施清除工作流。 清除每天运行一次，并删除所有超过三天的触发器。

### 营销活动工作流{#campaign-workflow}

触发器促销活动工作流程通常与已使用的其他定期促销活动类似。
例如，它可以从触发器上的查询开始，查找最后一天的特定事件。 该目标用于发送电子邮件。 扩充或数据可能来自触发器。 由于无需任何配置，因此营销人员可以安全地使用它。
