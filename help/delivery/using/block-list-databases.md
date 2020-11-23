---
solution: Campaign Classic
product: campaign
title: 阻止列表数据库
description: 阻止列表数据库
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# 阻止列表数据库{#denylist-databases}

一些组织维护着据称被垃圾邮件发送者使用的IP地址和域数据库。 咨询这些站点有助于了解为什么某些邮件会被拒绝为垃圾邮件。 通常可以请求删除错误地添加到这些列表的地址。

这些列表库称为RBL（实时黑洞），它们通过DNS机制进行查询。 RBL有三种类型：

* 按IP地址：列表发送垃圾邮件或可能转发垃圾邮件的IP地址。
* 按发件人域：列表发送垃圾邮件或配置不正确的发件人域（弹回邮件地址的完整域）。
* 按Web域：列表在垃圾邮件内容中包含的链接和图像的URL中找到的域（通过注册器注册的高级域）。 在Adobe Campaign中，要考虑的域通常是用于跟踪的地址。

以下是使用最广的RBL的列表。 有关更全面的列表，请参阅 [https://www.dnsstuff.com/](https://tools.dnsstuff.com/)。

* **Spamhaus**

   请参阅 [https://www.spamhaus.org/](https://www.spamhaus.org/)

   数据库更重要。 在这一列表上保密通常是一种严重的情况。 如果发生这种情况，您必须立即采取行动，并警告商业服务、交付能力和Adobe Campaign支持。

* **SpamCop**

   请参阅 [https://www.spamcop.net/](https://www.spamcop.net/)

   它是最著名的数据库之一。 如果您的某个IP地址被放置在此列表上，这通常意味着SpamCop用户已将您的邮件声明为垃圾邮件，或者您已将邮件发送到SpamCop蜜罐。

* **URIBL**

   请参阅 [https://www.uribl.com/](https://www.uribl.com/)

   此列表标识在声明为垃圾邮件的邮件中定期显示的域。 如果您的域出现在此列表上，则可能会显着影响您的交付能力。 您应立即通知提供服务和Adobe Campaign支持。

* **SURBL**

   请参阅 [http://www.surbl.org/](http://www.surbl.org/)

   SURBL识别定期出现在垃圾邮件中的网站。 如果您的域出现在此列表上，则可能会显着影响您的交付能力。 您应立即通知提供服务和Adobe Campaign支持。

* **iX Manitu**

   这是知识产权的列表，在德国广泛使用。 请参阅 [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->