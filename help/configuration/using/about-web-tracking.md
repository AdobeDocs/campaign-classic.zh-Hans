---
title: 关于Web跟踪
seo-title: 关于Web跟踪
description: 关于Web跟踪
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 关于Web跟踪{#about-web-tracking}

除了显示Internet用户单击电子邮件中链接的行为的标准跟踪外，Adobe Campaign平台还允许您收集有关Internet用户浏览网站的方式的信息。 该数据收集由网络跟踪模块执行。

当因特网用户单击来自给定交付的电子邮件中的跟踪链接时，重定向服务器联系到的会话cookie会保存包含广播标识符(broadlogId)和交付标识符(deliveryId)的会话cookie。

然后，当用户每次访问包含Web跟踪标记的页面时，Web客户端都会向服务器发送此Cookie。 在整个会话中，即直到关闭Web客户端。

重定向服务器通过这种方式收集以下数据：

* 通过作为参数发送的标识符查看的页面的URL,
* 通过会话Cookie访问网页的传送，
* 通过会话Cookie单击的Internet用户的标识符，
* 其他信息，如生成的业务量。

下图显示了客户端与各种服务器之间对话的各个阶段。

![](assets/d_ncs_integration_webtracking_structure1.png)

