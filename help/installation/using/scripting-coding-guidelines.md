---
solution: Campaign Classic
product: campaign
title: 脚本和编码指南
description: 进一步了解在Adobe Campaign中进行开发时应遵循的准则(工作流、Javascript、JSSP等)。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 4%

---


# 脚本和编码指南{#scripting-coding-guidelines}

## 脚本

有关详细信息，请参阅[活动 JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

如果您使用工作流、Web应用程序、jssp编写脚本，请遵循以下最佳实践：

* 尽量避免使用SQL语句。

* 如果需要，请使用参数化（prepare语句）函数，而不是字符串连接。

   坏做法：

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

要避免SQL注入，必须将SQL函数添加到要在Adobe Campaign中使用的允许列表中。 将它们添加到允许列表后，操作员在表达式编辑器中就会看到它们。 请参见[此页面](../../configuration/using/adding-additional-sql-functions.md)。

>[!IMPORTANT]
>
>如果使用的内部版本早于8140，则&#x200B;**XtkPassUnknownSQLFunctionsToRDBMS**&#x200B;选项可能设置为“1”。 如果要保护数据库，请删除此选项（或将其设置为“0”）。

如果您使用用户输入在查询或SQL语句中构建过滤器，则始终必须对它们进行转义(请参阅[活动 JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) — 数据保护：转义函数)。 这些函数包括：

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## 保护新数据模型

### 文件夹库

请参阅以下页面：

* [文件夹访问属性](../../platform/using/access-management.md)
* [链接文件夹](../../configuration/using/configuration.md#linked-folder)

### 已命名权限

除了基于文件夹的安全模型之外，您还可以使用已命名权限来限制操作符操作：

* 您可以添加一些系统过滤器(sysFilter)以防止对数据进行读/写（请参阅[此页](../../configuration/using/filtering-schemas.md)）。

   ```
   <sysFilter name="writeAccess">    
       <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
   </sysFilter>
   ```

* 您还可以保护在模式中定义的某些操作（SOAP方法）。 只需设置访问属性，并将相应的名为right的值设置为值。

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
>您可以在navtree的命令节点中使用已命名权限。 它提供了更好的用户体验，但不提供任何保护（仅使用客户端隐藏/禁用它们）。 您必须使用access属性。

### 溢出表

如果您需要根据操作符访问级别保护机密数据(模式的一部分)，请不要在表单定义（enabledIf/visibleIf条件）中隐藏机密数据。

整个实体由屏幕加载，您还可以在列定义中显示它们。 为此，必须创建溢出表。 请参阅[此页](../../configuration/using/examples-of-schemas-edition.md#overflow-table)。

## 在Web应用程序中添加捕捉

在公共登陆页/订阅页面中添加验证码是一个好做法。 很遗憾，在数字内容编辑器(数字内容编辑器)页面中添加验证码并非易事。 我们将向您展示如何添加v5 captcha或Google reCAPTCHA。

在数字内容编辑器中添加验证码的一般方法是创建个性化基块以将其轻松包含在页面内容中。 您必须添加&#x200B;**脚本**&#x200B;活动和&#x200B;**测试**。

### 个性化基块

1. 转到&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Personalization blocks]**&#x200B;并新建一个。

1. 使用&#x200B;**[!UICONTROL Web application]**&#x200B;内容类型并检查&#x200B;**[!UICONTROL Visible in the customization menus]**。

   有关详细信息，请参见[此页面](../../delivery/using/personalization-blocks.md)。

   以下是&#x200B;**活动captcha**&#x200B;的示例：

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

   * 第1至6行生成所有所需输入。
   * 第7行到末端手柄错误。
   * 第4行允许您更改验证码灰框大小（宽度/高度）和生成字的长度(minWordSize/maxWordSize)。
   * 在使用Google reCAPTCHA之前，您必须在Google上注册并创建新的reCAPTCHA站点。

      `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`
   您应该可以禁用验证按钮，但由于我们没有任何标准按钮/链接，最好在HTML中自行禁用它。 要了解如何操作，请参阅[此页](https://developers.google.com/recaptcha/)。

### 更新Web应用程序

1. 访问Web应用程序的属性，以添加一个名为&#x200B;**captchaValid**&#x200B;的布尔变量。

   ![](assets/scripting-captcha.png)

1. 在最后一页和&#x200B;**[!UICONTROL Storage]**&#x200B;活动之间，添加&#x200B;**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL Test]**。

   将分支&#x200B;**[!UICONTROL True]**&#x200B;插入&#x200B;**[!UICONTROL Storage]**，将分支插入具有captcha的页面。

   ![](assets/scripting-captcha2.png)

1. 编辑分支True的条件，`"[vars/captchaValid]"`等于True。

   ![](assets/scripting-captcha3.png)

1. 编辑&#x200B;**[!UICONTROL Script]**&#x200B;活动。 内容取决于所选的captcha引擎。

1. 最后，您可以在页面中添加您的个性化区块：请参阅[此页](../../web/using/editing-content.md)。

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>要进行reCAPTCHA集成，必须在HTML中添加客户端JavaScript（在`<head>...</head>`中）：
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### 活动 captcha

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

第6行：你可以放任何类型的错误消息。

### Google recaptcha

请参阅[官方文件](https://developers.google.com/recaptcha/docs/verify)。

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

自构建8797以来，为了使用验证API URL，您必须通过添加到urlPermission节点，将其添加到serverConf文件中的允许列表:

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`