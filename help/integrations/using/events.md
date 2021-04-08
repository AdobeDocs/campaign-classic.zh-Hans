---
solution: Campaign Classic
product: campaign
title: 配置事件
description: 了解如何为自定义实施配置事件
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 0%

---

# 为自定义实施配置事件 {#events}

此配置的某些部分是自定义开发，需要：

* JSON、XML和Javascript分析方面的工作知识，Adobe Campaign。
* 有关QueryDef和Writer API的工作知识。
* 使用私钥进行加密和身份验证的工作概念。

由于编辑Javascript代码需要技术技能，请在没有适当理解的情况下不要尝试。

## 在JavaScript {#events-javascript}中处理事件

### JavaScript文件{#file-js}

管道使用JavaScript函数处理每条消息。 此函数是用户定义的。

它在“JSConnector”属性下的&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;选项中配置。 每次收到事件时都会调用此javascript。 它由[!DNL pipelined]进程运行。

示例Javascript文件为cus:triggers.js。

### JavaScript函数{#function-js}

[!DNL pipelined] Javascript必须与特定函数开始。

对每个事件调用此函数一次：

```
function processPipelineMessage(xmlTrigger) {}
```

它应返回

```
<undefined/>
```

您应在编辑Javascript后重新启动[!DNL pipelined]。

### 触发数据格式{#trigger-format}

[!DNL trigger]数据以XML格式传递给JS函数。

* **[!UICONTROL @triggerId]**&#x200B;属性包含[!DNL trigger]的名称。
* JSON格式的&#x200B;**扩充**&#x200B;元素包含Adobe Analytics生成的数据，并附加到触发器。
* **[!UICONTROL @offset]** 是消息的“指针”。它指示消息在队列中的顺序。
* **[!UICONTROL @partition]** 是队列中消息的容器。偏移量相对于分区。 <br>队列中大约有15个分区。

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
>它是各种可能实现的一个具体示例。

内容在Adobe Analytics中以JSON格式为每个触发器定义。
例如，在触发器LogoUpload_uploading_Vicits中：

* **[!UICONTROL eVar01]** can contain the Shopper ID in String format， whis used to reconcile with Adobe Campaign收件人。<br>It must be anovible to find the Shopper ID， which is the primary key.

* **[!UICONTROL timeGMT]** 可以包含Adobe Analytics端触发器的时间（UTC Epoc格式）(自01/01/1970 UTC以来的秒)。

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

事件按偏移顺序一次处理一次。 [!DNL pipelined]的每个线程都处理不同的分区。

上次检索的事件的“偏移”存储在数据库中。 因此，如果进程停止，则从最后一条消息重新启动。 此数据存储在内置模式xtk:pipelineOffset中。

此指针特定于每个实例和每个用户。 因此，当许多实例以不同的消费者访问同一管道时，它们会以相同的顺序获得所有消息。

管线选项的&#x200B;**consumer**&#x200B;参数标识调用实例。

目前，无法为“暂存”或“开发”等单独环境设置不同的队列。

### 日志记录和错误处理{#logging-error-handling}

日志(如logInfo())将定向到[!DNL pipelined]日志。 将logError()等错误写入[!DNL pipelined]日志，并导致事件被置于重试队列中。 在这种情况下，应检查流水线日志。
在[!DNL pipelined]选项中设置的持续时间中，多次重试发生错误的消息。

出于调试和监视目的，完整的触发器数据以XML格式写入“data”字段的触发器表中。 或者，包含触发器数据的logInfo()也具有相同的用途。

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

分析时要小心，以避免出错。
由于此代码用于所有触发器，因此大多数数据都不是必需的。 因此，当不存在时，它可以留空。

### 存储触发器{#storing-triggers-js}

>[!NOTE]
>
>它是各种可能实现的一个具体示例。

此示例JS代码将触发器保存到数据库。

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

### 约束{#constraints}

此代码的性能必须是最佳的，因为它以高频率运行，并可能对其他营销活动产生潜在的负面影响。 尤其是当在营销服务器上每小时处理超过100万个触发事件或未正确调整时。

此Javascript的上下文有限。 并非API的所有功能都可用。 例如，getOption()或getCurrentdate()不起作用。

要实现更快的处理，将同时执行此脚本的多个线程。 代码必须是线程安全的。

## 存储事件{#store-events}

>[!NOTE]
>
>它是各种可能实现的一个具体示例。

### 管道事件模式{#pipeline-event-schema}

事件存储在数据库表中。 营销活动使用它来目标客户，并使用触发器丰富电子邮件。
尽管每个触发器可以具有不同的数据结构，但所有触发器都可以放在一个表中。
triggerType字段标识数据从中发起触发器。

下面是此表的示例模式代码：

| 属性 | 类型 | 标签 | 说明 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | 长 | 主键 | 触发器的内部主键。 |
| 数据 | 备忘录 | 触发数据 | 以XML格式触发数据的完整内容。 用于调试和审核目的。 |
| triggerType | 字符串50 | TriggerType | 触发器的名称。 确定客户在网站上的行为。 |
| shopper_id | 字符串32 | shopper_id | The shopper&#39;s Internal Identifier. 由对帐工作流设置。 如果为零，则表示活动中的客户未知。 |
| shopper_key | 长 | shopper_key | Analytics捕获的购物者外部标识符。 |
| 已创建 | 日期时间 | 已创建 | 在活动中创建事件的时间。 |
| lastModified | 日期时间 | 上次修改时间 | 上次在Adobe中修改事件的时间。 |
| timeGMT | 日期时间 | 时间戳 | 在Analytics中生成事件的时间。 |

### 显示事件{#display-events}

事件可以基于事件模式以简单的表单显示。

>[!NOTE]
>
>管道事件节点未内置，需要添加，并且相关表单需要在活动中创建。 这些操作仅限专家用户。 有关此内容的详细信息，请参阅以下部分：[导航层次](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)。 和[编辑表单](../../configuration/using/editing-forms.md)。

![](assets/triggers_7.png)

## 正在处理事件{#processing-the-events}

### 协调工作流{#reconciliation-workflow}

对帐是将客户从Adobe Analytics匹配到Adobe Campaign数据库的过程。 例如，匹配的条件可以是shopper_id。

由于性能原因，匹配必须由工作流在批处理模式下完成。
必须将频率设置为15分钟以优化工作量。 因此，Adobe Campaign中的事件接收与营销工作流处理之间的延迟最多为15分钟。

### JavaScript {#options-unit-reconciliation}中的单元协调选项

可以在JavaScript中为每个触发器运行协调查询。 它对性能的影响更大，并且效果更快。 当需要反应性时，可能需要对特定用例进行反应。

如果shopper_id上未设置索引，则可能难以实现。 如果标准位于与营销服务器不同的单独数据库服务器上，则它使用数据库链接，因为该链接的性能较差。

### 清除工作流{#purge-workflow}

触发器将在一小时内得到处理。 该卷可以是每小时100万个触发器。 它解释了为什么必须设置清除工作流。 清除每天运行一次，并删除所有早于三天的触发器。

### 活动工作流{#campaign-workflow}

触发器活动工作流通常类似于已使用的其他循环活动。
例如，它可以在触发器上开始一个查询，在最后一天查找特定事件。 该目标用于发送电子邮件。 扩充或数据可能来自触发器。 Marketing可以安全地使用它，因为它不需要配置。
