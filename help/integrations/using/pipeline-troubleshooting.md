---
product: campaign
title: 管道故障排除
description: 管道故障排除
feature: Triggers
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# 管道故障排除 {#pipeline-troubleshooting}



**管道化失败，错误为“没有任务对应到掩码管道化@&lt;实例>”**

您的Adobe Campaign Classic版本不支持该管道。

1. 检查配置文件中是否存在[!DNL pipelined]元素。 如果不支持，则表示不支持它。
1. 升级到Campaign 20.3 / [!DNL Gold Standard] 11或更高版本。

**管道化失败，出现“ aurait du commencer par `[` ou `{` (iRc=16384)”**

未设置&#x200B;**NmsPipeline_Config**选项。 这实际上是一个JSON解析错误。
在选项**NmsPipeline_Config**&#x200B;中设置JSON配置。 请参阅本页的“路由选项”。

**管道化失败，原因是“主题必须是有效的组织或客户端”**

组织ID配置无效。

1. 检查在serverConf.xml中是否设置了组织ID (ImsOrgId)。
1. 检查实例配置文件中的空组织ID是否可以覆盖默认组织ID。 如果是，请删除它。
1. 检查组织ID是否正确。 要查找您的组织ID，请参阅[此页面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans){_blank}

**管道化失败，出现“无效键”**

实例配置文件的@authPrivateKey参数不正确。

1. 检查是否已设置authPrivateKey。
1. 检查authPrivateKey：是否以@开头，以=结尾，并且长度约为4000个字符。
1. 查找原始密钥并检查它是否为：RSA格式，4096位长，以`-----BEGIN RSA PRIVATE KEY-----`开头。
   <br>如有必要，请重新创建密钥并在Adobe Analytics上注册它。
1. 检查密钥是否在与[!DNL pipelined]相同的实例中进行编码。 <br>如有必要，请使用示例JavaScript或工作流重做编码。

**管道化失败，因为“在身份验证期间无法读取令牌”**

私钥的格式无效。

1. 在此页上运行密钥加密步骤。
1. 检查密钥是否已在同一实例上加密。
1. 检查配置文件中的authPrivateKey是否与生成的密钥匹配。 <br>确保使用OpenSSL生成密钥对。 例如，PuttyGen不生成正确的格式。

**管道化失败，“不再允许获取访问令牌”**

日志应如下所示：

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

此错误消息表示使用旧版Omniture基本OAuth配置身份验证。 请参阅[为Adobe Experience Cloud Triggers配置Adobe I/O](../../integrations/using/about-triggers.md#implement)文档以升级您的身份验证。

**未检索到任何触发器**

当[!DNL pipelined]进程正在运行且未检索到触发器时：

1. 确保触发器在Analytics中处于活动状态并正在生成事件。
1. 确保[!DNL pipelined]进程正在运行。
1. 在[!DNL pipelined]日志中查找错误。
1. 在[!DNL pipelined]状态页中查找错误。 trigger-discarted， trigger-failures应为0。
1. 检查触发器名称是否在&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;选项中配置。 如有疑问，请使用通配符选项。
1. 检查Analytics是否具有活动的触发器并正在生成事件。 在Analytics中进行配置后，该配置在处于活动状态之前可能会延迟几个小时。

**事件未链接到客户**

当某些事件未链接到客户时：

1. 如果适用，检查协调工作流是否正在运行。
1. 检查事件是否包含客户ID。
1. 使用客户ID查询customer表。
1. 检查客户导入的频率。 新客户会通过工作流导入Adobe Campaign。

**事件处理延迟**

当Analytics时间戳比Campaign中事件的创建日期晚得多时。

通常，触发器可能需要15到90分钟的时间来启动营销活动。 此时间根据数据收集的实施、管道的加载、定义触发器的自定义配置以及Adobe Campaign中的工作流而有所不同。

1. 检查[!DNL pipelined]进程是否正在运行。
1. 在pipelined.log中查找可能导致重试的错误。 修复错误（如果适用）。
1. 检查[!DNL pipelined]状态页面以了解队列大小。 如果队列大小很大，则提高JS的性能。
1. 由于延迟似乎随着流量而增加，请在Analytics上使用较少的消息配置触发器。

**正在将阶段实例从旧身份验证升级到AdobeIO身份验证**

更改暂存实例上的集成身份验证不会影响生产实例的配置。 您可以选择升级暂存实例，然后更新身份验证以AdobeIO，并在暂存实例上测试触发器。

您的生产实例将继续使用旧版身份验证，并且不会受到此更改的影响。
