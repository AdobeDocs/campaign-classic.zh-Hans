---
product: campaign
title: 自动隐私请求流程
description: 了解如何设置自动隐私请求流程
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: a93bac61-f615-4178-bc12-0f056e48687d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 100%

---

# 自动隐私请求流程 {#automatic-privacy-request-api}



Adobe Campaign 提供了一个 **API**，您可使用它设置一个自动隐私请求流程。

使用 API 时，一般隐私处理流程与[使用 ](privacy-requests-ui.md) 界面的流程相同。唯一的区别是创建隐私请求。会向 Campaign 发送包含请求信息的 POST，而不是在 Adobe Campaign 中创建请求。对于每个请求，将在 **[!UICONTROL Privacy Requests]** 屏幕中添加一个新条目。然后，隐私技术工作流会处理该请求，与处理使用界面添加的请求的方式相同。

如果您使用 API 提交隐私请求，我们建议您在第一次删除请求时，使&#x200B;**两步流程**&#x200B;保持激活状态，以便测试返回的数据。测试完成后，您可以取消激活两步流程，以便自动运行删除请求进程。

**[!UICONTROL CreateRequestByName]** JS API 的定义如下。

>[!NOTE]
>
>如果您使用的是 **gdprRequest** API，您仍可以使用它，但建议使用新的 **privacyRequest** API。

>[!IMPORTANT]
>
>使用 API 需要 **[!UICONTROL Privacy Data Right]** 指明权限。

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
>“regulation”字段仅在您使用 Campaign Classic 20.2（内部版本 9178+）时可用。
>
>如果您要迁移到 20.2，并且您已经在使用这个 API，则必须添加如上所示的“regulation”字段。如果您使用的是以前的版本，则可以继续使用这个 API，而无须添加“regulation”字段。

## 从外部调用 API {#invoking-api-externally}

下方是一个示例，说明如何从外部调用 API（通过 API 进行身份验证，并具体说明隐私 API 的详细信息）。有关隐私 API 的更多信息，请查阅 [API 文档](https://experienceleague.adobe.com/developer/campaign-api/api/s-nms-privacyRequest.html?lang=zh-Hans)。您还可以查阅 [Web 服务调用文档](../../configuration/using/web-service-calls.md)。

首先，您需要通过 API 执行身份验证：

1. 通过以下 URL 下载 **xtk:session** WSDL：**`<server url>`/nl/jsp/schemawsdl.jsp?schema=xtk:session**。

1. 使用“登录”方法，将用户名和密码作为请求中的参数传递。您会获得一个包含会话令牌的响应。以下是使用 SoapUI 的示例。

   ![](assets/do-not-localize/privacy-api.png)

1. 使用返回的会话令牌作为所有子序列 API 调用的身份验证。令牌会在 24 小时后失效。

然后调用隐私 API：

1. 从以下 URL 下载 WSDL：**`<server url>`/nl/jsp/schemawsdl.jsp?schema=nms:privacyRequest**。

1. 使用 **[!UICONTROL CreateRequestByName]** 创建特定的隐私请求。

   以下是使用 **[!UICONTROL CreateRequestByName]** 的示例。请注意，我们使用上述会话令牌作为身份验证的方式。响应是已创建请求的 ID。

   ![](assets/do-not-localize/privacy-api-2.png)

   为了帮助您执行上述步骤，请考虑以下事项：

   * 您可以使用 **nms:gdprRequest** 模式上的 **queryDef** 来查看访问请求的状态。
   * 您可以使用 **nms:gdprRequestData** 模式上的 **queryDef** 来获取访问请求的结果。
   * 为了能够从 **&quot;$(serverUrl)&#39;/nms/gdpr.jssp?id=&#39;@id&quot;** 下载 XML 文件，您必须登录并从已列入允许列表的 IP 访问它。为此，请创建一个允许您访问 JSSP 生成的文件的 Web 应用程序。

## 从 JS 调用 API {#invoking-api-from-js}

下面是在 Campaign Classic 中从 JS 调用 API 的示例。

>[!NOTE]
>
>“regulation”字段仅在您使用 Campaign Classic 20.2（内部版本 9178+）时可用。
>
>如果您要迁移到 20.2，并且您已经在使用这个 API，则必须添加“regulation”字段。如果您使用的是以前的版本，则可以继续使用这个 API，而无须添加“regulation”字段。

* 如果您&#x200B;**使用的是以前的版本（带有 GDPR 包）**，则可以继续使用 API 而无须添加如下所述的“regulation”字段：

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
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

* 如果您要&#x200B;**迁移到 20.2**，并且您已经在使用这个 API，则必须添加如下所示的“regulation”字段：

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
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

* 如果您&#x200B;**使用的是 Campaign Classic 20.2（内部版本 9178+）或更高版本**，则如下所示的“regulation”字段为可选字段：

   ```
   loadLibrary("nms:gdpr.js");
   /**************************** 
   This code calls an API to create new Privacy request on the DB.
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
