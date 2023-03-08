---
product: campaign
title: 管道选项 NmsPipeline_Config
description: 管道选项 NmsPipeline_Config
audience: integrations
content-type: reference
source-git-commit: 36b10a49fe92853f98beeb9e7d2fea3f59b10b6f
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 3%

---


# 管道选项 NmsPipeline_Config {#nmspipeline_config}

![](../../assets/common.svg)

一旦验证成功， [!DNL pipelined] 可以检索事件并对其进行处理。 它仅处理Adobe Campaign中配置的触发器，而忽略其他触发器。 触发器必须预先从Analytics生成并推送到管道。
也可以使用通配符配置选项，以捕获所有触发器，而不管其名称如何。

触发器的配置是在一个选项中完成的，位于 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**. 选项名称为 **[!UICONTROL NmsPipeline_Config]**. 数据类型是JSON格式的“长文本”。

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
>此 [!DNL Trigger] Analytics界面中特定触发器名称的UID值可以作为Triggers界面中URL查询字符串参数的一部分找到。 triggerType UID在管道数据流中传递，并且代码可以写入pipeline.JS中，以将触发器UID映射到用户友好的标签，该标签可以存储在pipelineEvents架构的“触发器名称”列中。

## 使用者参数 {#consumer-parameter}

该管道适用于“供应商和消费者”模型。 同一队列中可能有许多消费者。 消息仅供个人消费者“使用”。 每个消费者都有其自己的报文“副本”。

“consumer”参数将实例标识为这些使用者之一。 它是调用管道的实例的标识。 可以使用实例名称填充它。 管道服务会跟踪每个使用者检索的消息。 对不同实例使用不同的使用者，可确保将每条消息都发送到每个实例。

## 如何配置管道选项 {#configure-pipeline-option}

在“触发器”数组下添加或编辑Experience Cloud触发器；不要编辑其余触发器。
借助此功能，确保JSON有效 [网站](https://jsonlint.com/).

* &quot;name&quot;是触发器ID。 通配符“*”可捕获所有触发器。
* “Consumer”是任何唯一标识nlserver实例的字符串。 它通常可以是实例名称本身。 对于多个环境（开发/暂存/生产），请确保每个环境都具有唯一性，以便每个实例都获得消息的副本。
* [!DNL Pipelined] 还支持“别名”主题。

重新启动 [!DNL pipelined] 进行更改之后。
