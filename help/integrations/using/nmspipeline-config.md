---
title: 配置集成
seo-title: 配置集成
description: 配置集成
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9957dabca4c63d504a3d06cf527a97b79fee46d5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# 管道选项NmsPipeline_Config {#nmspipeline_config}

一旦验证工作正常，管道可以检索事件并进行处理。 它只处理以Adobe Campaign配置的触发器，而忽略其他触发器。 触发器必须是Analytics发出的，并事先被推上管道。
也可以使用通配符配置该选项，以捕获所有触发器（无论名称如何）。

触发器的配置在选项中完成，位于 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** >下 **[!UICONTROL Options]**。 选项名称为 **[!UICONTROL NmsPipeline_Config]**。 数据类型为JSON格式的“长文本”。

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
>在Analytics [!DNL Trigger] 接口中，特定触发器名称的UID值可以作为触发器接口中URL查询字符串参数的一部分找到。 triggerType UID在管道数据流中传递，代码可写入pipeline.JS中，将触发器UID映射到用户友好标签，该标签可存储在pipelineEvents模式的“触发器名称”列中。

## 用户参数 {#consumer-parameter}

该管道采用“供应商和消费者”模式。 同一队列中可能有许多消费者。 消息仅用于单个消费者。 每个消费者都会收到自己的“邮件副本”。

“consumer”参数将实例标识为这些用户之一。 它是调用管道的实例的标识。 您可以用实例名称填充它。 管道服务跟踪每个消费者检索到的消息。 对不同实例使用不同的使用者可确保将每个消息发送到每个实例。

## 如何配置管道选项 {#configure-pipeline-option}

在“触发器”数组下添加或编辑Experience Cloud触发器； 不要编辑其余内容。
确保在此网站的帮助下JSON有效 [](http://jsonlint.com/)。

* “name”是触发器ID。 通配符“*”捕获所有触发器。
* “Consumer”是唯一标识nlserver实例的唯一字符串。 它通常可以是实例名称本身。 对于多个环境(dev/stage/prod)，请确保每个实例都具有唯一性，以便每个实例都获得消息的副本。
* 管道还支持“别名”主题。

进行更改后重新启动管道。
