---
product: campaign
title: 个性化链接跟踪入门
description: 了解如何在电子邮件中编写可进行个性化的链接，并在Campaign Classic中支持跟踪。
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 7%

---

# 个性化链接跟踪入门 {#tracking-personalized-links}

![](../../assets/common.svg)

包含个性化的电子邮件内容中的链接需要跟踪特定的语法。

通过在电子邮件内容（HTML或文本）中使用JavaScript，可生成动态内容并将其发送给收件人，但存在两个限制：

* 脚本无法直接访问数据库（SQL函数和API函数不可用），
* Adobe Campaign必须能够检测URL，才能跟踪链接。 [了解详情](detecting-tracking-urls.md)

您可以添加特定的预处理说明来编写URL脚本并跟踪它。 [了解详情](pre-processing-instructions.md)

为了进行跟踪检测，Adobe Campaign嵌入了[Tidy](https://www.html-tidy.org/)以解析HTML源并检测模式。 其中列出了内容的所有URL，以便能够单独跟踪这些URL。 Adobe Campaign再次使用Tidy将URL(`http://myurl.com`)替换为指向Adobe Campaign重定向服务器的URL。

例如，在初始内容中：`http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>`对于一个特定收件人替换为：`http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

其中：

* “h”表示HTML内容（或文本内容的“t”）。
* 617791是消息ID / broadLog ID（十六进制）。
* 71ffa3是NmsDelivery ID（十六进制）。
* 71ffa8是NmsTrackingUrl ID（十六进制）。
* p1、p2等都是URL中要替换的参数。
