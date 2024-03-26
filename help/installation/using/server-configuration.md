---
product: campaign
title: 服务器安全配置
description: 了解有关服务器配置最佳实践的更多信息
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: e1aff73a-54fb-444e-b183-df11c9b3df31
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 5%

---

# 服务器安全设置 {#server-configuration}

## 文件上传保护

与运行用户核实，他们使用Campaign客户端控制台或Web界面将哪种文件上传到服务器。 提醒一下，业务需求可以是：

* 图像(jpg、gif、png、...)
* 内容(zip、html、css、...)
* 营销资产(doc、xls、pdf、psd、tiff、...)
* 电子邮件附件(doc， pdf， ...)
* ETL (txt、csv、tab、...)
* 等等。

在serverConf/shared/datastore/@uploadAllowlist（有效的java正则表达式）中添加所有这些变量。 请参阅[此页面](../../installation/using/file-res-management.md)以了解详情。

Adobe Campaign不限制文件大小。 但您可以通过配置IIS/Apache来实现这一点。 可在[此部分](../../installation/using/web-server-configuration.md)中了解详情。

## 中继

请参阅 [此页面](../../installation/using/configuring-campaign-server.md#dynamic-page-security-and-relays) 以了解更多信息。

默认情况下，所有动态页面都会自动中继到启动Web模块的计算机的本地Tomcat服务器。 你可以选择不转送其中一些。 如果您没有使用某些Adobe Campaign模块（如webapp、交互、某些jsp），则可以从中继规则中删除它们。

我们强制使用http (httpAllowed=&quot;true&quot;)开箱即用地显示最终用户资源。 由于这些页面可以显示一些PII（例如电子邮件内容、地址）、兑换优惠券、选件，因此您应该在这些路径上再次强制使用HTTPS。

如果您使用不同的主机名（一个公用，另一个用于操作员），您还可以阻止操作员通过公用DNS名称中继某些所需的资源。

## 外连接保护

Campaign Classic 实例可以通过 JavaScript 代码（工作流等）受限。 要允许新URL，管理员需要在 [serverConf.xml文件](../../installation/using/the-server-configuration-file.md).

存在三种连接保护模式：

* **阻止** ：阻止所有不属于允许列表的URL，并出现错误消息。 这是升级后默认模式。
* **许可** 列入允许列表 ：允许所有不属于的URL。
* **警告** 列入允许列表 ：允许不在上的所有URL，但JS解释器会发出警告，以便管理员可以收集。 此模式会添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

新客户端将使用阻止模式。 如果他们希望允许新URL，则需要联系管理员以将其添加到允许列表。

进行迁移的现有客户可暂时使用警告模式。 同时，他们需要在授权URL之前分析出站流量。

## 命令限制（服务器端）

阻止列表中包含多个命令，不能使用execCommand函数执行。 专用Unix用户为执行外部命令提供了额外的安全性。 对于托管安装，此限制将自动应用。 对于内部部署，您可以按照中的说明手动设置此限制 [此页面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands). 另外， **[!UICONTROL Script]** 和 **[!UICONTROL External task]** 工作流活动不可用（新安装的实例）。

## 其他配置

您可以为所有页面添加额外的HTTP标头(有关更多信息，请参阅 [此页面](../../installation/using/configuring-campaign-server.md#restricting-authorized-external-commands))：

* 您可以添加其他标头，如HSTS、X-FRAMEOPTIONS、CSP...
* 您必须在测试环境中测试这些组件，然后才能将其应用于生产环境。

  >[!IMPORTANT]
  >
  >可以通过添加某些标头来破坏Adobe Campaign。

Adobe Campaign允许您在中设置普通密码 `<dbcnx .../>` 元素。 请勿使用此功能。

默认情况下，Adobe Campaign不会将会话附加到特定IP，但您可以将其激活以防止会话被盗。 为此，请在 [serverConf.xml文件](../../installation/using/the-server-configuration-file.md)，将checkIPConsistent属性设置为 **true** 在 `<authentication>` 节点。

默认情况下，Adobe Campaign的MTA不使用安全连接将内容发送到SMTP服务器。 您必须启用此功能（可能会降低投放速度）。 为此，请设置 **enableTLS** 到 **true** 在 `<smtp ...>` 节点。

您可以缩短身份验证节点中会话的生命周期（sessionTimeOutSec属性）。
