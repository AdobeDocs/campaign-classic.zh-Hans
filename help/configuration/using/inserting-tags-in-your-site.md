---
product: campaign
title: 在网站中输入Web跟踪标记
description: 了解如何在网站中插入Web跟踪标记
exl-id: e7fcec75-82fe-45ff-8d45-7d6e95baeb14
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 在您的网站中插入Web跟踪标记{#inserting-tags-in-your-site}

![](../../assets/v7-only.svg)

## 简单方法 {#simple-method}

此方法包括通过插入 **`<img>`** HTML标记。

>[!IMPORTANT]
>
>此方法使用Web浏览器发送的Cookie来标识收件人，不是100%可靠。

**示例**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

插入的标记与重定向服务器联系。

![](assets/d_ncs_integration_webtracking_structure2.png)

在控制台中定义要跟踪的页面时，可以生成一个示例Web跟踪标记，以将其复制并粘贴到网页的源代码中。

但是，在使用TRANSACTION类型标记时，必须使用JavaScript修改示例标记，以插入事务信息（金额、项目数）和扩展架构定义的任何信息。

### 标记的静态插入 {#static-insertion-of-tags}

要执行静态标签插入，只需将控制台生成或手动构建的标签复制并粘贴到网页源中即可。

**示例**:在显示表单的页面上插入web跟踪标记。

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

在确认页面(“amount.md”)中插入TRANSACTION类型的Web跟踪标记。

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### 动态生成Web跟踪标记 {#dynamic-generation-of-web-tracking-tags}

当网页是动态生成的时，您可以在页面生成时添加Web跟踪标记。

**示例**:Web跟踪已添加到JSP。

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## 最佳方法 {#optimum-method-}

如果您希望控制发送到重定向服务器的信息，最可靠的方法是使用页面生成语言同步地执行HTTP查询。

您构建的URL必须遵循中定义的语法规则 [Web跟踪标记：定义](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>重定向和Web跟踪使用Cookie，执行同步HTTP调用的Web服务器必须与重定向服务器位于同一域中，这一点很重要。 各种HTTP交换必须传达“id”、“uuid”和“uuid230”Cookie。

**示例**:在Java中动态生成，并使用收件人的帐号进行身份验证。

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```
