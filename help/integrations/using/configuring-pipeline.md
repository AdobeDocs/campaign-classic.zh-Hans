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
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 3%

---


# 配置管道 {#configuring-pipeline}

身份验证参数（如客户ID、私钥和身份验证端点）在实例配置文件中进行配置。
要处理的触发器列表在选项中进行配置。 它采用JSON格式。
触发器会立即使用Javascript代码进行处理。 它将保存到数据库表中，无需进行进一步的实时处理。
触发器用于通过发送电子邮件的活动工作流进行定位。 设置活动，以便同时触发事件的客户收到电子邮件。

## 先决条件{#prerequisites}

在活动 [!DNL Experience Cloud Triggers] 中使用需要：

* Adobe Campaign版本6.11内部版本8705或更高版本。
* Adobe Analytics Ultimate、Premium、Foundation、OD、Select、Prime、Mobile Apps、Select 或 Standard。

先决条件配置包括：

* 创建私钥文件，然后创建用该密钥注册的Oauth应用程序。
* Adobe Analytics的触发器配置。

Adobe Analytics配置超出本文档的范围。

Adobe Campaign需要Adobe Analytics提供以下信息：

* 身份验证应用程序的名称。
* IMSOrgId,Experience Cloud客户的标识符。
* 在Analytics中配置的触发器的名称。
* 要与Marketing数据库协调的数据字段的名称和格式。

此配置的一部分是自定义开发，需要：

* 在Adobe Campaign中分析JSON、XML和Javascript的工作知识。
* QueryDef和Writer API的工作知识。
* 使用私钥进行加密和身份验证的工作概念。

>[!NOTE]
>
>由于编辑JS代码需要技术技能，因此在没有适当理解的情况下不要尝试。 <br>触发器将保存到数据库表。 因此，营销运营商可以安全地使用触发工作流。

## 身份验证和配置文件 {#authentication-configuration}

由于管道托管在Adobe Experience Cloud，因此需要身份验证。
如果Marketing Server是在事先托管的，则当它登录到Pipeline时，它必须进行身份验证才能建立安全连接。
它使用一对公钥和私钥。 此过程与用户／密码功能相同，只是更加安全。

### IMSOrgId {#imsorgid}

IMSOrgId是Adobe Experience Cloud上客户的标识符。
在实例serverConf.xml文件中，在IMSOrgId属性下设置它。
示例:

```
<redirection IMSOrgId="C5E715(…)98A4@AdobeOrg" (…)
```

### 密钥生成 {#key-generation}

密钥是一对文件。 它采用RSA格式，长4096字节。 它可以使用开放源代码工具（如OpenSSL）生成。 每次运行该工具时，都会随机生成一个新键。
为方便起见，下面列出了这些步骤：

* ```openssl genrsa -out <private_key.pem> 4096```

* ```openssl rsa -pubout -in <private_key.pem> -out <public_key.pem>```

示例private_key.pem文件：

```
----BEGIN RSA PRIVATE KEY----
MIIEowIBAAKCAQEAtqcYzt5WGGABxUJSfe1Xy8sAALrfVuDYURpdgbBEmS3bQMDb
(…)
64+YQDOSNFTKLNbDd+bdAA+JoYwUCkhFyvrILlgvlSBvwAByQ2Lx
----END RSA PRIVATE KEY----
```

公共密钥。pem文件示例：

```
----BEGIN PUBLIC KEY----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtqcYzt5WGGABxUJSfe1X
(…)
EwIDAQAB
----END PUBLIC KEY----
```

>[!NOTE]
>
>密钥不应由PuttyGen生成，OpenSSL是最佳选择。

### 在Adobe Experience Cloud创建身份验证客户端 {#oauth-client-creation}

需要通过登录>下正确的组织帐户中的Adobe Analytics来创建JWT类型的应用 **[!UICONTROL Admin]** 程 **[!UICONTROL User Management]** 序 **[!UICONTROL Legacy Oath application]**。

按照以下步骤操作：

1. 选择 **[!UICONTROL Service Account (JWT Assertion)]**。
1. 输入 **[!UICONTROL Application Name]**。
1. 注册 **[!UICONTROL Public key]**。
1. 选择触发器 **[!UICONTROL Scopes]**。

   ![](assets/triggers_5.png)

1. 单击并 **[!UICONTROL Create]** 检查已创 **[!UICONTROL Application ID]** 建的 **[!UICONTROL Application Secret]** 页面。

   ![](assets/triggers_6.png)

### Adobe Campaign Classic申请名注册 {#application-name-registration}

创建的身份验证客户端的应用程序 ID必须以Adobe Campaign配置。 您可以通过在元素中编辑实例配置文件( [!DNL pipelined] 尤其是appName属性)来完成此操作。

示例:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### 密钥加密 {#key-encription}

要供使用， [!DNL pipelined]必须加密私钥。 加密是使用cryptString Javascript函数完成的，必须对与相同的实例执行 [!DNL pipelined]。

本页中提供了使用JavaScript进行私钥加密的 [示例](../../integrations/using/pipeline-troubleshooting.md)。

加密的私钥必须以Adobe Campaign注册。 您可以通过编辑元素中的实例配置文件( [!DNL pipelined] 特别是authPrivateKey属性)来执行此操作。

示例:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### 流水线处理自动开始 {#pipelined-auto-start}

该 [!DNL pipelined] 进程必须自动启动。
为此，请将配置文件中的元素设置为autostart=&quot;true&quot;:

```
<pipelined autoStart="true" appName="applicationID" authPrivateKey="@qQf146pexBksGvo0esVIDO(…)"/>
```

### 流水线处理重启 {#pipelined-restart}

还可以使用命令行手动启动它：

```
nlserver start pipelined@instance
```

更改生效需要重新启动：

```
nlserver restart pipelined@instance
```

如果出错，请在标准输出（如果您手动启动）或日志文件中查找 [!DNL pipelined] 错误。 有关解决问题的详细信息，请参阅本文档的“疑难解答”部分。

### 流水线配置选项 {#pipelined-configuration-options}

| 选项 | 说明 |
|:-:|:-:|
| appName | 在Adobe Analytics注册的OAuth应用程序(应用程序 ID)的ID（其中上传了公钥）:“管理员”>“用户管理”>“旧版宣誓应用程序”。 Refer to this [section](../../integrations/using/configuring-pipeline.md#oauth-client-creation). |
| authGatewayEndpoint | 获取“网关令牌”的URL。 <br> 默认：https://api.omniture.com |
| authPrivateKey | 私钥(在Adobe Analytics上传的公共部件（请参阅本节）。 使用XtkSecretKey选项加密的AES:xtk.session.EncryptPassword(&quot;PRIVATE_KEY&quot;); |
| disableAuth | 禁用身份验证（仅某些开发管道端点接受不带网关令牌的连接） |
| discoverPipelineEndpoint | 用于发现要用于此租户的Pipeline Services端点的URL。 默认：https://producer-pipeline-pnw.adobe.net |
| dumpStatePeriodSec | 在var/INSTANCE/pipelined.json内部状态下的2个进程内部状态转储之间的期间也可在http://INSTANCE/pipelined/status（端口7781）按需访问。 |
| forcedPipelineEndpoint | 禁用发现PipelineServicesEndpoint并强制它 |
| monitorServerPort | 进 [!DNL pipelined] 程监听此端口以提供进程内部状态，网址为http://INSTANCE/pipelined/status（端口7781）。 |
| pointerFlushMessageCount | 处理此数量的消息时，偏移量将保存在数据库中。 默认值为1000 |
| pointerFlushPeriodSec | 在此期间后，偏移将保存在数据库中。 默认值为5（秒） |
| processingJSThreads | 使用自定义JS连接器处理消息的专用线程数。 默认值为4 |
| processingThreads | 使用内置代码处理消息的专用线程数。 默认值为4 |
| retryPeriodSec | 重试之间的延迟（如果存在处理错误）。 默认值为30（秒） |
| retryValiditySec | 如果消息在此时段后未成功处理(重试过多)，请放弃消息。 默认值为300（秒） |
