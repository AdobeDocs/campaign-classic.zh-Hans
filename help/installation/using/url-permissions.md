---
product: campaign
title: 配置URL权限
description: 了解如何配置URL权限
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 24%

---

# 配置URL权限（内部部署）{#url-permissions}



Campaign Classic 实例可以通过 JavaScript 代码（工作流等）调用的 URL 默认列表是有限的。这些 URL 允许实例正常运行。

默认情况下，实例不允许连接到外部 URL。但是，可以将一些外部URL添加到经授权的URL列表中，以便您的实例可以连接到这些URL。 这允许您将 Campaign 实例连接到外部系统，例如 SFTP 服务器或网站，以启用文件和/或数据传输。

>[!NOTE]
>
>此过程仅限于 **内部部署** 部署。
>
>作为 **托管** 客户，如果您可以访问 [营销活动控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)，您可以使用URL权限自助服务界面。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=zh-Hans)
>
>其他 **混合/托管** 客户需要联系Adobe列入允许列表支持团队以将IP添加到。
>

对象 **混合** 和 **内部部署** 部署，管理员需要引用新的 **urlPermission** 在 **serverConf.xml** 文件。


提供了三种连接保护模式：

* **阻止**：阻止所有不属于允许列表的URL，并出现错误消息。 这是升级后默认模式。
* **许可**&#x200B;列入允许列表 ：允许所有不属于的URL。
* **警告**：允许所有不属于JS允许列表的URL，但JS解释器会发出警告，以便管理员可以收集这些URL。 此模式会添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>默认情况下，新实施使用 **阻止** 模式。
>
>作为迁移的现有客户，您可以临时使用 **警告** 模式。 在允许URL之前分析出站流量。 列入允许列表一旦定义了允许的URL列表，您就可以将URL添加到并激活 **阻止** 模式。

有关更多信息，请参阅以下章节：

* [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)
* [托管模型](hosting-models.md)
* [Campaign 服务器配置](configuring-campaign-server.md)
* [Campaign服务器配置文件参数](the-server-configuration-file.md)
* [安全和隐私检查清单](get-started-security-privacy.md)
