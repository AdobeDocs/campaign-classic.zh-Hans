---
product: campaign
title: 配置事件
description: 了解如何为自定义实施配置事件
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 1%

---

# 为自定义实施配置事件 {#events}



此配置的组成部分是自定义开发，需要满足以下条件：

* 了解Adobe Campaign中的JSON、XML和Javascript解析的工作知识。
* QueryDef和Writer API的工作知识。
* 使用私钥进行加密和身份验证的工作概念。

由于编辑Javascript代码需要技术技能，因此在没有适当了解的情况下请勿尝试这样做。

## 在JavaScript中处理事件 {#events-javascript}

### JavaScript文件 {#file-js}

Pipeline使用JavaScript函数处理每条消息。 此函数由用户定义。

它可在中进行配置 **[!UICONTROL NmsPipeline_Config]** “JSConnector”属性下的选项。 每次收到事件时都会调用此JavaScript。 它由 [!DNL pipelined] 进程。

示例Javascript文件为cus：triggers.js。

### JavaScript 函数 {#function-js}

此 [!DNL pipelined] Javascript必须以特定函数开头。

此函数为每个事件调用一次：

```
function processPipelineMessage(xmlTrigger) {}
```

它应返回为

```
<undefined/>
```

您应该重新启动 [!DNL pipelined] 在编辑Javascript之后。

### 触发数据格式 {#trigger-format}

此 [!DNL trigger] 数据以XML格式传递到JS函数。

* 此 **[!UICONTROL @triggerId]** 属性包含 [!DNL trigger].
* 此 **丰富** JSON格式的元素包含Adobe Analytics生成的数据，并附加到触发器。
* **[!UICONTROL @offset]** 是消息的“指针”。 它指示消息在队列中的顺序。
* **[!UICONTROL @partition]** 是队列中的消息容器。 偏移相对于分区。 <br>队列中有大约15个分区。

例如：

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### 数据格式扩充 {#enrichment-format}

>[!NOTE]
>
>这是来自各种可能实施的具体示例。

在Adobe Analytics中为每个触发器定义了JSON格式的内容。
例如，在触发器LogoUpload_uploading_Visits中：

* **[!UICONTROL eVar01]** 可以包含字符串格式的购物者ID，此ID用于与Adobe Campaign收件人进行协调。 <br>必须对其进行协调才能找到购物者ID，它是主键。

* **[!UICONTROL timeGMT]** 可以在Adobe Analytics端以纪元格式包含触发器的时间（自UTC时间01/01/1970以来的秒数）。

例如：

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

按偏移量顺序逐个处理事件。 每个线程的 [!DNL pipelined] 处理不同的分区。

检索的最后一个事件的“offset”存储在数据库中。 因此，如果进程停止，它会从上一条消息重新启动。 此数据存储在内置模式xtk：pipelineOffset中。

此指针特定于每个实例和每个使用者。 因此，当多个实例使用不同的使用者访问同一管道时，它们都会按相同的顺序获取所有消息。

此 **消费者** 管线选项的参数标识调用实例。

目前，无法为单独的环境（例如“暂存”或“开发”）设置不同的队列。

### 日志记录和错误处理 {#logging-error-handling}

诸如logInfo()之类的日志将被定向到 [!DNL pipelined] 日志。 诸如logError()之类的错误将写入 [!DNL pipelined] 记录并使该事件被放入重试队列。 在这种情况下，您应该检查管道化日志。
出错的消息会在中设置的持续时间内重试多次 [!DNL pipelined] 选项。

出于调试和监控目的，完整的触发器数据以XML格式写入“数据”字段的触发器表中。 或者，包含触发器数据的logInfo()也可达到相同目的。

### 解析数据 {#data-parsing}

此示例Javascript代码解析扩充功能中的eVar01。

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

解析时要小心，以免出现错误。
由于此代码用于所有触发器，因此大部分数据不是必需的。 因此，当不存在时，可以将其留空。

### 存储触发器 {#storing-triggers-js}

>[!NOTE]
>
>这是来自各种可能实施的具体示例。

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

此代码的性能必须最佳，因为它以高频率运行，可能会对其他营销活动产生潜在的负面影响。 特别是如果每小时在营销服务器上处理超过100万次会触发事件，或者未正确优化该服务器。

此Javascript的上下文有限。 并非该API的所有函数都可用。 例如，getOption()或getCurrentdate()不起作用。

为了加快处理速度，将同时执行此脚本的多个线程。 代码必须是线程安全的。

## 存储事件 {#store-events}

>[!NOTE]
>
>这是来自各种可能实施的具体示例。

### 管道事件架构 {#pipeline-event-schema}

事件存储在数据库表中。 营销活动使用该功能来定位客户，并通过触发器丰富电子邮件。
虽然每个触发器可以具有独特的数据结构，但所有触发器都可以保存在单个表中。
triggerType字段标识数据来源的触发器。

以下是此表的模式代码示例：

| 属性 | 类型 | 标签 | 说明 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | 长 | 主键 | 触发器的内部主键。 |
| 数据 | 备注 | 触发数据 | XML格式的触发器数据的完整内容。 用于调试和审核。 |
| triggerType | 字符串50 | TriggerType | 触发器的名称。 标识客户在网站上的行为。 |
| shopper_id | 字符串32 | shopper_id | 购物者的内部标识符。 由协调工作流设置。 如果为0，则表示在Campaign中未知该客户。 |
| shopper_key | 长 | shopper_key | 购物者的Analytics捕获的外部标识符。 |
| 已创建 | 日期时间 | 已创建 | 在Campaign中创建事件的时间。 |
| lastModified | 日期时间 | 上次修改时间 | 上次在Adobe中修改事件的时间。 |
| 时间GMT | 日期时间 | 时间戳 | 在Analytics中生成事件的时间。 |

### 显示事件 {#display-events}

事件可以通过基于事件架构的简单表单显示。

>[!NOTE]
>
>管道事件节点不是内置节点，需要添加，并且需要在Campaign中创建相关表单。 这些操作仅限专家用户执行。 有关更多信息，请参阅以下章节： [导航层次结构](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy). 和 [编辑表单](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## 处理事件 {#processing-the-events}

### 协调工作流 {#reconciliation-workflow}

协调是将客户从Adobe Analytics匹配到Adobe Campaign数据库的过程。 例如，匹配的条件可以是shopper_id。

出于性能原因，必须通过工作流以批处理模式进行匹配。
频率必须设置为15分钟以优化工作负载。 因此，在Adobe Campaign中接收事件到营销工作流处理该事件之间的延迟最长为15分钟。

### JavaScript中单元协调的选项 {#options-unit-reconciliation}

可以在JavaScript中为每个触发器运行协调查询。 它有更高的性能影响并提供更快的结果。 对于需要反应性的特定用例，可能需要此参数。

如果未对shopper_id设置索引，则可能难以实施。 如果标准与营销服务器位于不同的数据库服务器上，则它会使用性能较差的数据库链接。

### 清除工作流 {#purge-workflow}

触发器在小时内处理。 该数量大约可达每小时100万次触发。 它解释了必须设置清除工作流的原因。 清除每天运行一次，并删除所有超过三天的触发器。

### 活动工作流 {#campaign-workflow}

触发活动工作流通常与其他已使用的定期活动类似。
例如，它可以从对触发器的查询开始，在最后一天查找特定事件。 该目标用于发送电子邮件。 “扩充”或“数据”可能来自触发器。 营销人员可以安全地使用它，因为它不需要进行配置。
