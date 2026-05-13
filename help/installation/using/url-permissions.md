---
product: campaign
title: 配置URL权限
description: 了解如何配置URL权限
feature: Installation, Instance Settings, Permissions
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 6fe8da3b-57b9-4a69-8602-a03993630b27
TQID: https://experienceleague.adobe.com/5F4SRt978KzXMI06t3rNt3YRnYI-EWwSkQIrAd0oDq8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
  - id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 380
ht-degree: 26%

---

# 配置URL权限（内部部署）{#url-permissions}



可由JavaScript代码（工作流等）调用的默认URL列表 的URL代码有限。 这些 URL 允许实例正常运行。

默认情况下，实例不允许连接到外部 URL。 但是，可以将一些外部URL添加到经授权的URL列表中，以便您的实例可以连接到这些URL。 这允许您将 Campaign 实例连接到外部系统，例如 SFTP 服务器或网站，以启用文件和/或数据传输。

>[!NOTE]
>
>此过程仅限于&#x200B;**内部部署**。
>
>作为&#x200B;**托管**&#x200B;客户，如果您可以访问[Campaign控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)，则可以使用URL权限自助服务界面。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html?lang=zh-Hans)
>
>其他&#x200B;**混合/托管**&#x200B;客户需要联系Adobe支持团队以将IP添加到。
>

对于&#x200B;**混合**&#x200B;和&#x200B;**内部部署**&#x200B;部署，管理员需要在&#x200B;**serverConf.xml**&#x200B;文件中引用新的&#x200B;**urlPermission**。


提供了三种连接保护模式：

* **阻止**：所有不属于的URL都将被阻止，并出现错误消息。 这是升级后默认模式。
* **允许**：允许所有不属于的URL。
* **警告**：允许所有不属于的URL，但JS解释器会发出警告，以便管理员可以收集这些URL。 此模式会添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>默认情况下，新实施使用&#x200B;**阻止**&#x200B;模式。
>
>作为来自迁移的现有客户，您可以临时使用&#x200B;**警告**&#x200B;模式。 在允许URL之前分析出站流量。 定义允许的URL列表后，您可以将URL添加到并激活&#x200B;**阻止**&#x200B;模式。

有关更多信息，请参阅以下章节：

* [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)
* [托管模型](hosting-models.md)
* [Campaign 服务器配置](configuring-campaign-server.md)
* [Campaign服务器配置文件参数](the-server-configuration-file.md)
* [安全和隐私检查清单](get-started-security-privacy.md)
