---
product: campaign
title: 在Adobe Campaign Classic中管理可投放性时的要点
description: 了解在Adobe Campaign中管理可投放性时要检查的要点
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
TQID: https://experienceleague.adobe.com/ZRai7Bd-IRaWUQQmkuUYwXhNXp2BI-B4k-4cGq1k6uk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: b631758a-142d-425f-b9aa-f756d85cb979id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2: id: e95a583b-fcfa-4524-8666-46a29c828119id: c8da4fdd-eb94-4751-a43c-f82733fb2d6eid: d5bbe3da-ba85-4242-817e-54f7c4b943e0id: f4da0e76-df77-451e-ad61-21afb7bd8810
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 660
ht-degree: 2%

---

# 可投放性故障排除{#deliverability-faq}

您是否遇到过可投放性问题？ 您可以在此处找到解决方案。

## MX规则错误 {#mx-rule-error}

**错误消息“满足配额”是什么意思？**

此消息表示您已达到特定MX的配额限制，必须等待才能向此提供商发送另一封电子邮件。

在Adobe Campaign中，有一个关于每小时可以发送的电子邮件数量的配置。 此配置必须谨慎使用，因为实例中定义的数字与通过ISP进行的连接数有关，而不是与实际发送的电子邮件数有关。

这意味着连接可以使用MX规则而不成功发送电子邮件。 在这种情况下，具有IP或信誉较低的域的配置在发送电子邮件之前必须尝试多个连接。 对于每次尝试，将使用每小时信用的消息。 因此，营销活动效果将受显着影响。

因此，“满足配额”不仅是一个配置问题，还可以与信誉相关联。 在[SMTP日志](../../production/using/monitoring-processes.md#smtp-errors-per-domain)中分析错误消息很重要。

有关MX配置的详细信息，请参阅[此部分](../../installation/using/email-deliverability.md#mx-configuration)。

## ISP的同一错误消息 {#same-error-for-an-isp}

**为什么我总是收到针对特定ISP的相同错误消息？**

如果您总是收到与ISP相同的错误消息，则您的电子邮件或IP可能被ISP检测到为故障。 执行以下建议：
* 检查您是否收到大量与不存在电子邮件地址关联的故障（**用户未知**&#x200B;个故障）。
* 更新您的订阅表单，以检测输入的域名中是否有任何错误（例如：gmaul.com或yaho.com）。
* 如果您发现错误，指出您的邮件被声明为垃圾邮件，或您的邮件被持续阻止，请尝试排除过去12个月内未打开或单击您邮件之一的收件人，使其离开目标。

如果问题仍然存在，请联系商业或可投放性服务，[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 阻止列表与隔离 {#denylist-versus-quarantine}

* **阻止列表的电子邮件地址与隔离的电子邮件地址有何区别？**

   * 状态&#x200B;**[!UICONTROL Denylisted]**&#x200B;是反馈循环（当某人报告邮件为垃圾邮件时）的结果。

   * 状态&#x200B;**[!UICONTROL Quarantined]**&#x200B;是软退回或硬退回的结果。

  有关更多信息，请参阅[此小节](delivery-failures-quarantine.md#quarantine-vs-denylist)。

* **不同的隔离错误原因意味着什么？**

  以下是10个可能的原因：未定义、用户未知、域无效、阻止列表时、被拒绝、错误被忽略、无法访问、帐户被禁用、邮箱已满、未连接。

  有关此内容的详细信息，请参阅[了解隔离管理](delivery-failures-quarantine.md)。

## 从阻止列表中删除 {#remove-from-denylist}

* **我的一名收件人被错误地添加到阻止列表。 如何将其从阻止列表中移除，以便可以重新向他们发送消息？**

   * 转到&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**。
   * 在对应的记录的详细信息中，将&#x200B;**[!UICONTROL Status]**&#x200B;字段的值设置为&#x200B;**[!UICONTROL Valid]**。
   * 保存记录。

* **如何确定我的IP是否位于上？ 如何从阻止列表中删除我的IP？**

  要检查您的IP地址是否位于阻止列表上，您可以使用各种网站对其进行验证，例如：
   * [MX Toolbox](https://mxtoolbox.com/)
   * [我的IP地址是什么](https://whatismyipaddress.com)

  通常，IP地址检查的结果将返回一个列表，其中包含IP地址的详细信息，以及拒绝IP地址的网站的名称。

  通过单击相应的链接，您可以访问网站详细信息。 然后，您可以请求将您的网站从将IP地址添加到其的网站中除名。

  >[!NOTE]
  >
  >除名过程可能因网站而异。 有些站点要求您创建帐户，而有些站点仅要求您提供IP地址。
