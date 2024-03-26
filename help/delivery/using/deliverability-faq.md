---
product: campaign
title: 在Adobe Campaign Classic中管理可投放性时的要点
description: 了解在Adobe Campaign中管理可投放性时要检查的要点
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 1%

---

# 可投放性故障排除{#deliverability-faq}

您是否遇到过可投放性问题？ 您可以在此处找到解决方案。

## MX规则错误 {#mx-rule-error}

**错误消息“满足配额”是什么意思？**

此消息表示您已达到特定MX的配额限制，必须等待才能向此提供商发送另一封电子邮件。

在Adobe Campaign中，有一个关于每小时可以发送的电子邮件数量的配置。 此配置必须谨慎使用，因为实例中定义的数字与通过ISP进行的连接数有关，而不是与实际发送的电子邮件数有关。

这意味着连接可以使用MX规则而不成功发送电子邮件。 在这种情况下，具有IP或信誉较低的域的配置在发送电子邮件之前必须尝试多个连接。 对于每次尝试，将使用每小时信用的消息。 因此，营销活动效果将受显着影响。

因此，“满足配额”不仅是一个配置问题，还可以与信誉相关联。 分析中的错误消息很重要 [SMTP日志](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

有关MX配置的更多信息，请参见 [本节](../../installation/using/email-deliverability.md#mx-configuration).

## ISP的同一错误消息 {#same-error-for-an-isp}

**为什么我总是收到针对特定ISP的相同错误消息？**

如果您总是收到与ISP相同的错误消息，则您的电子邮件或IP可能被ISP检测到为故障。 执行以下建议：
* 检查您是否收到大量与不存在电子邮件地址关联的故障(**用户未知** 失败)。
* 更新您的订阅表单，以检测输入的域名中是否有任何错误(例如：gmaul.com或yaho.com)。
* 如果您发现错误，指出您的邮件被声明为垃圾邮件，或您的邮件被持续阻止，请尝试排除过去12个月内未打开或单击您邮件之一的收件人，使其离开目标。

如果问题仍然存在，请与商业或可投放性服务部门联系， [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 阻止列表与隔离 {#denylist-versus-quarantine}

* **阻止列表上的电子邮件地址与隔离的电子邮件地址之间有何区别？**

   * 状态 **[!UICONTROL Denylisted]** 是反馈循环（当个人将邮件报告为垃圾邮件时）的结果。

   * 状态 **[!UICONTROL Quarantined]** 是软退回或硬退回的结果。

  有关更多信息，请参阅[此小节](understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔离错误原因意味着什么？**

  以下是10个可能的原因：未定义、用户未知、域无效、阻止列表时、被拒绝、错误被忽略、无法访问、帐户被禁用、邮箱已满、未连接。

  有关此内容的更多信息，请参阅 [了解隔离管理](understanding-quarantine-management.md).

## 从阻止列表中删除 {#remove-from-denylist}

* **我的一名收件人被错误地添加到阻止列表中。 如何将其从拒绝列表中删除，以便可以重新开始向其发送消息？**

   * 转到 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * 在对应的记录的详细信息中，设置 **[!UICONTROL Status]** 字段至 **[!UICONTROL Valid]**.
   * 保存记录。

* **如何确定我的IP之一是否位于阻止列表上？ 如何从阻止列表中删除我的IP？**

  要检查您的IP地址是否位于阻止列表上，您可以使用各种网站对其进行验证，例如：
   * [MX Toolbox](https://mxtoolbox.com/)
   * [我的IP地址是什么](https://whatismyipaddress.com)

  列入阻止列表通常，IP地址检查的结果将返回一个列表，其中包含IP地址的详细信息，以及拒绝IP地址的网站的名称。

  通过单击相应的链接，您可以访问网站详细信息。 列入阻止列表然后，您可以请求将您的网站从将IP地址添加到其的网站中除名。

  >[!NOTE]
  >
  >除名过程可能因网站而异。 有些站点要求您创建帐户，而有些站点仅要求您提供IP地址。
