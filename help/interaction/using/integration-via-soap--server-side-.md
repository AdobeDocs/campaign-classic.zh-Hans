---
product: campaign
title: 通过 SOAP（服务器端）进行集成
description: 通过 SOAP（服务器端）进行集成
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 3%

---

# 通过SOAP（服务器端）进行集成{#integration-via-soap-server-side}

![](../../assets/v7-only.svg)

为选件管理提供的SOAP Web服务与Adobe Campaign中常用的服务不同。 您可以通过上一节中描述的交互URL访问这些选件，并让您展示或更新给定联系人的选件。

## 优惠建议 {#offer-proposition}

有关通过SOAP提供的建议，请在 **nms:campation#Propose** 命令后跟以下参数：

* **targetId**:收件人的主键（可以是复合键）。
* **maxCount**:指定联系人的选件建议数。
* **上下文**:允许您在空间架构中添加上下文信息。 如果使用的架构为 **nms:interaction**, **`<empty>`** 值。
* **类别**:指定选件必须属于的类别。
* **主题**:指定选件必须属于的主题。
* **uid**:Adobe Campaign永久cookie的值(“uuid230”)。
* **nli**:Adobe Campaign会话Cookie(“nlid”)的值。
* **noProp**:使用“true”值停用建议书插入。

>[!NOTE]
>
>的 **targetId** 和 **maxCount** 设置是强制性的。 其他选项是可选的。

响应查询，SOAP服务将返回以下参数：

* **interactionId**:交互的ID。
* **命题**:XML元素，包含命题列表，每个命题都有自己的ID和HTML表示。

## 选件更新 {#offer-update}

添加 **nms:interaction#UpdateStatus** 命令到URL，然后是以下参数：

* **命题**:字符串，它包含在选件建议期间作为输出给出的建议ID。 请参阅 [优惠建议](#offer-proposition).
* **状态**:字符串类型，它会指定选件的新状态。 可能的值列在 **命题状态** 枚举，在 **nms:common** 架构。 例如，现成的数字3对应于 **已接受** 状态。
* **上下文**:XML元素，用于在空间架构中添加上下文信息。 如果使用的架构为 **nms:interaction**, **`<empty>`** 值。

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
