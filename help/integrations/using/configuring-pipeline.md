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
translation-type: tm+mt
source-git-commit: 3e73d7c91fbe7cff7e1e31bdd788acece5806e61
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 1%

---


# 配置管道 {#configuring-pipeline}

身份验证参数（如客户ID、私钥和身份验证端点）在实例配置文件中进行配置。
要处理的触发器列表在JSON格式的选项中进行配置。
触发器用于通过发送电子邮件的活动工作流进行定位。 设置活动，以便同时触发事件的客户收到电子邮件。

>[!CAUTION]
>
>如果是混合部署，请确保在中间实例上配置管道。

## 先决条件{#prerequisites}

在活动 [!DNL Experience Cloud Triggers] 中使用需要：

* Adobe Campaign19.1.9版本或20.3.1.及更高版本。
* Analytics Standard版本。

先决条件配置包括：

* AdobeIO项目身份验证
* IMSOrgId，添加了Experience Cloud客户的Adobe Analytics标识符。
* 供应团队必须对客户的IMS组织具有系统管理员权限
* Adobe Analytics的触发器配置。

## 身份验证和配置文件 {#authentication-configuration}

由于管道托管在Adobe Experience Cloud，因此需要身份验证。
它使用一对公钥和私钥。 此过程与用户／密码功能相同，但更安全。
支持通过Marketing CloudIO项目对Adobe进行身份验证。

## 第1步：创建／更新AdobeIO项目 {#creating-adobe-io-project}

对于托管客户，您可以创建客户关怀票证，以便为您的组织启用AdobeIO技术帐户令牌以进行触发器集成。

对于内部部署客户，请参阅为 [Adobe Experience Cloud触发器配置Adobe](../../integrations/using/configuring-adobe-io.md) IO页。 请注意，在向AdobeIO **[!UICONTROL Adobe Analytics]** 凭据添加API时，您需要进行选择。

## 第2步：配置NmsPipeline_Config管道选项 {#configuring-nmspipeline}

设置身份验证后，管道将检索事件。 它将仅处理以Adobe Campaign配置的触发器。 触发器必须是从Adobe Analytics生成的，并被推至管道，该管道将仅处理以Adobe Campaign配置的触发器。
也可以使用通配符配置该选项，以捕获所有触发器，而不管其名称如何。

1. 在Adobe Campaign中，访问> **[!UICONTROL Administration]** > **[!UICONTROL Platform]** 下的 **[!UICONTROL Options]** 选项菜 **[!UICONTROL Explorer]**&#x200B;单。

1. 选择选 **[!UICONTROL NmsPipeline_Config]** 项。

1. 在该字 **[!UICONTROL Value (long text)]** 段中，您可以粘贴以下指定两个触发器的JSON代码。 您需要确保删除注释。

   ```
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
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

1. 您还可以选择粘贴以下可捕获所有触发器的JSON代码。

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

### Consumer参数 {#consumer-parameter}

管道的工作方式类似于供应商和消费者模型。 消息仅用于单个消费者：每个消费者都会收到自己的消息副本。

Consumer **** （消费者）参数将实例标识为这些消费者之一。 实例的标识将调用管道。 您可以用实例名称填充该实例，该名称可在客户端控制台的“监视”页面上找到。

管道服务跟踪每个消费者检索到的消息。 对不同实例使用不同的使用者可确保将每个消息发送到每个实例。

### 管道选项建议 {#pipeline-option-recommendation}

要配置管道选项，您应遵循以下建议：

* 在下面添加或编 **[!UICONTROL Triggers]**&#x200B;辑触发器，您不应编辑其余的。
* 确保JSON有效。 您可以使用JSON验证程序，例 [如](http://jsonlint.com/) ，参阅此网站。
* “name”与触发器ID对应。 通配符“*”将捕获所有触发器。
* “消费者”与调用实例或应用程序的名称相对应。
* Pipelined还支持“别名”主题。
* 进行更改后，应始终重新启动管道。

## 第3步：可选配置 {#step-optional}

您可以根据负载要求更改一些内部参数，但请确保在将它们投入生产之前对其进行测试。

可选参数的列表如下所示：

| 选项 | 说明 |
|:-:|:-:|
| appName（传统） | 在上传公钥的Legacy Oath应用程序中注册的OAuth应用程序的AppID。 For more on this, refer to this [page](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint（传统） | 获取网关令牌的URL。 默认： ```https://api.omniture.com``` |
| authPrivateKey（传统） | 私钥，上传到Legacy Oath应用程序中的公共部分，AES使用XtkKey选项进行加密： ```cryptString("PRIVATE_KEY")``` |
| disableAuth（旧版） | 禁用身份验证，在没有网关令牌的情况下进行连接只会被某些开发管道端点接受。 |
| discoverPipelineEndpoint | 用于查找要用于此租户的Pipeline Services端点的URL。 默认： ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | 内部状态中内部状态进程的两个转储 ```var/INSTANCE/pipelined.json.``` 之 <br> 间的期间也可在以下位置按需访问： ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | 禁用对PipelineServicesEndpoint的检测以强制它 |
| monitorServerPort | 管道化进程将监听此端口以提供内部状态进程： ```http://INSTANCE:PORT/pipelined/status```. <br>默认为7781 |
| pointerFlushMessageCount | 处理此数量的消息时，偏移将保存在数据库中。 <br> 默认值为1000 |
| pointerFlushPeriodSec | 在此期间后，偏移将保存在数据库中。 <br>默认值为5（秒） |
| processingJSThreads | 使用自定义JS连接器处理消息的专用线程数。 <br> 默认值为4 |
| processingThreads | 使用内置代码处理消息的专用线程数。 <br>默认值为4 |
| retryPeriodSec | 处理错误时重试之间的延迟。 <br>默认值为30（秒） |
| retryValiditySec | 如果消息在此时段后未成功处理(重试过多)，请放弃消息。 <br>默认值为300（秒） |

### 流水线处理自动开始 {#pipelined-process-autostart}

需要自动启动流水线处理。

为此，在配置文件中将&lt; pipelined >元素设置为autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### 流水线处理重启 {#pipelined-process-restart}

更改生效需要重新启动：

```
nlserver restart pipelined@instance
```

## 第4步：验证 {#step-validation}

要验证管道设置以进行设置，请执行以下步骤：

* 确保进 [!DNL pipelined] 程正在运行。
* 检查pipelined.log是否有管道连接日志。
* 验证连接，并检查是否收到ping。 托管客户可以从客户端控制台使用监视。
