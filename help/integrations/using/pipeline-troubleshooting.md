---
product: campaign
title: 配置集成
description: 配置集成
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 45a84e1bf43678bbc31d8bac15a7e6520204fdc2
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 1%

---

# 管道故障排除 {#pipeline-troubleshooting}

**管道化失败，出现错误“没有任务与掩码管道@&lt;>”**

您的Adobe Campaign Classic版本不支持管道。

1. 检查配置文件中是否存在[!DNL pipelined]元素。 如果不支持，则表示不支持。
1. 升级到Campaign 20.3或[!DNL Gold Standard] 11。

**管道失败，出现“ aurait duly commencer par  `[` ou( `{` iRc=16384)”**

未设置&#x200B;**NmsPipeline_Config**选项。 这实际上是JSON解析错误。
在选项**NmsPipeline_Config**&#x200B;中设置JSON配置。 请参阅此页面中的“路由选项”。

**管道化失败，出现“主体必须是有效的组织或客户”**

组织标识符配置无效。

1. 检查IMSOrgId是否在serverConf.xml中设置。
1. 在实例配置文件中查找可覆盖默认值的空IMSOrgId。 如果是，请将其删除。
1. 检查IMSOrgId是否与Experience Cloud中的客户IMSOrgId匹配。

**管道化失败，出现“无效密钥”**

实例配置文件的@authPrivateKey参数不正确。

1. 检查是否已设置authPrivateKey。
1. 检查authPrivateKey:以@开头，以=结尾，大约长4000个字符。
1. 查找原始密钥，并确认其为：在RSA格式中，4096位长，以 — BEGIN RSA PRIVATE KEY — 开头。
   <br> 如有必要，请重新创建密钥，并在Adobe Analytics上注册。
1. 检查键是否在与[!DNL pipelined]相同的实例内进行编码。 <br>如有必要，请使用示例JavaScript或工作流重做编码。

**管道化失败，“身份验证期间无法读取令牌”**

私钥的格式无效。

1. 在此页面上运行密钥加密步骤。
1. 检查密钥是否在同一实例上加密。
1. 检查配置文件中的authPrivateKey是否与生成的密钥匹配。 <br>确保使用OpenSSL生成密钥对。例如，PuttyGen不生成正确的格式。

**不会检索任何触发器**

当[!DNL pipelined]进程运行且未检索任何触发器时：

1. 确保触发器在Analytics中处于活动状态，并且正在生成事件。
1. 确保[!DNL pipelined]进程正在运行。
1. 在[!DNL pipelined]日志中查找错误。
1. 在[!DNL pipelined]状态页面中查找错误。 触发器丢弃，触发器失败应为零。
1. 检查触发器名称是否在&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;选项中配置。 如有疑问，请使用通配符选项。
1. 检查Analytics是否具有活动触发器并正在生成事件。 在Analytics中进行配置后，可能会延迟几个小时，才会激活配置。

**事件未与客户关联**

当某些事件未与客户关联时：

1. 检查协调工作流是否正在运行（如果适用）。
1. 检查事件是否包含客户ID。
1. 使用客户ID对客户表进行查询。
1. 检查客户导入的频率。 新客户会通过工作流导入到Adobe Campaign中。

**事件处理中的延迟**

当Analytics时间戳比Campaign中事件的创建日期早得多时。

通常，触发器可能需要15-90分钟才能启动营销活动。 这会因数据收集的实施、管道的加载、定义触发器的自定义配置以及Adobe Campaign中的工作流而异。

1. 检查[!DNL pipelined]进程是否正在运行。
1. 在pipelined.log中查找可能导致重试的错误。 修复错误（如果适用）。
1. 检查[!DNL pipelined]状态页以了解队列大小。 如果队列大小较大，请提高JS的性能。
1. 由于延迟似乎随卷而增加，因此在Analytics上使用较少的消息配置触发器。

**将阶段实例从旧版身份验证升级到AdobeIO身份验证**

更改暂存实例上的集成身份验证不会影响生产实例的配置。 您可以选择升级您的Stage实例，然后更新身份验证以AdobeIO，并在Stage实例上测试触发器。

您的生产实例将继续使用旧版身份验证，且不会受此更改的影响。
