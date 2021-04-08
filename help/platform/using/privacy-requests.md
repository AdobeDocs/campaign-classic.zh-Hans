---
solution: Campaign Classic
product: campaign
title: 隐私请求
description: 了解如何管理隐私请求
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
translation-type: tm+mt
source-git-commit: 5b1c4426a0d59861aa61a7e53154b9adfda31d71
workflow-type: tm+mt
source-wordcount: '2415'
ht-degree: 21%

---

# 管理隐私请求{#privacy-requests}

有关隐私管理的一般演示文稿，请参阅[此部分](../../platform/using/privacy-management.md)。

此信息适用于 GDPR、CCPA、PDPA 和 LGPD。有关这些法规的更多信息，请参阅[此部分](../../platform/using/privacy-management.md#privacy-management-regulations)。

[此部分](#sale-of-personal-information-ccpa)中说明了特定于 CCPA 的个人信息销售的选择退出。

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

## 关于隐私请求{#about-privacy-requests}

为了帮助您促进隐私就绪，Adobe Campaign 允许您处理访问和删除请求。**访问权**&#x200B;和&#x200B;**被遗忘权**（删除请求）在[此部分](../../platform/using/privacy-management.md#right-access-forgotten)中进行了描述。

让我们看看您如何创建访问和删除请求，以及Adobe Campaign如何处理这些请求。

### 原则{#principles}

Adobe Campaign优惠数据控制者执行隐私访问和删除请求的两种可能性：

* 通过&#x200B;**Adobe Campaign接口**:对于每个隐私请求，数据控制器将在Adobe Campaign中创建新的隐私请求。 请参阅[此章节](#create-privacy-request-ui)。
* 通过&#x200B;**API**:Adobe Campaign提供了一个API，它允许使用SOAP自动处理隐私请求。 请参阅[此章节](#automatic-privacy-request-api)。

>[!NOTE]
>
>有关个人数据以及管理数据的不同实体（数据控制者、数据处理者和数据主体）的更多信息，请参阅[个人数据和角色](../../platform/using/privacy-and-recommendations.md#personal-data)。

### 先决条件{#prerequesites}

Adobe Campaign 为数据控制者提供用于创建和处理 Adobe Campaign 中存储的数据的隐私请求的工具。但是，数据控制者负责处理与数据主体（电子邮件、客户关怀或 Web 门户）的关系。

因此，作为数据控制者，您的职责是确认发出请求的数据主体的身份，并确认返回给请求者的数据与数据主体有关。

### 安装隐私包{#install-privacy-package}

要使用此功能，您需要通过&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]**&#x200B;菜单安装&#x200B;**[!UICONTROL Privacy Data Protection Regulation]**&#x200B;包。 有关如何安装软件包的详细信息，请参阅[详细文档](../../installation/using/installing-campaign-standard-packages.md)。

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]**&#x200B;下创建了两个特定于隐私的新文件夹：

* **[!UICONTROL Privacy Requests]**:您将在此处创建您的隐私请求并跟踪其演变。
* **[!UICONTROL Namespaces]**:您将在此处定义用于在Adobe Campaign数据库中标识数据主体的字段。

![](assets/privacy-folders.png)

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;中，每天运行三个技术工作流以处理隐私请求。

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**:此工作流会生成存储在Adobe Campaign中的收件人数据，并使其可在隐私请求的屏幕中进行下载。
* **[!UICONTROL Delete privacy requests data]**:此工作流将删除收件人存储在Adobe Campaign中的数据。
* **[!UICONTROL Privacy request cleanup]**:此工作流会清除90天以前的访问请求文件。

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**&#x200B;中，已添加&#x200B;**[!UICONTROL Privacy Data Right]**&#x200B;命名权限。 数据管理者必须具有此命名权限才能使用隐私工具。 这允许他们创建新请求、跟踪其演变、使用API等。

![](assets/privacy-right.png)

### 命名空间 {#namesspaces}

在创建隐私请求之前，您需要定义将要使用的命名空间。这是用于在Adobe Campaign数据库中标识数据主体的键。

有三种命名空间现成可用：电子邮件、电话和手机。 如果您需要其他命名空间(例如，收件人自定义字段)，则可以从&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**&#x200B;创建新字段。

## 创建隐私请求 {#create-privacy-request-ui}

**Adobe Campaign接口**&#x200B;允许您创建隐私请求并跟踪其演变。 要创建新的隐私请求，请按照以下说明操作：

1. 访问&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Privacy Requests]**&#x200B;下的隐私请求文件夹。

   ![](assets/privacy-requests-folder.png)

1. 此屏幕允许您视图所有当前的隐私请求、其状态和日志。 单击&#x200B;**[!UICONTROL New]**&#x200B;以创建隐私请求。

   ![](assets/privacy-request-new.png)

1. 选择&#x200B;**[!UICONTROL Regulation]**（GDPR、CCPA、PDPA或LGPD）、**[!UICONTROL Request type]**（访问或删除），选择&#x200B;**[!UICONTROL Namespace]**&#x200B;并输入&#x200B;**[!UICONTROL Reconciliation value]**。 如果您使用电子邮件作为命名空间，请键入数据主体的电子邮件。

   ![](assets/privacy-request-properties.png)

隐私技术工作流每天运行一次，并处理每个新请求：

* 删除请求：收件人存储在Adobe Campaign中的数据被擦除。
* 访问请求：收件人存储在Adobe Campaign中的数据将生成并作为XML文件在请求屏幕的左侧提供。

![](assets/privacy-request-download.png)

### 表{#list-of-tables}的列表

当执行删除或访问隐私请求时，Adobe Campaign会根据所有表中具有指向收件人表（自有类型）链接的&#x200B;**[!UICONTROL Reconciliation value]**&#x200B;搜索所有数据主体的数据。

以下是执行隐私请求时考虑的现成表的列表:

* 收件人(收件人)
* 收件人投放日志(broadLogRcp)
* 收件人跟踪日志(trackingLogRcp)
* 归档的事件投放日志(broadLogEventHisto)
* 收件人列表内容(rcpGrpRel)
* 访客优惠建议（命题访客）
* 访客 (visitor)
* 订阅历史记录（子历史记录）
* 订阅(订阅)
* 收件人优惠建议（命题Rcp）

如果创建的自定义表具有指向收件人表（自有类型）的链接，则也会考虑这些表。 例如，如果您有一个与收件人表链接的事务处理表和一个与事务处理表链接的事务处理详细信息表，则这两个表都将被考虑在内。

>[!IMPORTANT]
>
>如果您使用用户档案删除工作流执行隐私批请求，请考虑以下说明：
>* 通过用户档案删除工作流不处理子表。
>* 您需要处理所有子表的删除。
>* Adobe建议您创建一个ETL工作流，该工作流将在“隐私访问”表中添加要删除的行，并让&#x200B;**[!UICONTROL Delete privacy requests data]**&#x200B;工作流执行删除。 出于性能原因，我们建议每天最多删除200个用户档案。


### 隐私请求状态 {#privacy-request-statuses}

以下是隐私请求的不同状态：

* **[!UICONTROL New]** / **[!UICONTROL Retry pending]**：进行中，工作流尚未处理请求。
* **[!UICONTROL Processing]** / **[!UICONTROL Retry in progress]**：工作流正在处理请求。
* **[!UICONTROL Delete pending]**：工作流已识别要删除的所有收件人数据。
* **[!UICONTROL Delete in progress]**：工作流正在处理删除。
* **[!UICONTROL Delete Confirmation Pending]** （在两步流程模式下删除请求）：工作流已处理访问请求。请求手动确认以执行删除。 该按钮可用15天。
* **[!UICONTROL Complete]**：请求的处理已完成，并且没有错误。
* **[!UICONTROL Error]**：工作流遇到错误。原因显示在&#x200B;**[!UICONTROL Request status]**&#x200B;列的“隐私请求”列表中。 例如，**[!UICONTROL Error data not found]** 表示在数据库中找不到与数据主体的 **[!UICONTROL Reconciliation value]** 匹配的收件人数据。

### 2步流程{#two-step-process}

默认情况下，将激活&#x200B;**2步进程**。 使用此模式创建新的删除请求时，Adobe Campaign始终会先执行访问请求。 这允许您在确认删除之前检查数据。

您可以从隐私请求版本屏幕更改此模式。 单击 **[!UICONTROL Advanced settings]**.

![](assets/privacy-request-advanced-settings.png)

激活了2步模式后，新Delete请求的状态将更改为&#x200B;**[!UICONTROL Confirm Delete Pending]**。 从隐私请求屏幕下载生成的XML文件并检查数据。 要确认擦除数据，请单击&#x200B;**[!UICONTROL Confirm delete data]**&#x200B;按钮。

![](assets/privacy-request-delete-data.png)

### JSSP URL {#jspp-url}

在处理访问请求时，Adobe Campaign会生成一个JSSP，它从收件人库中检索数据并将其导出到本地计算机上存储的XML文件中。 JSSP URL定义如下：

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

其中@id是隐私请求ID。

此URL存储在&#x200B;**[!UICONTROL Privacy Requests (gdprRequest)]**&#x200B;模式的&#x200B;**[!UICONTROL "File location" (@urlFile)]**&#x200B;字段中。

该信息在数据库中可用90天。 一旦技术工作流清理了请求，信息将从数据库中删除，URL就会过时。 从网页下载数据之前，请检查URL是否仍然有效。

以下是数据主体数据文件的示例：

![](assets/privacy-access-file.png)

数据控制者可以轻松创建包含相应JSSP URL的Web应用程序，以使数据主体的数据文件可从网页中访问。

![](assets/privacy-gdpr-jssp.png)

以下是一个代码片断，您可以在Web应用程序&#x200B;**[!UICONTROL Page]**&#x200B;活动中用作示例。

![](assets/privacy-page-activity.png)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv="Content-Language" content="en"> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> <link rel="stylesheet" type="text/css" href="/nl/webForms/landingPage.css"/> <title>Clickthrough</title> <style type="text/css" media="all"> /* override formulary area */ .formulary { top: 200px; position: absolute; left: 0; } </style> </head> <body style="" class="">
<center>
<div id="wrap">
<div id="header"><img class="nlui-widget" alt="placeholder_header" src="/nms/img/contentModels/placeholder_header.png" unselectable="on" />
<div class="header-title center-title">DOWNLOAD GDPR DATA</div>
<div class="formulary center-formulary"><form>
<div class="button large-button"><a href=[SERVER_URL]/nms/gdpr.jssp?id=13000" data-nl-type="externalLink">CLICK TO DOWNLOAD</a></div>
</form></div>
</div>
<div id="content">
<div class="row">
<div class="info">
<div class="desc">
<div class="title">EFFICIENCY</div>
<div class="desc">Our service is guaranteed to improve your efficiency. Increase performance and use our high-technology service to implement even the most ambitious of projects.</div>
</div>
</div>
</div>
</div>
<div id="footer">
<div style="text-align: center;">
<div style="float: left;"><a href="#">Contact us</a></div>
<div style="float: right;">&copy; Copyrights</div>
<div><a href="#"><img title="facebook" class="nlui-widget" alt="facebook" src="/xtk/img/facebook.png" unselectable="on" /></a> <a href="#"><img title="Twitter" class="nlui-widget" alt="twitter" src="/xtk/img/twitter.png" unselectable="on" /></a> <a href="#"><img title="Google" class="nlui-widget" alt="google_plus" src="/xtk/img/google_plus.png" unselectable="on" /></a> <a href="#"><img title="Linkedin" class="nlui-widget" alt="Linkedin" src="/xtk/img/linkedin.png" unselectable="on" /></a></div>
</div>
</div>
</div>
</center>
</body> </html>
```

由于访问数据主体的数据文件受到限制，因此必须禁用网页匿名访问。 只有名为&#x200B;**[!UICONTROL Privacy Data Right]**&#x200B;的运算符才能登录页面并下载数据。

## 自动隐私请求进程{#automatic-privacy-request-api}

Adobe Campaign提供了一个&#x200B;**API**，它允许您设置一个自动的隐私请求过程。

使用API时，一般的隐私过程与使用接口](#create-privacy-request-ui)的[相同。 唯一的区别是创建隐私请求。 将向活动发送包含请求信息的POST，而不是在Adobe Campaign中创建请求。 对于每个请求，将在&#x200B;**[!UICONTROL Privacy Requests]**&#x200B;屏幕中添加一个新条目。 然后，隐私技术工作流将处理该请求，与使用接口添加的请求相同。

如果您使用API提交隐私请求，我们建议您保留为第一个删除请求激活的&#x200B;**2步进程**，以测试返回的数据。 测试完成后，您可以取消激活两步进程，以便自动运行删除请求进程。

**[!UICONTROL CreateRequestByName]** JS API定义如下。

>[!NOTE]
>
>如果您使用的是&#x200B;**gdprRequest** API，您仍可以使用它，但建议使用新的&#x200B;**privacyRequest** API。

>[!IMPORTANT]
>
>使用API需要&#x200B;**[!UICONTROL Privacy Data Right]**&#x200B;命名权限。

```
<method library="nms:gdpr.js" name="CreateRequestByName" static="true">
 <help>Create a new GDPR Request using namespace internal name</help>
 <parameters>
  <param name="namespaceName" type="string" desc="Namespace internal name"/>
  <param name="reconciliationValue" type="string" desc="Reconciliation value"/>
  <param name="type" type="long" desc="Reconciliation value"/>
  <param name="confirmDeletePending" type="boolean" desc="Request confirm before deleting data"/>
  <param name="regulation" type="long" desc="regulation of newly created request"/>
  <param name="id" type="long" inout="out" desc="ID of newly created request"/>
 </parameters>
</method>
```

>[!NOTE]
>
>“规定”字段仅在您使用Campaign Classic 20.2（内部版本9178+）时可用。
>
>如果您要迁移到20.2，并且您已经使用了API，则必须添加上面所示的“规则”字段。 如果您使用的是以前的版本，则可以继续使用API，而不使用“regulation”字段。

### 在外部{#invoking-api-externally}调用API

下面是一个示例，说明如何在外部调用API（通过API进行身份验证，并具体说明隐私API的详细信息）。 有关隐私API的详细信息，请查阅[API文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/s-nms-privacyRequest.html)。 您还可以查阅[Web服务调用文档](../../configuration/using/web-service-calls.md)。

首先，您需要通过API执行身份验证：

1. 通过以下url下载&#x200B;**xtk:session** WSDL:**`<server url>`/nl/jsp/schemawsdl.jsp?模式=xtk:session**。

1. 使用“登录”方法，并将用户名和密码作为参数传递到请求中。 您将获得一个包含会话令牌的响应。 以下是使用SoapUI的示例。

   ![](assets/privacy-api.png)

1. 使用返回的会话令牌作为所有子序列API调用的身份验证。 24小时后到期。

然后调用隐私API:

1. 从以下URL下载WSDL:**`<server url>`/nl/jsp/schemawsdl.jsp?模式=nms:privacyRequest**。

1. 使用&#x200B;**[!UICONTROL CreateRequestByName]**&#x200B;创建特定的隐私请求。

   以下是使用&#x200B;**[!UICONTROL CreateRequestByName]**&#x200B;的示例。 请注意我们如何使用上述会话令牌作为身份验证。 响应是已创建请求的ID。

   ![](assets/privacy-api-2.png)

   要帮助您执行上述步骤，请考虑以下事项：

   * 可以在&#x200B;**nms:gdprRequest**&#x200B;模式上使用&#x200B;**queryDef**&#x200B;来检查访问请求的状态。
   * 可以在&#x200B;**nms:gdprRequestData**&#x200B;模式上使用&#x200B;**queryDef**&#x200B;来获取访问请求的结果。
   * 要能够从&#x200B;**&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;**&#x200B;下载XML文件，您必须登录并从列入白名单的IP访问它。 为此，请创建一个Web应用程序，允许您访问JSSP生成的文件。

### 从JS {#invoking-api-from-js}调用API

下面是一个示例，说明如何在Campaign Classic中从JS调用API。

>[!NOTE]
>
>“规定”字段仅在您使用Campaign Classic 20.2（内部版本9178+）时可用。
>
>如果您要迁移到20.2，并且您已经使用了API，则必须添加“regulation”字段。 如果您使用的是以前的版本，则可以继续使用API，而不使用“regulation”字段。

* 如果您&#x200B;**使用的是上一个版本（带有GDPR包）**，则可以继续使用API而不使用“规则”字段，如下所示：

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 4 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // GDPR_REQUEST_TYPE_ACCESS = 1;
   // GDPR_REQUEST_TYPE_DELETE = 2;
   var requestType = GDPR_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* 如果您正在&#x200B;**迁移到20.2**，并且您已经使用了API，则必须添加“regulation”字段，如下所示：

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values.
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is mandatory parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

* 如果您&#x200B;**使用Campaign Classic 20.2(build 9178+)或更高版本**，则“regulation”字段为可选字段，如下所示：

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privay request on the DB.
   It requires 5 parameters below.
   Feel free to change parameter values 
   ****************************/
   // 1. Namespace internal name
   var namespaceName = "defaultNamespace1";
   // 2. Reconciliation value for privacy request
   var reconciliationValue = "example@adobe.com";
   // 3. Privacy request type
   // PRIVACY_REQUEST_TYPE_ACCESS = 1;
   // PRIVACY_REQUEST_TYPE_DELETE = 2;
   var requestType = PRIVACY_REQUEST_TYPE_ACCESS;
   // 4. Confirm deleting data required.
   // value : true or false
   var ConfirmDeletePending = true;
   // 5. Specify which regulation applies to newly created request. This is optional parameter.
   // GDPR = 1
   // CCPA = 2
   // PDPA = 3
   // LGPD = 4
   var regulation = 1;
   // BEGIN
   var requestId = nms.privacyRequest.CreateRequestByName(namespaceName, reconciliationValue, requestType, ConfirmDeletePending, regulation);
   // User can use a simple queryDef with requestID as a parameter to check request status.
   ```

## 选择退出个人信息销售 (CCPA) {#sale-of-personal-information-ccpa}

**加州消费者隐私法案** (CCPA) 为加利福尼亚州居民提供了与其个人信息有关的新权利，并要求在加利福尼亚开展业务的特定实体承担数据保护责任。

访问和删除请求的配置和使用对于 GDPR 和 CCPA 均通用。此部分介绍特定于 CCPA 的个人数据销售的选择退出。

除了Adobe Campaign提供的[同意管理](../../platform/using/privacy-management.md#consent-management)工具外，您还可以跟踪消费者是否已选择出售个人信息。

消费者通过您的系统决定不允许将其个人信息销售给第三方。在 Adobe Campaign 中，您将能够存储和跟踪此信息。

为了使此功能正常工作，您需要扩展用户档案表并添加&#x200B;**[!UICONTROL Opt-Out for CCPA]**&#x200B;字段。

>[!IMPORTANT]
>
>作为数据控制者，您负责接收数据主体的请求并跟踪 CCPA 的请求日期。作为技术提供商，我们仅提供选择退出的方式。有关您作为数据控制者的角色的更多信息，请参阅[个人数据和角色](../../platform/using/privacy-and-recommendations.md#personal-data)。

### 先决条件{#ccpa-prerequisite}

要利用此信息，您需要在Adobe Campaign Classic中创建此字段。 对于此，您将向&#x200B;**[!UICONTROL Recipient]**&#x200B;表添加一个布尔字段。 创建新字段后，Campaign API 自动支持该字段。

如果您使用自定义收件人表，则还需要执行此操作。

有关如何创建新字段的详细信息，请参阅[模式版文档](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>修改模式是敏感操作，只能由专家用户执行。

1. 转至&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**，选择&#x200B;**[!UICONTROL Recipients]**&#x200B;作为&#x200B;**[!UICONTROL Document type]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**。 有关向表添加字段的详细信息，请参阅[此部分](../../configuration/using/new-field-wizard.md)。

   ![](assets/privacy-ccpa-1.png)

1. 对于&#x200B;**[!UICONTROL Field type]**，选择&#x200B;**[!UICONTROL SQL field]**。 对于“标签”，请使用&#x200B;**[!UICONTROL Opt-Out for CCPA]**。 选择&#x200B;**[!UICONTROL 8-bit integer (boolean)]**&#x200B;类型并定义以下唯一&#x200B;**[!UICONTROL Relative path]**:@OPTOUTCCPA。 单击 **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   这将扩展或创建&#x200B;**[!UICONTROL Recipient (cus)]**&#x200B;模式。 单击它可验证字段是否已正确添加。

   ![](assets/privacy-ccpa-3.png)

1. 单击资源管理器的&#x200B;**[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**&#x200B;节点。 在&#x200B;**[!UICONTROL Recipient (nms)]**&#x200B;的“常规包”下，添加一个`<input>`元素，并使用步骤2中定义的相对路径作为xpath值。 有关标识表单的详细信息，请参阅[此部分](../../configuration/using/identifying-a-form.md)。

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. 断开连接并重新连接。 按照下一节中所述的步骤验证字段是否可用于收件人的详细信息。

### 使用情况 {#usage}

数据控制者负责填写字段值，并遵循关于数据销售的 CCPA 准则和规则。

要填写值，可以使用以下几种方法：

* 通过编辑活动的详细信息，使用收件人的界面
* 使用API
* 通过数据导入工作流

然后，您应确保永远不要向已选择退出的任何第三方销售用户档案的个人信息。

1. 要更改退出状态，请转到&#x200B;**[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]**&#x200B;并选择收件人。 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，您将看到在上一节中配置的字段。

   ![](assets/privacy-ccpa-5.png)

1. 配置收件人列表以显示输出列。 要了解如何配置列表，请参阅[详细文档](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

   ![](assets/privacy-ccpa-6.png)

1. 您可以单击该列，以根据选择退出信息对收件人进行排序。您还可以创建一个筛选器以仅显示已选择退出的收件人。 有关创建过滤器的详细信息，请参阅[此部分](../../platform/using/creating-filters.md)。

   ![](assets/privacy-ccpa-7.png)
