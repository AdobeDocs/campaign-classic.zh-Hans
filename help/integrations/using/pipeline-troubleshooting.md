---
product: campaign
title: '管道故障排除 '
description: '管道故障排除 '
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 1%

---

# 管道故障排除 {#pipeline-troubleshooting}

![](../../assets/common.svg)

**管道化失败，出现错误“没有任务与掩码管道化@&lt;实例>相对应”**

您的Adobe Campaign Classic版本不支持管道。

1. 检查 [!DNL pipelined] 元素存在于配置文件中。 如果不支持，则表示不支持。
1. 升级到Campaign 20.3 / [!DNL Gold Standard] 11或更高版本。

**使用“ aurait duty commencer par管道失败 `[` 欧 `{` (iRc=16384)”**

的 **NmsPipeline_Config** 选项。 这实际上是JSON解析错误。
在选项中设置JSON配置 **NmsPipeline_Config**. 请参阅此页面中的“路由选项”。

**管道化失败，出现“主体必须是有效的组织或客户”**

组织ID配置无效。

1. 检查是否在serverConf.xml中设置了组织ID(ImsOrgId)。
1. 检查实例配置文件中的空组织ID是否可以覆盖默认组织ID。 如果是，请将其删除。
1. 检查组织ID是否正确。 要查找您的组织ID，请参阅 [本页](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hans){_blank}

**管道化失败，出现“无效密钥”**

实例配置文件的@authPrivateKey参数不正确。

1. 检查是否已设置authPrivateKey。
1. 检查authPrivateKey:以@开头，以=结尾，大约长4000个字符。
1. 查找原始密钥，并确认其为：以RSA格式，长4096位，开头为 `-----BEGIN RSA PRIVATE KEY-----`.
   <br> 如有必要，请重新创建密钥，并在Adobe Analytics上注册。
1. 检查键是否在与 [!DNL pipelined]. <br>如有必要，请使用示例JavaScript或工作流重做编码。

**管道化失败，“身份验证期间无法读取令牌”**

私钥的格式无效。

1. 在此页面上运行密钥加密步骤。
1. 检查密钥是否在同一实例上加密。
1. 检查配置文件中的authPrivateKey是否与生成的密钥匹配。 <br>确保使用OpenSSL生成密钥对。 例如，PuttyGen不生成正确的格式。

**管道化失败，其中“不再允许获取访问令牌”**

日志应如下所示：

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

此错误消息表示身份验证是使用旧版Omniture基本OAuth配置的。 请参阅 [为Adobe Experience Cloud Triggers配置Adobe I/O](../../integrations/using/configuring-adobe-io.md) 文档以升级您的身份验证。

**不会检索任何触发器**

当 [!DNL pipelined] 进程正在运行，且未检索任何触发器：

1. 确保触发器在Analytics中处于活动状态，并且正在生成事件。
1. 确保 [!DNL pipelined] 进程正在运行。
1. 在 [!DNL pipelined] 日志。
1. 在 [!DNL pipelined] 状态页面。 触发器丢弃，触发器失败应为零。
1. 检查是否在 **[!UICONTROL NmsPipeline_Config]** 选项。 如有疑问，请使用通配符选项。
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

1. 检查 [!DNL pipelined] 进程正在运行。
1. 在pipelined.log中查找可能导致重试的错误。 修复错误（如果适用）。
1. 检查 [!DNL pipelined] “队列大小”的“状态”页。 如果队列大小较大，请提高JS的性能。
1. 由于延迟似乎随卷而增加，因此在Analytics上使用较少的消息配置触发器。

**将阶段实例从旧版身份验证升级到AdobeIO身份验证**

更改暂存实例上的集成身份验证不会影响生产实例的配置。 您可以选择升级您的Stage实例，然后更新身份验证以AdobeIO，并在Stage实例上测试触发器。

您的生产实例将继续使用旧版身份验证，且不会受此更改的影响。
