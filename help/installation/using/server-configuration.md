---
product: campaign
title: 服务器安全配置
description: 了解有关服务器配置最佳实践的更多信息
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 4%

---

# 服务器安全设置 {#server-configuration}

## 文件上传保护

使用Campaign客户端控制台或Web界面，与操作用户确认他们上传到服务器的文件类型。 请注意，业务需求可以是：

* 图像(jpg、gif、png、...)
* 内容(zip、html、css、...)
* 营销资产(doc、xls、pdf、psd、tiff、...)
* 电子邮件附件(doc、pdf、...)
* ETL（txt、csv、选项卡、 ...）
* 等。

在serverConf/shared/datastore/@uploadAllowlist（有效的java正则表达式）中添加所有这些变量。 请参阅[此页面](../../installation/using/file-res-management.md)以了解详情。

Adobe Campaign不限制文件大小。 但您可以通过配置IIS/Apache来执行此操作。 在[此部分](../../installation/using/web-server-configuration.md)中了解详情。

## 中继

有关详细信息，请参阅[此页面](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays)。

默认情况下，所有动态页面会自动中继到启动Web模块的计算机的本地Tomcat服务器。 你可以选择不传递其中一些。 如果您没有使用某些Adobe Campaign模块（例如webapp、交互、一些jsp），则可以从中继规则中删除它们。

我们现成已强制使用http(httpAllowed=&quot;true&quot;)显示最终用户资源。 由于这些页面可以显示某些PII（如电子邮件内容、地址）、兑换优惠券和选件，因此您应该在这些路径上再次强制使用HTTPS。

如果您使用的主机名不同（一个公有主机名，一个用于操作员），则还可以阻止操作员通过公共DNS名称中继某些资源。

## 外连接保护

Campaign Classic 实例可以通过 JavaScript 代码（工作流等）限制。 要允许新URL，管理员需要在[serverConf.xml文件](../../installation/using/the-server-configuration-file.md)中引用它。

存在三种连接保护模式：

* **阻止** :所有不属于该允许列表的URL都将被阻止，并显示一条错误消息。这是升级后的默认模式。
* **许可** :允许所有不属于该允许列表的URL。
* **警告** :允许允许列表上未包含的所有URL，但JS解释器会发出警告，以便管理员可以收集这些URL。此模式会添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

新客户端将使用阻止模式。 如果他们希望允许新URL，则需要联系管理员以将其添加到允许列表。

来自迁移的现有客户可能会在一段时间内使用警告模式。 同时，在授权URL之前，需要分析出站流量。

## 命令限制（服务器端）

一些命令已列入黑名单，无法使用execCommand函数执行。 专用Unix用户为执行外部命令提供了额外的安全性。 对于托管安装，将自动应用此限制。 对于内部部署安装，您可以按照[此页面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)中的说明手动设置此限制。 此外，**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL External task]**&#x200B;工作流活动不可用（新安装的实例）。

## 其他配置

您可以为所有页面添加额外的HTTP标头（有关更多信息，请参阅[此页面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands)）：

* 您可以添加一些其他标头，如HSTS、X-FRAME-OPTIONS、CSP...
* 您必须先在测试环境中测试它们，然后才能在生产中应用它们。

   >[!IMPORTANT]
   >
   >Adobe Campaign可能会通过添加某些标头而被破坏。

Adobe Campaign允许您在`<dbcnx .../>`元素中设置纯密码。 请勿使用此功能。

默认情况下，Adobe Campaign不会将会话固定到特定IP，但您可以激活它以防止会话被盗。 要执行此操作，请在[serverConf.xml文件](../../installation/using/the-server-configuration-file.md)中，将`<authentication>`节点中的checkIPConsistent属性设置为&#x200B;**true**。

默认情况下，Adobe Campaign的MTA不使用安全连接将内容发送到SMTP服务器。 您必须启用此功能（可能会降低交付速度）。 为此，请在`<smtp ...>`节点中将&#x200B;**enableTLS**&#x200B;设置为&#x200B;**true**。

您可以缩短身份验证节点中会话的生命周期（sessionTimeOutSec属性）。
