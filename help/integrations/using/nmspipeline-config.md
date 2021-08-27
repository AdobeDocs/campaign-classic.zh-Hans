---
product: campaign
title: 配置集成
description: 配置集成
audience: integrations
content-type: reference
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 2%

---


# 管道选项 NmsPipeline_Config {#nmspipeline_config}

![](../../assets/common.svg)

验证完成后，[!DNL pipelined]可以检索事件并处理它们。 它仅处理在Adobe Campaign中配置的触发器，而忽略其他触发器。 触发器必须事先从Analytics生成并推送到管道。
也可以使用通配符配置选项，以捕获所有触发器（无论其名称如何）。

触发器的配置在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;下的选项中完成。 选项名称为&#x200B;**[!UICONTROL NmsPipeline_Config]**。 数据类型为JSON格式的“长文本”。

此示例指定两个触发器。

将此模板中的JSON代码粘贴到选项值中。 确保删除注释。

```
{
    "topics": [ // list of "topics" that the pipelined is listening to.
        {
            "name": "triggers", // Name of the first topic: triggers.
            "consumer": "customer_dev", // Name of the instance that listens. 
            "triggers": [ // Array of triggers. 
                {
                    "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                    "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
                }, {
                    "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                    "jsConnector": "cus:triggers.js" // Can use the same JS for all.
                },
            ]
        }
    ]
}
```

第二个示例捕获所有触发器。

```
{
 "topics": [
    {
      "name": "triggers",
      "consumer":  "customer_dev",
      "triggers": [
        {
          "name": "*",
          "jsConnector": "cus:pipeline.js"
        }
      ]
    }
 ]
 }
```

>[!NOTE]
>
>在Analytics界面中，特定触发器名称的[!DNL Trigger] UID值可作为URL查询字符串参数的一部分在Triggers界面中找到。 triggerType UID在管道数据流中传递，并且可以将代码写入pipeline.JS中，以将触发器UID映射到用户友好标签，该标签可以存储在pipelineEvents架构的“触发器名称”列中。

## 使用者参数 {#consumer-parameter}

管道与“供应商和消费者”模型配合使用。 同一队列中可能有许多消费者。 仅对单个消费者“使用”消息。 每个消费者都会获得自己的“报文副本”。

“consumer”参数将实例标识为这些用户之一。 它是调用管道的实例的标识。 您可以使用实例名称进行填充。 管道服务会跟踪每个消费者检索到的消息。 对不同实例使用不同的使用者可确保将每个消息发送到每个实例。

## 如何配置管道选项 {#configure-pipeline-option}

在“触发器”数组下添加或编辑Experience Cloud触发器；请勿编辑其余内容。
确保JSON在此[website](http://jsonlint.com/)的帮助下有效。

* “name”是触发器ID。 通配符“*”捕获所有触发器。
* “消费者”是唯一标识nlserver实例的任何唯一字符串。 它通常可以是实例名称本身。 对于多个环境（开发/暂存/生产），请确保每个环境具有唯一性，以便每个实例都获得消息的副本。
* [!DNL Pipelined] 还支持“别名”主题。

进行更改后，重新启动[!DNL pipelined]。
