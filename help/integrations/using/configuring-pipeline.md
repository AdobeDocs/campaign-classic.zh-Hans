---
product: campaign
title: 配置管道
description: 了解如何配置管道
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 6a5253c1aa35e904635919f6c863930d376b473f
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 1%

---

# 配置管道 {#configuring-pipeline}

在实例配置文件中配置了身份验证参数，如客户ID、私钥和身份验证端点。
要处理的触发器列表是以JSON格式的选项配置的。
触发器用于通过发送电子邮件的营销活动工作流进行定位。 营销活动已设置，以便同时具有触发器事件的客户会收到电子邮件。

>[!CAUTION]
>
>对于混合部署，请确保在中间实例上配置了管道。

## 先决条件 {#prerequisites}

在开始此配置之前，请检查您使用的是：

* 至少，以下Adobe Campaign内部版本之一：
   * 19.1.8.9039
   * 19.1.4.9032 - Gold Standard 11
   * 20.2.4.9187
   * 20.3.1
* Adobe Analytics Standard版本

您还需要：

* Adobe I/O项目身份验证
* 有效的IMSOrgID ，即添加了Adobe Analytics的Experience Cloud客户的标识符
* 开发人员访问IMS组织
* 触发器配置在Adobe Analytics中完成

## 身份验证和配置文件 {#authentication-configuration}

由于管道托管在Adobe Experience Cloud中，因此需要进行身份验证。
它使用一对公钥和私钥。 此过程与用户/密码具有相同的功能，但更加安全。
Marketing Cloud支持通过Adobe I/O项目进行身份验证。

## 步骤1:创建/更新Adobe I/O项目 {#creating-adobe-io-project}

对于托管客户，您可以创建客户关怀票证，以便为您的组织启用Adobe I/O技术帐户令牌以用于触发器集成。

对于On Premise客户，请参阅[为Adobe Experience Cloud Triggers配置Adobe I/O](../../integrations/using/configuring-adobe-io.md)页面。 请注意，在将API添加到Adobe I/O凭据时，您需要选择&#x200B;**[!UICONTROL Adobe Analytics]**。

## 步骤2:配置NmsPipeline_Config管道选项 {#configuring-nmspipeline}

设置身份验证后，管道将检索事件。 它将仅处理在Adobe Campaign中配置的触发器。 触发器必须是从Adobe Analytics生成，并推送到管道，该管道将仅处理在Adobe Campaign中配置的触发器。
也可以使用通配符配置选项，以便无论名称如何都捕获所有触发器。

1. 在Adobe Campaign中，访问&#x200B;**[!UICONTROL Explorer]**&#x200B;中&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;下的选项菜单。

1. 选择&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;选项。

1. 在&#x200B;**[!UICONTROL Value (long text)]**&#x200B;字段中，您可以粘贴以下JSON代码，该代码指定两个触发器。 您需要确保删除注释。

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

管道的工作方式类似于供应商和消费者模型。 消息仅供个人消费者使用：每个消费者都有自己的报文副本。

**Consumer**&#x200B;参数将实例标识为这些使用者之一。 实例的标识将调用管道。 您可以使用实例名称进行填充，该实例名称可在客户端控制台的“监视”页面上找到。

管道服务会跟踪每个消费者检索到的消息。 通过对不同实例使用不同的使用者，您可以确保将每条消息发送到每个实例。

### 管道选项建议 {#pipeline-option-recommendation}

要配置管道选项，您应遵循以下建议：

* 在&#x200B;**[!UICONTROL Triggers]**&#x200B;下添加或编辑触发器，则不应编辑其余触发器。
* 确保JSON有效。 您可以使用JSON验证器，例如，请参阅此[website](http://jsonlint.com/)。
* “name”对应于触发器ID。 通配符“*”将捕获所有触发器。
* “消费者”对应于调用实例或应用程序的名称。
* 管道化还支持“别名”主题。
* 进行更改后，应始终重新启动管道。

## 步骤3:可选配置 {#step-optional}

您可以根据负载要求更改一些内部参数，但请确保在将其投入生产之前对其进行测试。

可选参数列表可在以下位置找到：

| 选项 | 说明 |
|:-:|:-:|
| appName（旧版） | 在上传公钥的旧版Oath应用程序中注册的OAuth应用程序的应用程序ID。 有关更多信息，请参阅此[页面](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint（旧版） | 用于获取网关令牌的URL。 默认：```https://api.omniture.com``` |
| authPrivateKey（旧版） | 私钥是Legacy Oath应用程序中上传的公共部分，AES使用XtkKey选项进行加密：```cryptString("PRIVATE_KEY")``` |
| disableAuth（旧版） | 禁用身份验证时，仅某些开发管道端点会接受在不使用网关令牌的情况下进行连接。 |
| discoverPipelineEndpoint | 用于查找要用于此租户的Pipeline Services端点的URL。 默认：```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | ```var/INSTANCE/pipelined.json.``` <br>内部状态进程的两个转储之间的时间段。内部状态也可以在此处根据需要访问：```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | 禁用对PipelineServicesEndpoint的检测以强制执行 |
| monitorServerPort | 流水线进程将监听此端口，以在此处提供内部状态进程：```http://INSTANCE:PORT/pipelined/status```。 <br>默认为7781 |
| pointerFlushMessageCount | 处理此数量的消息时，偏移将保存在数据库中。 <br> 默认值为1000 |
| pointerFlushPeriodSec | 在此期间之后，偏移将保存在数据库中。 <br>默认值为5（秒） |
| processingJSThreads | 使用自定义JS连接器处理消息的专用线程数。 <br> 默认值为4 |
| processingThreads | 使用内置代码处理消息的专用线程数。 <br>默认值为4 |
| retryPeriodSec | 在发生处理错误时，重试之间会延迟。 <br>默认值为30（秒） |
| retryValiditySec | 如果在此时间段后未成功处理消息（重试过多），请放弃该消息。 <br>默认值为300（秒） |

### 流水线处理自动启动 {#pipelined-process-autostart}

需要自动启动流水线处理。

为此，请将配置文件中的&lt; pipelined >元素设置为autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### 流水线流程重启 {#pipelined-process-restart}

更改需要重新启动才能生效：

```
nlserver restart pipelined@instance
```

## 步骤4:验证 {#step-validation}

要验证管道设置以进行预配，请执行以下步骤：

* 确保[!DNL pipelined]进程正在运行。
* 检查pipelined.log中的管道连接日志。
* 验证连接并检查是否收到ping。 托管客户可以从客户端控制台中使用监控。
