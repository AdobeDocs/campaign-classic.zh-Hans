---
product: campaign
title: 关于 Web 跟踪
feature: Configuration, Instance Settings
description: 关于 Web 跟踪
role: User, Developer
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
TQID: https://experienceleague.adobe.com/FfA6FEH5WP2JJGVR4BhpjO19Yj4mt8irvyJLwuzCThs
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 192
ht-degree: 4%

---

# 关于 Web 跟踪{#about-web-tracking}

除了可显示Internet用户点击电子邮件中链接的行为标准的跟踪之外，Adobe Campaign平台还允许您收集Internet用户浏览网站的方式信息。 此数据收集由Web跟踪模块执行。

当互联网用户单击来自给定投放的电子邮件中的跟踪链接时，所联系的重定向服务器会存储包含broadlog标识符(broadlogId)和投放标识符(deliveryId)的会话Cookie。

然后，Web客户端在用户每次访问包含Web跟踪标记的页面时向服务器发送此Cookie。 此过程将在整个会话期间持续进行，即直到Web客户端关闭。

重定向服务器通过这种方式收集以下数据：

* 已查看页面的URL，通过作为参数发送的标识符，
* 通过会话Cookie访问网页的投放，
* 通过会话Cookie单击的Internet用户的标识符
* 其他信息，如产生的业务量。

下图显示了客户端和各种服务器之间的对话阶段。

![](assets/d_ncs_integration_webtracking_structure1.png)
