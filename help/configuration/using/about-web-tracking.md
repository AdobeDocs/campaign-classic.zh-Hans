---
product: campaign
title: 关于 Web 跟踪
description: 关于 Web 跟踪
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# 关于 Web 跟踪{#about-web-tracking}

![](../../assets/v7-only.svg)

除了显示Internet用户单击电子邮件中链接的行为的标准跟踪之外，Adobe Campaign平台还允许您收集有关Internet用户如何浏览您网站的信息。 此数据收集由Web跟踪模块执行。

当互联网用户单击来自给定投放的电子邮件中的跟踪链接时，已联系的重定向服务器会存储一个会话Cookie，其中包含broadlog标识符(broadlogId)和投放标识符(deliveryId)。

然后，当用户每次访问包含Web跟踪标记的页面时，Web客户端会将此Cookie发送到服务器。 在整个会话期间（即，直到Web客户端关闭为止），这将一直持续。

重定向服务器以这种方式收集以下数据：

* 通过作为参数发送的标识符查看的页面URL
* 通过会话cookie访问网页的投放，
* 通过会话cookie单击了
* 其他信息，如生成的业务量。

下图显示了客户端与各种服务器之间对话的各个阶段。

![](assets/d_ncs_integration_webtracking_structure1.png)
