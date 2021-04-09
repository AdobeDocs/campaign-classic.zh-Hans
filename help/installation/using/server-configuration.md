---
solution: Campaign Classic
product: campaign
title: 服务器安全配置
description: 了解有关服务器配置最佳实践的更多信息
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 3%

---

# 服务器安全设置 {#server-configuration}

## 文件上载保护

使用活动 Client Console或Web界面向操作用户检查他们上传到服务器的文件类型。 作为提醒，业务需求可以是：

* 图像(jpg、gif、png、...)
* 内容(zip、html、css、...)
* 营销资产(doc、xls、pdf、psd、tiff、...)
* 电子邮件附件(doc、pdf、...)
* ETL(txt、csv、tab、...)
* 等。

将所有这些内容添加到serverConf/shared/datastore/@uploadAllowlist(有效的java常规表达式)中。 请阅读[本页](../../installation/using/configuring-campaign-server.md#limiting-uploadable-files)了解更多信息。

Adobe Campaign不限制文件大小。 但是，您可以通过配置IIS/Apache来完成此操作。 请阅读[本节](../../installation/using/web-server-configuration.md)了解更多信息。

## 中继

有关详细信息，请参阅[此页](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays)。

默认情况下，所有动态页面都会自动中继到启动Web模块的计算机的本地Tomcat服务器。 你可以选择不把其中一些转送。 如果您没有使用某些Adobe Campaign模块（如webapp、interaction、jsp），则可以从中继规则中删除这些模块。

开箱即用后，我们强制使用http(httpAllowed=&quot;true&quot;)显示最终用户资源。 由于这些页面可显示某些PII（如电子邮件内容、地址）、兑换优惠券和优惠，因此您应在这些路径上再次强制使用HTTPS。

如果您使用不同的主机名（一个公共主机名，一个用于操作员），则还可以阻止操作员通过公共DNS名称中继某些所需资源。

## 外连接保护

Campaign Classic 实例可以通过 JavaScript 代码（工作流等）有限。 要允许新URL，管理员需要在[serverConf.xml文件](../../installation/using/the-server-configuration-file.md)中引用它。

存在三种连接保护模式：

* **阻止** :将阻止所有不属于该允许列表的URL，并显示错误消息。这是配置升级后的默认模式。
* **允许** :允许所有不属于该允许列表的URL。
* **警告** :允许不在允许列表上的所有URL，但JS解释器会发出警告，以便管理员可以收集这些URL。此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

新客户端将使用阻止模式。 如果他们希望允许新URL，则需要联系其管理员以将其添加到允许列表。

来自迁移的现有客户可以在一段时间内使用警告模式。 同时，他们需要先分析出站流量，然后再批准URLS。

## 命令限制（服务器端）

几个命令是已列入黑名单的，不能使用execCommand函数执行。 专用的Unix用户为执行外部命令提供了额外的安全性。 对于托管安装，将自动应用此限制。 对于内部部署安装，您可以按照[此页面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)中的说明手动设置此限制。 此外，**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL External task]**&#x200B;工作流活动不可用（新安装的实例）。

## 其他配置

您可以为所有页面添加额外的HTTP头（有关详细信息，请参阅[此页面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)）：

* 您可以添加一些其他标头，如HSTS、X-FRAME-OPTIONS、CSP...
* 在生产中应用之前，必须在测试环境中测试它们。

   >[!IMPORTANT]
   >
   >Adobe Campaign可以通过添加某些标头来断开。

Adobe Campaign允许您在`<dbcnx .../>`元素中设置纯口令。 请勿使用此功能。

默认情况下，Adobe Campaign不会将会话粘贴到特定IP，但您可以激活会话以防止会话被盗。 为此，请在[serverConf.xml文件](../../installation/using/the-server-configuration-file.md)中，将`<authentication>`节点中的checkIPConsistent属性设置为&#x200B;**true**。

默认情况下，Adobe Campaign的MTA不使用安全连接将内容发送到SMTP服务器。 您必须启用此功能(可能会降低投放速度)。 为此，请在`<smtp ...>`节点中将&#x200B;**enableTLS**&#x200B;设置为&#x200B;**true**。

可以减少身份验证节点（sessionTimeOutSec属性）中会话的生存时间。
