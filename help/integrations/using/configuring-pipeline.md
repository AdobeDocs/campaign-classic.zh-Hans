---
product: campaign
title: 配置管道
description: 了解如何配置管道
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 2%

---

# 配置管道 {#configuring-pipeline}

![](../../assets/common.svg)

在实例配置文件中配置客户ID、私钥和身份验证端点等身份验证参数。
要处理的触发器列表是以JSON格式的选项配置的。
触发器由发送电子邮件的营销活动工作流用于定位。 活动设置为让具有两个触发事件的客户收到电子邮件。

## 先决条件 {#prerequisites}

在启动此配置之前，请检查您是否使用：

* 最小值，以下Adobe Campaign构建之一：
   * 19.1.8.9039
   * 19.1.4.9032 - Gold Standard 11
   * 20.2.4.9187
   * 20.3.1
* Adobe Analytics Standard版本

您还需要：

* Adobe I/O项目身份验证
* 有效的组织ID — 要查找您的组织ID，请参阅 [此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans){_blank}
* 开发人员对贵组织的访问权限
* 在Adobe Analytics中完成触发器配置

## 身份验证和配置文件 {#authentication-configuration}

由于管道托管在Adobe Experience Cloud中，因此需要身份验证。
它使用一对公钥和私钥。 此进程与用户/密码具有相同的功能，但更安全。
Marketing Cloud支持通过Adobe I/O项目进行身份验证。

## 步骤1：创建/更新Adobe I/O项目 {#creating-adobe-io-project}

对于托管客户，您可以创建一个客户关怀票证，以便为贵组织启用Adobe I/OTriggers集成的技术帐户令牌。

对于内部部署客户，请参阅 [为Adobe Experience Cloud Triggers配置Adobe I/O](../../integrations/using/configuring-adobe-io.md) 页面。 请注意，您需要选择 **[!UICONTROL Adobe Analytics]** 将API添加到Adobe I/O凭据时。

## 步骤2：配置NmsPipeline_Config管道选项 {#configuring-nmspipeline}

设置身份验证后，管道将检索事件。 它只会处理在Adobe Campaign中配置的触发器。 触发器必须从Adobe Analytics生成，并推送到管道，这将仅处理Adobe Campaign中配置的触发器。
也可以使用通配符配置选项，以捕获所有触发器，而不管其名称如何。

1. 在Adobe Campaign中，访问 **[!UICONTROL Administration]** > **[!UICONTROL Platform]**  > **[!UICONTROL Options]** 在 **[!UICONTROL Explorer]**.

1. 选择 **[!UICONTROL NmsPipeline_Config]** 选项。

1. 在 **[!UICONTROL Value (long text)]** 字段中，您可以粘贴以下JSON代码，这会指定两个触发器。 您需要确保删除注释。

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

1. 您还可以选择粘贴以下捕获所有触发器的JSON代码。

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

管道的工作方式类似于供应商和消费者模型。 消息仅供个人消费者使用：每个消费者都有自己的消息副本。

此 **消费者** parameter将实例标识为这些使用者之一。 实例的标识将调用管道。 您可以使用实例名称来填充，该名称可在客户端控制台的“监视”页面上找到。

管道服务会跟踪每个使用者检索的消息。 对不同实例使用不同的使用者，可确保将每条消息都发送到每个实例。

### 管道选项建议 {#pipeline-option-recommendation}

要配置管道选项，您应遵循以下建议：

* 在下面添加或编辑触发器 **[!UICONTROL Triggers]**，则不应编辑其余部分。
* 确保JSON有效。 您可以使用JSON验证器，请参阅此 [网站](https://jsonlint.com/) 例如。
* “name”对应于触发器ID。 通配符“*”将捕获所有触发器。
* “使用者”对应于调用实例或应用程序的名称。
* 管道化还支持“别名”主题。
* 进行更改后，应始终重新启动管道。

## 步骤3：可选配置 {#step-optional}

您可以根据负载要求更改某些内部参数，但请确保在将这些参数投入生产之前对其进行测试。

可选参数列表如下所示：

| Option | 说明 |
|:-:|:-:|
| appName（旧版） | 在上传公钥的旧版Oath应用程序中注册的OAuth应用程序的AppID。 有关更多信息，请参阅此[页面](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint（旧版） | 用于获取网关令牌的URL。 默认: ```https://api.omniture.com``` |
| authPrivateKey（旧版） | 私钥、旧版Oath应用程序中上传的公共部分、使用XtkKey选项加密的AES： ```cryptString("PRIVATE_KEY")``` |
| disableAuth（旧版） | 禁用身份验证，没有网关令牌的连接将仅被某些开发管道端点接受。 |
| discoverPipelineEndpoint | 用于查找要用于此租户的管道服务端点的URL。 默认: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | 中的两个内部状态进程转储之间的周期 ```var/INSTANCE/pipelined.json.``` <br> 内部状态也可在此处按需访问： ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | 禁用检测PipelineServicesEndpoint以强制执行该操作 |
| monitorServerPort | 管道化进程将侦听此端口，以在此处提供内部状态进程： ```http://INSTANCE:PORT/pipelined/status```. <br>默认为7781 |
| pointerFlushMessageCount | 在处理此数量的消息时，偏移将保存在数据库中。 <br> 默认值为1000 |
| pointerFlushperiodSec | 在此时段后，偏移将保存在数据库中。 <br>默认为5（秒） |
| processingJSThreads | 使用自定义JS连接器处理消息的专用线程数。 <br> 默认为4 |
| processingThreads | 使用内置代码处理消息的专用线程数。 <br>默认为4 |
| retryPeriodSec | 发生处理错误时，重试之间的延迟。 <br>默认为30（秒） |
| retryValidSec | 如果在此时段后未成功处理消息（重试次数过多），则放弃该消息。 <br>默认值为300（秒） |

### 流水线进程自动启动 {#pipelined-process-autostart}

管道化进程需要自动启动。

为此，请将配置文件中的&lt; pipelined >元素设置为autostart=&quot;true&quot;：

```
 <pipelined autoStart="true" ... "/>
```

### 管道化进程重新启动 {#pipelined-process-restart}

需要重新启动才能使更改生效：

```
nlserver restart pipelined@instance
```

## 步骤4：验证 {#step-validation}

要验证用于配置的管道设置，请执行以下步骤：

* 确保 [!DNL pipelined] 进程正在运行。
* 检查pipelined.log以获取管道连接日志。
* 验证连接以及是否收到ping。 托管客户可以从客户端控制台使用监控。
