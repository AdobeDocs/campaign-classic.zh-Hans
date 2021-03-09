---
solution: Campaign Classic
product: campaign
title: 服务器配置
description: 了解有关服务器配置最佳实践的更多信息。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 3%

---


# 服务器配置{#server-configuration}

## 配置安全区域

>[!IMPORTANT]
>
>从构建8977开始，安全区自助服务用户界面不再可用。
>
>* 如果您托管在AWS上，则必须在控制面板中执行向允许列表添加IP。 有关详细信息，请参阅[专用文档](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)。
>* 如果您未托管在AWS上，请联系Adobe支持团队，将IP添加到允许列表。

>
>
要检查您的实例是否托管在 AWS 上，请按照[此部分](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)详述的步骤操作。

要了解如何使用Security Zones Self Service UI管理VPN Security Zone配置中的条目，请参阅[此技术说明](https://helpx.adobe.com/cn/campaign/kb/configuring-security-zones-self-service.html)。

* 请确保在subNetwork中不允许使用反向代理。 如果是，将检测到&#x200B;**所有**&#x200B;通信来自此本地IP，因此将受信任。

* 将sessionTokenOnly=&quot;true&quot;的使用降至最低：

   * 警告：如果此属性设置为true，则操作符可以暴露给&#x200B;**CRSF攻击**。
   * 此外，sessionToken cookie未使用httpOnly标志进行设置，因此某些客户端javascript代码可以读取它。
   * 但是，多个执行单元格上的消息中心需要sessionTokenOnly:新建一个安全区域，将sessionTokenOnly设置为“true”，并在此区域中仅添加所需的IP **。**

* 如果可能，将alllowHTTP、showErrors设置为false（而非localhost）并检查它们。

   * allowHTTP = &quot;false&quot;:强制操作符使用HTTPS
   * showErrors = &quot;false&quot;:隐藏技术错误（包括SQL错误）。 它可以防止显示过多信息，但会减少营销人员解决错误的能力（无需向管理员请求更多信息）

* 仅在需要创建(事实上是预览)调查、WebApps和报表的营销用户/管理员使用的IP上，将allowDebug设置为true。 此标志允许这些IP显示中继规则并调试它们。

* 请勿将allowEmptyPassword、allowUserPassword、allowSQLIncompention设置为true。 这些属性仅用于从v5和v6.0顺利迁移：

   * **allowEmptyPasswordlets** 运算符的密码为空。如果是这种情况，请通知您的所有操作员要求他们在最后期限前设置密码。 在此截止日期过后，将此属性更改为false。

   * **allowUserPasswordlets** 操作符将其凭据作为参数发送（因此将由apache/IIS/proxy记录）。此功能过去曾用于简化API使用。 您可以查看说明书（或说明书），以确定某些第三方应用程序是否使用此说明书。 如果是，您必须通知他们更改他们使用我们API的方式并尽快删除此功能。

   * **allowSQLInjection** 允许用户使用旧语法执行SQL注入。尽快执行[此页面](../../migration/using/general-configurations.md)中所述的更正，以便能够将此属性设置为false。 您可以使用/nl/jsp/ping.jsp?zones=true检查您的安全区域配置。 此页显示当前IP的安全措施的活动状态（使用这些安全标志计算）。

* HttpOnly cookie/useSecurityToken:请参阅&#x200B;**sessionTokenOnly**&#x200B;标志。

* 将添加到允许列表的IP降至最低：开箱即用，在安全区中，我们为专用网络添加了3个范围。 您不太可能使用所有这些IP地址。 所以只保留您需要的。

* 将webApp/internal运算符更新为仅可在localhost中访问。

## 文件上载保护

使用nlclient/web界面向操作用户检查他们上传到服务器的文件类型。 作为提醒，业务需求可以是：

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

默认情况下，Adobe Campaign的MTA不使用安全连接将内容发送到SMTP服务器。 您必须启用此功能(可能会降低投放速度)。 为此，请在`<smtp ...>`节点中将enableTLS设置为tr**ue。

可以减少身份验证节点（sessionTimeOutSec属性）中会话的生存时间。
