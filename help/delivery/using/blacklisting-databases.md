---
title: 黑名单数据库
seo-title: 黑名单数据库
description: 黑名单数据库
seo-description: null
page-status-flag: never-activated
uuid: 8a4a69f9-87d5-4044-bc55-76cdcb2e7800
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: eede254d-2b25-46ed-b10f-fa1d54780a75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 62553344f557206443fa2de0499df42d8b771e21

---


# 黑名单数据库{#blacklisting-databases}

一些组织维护IP地址和域的数据库，这些数据库被垃圾邮件发送者称为使用。 咨询这些站点有助于了解为什么某些邮件被拒绝为垃圾邮件。 通常可以请求删除错误地添加到这些列表的地址。

这些数据库称为RBL（实时黑洞列表），并通过DNS机制查询它们。 RBL有三种类型：

* 按IP地址：列出发送垃圾邮件或可能中继垃圾邮件的IP地址。
* 按发送者域：列出发送垃圾邮件的发送者域（弹回邮件地址的完整域）或错误配置。
* 按Web域：列出在垃圾邮件内容中包含的链接和图像的URL中找到的域（通过注册商注册的高级域）。 在Adobe Campaign中，要考虑的域通常是用于跟踪的地址。

以下是使用最广泛的RBL列表。 有关更全面的列表，您可以参阅 [https://www.declude.com/Articles.asp?ID=97](https://www.declude.com/Articles.asp?ID=97) 或 [https://www.dnsstuff.com/](https://www.dnsstuff.com/) （“IP工具”部分，“垃圾数据库查找”表单）。

* **Spamhaus**

   请参阅 [https://www.spamhaus.org/](https://www.spamhaus.org/)

   数据库更重要。 被列入这一名单，通常情况很严重。 如果发生这种情况，您必须立即采取行动并警告商业服务、交付性和Adobe Campaign支持。

* **SpamCop**

   请参阅 [https://www.spamcop.net/](https://www.spamcop.net/)

   它是最著名的数据库之一。 如果您的某个IP地址被放在此列表上，这通常意味着SpamCop用户已将您的消息声明为垃圾邮件，或者您已将消息发送到SpamCop蜜罐。

* **URIBL**

   请参阅 [https://www.uribl.com/](https://www.uribl.com/)

   此列表标识在声明为垃圾邮件的邮件中定期显示的域。 如果您的域出现在此列表中，则可能会显着影响您的可交付性。 您应立即通知提供服务和Adobe Campaign支持。

* **SURBL**

   请参阅 [https://www.surbl.org/](https://www.surbl.org/)

   SURBL识别定期显示在垃圾信息中的网站。 如果您的域出现在此列表中，则可能会显着影响您的可交付性。 您应立即通知提供服务和Adobe Campaign支持。

* **iX Manitu**

   这是一系列知识产权，在德国被广泛使用。 请参阅 [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->