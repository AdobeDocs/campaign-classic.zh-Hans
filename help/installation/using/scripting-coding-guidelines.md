---
product: campaign
title: 脚本和编码准则
description: 进一步了解在Adobe Campaign中进行开发时应遵循的准则（工作流、Javascript、JSSP等）
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 1f96c3df-0ef2-4f5f-9c36-988cbcc0769f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 5%

---

# 脚本和编码准则 {#scripting-coding-guidelines}



## 脚本

有关更多详细信息，请参阅 [Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans).

如果您使用工作流、Web应用程序、jssp编写脚本，请遵循以下最佳实践：

* 尽量避免使用SQL语句。

* 如果需要，请使用参数化（prepare语句）函数，而不是字符串连接。

   错误做法：

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
   ```

   良好做法：

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
   ```

   >[!IMPORTANT]
   >
   >sqlSelect不支持此功能，因此您必须使用DBEngine类的查询函数：

   ```
   var cnx = application.getConnection()
   var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
   for each(var row in stmt) logInfo(row[0] + " : " + row[1])
   cnx.dispose()
   ```

要避免SQL注入，必须将SQL函数添加到要允许列表在Adobe Campaign中使用的。 将它们添加到后，它们允许列表便会在表达式编辑器中对运算符可见。 请参见[此页面](../../configuration/using/adding-additional-sql-functions.md)。

>[!IMPORTANT]
>
>如果您使用的内部版本低于8140，则 **XtkPassUnknownSQLFunctionsToRDBMS** 选项可能会设置为“1”。 如果要保护数据库，请删除此选项（或将其设置为“0”）。

如果使用用户输入在查询或SQL语句中生成过滤器，则始终必须对它们进行转义(请参阅 [Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans)  — 数据保护：转义函数)。 这些函数包括：

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## 保护新数据模型

### 文件夹库

请参阅以下页面：

* [文件夹访问属性](../../platform/using/access-management.md)
* [链接的文件夹](../../configuration/using/configuration.md#linked-folder)

### 已命名权限

除了基于文件夹的安全模型之外，您还可以使用命名权限来限制运算符操作：

* 您可以添加一些系统过滤器(sysFilter)，以防止对数据进行读/写(请参阅 [本页](../../configuration/using/filtering-schemas.md))。

   ```
   <sysFilter name="writeAccess">    
       <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
   </sysFilter>
   ```

* 您还可以保护在架构中定义的某些操作（SOAP方法）。 只需将具有相应命名权限的访问属性设置为值即可。

   ```
   <method name="grantVIPAccess" access="myNewRole">
       <parameters>
   ...
       </parameters>
   </method>
   ```

   有关详细信息，请参见[此页面](../../configuration/using/implementing-soap-methods.md)。

>[!IMPORTANT]
>
>您可以在navtree的命令节点中使用命名权限。 它提供了更好的用户体验，但不提供任何保护（仅使用客户端来隐藏/禁用它们）。 您必须使用访问属性。

### 溢出表

如果您需要根据操作员访问级别保护机密数据（架构的一部分），请不要在表单定义（enabledIf/visibleIf条件）中隐藏机密数据。

整个实体由屏幕加载，您还可以在列定义中显示它们。 要实现此目的，必须创建一个溢出表。 请参阅 [本页](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## 在Web应用程序中添加捕获

最好在公共登陆页面/订阅页面中添加验证码。 遗憾的是，在DCE（数字内容编辑器）页面中添加验证码并非易事。 我们将向您展示如何添加v5验证码或Google reCAPTCHA。

在DCE中添加验证码的一般方法是创建个性化块，以便将其轻松包含在页面内容中。 您必须添加 **脚本** 活动和 **测试**.

### 个性化块

1. 转到 **[!UICONTROL Resources]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Personalization blocks]** 然后创建一个新的。

1. 使用 **[!UICONTROL Web application]** 内容类型和检查 **[!UICONTROL Visible in the customization menus]**.

   有关详细信息，请参见[此页面](../../delivery/using/personalization-blocks.md)。

   以下是 **Campaign captcha**:

   ```javascript
   <%
   var captchaID = CaptchaIDGen();
   %>
   <img src="/nms/jsp/captcha.jsp?captchaID=<%=captchaID%>&width=200&height=50&minWordSize=8&maxWordSize=8"/>
   <input id="captchaValue" name="captchaValue" <%= String(ctx.vars.captchaValid) === "false" ? class="ui-state-error" : "" %>>
   <input type="hidden" name="captchaID" value="<%=captchaID%>"/>
   <%
   if( serverForm.isInputErroneous("captchaValue") ) {
   %>
   <script type="text/javascript"> 
   $("#captchaValue").addClass("ui-state-error")
   </script>
   <%
   }
   %>
   ```

   * 第1至6行生成所有需要的输入。
   * 第7行到末端句柄错误。
   * 第4行允许您更改验证码灰色框大小（宽度/高度）和生成字的长度(minWordSize/maxWordSize)。
   * 使用Google reCAPTCHA之前，必须在Google上注册并创建新的reCAPTCHA网站。

      `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`
   您应该能够禁用验证按钮，但由于我们没有任何标准按钮/链接，因此最好在HTML中自行禁用验证按钮。 要了解如何执行此操作，请参阅 [本页](https://developers.google.com/recaptcha/).

### 更新Web应用程序

1. 访问Web应用程序的属性，以添加名为的布尔变量 **captchaValid**.

   ![](assets/scripting-captcha.png)

1. 在最后一页和 **[!UICONTROL Storage]** 活动，添加 **[!UICONTROL Script]** 和 **[!UICONTROL Test]**.

   插入分支 **[!UICONTROL True]** 到 **[!UICONTROL Storage]** 另一个在页面上有验证码。

   ![](assets/scripting-captcha2.png)

1. 使用编辑分支True的条件 `"[vars/captchaValid]"` 等于True。

   ![](assets/scripting-captcha3.png)

1. 编辑 **[!UICONTROL Script]** 活动。 内容将取决于所选的captcha引擎。

1. 最后，您可以在页面中添加个性化块：请参阅 [本页](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>对于reCAPTCHA集成，您必须在HTML中添加客户端JavaScript(在 `<head>...</head>`):
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Campaign captcha

```javascript
var captchaID = request.getParameter("captchaID");
var captchaValue = request.getParameter("captchaValue");
  
if( !CaptchaValidate(captchaID, captchaValue) ) {
  serverForm.logInputError("captchaValue",
                           "The characters you typed for the captcha must match the image ones.",
                           "captchaValue")
  ctx.vars.captchaValid = false
}
else
  ctx.vars.captchaValid = true
```

第6行：你可以放任何类型的错误信息。

### Google recapcha

请参阅 [官方文档](https://developers.google.com/recaptcha/docs/verify).

```javascript
ctx.vars.captchaValid = false
var gReCaptchaResponse = request.getParameter("g-recaptcha-response");
  
// Call reCaptcha API to validate it
var req = new HttpClientRequest("https://www.google.com/recaptcha/api/siteverify")
req.method = "POST"
req.header["Content-Type"] = "application/x-www-form-urlencoded"
req.body = "secret=YOUR_SECRET_HERE&response=" + encodeURIComponent(gReCaptchaResponse)
req.execute()
var response = req.response
if( response.code == 200 ) {
  captchaRes = JSON.parse(response.body.toString(response.codePage));
  ctx.vars.captchaValid = captchaRes.success
}
  
if( ctx.vars.captchaValid == false ) {
  serverForm.logInputError("reCaptcha",
                           "Please validate the captcha",
                           "reCaptcha")
  logInfo("reCaptcha not validated")
}
```

要使用JSON.parse，您必须在webApp中包含“shared/json2.js”：

![](assets/scripting-captcha6.png)

自版本8797起，要使用验证API URL，您必须通过在urlPermission节点中添加，将其允许列表添加到serverConf文件的中：

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`
