---
solution: Campaign Classic
product: campaign
title: 配置URL权限
description: 了解如何配置URL权限
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
translation-type: tm+mt
source-git-commit: 8ab0aab42accbd1253d53e8133f5af0a38c724ea
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 23%

---


# 配置URL权限（内部部署）{#url-permissions}

Campaign Classic 实例可以通过 JavaScript 代码（工作流等）调用的 URL 默认列表是有限的。这些 URL 允许实例正常运行。

默认情况下，实例不允许连接到外部 URL。但是，可以向授权URL的列表添加一些外部URL，以便您的实例可以连接到它们。 这允许您将 Campaign 实例连接到外部系统，例如 SFTP 服务器或网站，以启用文件和/或数据传输。

>[!NOTE]
>
>此过程仅限于&#x200B;**内部部署**&#x200B;部署。
>
>作为&#x200B;**托管的**&#x200B;客户，如果您可以访问[活动控制面板](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)，则可以使用URL权限自助服务界面。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/url-permissions.html)
>
>其他&#x200B;**混合/托管**&#x200B;客户需要联系Adobe支持团队以向允许列表添加IP。


对于&#x200B;**Hybrid**&#x200B;和&#x200B;**内部部署**&#x200B;部署，管理员需要在&#x200B;**serverConf.xml**&#x200B;文件中引用新的&#x200B;**urlPermission**。


有三种连接保护模式可用：

* **阻止**:将阻止所有不属于该允许列表程序的URL，并显示错误消息。这是配置升级后的默认模式。
* **允许**:允许所有不属于该允许列表的URL。
* **警告**:允许所有不属于该程序允许列表的URL，但JS解释程序会发出警告，以便管理员可以收集这些URL。此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>默认情况下，新实现使用&#x200B;**阻止**&#x200B;模式。
>
>作为迁移中的现有客户，您可以临时使用&#x200B;**警告**&#x200B;模式。 在允许URL之前分析出站流量。 定义允许的URL的列表后，您可以将URL添加到允许列表，并激活&#x200B;**阻止**&#x200B;模式。

有关详细信息，请参阅以下部分：

* [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)
* [托管模型](hosting-models.md)
* [Campaign 服务器配置](configuring-campaign-server.md)
* [活动服务器配置文件参数](the-server-configuration-file.md)
* [安全性和隐私核对清单](get-started-security-privacy.md)