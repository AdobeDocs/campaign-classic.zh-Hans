---
solution: Campaign Classic
product: campaign
title: 配置事件
description: 了解如何为自定义实施配置事件
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 0%

---


# 为自定义实施配置事件 {#events}

此配置的部分是自定义开发，需要：

* 在Adobe Campaign中分析JSON、XML和Javascript的工作知识。
* QueryDef和Writer API的工作知识。
* 使用私钥进行加密和身份验证的工作概念。

由于编辑Javascript代码需要技术技能，请在没有正确理解的情况下不要尝试。

## 在JavaScript中处理事件 {#events-javascript}

### JavaScript文件 {#file-js}

管道使用JavaScript函数处理每条消息。 此函数是用户定义的。

它在“JSConnector” **[!UICONTROL NmsPipeline_Config]** 属性下的选项中配置。 每次收到事件时都会调用此javascript。 它由流程运 [!DNL pipelined] 行。

示例Javascript文件为cus:triggers.js。

### JavaScript函数 {#function-js}

Javascript [!DNL pipelined] 必须开始特定的函数。

每个事件调用此函数一次：

```
function processPipelineMessage(xmlTrigger) {}
```

它应返回为

```
<undefined/>
```

您应在编 [!DNL pipelined] 辑Javascript后重新启动。

### 触发数据格式 {#trigger-format}

数 [!DNL trigger] 据以XML格式传递到JS函数。

* 属 **[!UICONTROL @triggerId]** 性包含名称 [!DNL trigger]。
* JSON **格式** 的扩充元素包含由Adobe Analytics生成的数据，并附加到触发器。
* **[!UICONTROL @offset]** 是消息的“指针”。 它指示消息在队列中的顺序。
* **[!UICONTROL @partition]** 是队列中消息的容器。 偏移量相对于分区。 <br>队列中有大约15个分区。

示例:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### 数据格式扩充 {#enrichment-format}

>[!NOTE]
>
>它是各种可能实现的一个特定示例。

内容在Adobe Analytics以JSON格式为每个触发器定义。
例如，在触发器LogoUpload_uploading_Victs中：

* **[!UICONTROL eVar01]** can contain Shopper ID in String format, is used to reconcile withAdobe Campaign收件人。 <br>它必须协调以查找Shopper ID，它是主键。

* **[!UICONTROL timeGMT]** 可以包含Adobe Analytics一侧触发时间（UTC Epoc格式）（自01/01/1970 UTC起的秒）。

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

### 事件处理订单{#order-events}

事件按偏移顺序一次处理一个。 每个线程处 [!DNL pipelined] 理不同的分区。

上次检索的事件的“偏移”存储在数据库中。 因此，如果进程停止，则从最后一条消息重新启动。 此模式存储在内置的xtk:pipelineOffset中。

此指针特定于每个实例和每个用户。 因此，当许多实例以不同的用户访问同一管道时，它们会以相同的顺序获得所有消息。

管道 **选项** 的使用者参数标识调用实例。

当前，无法为“暂存”或“开发”等单独环境设置不同的队列。

### 日志记录和错误处理 {#logging-error-handling}

日志(如logInfo())被定向到日 [!DNL pipelined] 志。 日志中写入了logError()等 [!DNL pipelined] 错误，导致事件被置于重试队列中。 在这种情况下，应检查管道日志。
错误消息在选项中设置的持续时间内重试 [!DNL pipelined] 多次。

为了调试和监控目的，完全触发数据以XML格式写入“data”字段的触发表。 或者，包含触发器数据的logInfo()也具有相同的用途。

### 解析数据 {#data-parsing}

此示例Javascript代码解析eVar中的扩充01。

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

### 存储触发器 {#storing-triggers-js}

>[!NOTE]
>
>它是各种可能实现的一个特定示例。

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

### 约束 {#constraints}

此代码的性能必须是最佳的，因为它运行于高频率，并可能对其他营销活动产生潜在负面影响。 尤其是当在营销服务器上每小时处理超过100万个触发事件，或者未正确调整时。

此Javascript的上下文有限。 并非API的所有功能都可用。 例如，getOption()或getCurrentdate()不起作用。

要实现更快的处理，将同时执行此脚本的多个线程。 代码必须是线程安全的。

## 存储事件 {#store-events}

>[!NOTE]
>
>它是各种可能实现的一个特定示例。

### 管道事件模式 {#pipeline-event-schema}

事件存储在数据库表中。 营销活动使用它来目标客户，并使用触发器丰富电子邮件。
尽管每个触发器都可以具有不同的数据结构，但所有触发器都可以放在一个表中。
triggerType字段标识数据从哪个触发器发起。

以下是此表的示例模式代码：

| 属性 | 类型 | 标签 | 说明 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | 长 | 主键 | 触发器的内部主键。 |
| 数据 | 备忘录 | 触发数据 | 以XML格式触发数据的完整内容。 用于调试和审核目的。 |
| triggerType | 字符串50 | TriggerType | 触发器的名称。 确定客户在网站上的行为。 |
| shopper_id | 字符串32 | shopper_id | 购物者的内部标识符。 由对帐工作流设置。 如果为零，则表示活动中的客户未知。 |
| shopper_key | 长 | shopper_key | Analytics捕获的购物者外部标识符。 |
| 已创建 | 日期时间 | 已创建 | 在活动中创建事件的时间。 |
| lastModified | 日期时间 | 上次修改时间 | 事件上次以Adobe修改的时间。 |
| timeGMT | 日期时间 | 时间戳 | 在Analytics中生成事件的时间。 |

### 显示事件 {#display-events}

事件可以基于事件模式以简单的形式显示。

>[!NOTE]
>
>管道事件节点未内置，需要添加，并且相关表单需要在活动中创建。 这些操作仅限专家用户。 有关此内容的详细信息，请参阅以下部分： [导航层次](../../configuration/using/about-navigation-hierarchy.md) 和 [编辑表单](../../configuration/using/editing-forms.md)。

![](assets/triggers_7.png)

## 处理事件 {#processing-the-events}

### 对帐工作流 {#reconciliation-workflow}

协调是将Adobe Analytics的客户匹配到Adobe Campaign数据库的过程。 例如，匹配的条件可以是shopper_id。

由于性能原因，匹配必须由工作流在批处理模式下完成。
必须将频率设置为15分钟，以优化工作量。 因此，在Adobe Campaign中的事件接收与由营销工作流处理之间的延迟最多为15分钟。

### JavaScript中的单元协调选项 {#options-unit-reconciliation}

可以在JavaScript中为每个触发器运行协调查询。 它对性能的影响更大，效果更快。 当需要反应性时，可能需要这种反应性。

如果未在shopper_id上设置索引，则可能难以实现。 如果标准位于与营销服务器不同的单独的数据库服务器上，则它使用数据库链接，该链接的性能很差。

### 清除工作流 {#purge-workflow}

触发器在一小时内得到处理。 每小时的触发量可达100万个。 它解释了清除工作流必须到位的原因。 清除每天运行一次，并删除所有早于三天的触发器。

### 活动工作流 {#campaign-workflow}

触发活动工作流通常类似于已使用的其他循环活动。
例如，它可以开始触发器上的查询，在最后一天查找特定事件。 该目标用于发送电子邮件。 扩充或数据可能来自触发器。 Marketing可以安全地使用它，因为它不需要配置。
