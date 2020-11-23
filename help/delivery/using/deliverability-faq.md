---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign Classic管理可交付性时的要点
description: 在Adobe Campaign Classic管理可交付性时，需要检查哪些要点？
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 0%

---


# 交付性疑难解答{#deliverability-faq}

您是否遇到交付能力问题？ 您可以在此处找到解决方案。

## MX规则错误 {#mx-rule-error}

**错误消息“配额已满”表示什么？**

此消息表示您已达到特定MX的配额限制，并且您必须等待才能向此提供者发送其他电子邮件。

在Adobe Campaign中，有一个关于每小时可发送的电子邮件数的配置。 此配置必须引起警惕，因为实例中定义的数字与ISP进行的连接数有关，而与实际发送的电子邮件数无关。

这意味着连接可以使用MX规则，而不能成功发送电子邮件。 在这种情况下，具有IP或信誉低的域的配置在发送电子邮件之前必须尝试多个连接。 每次尝试时，都会使用每小时信用消息。 因此，营销活动表现将受到重大影响。

因此，&quot;配额满足&quot;不仅是配置问题，也与声誉挂钩。 分析SMTP日志中的错误消 [息很重要](../../production/using/monitoring-processes.md#smtp-errors-per-domain)。

For more on MX configuration, see [this section](../../installation/using/email-deliverability.md#mx-configuration).

## ISP的相同错误消息 {#same-error-for-an-isp}

**为什么对于特定ISP，我始终收到相同的错误消息？**

如果您始终收到与ISP相同的错误消息，则ISP可能已检测到您的电子邮件或IP存在错误。 执行以下建议：
* 检查您是否收到链接到不存在的电子邮件地址的大部分失败(用&#x200B;**户未知** 失败)。
* 更新订阅表单以检测输入的域名中的任何错误(例如：gmaul.com或yaho.com)。
* 如果您注意到错误消息被声明为垃圾邮件或消息被持续阻止的错误，请尝试排除在目标过去12个月中未打开或单击某封邮件的收件人。

如果问题仍然存在，请联系商业或可交付性服务、Adobe Campaign客户服务或Adobe Campaign支持。

## 阻止列表与隔离 {#denylist-versus-quarantine}

* **电子邮件地址与隔离电子邮件地阻止列表址之间有何差异？**

   * 状态 **[!UICONTROL Denylisted]** 是反馈循环的结果（当人员将邮件报告为垃圾邮件时）。

   * 状态 **[!UICONTROL Quarantined]** 是软弹回或硬弹回的结果。
   有关更多信息，请参阅[此章节](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)。

* **不同的隔离错误原因意味着什么？**

   以下是10个可能的原因：未定义、用户未知、无效域、、拒阻止列表绝、忽略错误、不可到达、帐户禁用、邮箱已满、未连接。

   For more on this, see [Understanding quarantine management](../../delivery/using/understanding-quarantine-management.md).

## 从阻止列表删除 {#remove-from-denylist}

* **我的一个收件人误阻止列表入。 如何从密文主义者中删除它们，以便我能够开始再次发送邮件？**

   * 转到 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**。
   * 在相应记录的详细信息中，将字段的值 **[!UICONTROL Status]** 设置为 **[!UICONTROL Valid]**。
   * 保存记录。

* **如何确定我的IP是否在阻止列表? 如何从中删除我的IP阻止列表?**

   要检查您的IP地址是否在阻止列表程序中，您可以使用各个网站验证它，例如：
   * [MX工具箱](https://mxtoolbox.com/)
   * [我的IP地址是什么](https://whatismyipaddress.com)

   通常，IP地址检查的结果将返回一个列表，其中包阻止列表含的详细信息以及拒绝IP地址的网站的名称。

   通过单击相应的链接，您可以访问网站详细信息。 然后，您可以请求从添加IP地址到其的网站中取消列出您的网阻止列表站。

   >[!NOTE]
   >
   >除名过程可能因网站而异。 某些站点需要您创建帐户，而其他站点只需要您提供IP地址。

## 最佳做法 {#best-practices}

以下是一些最佳实践，可帮助识别和解决可交付性问题。

### 确定可交付性问题 {#identify-deliverability-issue}

以下元素可能会引起您的注意：

* 邮件或活动指标：退订、滥用投诉和／或反弹率高于往常。
* 订户活动:打开、点击和／或事务比往常低。
* 种子帐户显示已过滤或未传送的邮件。

### 假设势的原因 {#potential-causes}

请扪心自问，确定可交付性问题的可能原因：

* 列表细分最近是否有变化？
* 我是否获得了任何新数据源？
* 我是不是意外地寄了隔离文件？
* 问题是否可能是由于我的邮件内容？
* 我发送的邮件是否足够频繁以保持温暖的IP?
* 我是按活动/参与还是发送完整文件来分段邮件？
* 从最近的情况看，我的文件上的“安全”部分是什么？
* 我是否为未定义为安全的区段制定了重新激活和重新确认策略？

### 解决问题 {#address-issue}

**投诉**

投诉由从收件箱中 **点击相应按钮将电子邮件报** 告为垃圾邮件的订户定义。

如果您的投放问题是由投诉引起的：
* 你需要尝试确定收件人抱怨的原因。
* 您可能还希望考虑将取消订阅链接移至电子邮件顶部。 这将鼓励订阅者取消订阅，而不是抱怨垃圾邮件按钮。

发送方可以从反馈循环投诉中获 [得大量信](../../delivery/using/technical-recommendations.md#feedback-loop) 息：
* 必须存储数据，并在选择加入来源、地址订阅时间、甚至某些行为人口统计等方面寻找模式。
* 投诉通常可以识别文件中有风险的数据源或细分。 “风险”被定义为最有可能抱怨的，这会损害声誉，进而会损害收件箱费率。

投诉还来自那些不再希望接收电子邮件的订户：
* 这通常可能是由于消息过多、用户对消息的感知、他们不期望消息，或者不记得选择加入。
* 运行审核以确保所有收集点都是清晰的，并且您的获取点中没有预先选中的框，这一点也很重要。
* 当订阅者选择加入时，您还应发送欢迎电子邮件，以设置基调并说明他们预期收到您电子邮件的频率。

**数据有效性**

**当您发送** 到ISP的无法传递的 **地址时** ，会出现硬弹回。 地址可能因以下诸多原因而无法送达：
* 地址拼写错误。 这可以通过实时数据验证服务解决，或在向该地址发送营销电子邮件之前要求确认的选择加入。
* 列表或数据源错误。 如果它来自新源，请查看地址的收集方式并确保获得许可。
* 邮寄到一次处于活动状态，但在一段时间不活动后已关闭或终止的地址。

**参与**

除了投诉和数据有效性外，ISP们比以往更加专注于积极 **的参与** ，以作出投放决策。 他们希望了解您的订阅者是打开您的电子邮件，还是在不阅读电子邮件的情况下将其删除。 由于他们不与发送方共享此数据，我们必须利用我们提供的信息，并将打开／点击／交易转换为互动。

作为持续声誉维护的一部分，了解参与列表的订阅者在您的中的情况并为每个文件的订 **阅者制定** 一个最近的风险等级。 最近期定义为上次打开／单击／处理或注册日期。 此时间帧可能因垂直而异。 操作步骤：

1. 确定每个垂直的活动（“安全”）区段。 这通常是过去3-6个月内处于活动状态的订阅者。
1. 减少不活跃的频率。
1. 创建重 [新参与系列](../../delivery/using/re-engagement-best-practices.md) ，以应对风险不足。 这通常为6-9个月，无需参与。
1. 为更高的风险失效制定重新确认活动。 这通常是9-12个月内未使用电子邮件的订阅者。
1. 最后，设置放弃规则并删除在“x”个月内未打开电子邮件的订阅者。 我们通常建议使用12个月以上的时间，但这可能因销售和购买周期而有所不同。
