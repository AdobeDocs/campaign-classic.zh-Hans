---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign Classic中管理交付性时的要点
description: 在Adobe Campaign Classic中管理可交付性时，需要检查哪些要点？
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 5d1a653a9a164c34bb70efcc86ff2d7bdf1130a2
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---


# 可交付性疑难解答{#deliverability-faq}

您是否遇到交付能力问题？ 您可以在此处找到解决方案。

## MX规则错误{#mx-rule-error}

**错误消息“配额满足”意味着什么？**

此消息表示您已达到特定MX的配额限制，并且您必须等待才能向此提供者发送其他电子邮件。

在Adobe Campaign中，有一个关于每小时可发送的电子邮件数的配置。 此配置必须保持警惕，因为实例中定义的数字与ISP进行的连接数有关，而不是实际发送的电子邮件数。

这意味着连接可以使用MX规则，而不能成功发送电子邮件。 在这种情况下，IP配置或信誉低的域在发送电子邮件之前必须尝试多个连接。 每次尝试都会使用每小时信用的消息。 因此，营销活动表现将受到重大影响。

因此，“满足配额”不仅是配置问题，还可以与声誉挂钩。 分析[SMTP日志](../../production/using/monitoring-processes.md#smtp-errors-per-domain)中的错误消息很重要。

有关MX配置的详细信息，请参阅[本节](../../installation/using/email-deliverability.md#mx-configuration)。

## ISP {#same-error-for-an-isp}的相同错误消息

**为什么我总是收到与特定ISP相同的错误消息？**

如果ISP始终收到相同的错误消息，则ISP可能已检测到您的电子邮件或IP存在错误。 执行以下建议：
* 检查您是否收到链接到不存在的电子邮件地址的大部分故障（**用户未知**&#x200B;故障）。
* 更新您的订阅表单以检测输入的域名中的任何错误(例如：gmaul.com或yaho.com)。
* 如果您注意到声明您的邮件被声明为垃圾邮件或您的邮件经常被阻止的错误，请尝试排除在目标的过去12个月中未打开或单击您的某封邮件的收件人。

如果问题仍然存在，请联系商业或可交付性服务，[Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 阻止列表与隔离{#denylist-versus-quarantine}

* **时的电子邮件地址与隔离的电阻止列表子邮件地址有何区别？**

   * 状态&#x200B;**[!UICONTROL Denylisted]**&#x200B;是反馈循环的结果（当某人将邮件报告为垃圾邮件时）。

   * 状态&#x200B;**[!UICONTROL Quarantined]**&#x200B;是软弹回或硬弹回的结果。
   有关更多信息，请参阅[此章节](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔离错误原因意味着什么？**

   以下是10个可能的原因：未定义、用户未知、无效域、、拒阻止列表绝、错误忽略、不可到达、帐户禁用、邮箱已满、未连接。

   有关此方面的详细信息，请参阅[了解隔离管理](../../delivery/using/understanding-quarantine-management.md)。

## 正在从阻止列表{#remove-from-denylist}中删除

* **我的一个收件人误阻止列表入。如何从密尼斯特中删除它们，以便我可以开始再次发送邮件？**

   * 转到&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**。
   * 在相应记录的详细信息中，将&#x200B;**[!UICONTROL Status]**&#x200B;字段的值设置为&#x200B;**[!UICONTROL Valid]**。
   * 保存记录。

* **如何确定我的IP是否在中阻止列表?如何从中删除我的阻止列表IP?**

   要检查您的IP地址是否在阻止列表程序中，您可以使用各个网站验证它，例如：
   * [MX工具箱](https://mxtoolbox.com/)
   * [我的IP地址是什么](https://whatismyipaddress.com)

   通常，IP地址检查的结果将返回一个列表，其中包含的详细信阻止列表息以及拒绝IP地址的网站的名称。

   通过单击相应的链接，您可以访问网站详细信息。 然后，您可以请求从添加IP地址到其的网站中取消列出您的网阻止列表站。

   >[!NOTE]
   >
   >除名过程可能因网站而异。 某些站点需要您创建帐户，而其他站点只需要您提供IP地址。
