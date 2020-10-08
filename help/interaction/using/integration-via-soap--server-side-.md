---
title: 通过 SOAP（服务器端）进行集成
seo-title: 通过 SOAP（服务器端）进行集成
description: 通过 SOAP（服务器端）进行集成
seo-description: null
page-status-flag: never-activated
uuid: 678371c5-4246-4886-994e-30dbbc70f14a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: unitary-interactions
discoiquuid: 477a2c31-0403-4db1-a372-c75dca58380d
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 6%

---


# 通过 SOAP（服务器端）进行集成{#integration-via-soap-server-side}

为优惠管理提供的SOAP Web服务与通常用于Adobe Campaign的服务不同。 您可以通过上一节中介绍的交互URL访问这些优惠，并让您展示或更新给定联系人的信息。

## 优惠建议 {#offer-proposition}

对于通过SOAP优惠建议，添 **加nms:postipation#Phoned** 命令后跟以下参数：

* **targetId**:收件人的主键（可以是复合键）。
* **maxCount**:指定联系人的优惠建议数。
* **上下文**:允许您在空间模式中添加上下文信息。 如果使用的模式 **是nms:interaction****`<empty>`** ，则应添加。
* **类别**:指定类别必须属于的优惠。
* **主题**:指定优惠必须属于的主题。
* **uuid**:adobe campaign永久cookie的值(“uuid230”)。
* **nli**:adobe campaign会话cookie(“nlid”)的值。
* **noProp**:使用“true”值取消激活建议插入。

>[!NOTE]
>
>targetId **和** maxCount **设置是必** 需的。 其他选项是可选的。

响应查询,SOAP服务将返回以下参数：

* **interactionId**:交互的ID。
* **命题**:XML元素，包含命题的列表，每个命题都有自己的ID和HTML表示。

## 优惠更新 {#offer-update}

将nms: **interaction#UpdateStatus命令添加** 到URL，后跟以下参数：

* **主张**:字符串，它包含在优惠建议期间作为输出给定的命题ID。 请参阅 [优惠建议](#offer-proposition)。
* **状态**:字符串类型，它指定优惠的新状态。 可能的值列在nms: **common** 明细列表的命 **名状态模式中** 。 例如，现成的数字3与“已接受”状 **态** 。
* **上下文**:XML元素，允许您在空间模式中添加上下文信息。 如果使用的模式 **是nms:interaction****`<empty>`** ，则应添加。

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
