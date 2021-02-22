---
solution: Campaign Classic
product: campaign
title: 配置集成
description: 配置集成
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 1%

---


# 管道故障排除 {#pipeline-troubleshooting}

**流水线失败，出现错误“没有任务与掩码流水线对应@&lt;>”**

您的Adobe Campaign Classic版本不支持该管道。

1. 检查配置文件中是否存在[!DNL pipelined]元素。 否则，表示不支持它。
1. 升级到活动 20.3或Gold Standard 11。

**Pipelined fails with &quot; aurait dcommencer par  `[` ou( `{` iRc=16384)&quot;**

未设置&#x200B;**NmsPipeline_Config**选项。 这实际上是JSON解析错误。
在选项**NmsPipeline_Config**&#x200B;中设置JSON配置。 请参阅本页中的“路由选项”。

**管道失败，“主题必须是有效的组织或客户”**

组织标识符配置无效。

1. 检查是否在serverConf.xml中设置了IMSOrgId。
1. 在实例配置文件中查找可以覆盖默认值的空IMSOrgId。 如果是，请删除它。
1. 检查IMSOrgId是否与Experience Cloud中的客户匹配。

**管道失败，且“无效密钥”**

实例配置文件的@authPrivateKey参数不正确。

1. 检查是否已设置authPrivateKey。
1. 检查authPrivateKey:带@的开始，以=结尾，长度为4000个字符。
1. 查找原始密钥并确认其为：采用RSA格式，4096位长，开始使用 — BEGIN RSA PRIVATE KEY —。
   <br> 如有必要，请重新创建密钥并在Adobe Analytics上注册。
1. 检查密钥是否与[!DNL pipelined]在同一实例中进行编码。 <br>如有必要，请使用示例JavaScript或工作流重做编码。

**“身份验证期间无法读取令牌”**

私钥的格式无效。

1. 在此页上运行密钥加密步骤。
1. 检查同一实例上的密钥是否已加密。
1. 检查配置文件中的authPrivateKey是否与生成的密钥匹配。 <br>确保使用OpenSSL生成密钥对。例如，PuttyGen不生成正确的格式。

**未检索任何触发器**

当[!DNL pipelined]进程正在运行且未检索任何触发器时：

1. 确保触发器在Analytics中处于活动状态并正在生成事件。
1. 确保[!DNL pipelined]进程正在运行。
1. 在[!DNL pipelined]日志中查找错误。
1. 在[!DNL pipelined]状态页中查找错误。 触发器被丢弃，触发器故障应为零。
1. 检查在&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;选项中是否配置了触发器名称。 如有疑问，请使用通配符选项。
1. 检查Analytics是否具有活动触发器并正在生成事件。 在Analytics中进行配置后，在处于活动状态之前，可能会延迟几个小时。

**事件未与客户链接**

当某些事件未与客户链接时：

1. 检查对帐工作流是否正在运行（如果适用）。
1. 检查事件是否包含客户ID。
1. 使用客户ID在客户表上进行查询。
1. 检查客户导入的频率。 新客户将通过工作流导入Adobe Campaign。

**事件处理中的延迟**

当Analytics时间戳比活动中事件的创建日期早得多时。

通常，触发器启动营销活动可能需要15-90分钟。 这取决于数据收集的实现、管线上的加载、定义触发器的自定义配置以及Adobe Campaign中的工作流。

1. 检查[!DNL pipelined]进程是否正在运行。
1. 在pipelined.log中查找可能导致重试的错误。 修复错误（如果适用）。
1. 检查[!DNL pipelined]状态页以了解队列大小。 如果队列大，请提高JS的性能。
1. 由于延迟似乎随卷而增加，因此在Analytics上使用较少的消息配置触发器。
