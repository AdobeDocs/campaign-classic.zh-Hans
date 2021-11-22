---
product: campaign
title: 在Adobe Campaign Classic中管理投放能力时的要点
description: 在Adobe Campaign Classic中管理投放能力时，需要检查哪些要点？
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 2%

---

# 投放能力疑难解答{#deliverability-faq}

![](../../assets/common.svg)

您遇到投放能力问题吗？ 你可以在这里找到解决方案。

## MX规则错误 {#mx-rule-error}

**错误消息“满足配额”表示什么？**

此消息表示您已达到特定MX的配额限制，您必须等待才能向此提供商发送另一封电子邮件。

在Adobe Campaign中，有关每小时可发送的电子邮件数量的配置。 此配置必须保持警惕，因为实例中定义的数字与与ISP进行的连接数有关，而与实际发送的电子邮件数无关。

这意味着连接可以使用MX规则，而无需成功发送电子邮件。 在这种情况下，使用IP或信誉不佳的域的配置必须先尝试多个连接，然后再发送电子邮件。 每次尝试时，将使用每小时点数的消息。 因此，营销活动的效果将受到重大影响。

因此，“满足配额”不仅是配置问题，还可能与声誉相关。 分析 [SMTP日志](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

有关MX配置的更多信息，请参阅 [此部分](../../installation/using/email-deliverability.md#mx-configuration).

## ISP的相同错误消息 {#same-error-for-an-isp}

**为什么对于特定ISP，我始终会收到相同的错误消息？**

如果ISP始终收到相同的错误消息，则ISP可能会检测到您的电子邮件或IP有错误。 执行以下建议：
* 检查您是否收到与不存在的电子邮件地址(**用户未知** 失败)。
* 更新订阅表单以检测输入的域名中是否存在任何错误(例如：gmaul.com或yaho.com)。
* 如果您发现错误，指出您的消息被声明为垃圾邮件，或您的消息被持续阻止，请尝试排除在目标位置最近12个月内未打开或单击其中一条消息的收件人。

如果问题仍然存在，请联系商业或可投放性服务， [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 阻止列表隔离 {#denylist-versus-quarantine}

* **“”上的电子邮件地址与隔离的阻止列表电子邮件地址之间有何区别？**

   * 状态 **[!UICONTROL Denylisted]** 是反馈循环（当人员将消息报告为垃圾邮件时）的结果。

   * 状态 **[!UICONTROL Quarantined]** 是软或硬退回的结果。
   有关更多信息，请参阅[此章节](understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔离错误原因意味着什么？**

   以下是10个可能的原因：未定义、用户未知、无效域、、拒阻止列表绝、错误已忽略、不可访问、帐户已禁用、邮箱已满、未连接。

   有关此内容的更多信息，请参阅 [了解隔离管理](understanding-quarantine-management.md).

## 从阻止列表中删除 {#remove-from-denylist}

* **我的一个收件人被错误地添阻止列表加到中。 如何从密文中删除这些邮件，以便我能够再次发送它们的邮件？**

   * 转到 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * 在相应记录的详细信息中，设置 **[!UICONTROL Status]** 字段 **[!UICONTROL Valid]**.
   * 保存记录。

* **如何确定我的一个IP是否在阻止列表上？ 如何从中删除我的IP阻止列表?**

   要检查您的IP地址是否在阻止列表上，您可以使用各种网站来验证它，例如：
   * [MX工具箱](https://mxtoolbox.com/)
   * [我的IP地址是什么](https://whatismyipaddress.com)

   通常，IP地址检查的结果将返回一个列表，其中包含的详细信阻止列表息以及拒绝IP地址的网站名称。

   通过单击相应的链接，可访问网站详细信息。 然后，您可以请求将您的网站从添加了IP地址的网站中除阻止列表名。

   >[!NOTE]
   >
   >除名过程可能因网站而异。 有些网站需要您创建帐户，而另一些网站则只需要您提供IP地址。
