---
product: campaign
title: 个性化链接跟踪入门
description: 了解如何在电子邮件中编写可个性化并支持在Campaign中跟踪的链接
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: d0e00b40-e7dd-4484-b37c-fd3f3ac70fda
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 7%

---

# 个性化链接跟踪入门 {#tracking-personalized-links}



包含个性化的电子邮件内容中的链接，需要跟踪特定的语法。

在电子邮件内容(HTML或文本)中使用JavaScript允许您生成动态内容并将其发送给收件人，但存在两个限制：

* 脚本无法直接访问数据库（SQL函数和API函数不可用），
* Adobe Campaign必须能够检测URL，以便能够跟踪链接。 [了解详情](detecting-tracking-urls.md)

您可以添加特定的预处理指令来编写URL脚本并跟踪它。 [了解详情](pre-processing-instructions.md)

对于跟踪检测，Adobe Campaign会嵌入 [整齐](https://www.html-tidy.org/) 分析HTML源并检测模式。 其中列出了内容的所有URL，以便可以单独跟踪这些URL。 Adobe Campaign再次使用Tidy替换URL (`http://myurl.com`)，其URL指向Adobe Campaign重定向服务器。

例如，在初始内容中： `http://myurl.com/a.php?name=<%=escapeUrl(recipient.lastName)%>` 被替换为一个特定收件人： `http://emailing.customer.com/r/?id=h617791,71ffa3,71ffa8&p1=CustomerName`

其中：

* “h”表示HTML内容（或“t”表示文本内容）。
* 617791是消息ID/broadLog ID（十六进制）。
* 71ffa3是NmsDelivery ID（十六进制）。
* 71ffa8是NmsTrackingUrl ID（十六进制）。
* p1、p2等都是URL中要替换的参数。
