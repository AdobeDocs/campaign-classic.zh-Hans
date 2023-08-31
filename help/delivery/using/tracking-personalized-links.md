---
product: campaign
title: 个性化链接跟踪入门
description: 了解如何在电子邮件中写入可在Campaign中个性化并支持跟踪的链接
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Personalization
role: User
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 7%

---

# 个性化链接跟踪入门 {#tracking-personalized-links}

电子邮件内容中包含个性化的链接需要跟踪特定语法。

在电子邮件内容(HTML或文本)中使用JavaScript允许您生成动态内容并将其发送给收件人，但存在两个限制：

* 脚本无法直接访问数据库（SQL函数和API函数不可用），
* Adobe Campaign必须能够检测URL，以便可以跟踪链接。 [了解详情](detecting-tracking-urls.md)

您可以添加特定的预处理指令来编写URL的脚本并对其进行跟踪。 [了解详情](pre-processing-instructions.md)

对于跟踪检测，Adobe Campaign会嵌入 [整洁](https://www.html-tidy.org/) 分析HTML源并检测模式。 其中列出了内容的所有URL，以便可以单独对其进行跟踪。 Adobe Campaign再次使用Tidy替换URL (`http://myurl.com`)，其URL指向Adobe Campaign重定向服务器。

例如，在初始内容中： `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` 被替换为一个特定收件人： `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

其中：

* “h”表示HTML内容（或“t”表示文本内容）。
* 617791是消息ID/broadLog ID（十六进制）。
* 71ffa3是NmsDelivery ID（十六进制）。
* 71ffa8是NmsTrackingUrl ID（十六进制）。
* p1、p2等都是要在URL中替换的参数。
