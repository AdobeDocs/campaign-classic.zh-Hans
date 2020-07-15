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
source-git-commit: 0112d5bd052ad66169225073276d1da4f3c245d8
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 0%

---


# 管道疑难解答 {#pipeline-troubleshooting}

**管道失败，错误为“没有任务与掩码管道@对应”**

您的Adobe Campaign经典版本不支持该管道。

1. 检查配置 [!DNL pipelined] 文件中是否存在元素。 否则，表示不支持。
1. 升级到版本6.11内部版本8705或更高版本。

**“aurait dcommencer par &#39;[&#39; ou &#39;{&#39;(iRc=16384)”**

未 **设置NmsPipeline** _Config选项。 这实际上是JSON解析错误。
在选项NmsPipeline_Config中设 **置JSON配置**。 请参阅本页中的“路由选项”。

**管道化失败，“主题必须是有效的组织或客户”**

IMSOrgid配置无效。

1. 检查IMSOrgId是否在serverConf.xml中设置。
1. 在实例配置文件中查找可覆盖默认值的空IMSOrgId。 如果是，请删除它。
1. 检查IMSOrgId是否与Experience Cloud中的客户匹配。

**管道失败，“无效密钥”**

实例配置文件的@authPrivateKey参数不正确。

1. 检查是否已设置authPrivateKey。
1. 检查authPrivateKey: 带@的开始，以=结尾，长度约为4000个字符。
1. 查找原始密钥并检查其是否为： 以RSA格式、4096位长和开始—BEGIN RSA PRIVATE KEY —。
   <br> 如有必要，请重新创建密钥并在AdobeAnalytics注册。 请参阅此 [部分](../../integrations/using/configuring-pipeline.md#oauth-client-creation)。
1. 检查密钥是否在与相同的实例中进行编码 [!DNL pipelined]。 <br>如有必要，请使用示例JavaScript或工作流重做编码。

**管道化失败，“身份验证期间无法读取令牌”**

私钥的格式无效。

1. 在此页面上运行密钥加密步骤。
1. 检查同一实例上的密钥是否已加密。
1. 检查配置文件中的authPrivateKey是否与生成的密钥匹配。 <br>确保使用OpenSSL生成密钥对。 例如，PuttyGen不生成正确的格式。

**未检索任何触发器**

当进程 [!DNL pipelined] 运行且没有检索任何触发器时：

1. 确保触发器在Analytics处于活动状态并正在生成事件。
1. 确保进程 [!DNL pipelined] 正在运行。
1. 在日志中查找 [!DNL pipelined] 错误。
1. 在状态页面中查 [!DNL pipelined] 找错误。 触发器丢弃，触发器故障应为零。
1. 检查是否在选项中配置了触发 **[!UICONTROL NmsPipeline_Config]** 器名称。 如有疑问，请使用通配符选项。
1. 检查Analytics是否有主动触发器并正在生成事件。 配置在Analytics完成后，可能会延迟几个小时，然后才会激活。

**事件未与客户关联**

当某些事件未与客户链接时：

1. 检查对帐工作流是否正在运行（如果适用）。
1. 检查事件是否包含客户ID。
1. 使用客户ID在客户表上创建查询。
1. 检查客户导入的频率。 新客户将通过工作流导入Adobe Campaign。

**事件处理中的延迟**

当Analytics时间戳比活动中事件的创建日期早得多时。

通常，触发可能需要15-90分钟才能启动营销活动。 这取决于数据收集的实现、管线上的加载、定义触发器的自定义配置以及Adobe Campaign中的工作流。

1. 检查进 [!DNL pipelined] 程是否正在运行。
1. 在pipelined.log中查找可能导致重试的错误。 修复错误（如果适用）。
1. 检查队 [!DNL pipelined] 列大小的状态页。 如果队列大，请提高JS的性能。
1. 由于延迟似乎随卷的增加而增加，因此在Analytics使用较少的消息配置触发器。
附件

**如何使用密钥加密JavaScript**

运行JavaScript以加密私钥。 管线配置需要它。

以下是可用于运行cryptString函数的代码示例：

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

在服务器上执行Javascript:

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

将输出中的编码密钥复制并粘贴到控制台。