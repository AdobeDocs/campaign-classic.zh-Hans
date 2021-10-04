---
product: campaign
title: 配置URL权限
description: 了解如何配置URL权限
audience: installation
content-type: reference
topic-tags: additional-configurations
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 29%

---

# 配置URL权限（内部部署）{#url-permissions}

![](../../assets/v7-only.svg)

Campaign Classic 实例可以通过 JavaScript 代码（工作流等）调用的 URL 默认列表是有限的。这些 URL 允许实例正常运行。

默认情况下，实例不允许连接到外部 URL。但是，可以向经授权的URL列表添加一些外部URL，以便您的实例可以连接到这些URL。 这允许您将 Campaign 实例连接到外部系统，例如 SFTP 服务器或网站，以启用文件和/或数据传输。

>[!NOTE]
>
>此过程仅限于&#x200B;**on-premise**&#x200B;部署。
>
>作为&#x200B;**托管的**&#x200B;客户，如果您可以访问[促销活动控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)，则可以使用URL权限自助服务界面。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=zh-Hans)
>
>其他&#x200B;**混合/托管**&#x200B;客户需要联系Adobe支持团队以将IP添加到允许列表。

对于&#x200B;**Hybrid**&#x200B;和&#x200B;**本地**&#x200B;部署，管理员需要在&#x200B;**serverConf.xml**&#x200B;文件中引用新的&#x200B;**urlPermission**。


提供了三种连接保护模式：

* **阻止**:所有不属于该的URL都允许列表将被阻止，并显示一则错误消息。这是升级后的默认模式。
* **许可**:允许所有不属于该允许列表的URL。
* **警告**:所有不属于该的URL都允许列表是允许的，但JS解释器会发出警告，以便管理员可以收集它们。此模式会添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>默认情况下，新实施使用&#x200B;**Blocking**&#x200B;模式。
>
>作为来自迁移的现有客户，您可以临时使用&#x200B;**警告**&#x200B;模式。 在允许URL之前分析出站流量。 定义允许的URL列表后，您可以将URL添加到允许列表并激活&#x200B;**Blocking**&#x200B;模式。

有关更多信息，请参阅以下章节：

* [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [托管模型](hosting-models.md)
* [Campaign 服务器配置](configuring-campaign-server.md)
* [Campaign服务器配置文件参数](the-server-configuration-file.md)
* [安全和隐私检查列表](get-started-security-privacy.md)
