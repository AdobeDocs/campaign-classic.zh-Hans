---
product: campaign
title: 通过 SOAP（服务器端）进行集成
description: 通过 SOAP（服务器端）进行集成
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 5%

---

# 通过SOAP（服务器端）进行集成{#integration-via-soap-server-side}



为选件管理提供的SOAP Web服务与Adobe Campaign中通常使用的服务不同。 您可以通过上一节所述的交互URL访问选件，并让您提供或更新给定联系人的选件。

## 优惠建议 {#offer-proposition}

对于通过SOAP提供的优惠建议，请添加 **nms：proposition#Propose** 命令后跟以下参数：

* **targetId**：收件人的主键（可以是复合键）。
* **maxCount**：指定联系人的优惠建议数量。
* **上下文**：用于在空间架构中添加上下文信息。 如果使用的架构为 **nms：interaction**， **`<empty>`** 应该添加的。
* **类别**：指定选件必须属于的类别。
* **主题**：指定选件必须属于的主题。
* **uuid**：Adobe Campaign永久cookie的值(“uuid230”)。
* **nli**：Adobe Campaign会话Cookie的值(“nlid”)。
* **noProp**：使用“true”值停用建议插入。

>[!NOTE]
>
>此 **targetId** 和 **maxCount** 必须设置。 其他则是可选的。

作为对该查询的响应，SOAP服务将返回以下参数：

* **interactionId**：交互的ID。
* **建议**： XML元素，包含建议列表，每个建议都有自己的ID和HTML表示形式。

## 优惠更新 {#offer-update}

添加 **nms：interaction#UpdateStatus** 命令前往URL，然后是以下参数：

* **建议**：字符串，它包含在优惠建议期间作为输出提供的建议ID。 请参阅 [优惠建议](#offer-proposition).
* **状态**：字符串类型，它指定选件的新状态。 可能的值列在 **propositionStatus** 枚举，在 **nms：common** 架构。 例如，出厂预装的数字3对应于 **已接受** 状态。
* **上下文**：XML元素，用于在空间架构中添加上下文信息。 如果使用的架构为 **nms：interaction**， **`<empty>`** 应该添加的。

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
