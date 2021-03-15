---
solution: Campaign Classic
product: campaign
title: 开始跟踪个性化链接
description: 了解如何在电子邮件中编写可以个性化的链接，并在Campaign Classic中支持跟踪。
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 6b81d0ea22bf9d8f33e486535b4ce02fbae7b9ae
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---


# 开始跟踪个性化链接 {#tracking-personalized-links}

电子邮件内容中包含个性化的链接需要跟踪特定的语法。

在电子邮件内容（HTML或文本）中使用JavaScript可以生成动态内容并将动态内容发送给收件人，但有两个限制：

* 脚本无法直接访问数据库（SQL函数和API函数不可用），
* Adobe Campaign必须能够检测URL，以便跟踪链接。 [了解详情](detecting-tracking-urls.md)

您可以添加特定的预处理说明来编写URL的脚本并跟踪它。 [了解详情](pre-processing-instructions.md)

对于跟踪检测，Adobe Campaign嵌入[Tidy](http://www.html-tidy.org/)以分析HTML源并检测模式。 它会列表内容的所有URL，以便可以单独跟踪它们。 Adobe Campaign再次使用“整洁”将URL(`http://myurl.com`)替换为指向Adobe Campaign重定向服务器的URL。

例如，在初始内容中：`http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>`被替换为：`http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

地点：

* “h”指HTML内容（或“t”指文本内容）。
* 617791是消息ID / broadLog ID（十六进制）。
* 71ffa3是NmsDelivery ID（十六进制）。
* 71ffa8是NmsTrackingUrl ID（十六进制）。
* p1、p2等都是URL中要替换的参数。
