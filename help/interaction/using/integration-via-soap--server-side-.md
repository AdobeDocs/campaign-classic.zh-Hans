---
title: 通过SOAP（服务器端）进行集成
seo-title: 通过SOAP（服务器端）进行集成
description: 通过SOAP（服务器端）进行集成
seo-description: null
page-status-flag: never-activated
uuid: 678371c5-4246-4886-994e-30dbbc70f14a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 477a2c31-0403-4db1-a372-c75dca58380d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 通过SOAP（服务器端）进行集成{#integration-via-soap-server-side}

为选件管理提供的SOAP web服务与Adobe Campaign中通常使用的服务不同。 您可以通过上一节所述的交互URL访问这些组件，并允许您为给定联系人演示或更新选件。

## 优惠主张 {#offer-proposition}

对于通过SOAP提供的建议，添加 **nms:postiption#Phoned** command后跟以下参数：

* **targetId**:收件人的主键（可以是复合键）。
* **maxCount**:指定联系人的选件建议数。
* **上下文**:允许您在空间架构中添加上下文信息。 如果使用的架构 **是nms:interaction**, **`<empty>`** 则应添加此架构。
* **类别**:指定选件必须属于的类别。
* **主题**:指定选件必须属于的主题。
* **uuid**:adobe Campaign永久cookie的值(“uuid230”)。
* **nli**:adobe Campaign会话cookie(“nlid”)的值。
* **noProp**:使用“true”值取消激活建议插入。

>[!NOTE]
>
>targetId **和maxCount** 设 **** 置是强制设置。 其他选项是可选的。

响应查询，SOAP服务将返回以下参数：

* **interactionId**:交互的ID。
* **命题**:XML元素，包含命题列表，每个命题都有自己的ID和HTML表示形式。

## 优惠更新 {#offer-update}

将 **nms:interaction#UpdateStatus命令添加到URL** ，后跟以下参数：

* **主张**:字符串，它包含在选件命题期间作为输出给出的命题ID。 请参阅 [优惠主张](#offer-proposition)。
* **status**:字符串类型，它指定选件的新状态。 可能的值列在 **nms:common架构中的命** 名状态 **，枚举** 中。 例如，现成数字3与“已接受”状 **态** 。
* **上下文**:XML元素，允许您在空间架构中添加上下文信息。 如果使用的架构 **是nms:interaction**, **`<empty>`** 则应添加此架构。

## 使用SOAP调用的示例 {#example-using-a-soap-call}

以下是SOAP调用的代码示例：

```
<%
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.mdSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
