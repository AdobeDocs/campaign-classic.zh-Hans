---
solution: Campaign Classic
product: campaign
title: 隐私请求
description: 了解如何管理隐私请求
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2444'
ht-degree: 0%

---


# 管理隐私请求 {#privacy-requests}

有关隐私管理的一般演示文稿，请参 [阅本节](../../platform/using/privacy-management.md)。

此信息适用于GDPR、CCPA、PDPA和LGPD。 For more on these regulations, see [this section](../../platform/using/privacy-management.md#privacy-management-regulations).

CCPA特有的个人信息销售选择退出部分将在本节 [中说明](#sale-of-personal-information-ccpa)。

>[!IMPORTANT]
>
>本文档中描述的安装过程从Campaign Classic18.4（内部版本8931+）开始适用。 如果您运行的是先前版本，请参阅此技 [术说明](https://helpx.adobe.com/cn/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)。

## 关于隐私请求 {#about-privacy-requests}

为了帮助您提高隐私准备，Adobe Campaign允许您处理访问和删除请求。 本 **节介绍了** “访问权 **”和“被遗忘权** （删除请求）” [等内容](../../platform/using/privacy-management.md#right-access-forgotten)。

让我们看看如何创建访问和删除请求，以及Adobe Campaign如何处理这些请求。

### 原则 {#principles}

Adobe Campaign优惠数据控制者执行隐私访问和删除请求的两种可能性：

* 通过 **Adobe Campaign界面**:对于每个隐私请求，数据控制器将在Adobe Campaign中创建新的隐私请求。 请参阅[此章节](#create-privacy-request-ui)。
* 通过 **API**:Adobe Campaign提供了一个API，它允许使用SOAP自动处理隐私请求。 请参阅[此章节](#automatic-privacy-request-api)。

>[!NOTE]
>
>有关个人数据以及管理数据的不同实体（数据控制者、数据处理者和数据主体）的详细信息，请参 [阅个人数据和角色](../../platform/using/privacy-and-recommendations.md#personal-data)。

### 先决条件{#prerequesites}

Adobe Campaign优惠数据管理者工具，用于创建和处理Adobe Campaign中存储的数据的隐私请求。 但是，数据管理者有责任处理与数据主体（电子邮件、客户关怀或门户网站）的关系。

因此，您作为数据管理者的责任是确认发出请求的数据主体的身份，并确认返回给请求者的数据与数据主体有关。

### 安装隐私包 {#install-privacy-package}

要使用此功能，您需要通过> > **[!UICONTROL Privacy Data Protection Regulation]** >菜单安 **[!UICONTROL Tools]** 装 **[!UICONTROL Advanced]** 该 **[!UICONTROL Import package]** 包 **[!UICONTROL Adobe Campaign Package]** 。 有关如何安装包的详细信息，请参阅详 [细文档](../../installation/using/installing-campaign-standard-packages.md)。

在>下创建了两个特定于隐私的新文 **[!UICONTROL Administration]** 件夹 **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**:这是您创建隐私请求并跟踪其演变的地方。
* **[!UICONTROL Namespaces]**:这是您定义用于在Adobe Campaign库中标识数据主体的字段的位置。

![](assets/privacy-folders.png)

在 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;中，每天运行三个技术工作流来处理隐私请求。

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**:此工作流会生成存储在Adobe Campaign中的收件人数据，并使其可在隐私请求的屏幕中进行下载。
* **[!UICONTROL Delete privacy requests data]**:此工作流将删除收件人中存储的Adobe Campaign数据。
* **[!UICONTROL Privacy request cleanup]**:此工作流会删除90天以前的访问请求文件。

在 **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**&#x200B;中，已 **[!UICONTROL Privacy Data Right]** 添加命名权限。 数据管理者必须具有此指定权限才能使用隐私工具。 这允许他们创建新请求、跟踪其发展、使用API等。

![](assets/privacy-right.png)

### 命名空间 {#namesspaces}

在创建隐私请求之前，您需要定义要使用的命名空间。 这是用于在Adobe Campaign库中标识数据主体的键。

现成提供三种命名空间:电子邮件、电话和移动电话。 如果您需要其他命名空间(例如，收件人自定义字段)，则可以从> >创建 **[!UICONTROL Administration]** 新 **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**。

## Creating a Privacy request {#create-privacy-request-ui}

Adobe Campaign **界面** ，允许您创建隐私请求并跟踪其演变。 要创建新的隐私请求，请按照以下说明操作：

1. 访问> >下的隐私请 **[!UICONTROL Administration]** 求文 **[!UICONTROL Platform]** 件夹 **[!UICONTROL Privacy Requests]**。

   ![](assets/privacy-requests-folder.png)

1. 此屏幕允许您视图所有当前隐私请求、其状态和日志。 单击 **[!UICONTROL New]** 以创建隐私请求。

   ![](assets/privacy-request-new.png)

1. 选择( **[!UICONTROL Regulation]** GDPR、CCPA、PDPA或LGPD)、 **[!UICONTROL Request type]** （访问或删除），选择一个 **[!UICONTROL Namespace]** 并输入 **[!UICONTROL Reconciliation value]**。 如果您使用电子邮件作为命名空间，请键入数据主体的电子邮件。

   ![](assets/privacy-request-properties.png)

隐私技术工作流每天运行一次并处理每个新请求：

* 删除请求：收件人存储在Adobe Campaign中的数据被擦除。
* 访问请求：收件人存储在Adobe Campaign中的数据将生成并作为XML文件在请求屏幕的左侧部分可用。

![](assets/privacy-request-download.png)

### 列表表 {#list-of-tables}

执行删除或访问隐私请求时，Adobe Campaign会根据所有具有指向收件人表（自有类型）链接的表 **[!UICONTROL Reconciliation value]** 中的数据搜索所有数据主体的数据。

以下是执行隐私请求时考虑的现成表的列表:

* 收件人语(收件人)
* 收件人投放日志(broadLogRcp)
* 收件人跟踪日志(trackingLogRcp)
* 归档的事件投放日志(broadLogEventHisto)
* 收件人列表内容(rcpGrpRel)
* 访客优惠建议（命题访客）
* 访客语(访客)
* 订阅历史记录（子历史记录）
* 订阅语(订阅)
* 收件人优惠建议（命题Rcp）

如果创建的自定义表具有指向收件人表（自己的类型）的链接，则也会考虑这些表。 例如，如果您有一个与收件人表链接的事务表和一个与事务表链接的事务详细信息表，则这两个表都将被考虑在内。

>[!IMPORTANT]
>
>如果您使用用户档案删除工作流执行隐私批请求，请考虑以下注释：
>* 通过用户档案删除工作流不处理子表。
>* 您需要处理所有子表的删除。
>* Adobe建议您创建一个ETL工作流，该工作流将要删除的行添加到“隐私访问”表中，并 **[!UICONTROL Delete privacy requests data]** 让该工作流执行删除。 出于性能原因，我们建议每天最多删除200个用户档案。


### 隐私请求状态 {#privacy-request-statuses}

以下是隐私请求的不同状态：

* **[!UICONTROL New]** / **[!UICONTROL Retry pending]**:正在进行中，该工作流尚未处理请求。
* **[!UICONTROL Processing]** / **[!UICONTROL Retry in progress]**:工作流正在处理请求。
* **[!UICONTROL Delete pending]**:该工作流已确定要删除的所有收件人数据。
* **[!UICONTROL Delete in progress]**:工作流正在处理删除。
* **[!UICONTROL Delete Confirmation Pending]** （在两步流程模式下删除请求）:工作流已处理访问请求。 请求手动确认以执行删除。 该按钮可用15天。
* **[!UICONTROL Complete]**:请求的处理已完成，无错误。
* **[!UICONTROL Error]**:工作流遇到错误。 原因显示在列的隐私请求列表 **[!UICONTROL Request status]** 中。 例如， **[!UICONTROL Error data not found]** 表示在收件人库中找不到与数据主体 **[!UICONTROL Reconciliation value]** 匹配的数据。

### 二步法 {#two-step-process}

默认情况下， **将激活两步进** 程。 使用此模式创建新的删除请求时，Adobe Campaign始终会先执行访问请求。 这允许您在确认删除之前检查数据。

您可以从隐私请求版本屏幕更改此模式。 单击 **[!UICONTROL Advanced settings]**.

![](assets/privacy-request-advanced-settings.png)

在激活了2步模式后，新的删除请求的状态将更改为 **[!UICONTROL Confirm Delete Pending]**。 从隐私请求屏幕下载生成的XML文件并检查数据。 要确认清除数据，请单击 **[!UICONTROL Confirm delete data]** 按钮。

![](assets/privacy-request-delete-data.png)

### JSSP URL {#jspp-url}

在处理访问请求时，Adobe Campaign会生成一个JSSP，它从收件人库检索数据并将其导出到存储在本地计算机上的XML文件中。 JSSP URL定义如下：

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

其中@id是隐私请求ID。

此URL存储在 **[!UICONTROL "File location" (@urlFile)]** 模式的字 **[!UICONTROL Privacy Requests (gdprRequest)]** 段中。

该信息在数据库中可用90天。 一旦技术工作流清理了请求，信息就会从数据库中删除，URL就会过时。 从网页下载数据之前，请检查URL是否仍然有效。

以下是数据主体数据文件的示例：

![](assets/privacy-access-file.png)

数据管理者可以轻松创建包含相应JSSP URL的Web应用程序，使数据主体的数据文件可以从网页中访问。

![](assets/privacy-gdpr-jssp.png)

以下是一个代码片断，您可以在Web应用程序活动中用作 **[!UICONTROL Page]** 示例。

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

由于对数据主体数据文件的访问受到限制，因此必须禁用网页匿名访问。 只有具有命 **[!UICONTROL Privacy Data Right]** 名权限的运算符才能登录页面并下载数据。

## 自动隐私请求流程 {#automatic-privacy-request-api}

Adobe Campaign提 **供** API，允许您设置自动隐私请求流程。

使用API时，一般的隐私过程与使用 [界面相同](#create-privacy-request-ui)。 唯一的区别是创建隐私请求。 将向Adobe Campaign发送包含请求信息的POST，而不是在活动中创建请求。 对于每个请求，屏幕中都会添加一个新 **[!UICONTROL Privacy Requests]** 条目。 然后，隐私技术工作流处理请求，与使用接口添加的请求相同。

如果您使用API提交隐私请求，我们建议您保留为第 **一个删除请求激活的** 2步流程，以测试返回的数据。 测试完成后，您可以取消激活两步流程，以便自动运行删除请求流程。

JS **[!UICONTROL CreateRequestByName]** API的定义如下。

>[!NOTE]
>
>如果您使用的 **是gdprRequest** API，您仍可以使用它，但建议使用新 **的privacyRequest** API。

>[!IMPORTANT]
>
>使 **[!UICONTROL Privacy Data Right]** 用API需要指定权限。

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
>“规则”字段仅在使用Campaign Classic20.2(build 9178+)时可用。
>
>如果您正在迁移到20.2，并且您已经使用了API，则必须添加如上所示的“规范”字段。 如果您使用的是以前的版本，则可以继续使用API，而不使用“规则”字段。

### 外部调用API {#invoking-api-externally}

以下是如何在外部调用API的示例（通过API进行身份验证，以及有关隐私API的详细信息）。 有关隐私API的详细信息，请查阅 [API文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/s-nms-privacyRequest.html)。 您还可以查阅Web [服务调用文档](../../configuration/using/web-service-calls.md)。

首先，您需要通过API执行身份验证：

1. 通过 **以下url下载xtk** :session WSDL: **`<server url>`/nl/jsp/schemawsdl.jsp?模式=xtk:session**。

1. 使用“登录”方法，并将用户名和密码作为参数传递到请求中。 您将获得包含会话令牌的响应。 以下是使用SoapUI的示例。

   ![](assets/privacy-api.png)

1. 使用返回的会话令牌作为所有后续API调用的身份验证。 24小时后过期。

然后调用隐私API:

1. 从此URL下载WSDL: **`<server url>`/nl/jsp/schemawsdl.jsp?模式=nms:privacyRequest**。

1. 用于 **[!UICONTROL CreateRequestByName]** 创建特定的隐私请求。

   以下是使用的示例 **[!UICONTROL CreateRequestByName]**。 请注意我们如何使用上述会话令牌作为身份验证。 响应是已创建请求的ID。

   ![](assets/privacy-api-2.png)

   要帮助您执行上述步骤，请考虑以下事项：

   * 您可以在nms **:gdprRequest** 模式 **上使** 用queryDef检查访问请求的状态。
   * 您可以在 **nms** :gdprRequestData **模式上使用queryDef** ，获取访问请求的结果。
   * 要能够从&quot;$(serverUrl)&#39; **/nms/gdpr.jssp?id=&#39;@id&quot;下载XML文件**，您必须登录并从列入白名单的IP访问它。 为此，请创建一个Web应用程序，允许您访问JSSP生成的文件。

### 从JS调用API {#invoking-api-from-js}

以下示例说明如何从Campaign Classic内的JS调用API。

>[!NOTE]
>
>“规则”字段仅在使用Campaign Classic20.2(build 9178+)时可用。
>
>如果您正在迁移到20.2，并且您已经使用了API，则必须添加“规则”字段。 如果您使用的是以前的版本，则可以继续使用API，而不使用“规则”字段。

* 如果您使 **用的是以前的版本（包含GDPR包）**，则可以继续使用API而不带有如下“规范”字段：

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

* 如果您正 **在迁移到20.2** ，并且您已经使用了API，则必须添加“规则”字段，如下所示：

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

* 如果您使 **用Campaign Classic20.2(build 9178+)或更高版本**，则“regulation”字段是可选的，如下所示：

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

The **California Consumer Privacy Act** (CCPA) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

访问和删除请求的配置和使用方式对GDPR和CCPA都是通用的。 本节介绍个人数据的销售选择，具体内容取决于CCPA。

除了Adobe Campaign提 [供的](../../platform/using/privacy-management.md#consent-management) “同意”管理工具外，您还可以跟踪消费者是否选择出售个人信息。

消费者通过您的系统决定不允许将其个人信息销售给第三方。 在Adobe Campaign中，您将能够存储和跟踪此信息。

要使此功能正常工作，您需要扩展用户档案表并添加字 **[!UICONTROL Opt-Out for CCPA]** 段。

>[!IMPORTANT]
>
>您作为数据管理者有责任接收数据主体的请求并跟踪CCPA的请求日期。 作为技术提供商，我们只提供一种选择退出的方式。 有关您作为数据管理者的角色的更多信息，请参 [阅个人数据和角色](../../platform/using/privacy-and-recommendations.md#personal-data)。

### 入门项目 {#ccpa-prerequisite}

要利用这些信息，您需要在Adobe Campaign Classic创建此领域。 对于此，您将向表中添加一个布尔 **[!UICONTROL Recipient]** 字段。 创建新字段时，活动API将自动支持该字段。

如果使用自定义收件人表，则还需要执行此操作。

有关如何创建新字段的更多详细信息，请参阅 [模式版文档](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>修改模式是敏感操作，只能由专家用户执行。

1. 转到> **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** ，选 **[!UICONTROL Add new fields]**&#x200B;择作为， **[!UICONTROL Recipients]** 然后单击 **[!UICONTROL Document type]****[!UICONTROL Next]**。 有关向表添加字段的详细信息，请参 [阅此部分](../../configuration/using/new-field-wizard.md)。

   ![](assets/privacy-ccpa-1.png)

1. 对于 **[!UICONTROL Field type]**，选 **[!UICONTROL SQL field]**&#x200B;择。 对于“标签”，请使用 **[!UICONTROL Opt-Out for CCPA]**。 选择类 **[!UICONTROL 8-bit integer (boolean)]** 型并定义以下唯一 **[!UICONTROL Relative path]**&#x200B;项：@OPTOUTCCPA。 单击 **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   这将扩展或创建 **[!UICONTROL Recipient (cus)]** 模式。 单击它以验证字段是否已正确添加。

   ![](assets/privacy-ccpa-3.png)

1. 单击资 **[!UICONTROL Configuration]** 源 **[!UICONTROL Input forms]** 管理器的>节点。 在“ **[!UICONTROL Recipient (nms)]**&#x200B;常规包”下，添加一 `<input>` 个元素，并使用步骤2中定义的相对路径作为xpath值。 有关标识表单的详细信息，请参 [阅此部分](../../configuration/using/identifying-a-form.md)。

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. 断开连接并重新连接。 按照下一节中所述的步骤验证字段是否可用于收件人的详细信息。

### 使用情况 {#usage}

数据管理者有责任填写现场价值，并遵循CCPA关于数据销售的准则和规则。

要填充这些值，可使用以下几种方法：

* 通过编辑活动的详细信息，使用收件人的界面
* 使用API
* 通过数据导入工作流

然后，您应确保永远不要向任何第三方销售已选择退出的用户档案的个人信息。

1. 要更改退出状态，请转到 **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** 并选择收件人。 在选项卡 **[!UICONTROL General]** 中，您将看到在上一节中配置的字段。

   ![](assets/privacy-ccpa-5.png)

1. 配置收件人列表以显示输出列。 要了解如何配置列表，请参阅详细 [文档](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

   ![](assets/privacy-ccpa-6.png)

1. 您可以单击该列，根据退出信息对收件人进行排序。 您还可以创建一个过滤器以仅显示已选择退出的收件人。 For more on creating filters, see [this section](../../platform/using/creating-filters.md).

   ![](assets/privacy-ccpa-7.png)
