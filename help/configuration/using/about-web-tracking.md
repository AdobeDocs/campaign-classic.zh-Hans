---
solution: Campaign Classic
product: campaign
title: 关于 Web 跟踪
description: 关于 Web 跟踪
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---


# 关于 Web 跟踪{#about-web-tracking}

除了显示Internet用户单击电子邮件中链接的行为的标准跟踪外，Adobe Campaign平台还允许您收集有关Internet用户如何浏览您的网站的信息。 此数据收集由Web跟踪模块执行。

当因特网用户单击来自给定投放的电子邮件中的跟踪链接时，重定向服务器联系到存储会话cookie，该会话cookie包含广播标识符(broadlogId)和投放标识符(deliveryId)。

然后，当用户每次访问包含Web跟踪标签的页面时，Web客户端会向服务器发送此Cookie。 在整个会话中，即直到关闭Web客户端。

重定向服务器通过这种方式收集以下数据：

* 通过作为参数发送的标识符查看的页面的URL,
* 通过会话cookie访问网页的投放,
* 通过会话cookie单击的Internet用户的标识符，
* 其他信息，如生成的业务量。

下图显示了客户端与各种服务器之间对话的各个阶段。

![](assets/d_ncs_integration_webtracking_structure1.png)

