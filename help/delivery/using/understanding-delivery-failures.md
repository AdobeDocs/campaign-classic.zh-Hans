---
title: 了解投放失败
description: 了解如何了解投放故障
page-status-flag: never-activated
uuid: 03a91f84-77fe-40a9-8be9-a6a35a873ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 78b58a7a-b387-4d5d-80d5-01c06f83d759
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '2440'
ht-degree: 16%

---


# 了解投放失败{#understanding-delivery-failures}

## 关于投放失败{#about-delivery-failures}

当消息（电子邮件、SMS、推送通知）无法发送到用户档案时，远程服务器自动发送错误消息，该消息由Adobe Campaign平台拾取，并且被限定以确定是否应隔离电子邮件地址或电话号码。 See [Bounce mail management](#bounce-mail-management).

>[!NOTE]
>
>电子邮件错误消息（或“弹回”）由inMail流程限定。 短信错误消息（或“状态报告”的“SR”）由 MTA 进行鉴别。

发送消息后，投放日志允许您视图每个用户档案的投放状态以及关联的故障类型和原因。

如果地址被隔离或投放处于隔离状态，则还可在用户档案准备过程中排除阻止列表消息。 排除的消息列在投放仪表板中。

**相关主题：**

* [投放日志和历史](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)
* [失败状态](../../delivery/using/monitoring-a-delivery.md#failed-status)
* [投放失败类型和原因](#delivery-failure-types-and-reasons)

## 投放失败类型和原因{#delivery-failure-types-and-reasons}

消息失败时有三种错误。 每种错误类型都决定是否将地址发送给隔离。 有关详细信息，请参 [阅向隔离发送地址的条件](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **Hard**：“Hard”错误表示地址无效。这涉及显式声明地址无效的错误消息，如：“未知用户”。
* **Soft**：这可能是临时错误，或者无法分类的错误，例如：“域名无效”或“邮箱已满”。
* **Ignored**：这是一个已知的临时错误，如“不在办公室”，或是一个技术错误，例如，如果发件人类型为“邮递员”。

投放失败可能的原因有：

<table> 
 <tbody> 
  <tr> 
   <td> 错误标签 </td> 
   <td> 错误类型 </td> 
   <td> 技术价值 </td> 
   <td> 说明 </td> 
  </tr> 
  <tr> 
   <td> 帐户已禁用 </td> 
   <td> 软／硬 </td> 
   <td> 4 </td> 
   <td> 链接到该地址的帐户不再有效。 当Internet访问提供商(IAP)检测到长时间的非活动时，它可以关闭用户帐户。 投放到用户地址将不可能。 如果帐户由于六个月的非活动状态而暂时禁用，并且仍可激活，则将分配状态“有错误”，并将再次尝试该帐户，直到错误计数器达到5。 If the error signals that the account is permanently deactivated, it will directly be set to Quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> 隔离地址 </td> 
   <td> 硬 </td> 
   <td> 9 </td> 
   <td> 地址已置于隔离。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未指定地址 </td> 
   <td> 硬 </td> 
   <td> 7 </td> 
   <td> 未为收件人提供地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 质量不佳的地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此地址的质量等级太低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 列入阻止列表地址 </td> 
   <td> 硬 </td> 
   <td> 8 </td> 
   <td> 地址已在发阻止列表送时添加到。 此状态用于将数据从外部列表和外部系统导入Adobe Campaign隔离列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制地址 </td> 
   <td> 已忽略 </td> 
   <td> 127 </td> 
   <td> 收件人的地址是对照组的一部分。<br /> </td> 
  </tr> 
  <tr> 
   <td> 多次 </td> 
   <td> 已忽略 </td> 
   <td> 10 </td> 
   <td> 收件人的地址已在此投放中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 忽略错误 </td> 
   <td> 已忽略 </td> 
   <td> 25 </td> 
   <td> 地址在允许列表。 因此，该错误会被忽略，并将发送一封电子邮件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 仲裁后排除 </td> 
   <td> 已忽略 </td> 
   <td> 12 </td> 
   <td> 收件人被“仲裁”类型的活动类型规则排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 被SQL规则排除 </td> 
   <td> 已忽略 </td> 
   <td> 11 </td> 
   <td> 收件人被“SQL”类型活动类型规则排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 无效域 </td> 
   <td> 柔和 </td> 
   <td> 2 </td> 
   <td> 电子邮件地址的域不正确或不再存在。 此用户档案将被重新定向，直到错误计数达到 5 为止。此后，该记录将设置为隔离状态，并且以后不会再进行重试。<br /> </td> 
  </tr> 
  <tr> 
   <td> 邮箱已满 </td> 
   <td> 柔和 </td> 
   <td> 5 </td> 
   <td> 此用户的邮箱已满，无法接受更多邮件。 此用户档案将被重新定向，直到错误计数达到 5 为止。此后，该记录将设置为隔离状态，并且以后不会再进行重试。<br /> 此类型的错误由清除进程管理，地址在30天后设置为有效状态。<br /> 警告：为了从隔离地址的列表中自动删除地址，必须启动数据库清理技术工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未连接 </td> 
   <td> 已忽略 </td> 
   <td> 6 </td> 
   <td> The recipient's mobile phone is switched off or not connected to the network when the message is sent.<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定义 </td> 
   <td> 未定义 </td> 
   <td> 0 </td> 
   <td> 地址已被限定，因为错误尚未递增。 当服务器发送新的错误消息时，会发生此类错误： 这可能是一个孤立的错误，但如果再次发生，则错误计数会增加，从而提醒技术团队。然后，他们可以通过树结构中的“管理”/“ <span class="uicontrol">分析</span> ”/“ <span class="uicontrol">活动管理”</span> /“ <span class="uicontrol">非可交付产品管理</span> ”节点执行消息并确认此错误。<br /> </td> 
  </tr> 
  <tr> 
   <td> 没有资格获得优惠 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 收件人没有资格获得投放中的优惠。<br /> </td> 
  </tr> 
  <tr> 
   <td> 拒绝 </td> 
   <td> 软／硬 </td> 
   <td> 20 </td> 
   <td> 由于作为垃圾邮件报告的安全反馈，该地址已置于隔离中。 根据错误，地址将再次尝试，直到错误计数器达到5，或直接发送给隔离。<br /> </td> 
  </tr> 
  <tr> 
   <td> 目标大小有限 </td> 
   <td> 已忽略 </td> 
   <td> 17 </td> 
   <td> 已达到投放的最大收件人大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不合格地址 </td> 
   <td> 已忽略 </td> 
   <td> 15 </td> 
   <td> 邮政地址不符合条件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不可到达 </td> 
   <td> 软／硬 </td> 
   <td> 3 </td> 
   <td> 消息投放链中出错。 它可能是SMTP中继的事件，是临时不可到达的域，等等。 根据错误，地址将再次尝试，直到错误计数器达到5，或直接发送给隔离。<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户未知 </td> 
   <td> 硬 </td> 
   <td> 1 </td> 
   <td> 地址不存在。 不再尝试对该用户档案进行投放。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 在投放临时失败后重试{#retries-after-a-delivery-temporary-failure}

如果消息由于临时 **的** Soft **或Ignored** （忽略）错误而失败，则投放将在重试持续期间执行。

>[!NOTE]
>
>临时未传送的消息只能与Soft **或Ignored** 错误 **相关** ，但不能与Hard **(硬错误** )相关(请参 [](#delivery-failure-types-and-reasons)阅投放故障类型和原因)。

要修改投放的持续时间，请转至投放或投放模板的高级参数，并在相应的字段中指定所需的持续时间。 本节介绍高级投放 [属性](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

默认配置允许每小时间隔五次重试，然后每天重试4天。 可以全局更改重试数(联系Adobe技术管理员)或针对每个投放或投放模板(请参 [阅本节](../../delivery/using/steps-sending-the-delivery.md#configuring-retries))。

## 同步和异步错误{#synchronous-and-asynchronous-errors}

消息在发送后可能立即失败（同步错误），或稍后失败（异步错误）。

* 同步错误：adobe campaign投放服务器联系的远程邮件服务器立即返回错误消息，不允许将投放发送到用户档案服务器。 Adobe Campaign对每个错误进行了鉴定，以确定是否应隔离相关电子邮件地址。 请参阅[退回邮件鉴别](#bounce-mail-qualification)。
* 异步错误：接收服务器会在迟些时间发送退回邮件或重新发送 SR。此邮件加载到应用程序用来标记邮件的技术邮箱中，但出现错误。 最晚的异步错误，可能发生在发送投放的一周之后。

   >[!NOTE]
   >
   >弹回邮箱的配置详见 [本节](../../installation/using/deploying-an-instance.md#managing-bounced-emails)。

   反馈循 [环就像](../../delivery/using/technical-recommendations.md#feedback-loop) “弹回电子邮件”一样。 当用户将电子邮件归为垃圾邮件时，您可以配置Adobe Campaign中的电子邮件规则，以阻止此用户的所有投放。 发送给已将电子邮件限定为垃圾邮件的用户的邮件会自动重定向到专为此目的而创建的邮箱。 这些用户的地址处于状阻止列表态，即使他们没有单击退订链接。 地址在阻止列表(NmsAddress ****)隔离表中&#x200B;**，而不在(NmsRecipient**)收件人表中。

   >[!NOTE]
   >
   >投诉管理详见“交付 [能力管理](../../delivery/using/about-deliverability.md) ”部分。

## 弹回邮件管理 {#bounce-mail-management}

Adobe Campaign平台允许您通过弹回邮件功能管理电子邮件投放失败。 当无法将电子邮件发送给收件人时，远程消息服务器会自动将错误消息（弹回邮件）返回到专为此目的设计的技术收件箱。 错误消息由Adobe Campaign平台收集，并由inMail流程进行限定，以丰富电子邮件管理规则的列表

### 退回邮件鉴别{#bounce-mail-qualification}

当电子邮件投放失败时，Adobe Campaign投放服务器从消息服务器或远程DNS服务器接收错误消息。 错误列表由远程服务器返回的消息中包含的字符串组成。 故障类型和原因被分配给每个错误消息。

此列表可通过节点 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** 使用。 它包含Adobe Campaign用来限定投放失败的所有规则。 它不是完全的，并且由Adobe Campaign定期更新，也可以由用户管理。

![](assets/tech_quarant_rules_qualif.png)

* 远程服务器在第一次出现此错误类型时返回的消息显示在 **[!UICONTROL First text]** 表的列 **[!UICONTROL Delivery log qualification]** 中。 如果未显示此列，请单 **[!UICONTROL Configure list]** 击列表右下方的按钮以选择它。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign过滤器此消息以删除变量内容（如ID、日期、电子邮件地址、电话号码等） 并在列中显示筛选结 **[!UICONTROL Text]** 果。 变量将替换为 **`#xxx#`**，但替换为的地址除外 **`*`**。

此过程可以汇总相同类型的所有故障，并避免在投放日志资格表中出现类似错误时出现多个条目。

>[!NOTE]
>
>字 **[!UICONTROL Number of occurrences]** 段显示消息在列表中出现的次数。 限于100 000次。 例如，您可以编辑字段，以重置它。

弹回邮件可能具有以下资格状态：

* **[!UICONTROL To qualify]** :弹回邮件无法验证。 必须向交付能力团队分配资格，以确保有效的平台交付能力。 只要邮件不符合条件，弹回邮件就不能用于丰富电子邮件管理规则的列表。
* **[!UICONTROL Keep]** :弹回邮件已经过鉴定，将由“刷新” **工作流用于交付** ，以与现有电子邮件管理规则进行比较并丰富列表。
* **[!UICONTROL Ignore]** :活动MTA会忽略弹回邮件，这意味着此弹回永远不会导致收件人地址被隔离。 Refresh将不会将其用于可 **交付性工作流** ，也不会将其发送到客户端实例。

![](assets/deliverability_qualif_status.png)

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到增强的MTA:
>
>* 表中的弹回资格 **[!UICONTROL Delivery log qualification]** 不再用于同步投放失败错误消息。 增强的MTA可确定退回类型和资格，并将该信息发回给活动。
   >
   >
* 异步退回仍然由 inMail 流程通过 **[!UICONTROL Inbound email]** 规则进行鉴别。For more on this, see [Email management rules](#email-management-rules).
   >
   >
* 对于使用无Webhooks/EFS的 **增强MTA**，规则 **[!UICONTROL Inbound email]** 还将用于处理来自增强MTA的同步弹回电子邮件，使用与异步弹回电子邮件相同的电子邮件地址。
>
>
有关Adobe Campaign增强MTA的详细信息，请参 [阅此文档](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)。

### 电子邮件管理规则 {#email-management-rules}

邮件规则通过节点 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 访问。 电子邮件管理规则显示在窗口的下半部分。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的默认参数在部署向导中进行配置。 For further information, refer to [this section](../../installation/using/deploying-an-instance.md).

默认规则如下所示。

>[!IMPORTANT]
>
>* 如果参数已更改，则必须重新启动投放服务器(MTA)。
>* 管理规则的修改或创建仅适用于专家用户。


#### 入站电子邮件 {#inbound-email}

这些规则包含可由远程服务器返回的字符串列表，并可让您鉴别错误（**Hard**、**Soft** 或 **Ignored**）。

当电子邮件失败时，远程服务器将返回一条弹回消息至平台参数中指定的地址。 Adobe Campaign将每个弹回邮件的内容与规则列表中的字符串进行比较，然后将其分配为三个错误 [类型之一](#delivery-failure-types-and-reasons)。

>[!NOTE]
>
>用户可以创建自己的规则。 在导入包时以及通过刷新以实现交 **付性工作流更新数据** 时，将覆盖用户创建的规则。

For more on bounce mail qualification, see [this section](#bounce-mail-qualification).

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到增强型MTA，并且您的实例具有 **Webhooks/EFS** ，则规 **[!UICONTROL Inbound email]** 则不再用于同步投放故障错误消息。 有关更多信息，请参阅[此章节](#bounce-mail-qualification)。
>
>有关Adobe Campaign增强MTA的详细信息，请参 [阅此文档](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)。

#### 域管理 {#domain-management}

Adobe Campaign消息服务器将单个域 **管理规则应** 用于所有域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以选择是否激活某些标识标准和加密密钥来检查 **域名**, **如发送** ID **、DomainKeys**、 **DKIM**&#x200B;和S/MIME Javi。
* SMTP **中继参数** ，允许您为特定域配置中继服务器的IP地址和端口。 有关更多信息，请参阅[此章节](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果邮件在Outlook中的发件人 **[!UICONTROL on behalf of]** 地址中显示，请确保您没有使用发件人ID(Microsoft的过时 **专有电子邮件身份验证标准**)对电子邮件进行签名。 如果选 **[!UICONTROL Sender ID]** 项已启用，请取消选中相应的框，然后与Adobe Campaign支持联系。 您的可交付性不会受到影响。

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到增强的MTA, **[!UICONTROL Domain management]** 则不再使用规则。 所有域名的所有消息，其 **DKIM（域名识别邮件）**&#x200B;电子邮件身份验证签名均由 Enhanced MTA 进行。除非在 Enhanced MTA 中专门说明，否则不会使用 **Sender ID**、**DomainKeys** 或 **S/MIME** 进行签名。
>
>有关Adobe Campaign增强MTA的详细信息，请参 [阅此文档](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)。

#### MX管理 {#mx-management}

* MX管理规则用于为特定域调节传出电子邮件的流。 他们对弹回消息进行采样，并在适当时阻止发送。

* Adobe Campaign消息服务器应用特定于域的规则，然后应用规则列表中由星号表示的一般大小写规则。

* 要配置MX管理规则，只需设置一个阈值并选择某些SMTP参数。 阈 **值** 是计算为错误百分比的限制，超过该百分比，将阻止针对特定域的所有消息。 例如，在一般情况下，如果错误率达到90%，则至少300条邮件的发送会被阻止3小时。

For more on MX management, refer to [this section](../../installation/using/email-deliverability.md#mx-configuration).

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到增强的MTA，则不 **[!UICONTROL MX management]** 再使用投放吞吐量规则。 增强的MTA使用其自己的MX规则，该规则允许它根据您自己的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，按域自定义您的吞吐量。
>
>有关Adobe Campaign增强MTA的详细信息，请参 [阅此文档](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)。
