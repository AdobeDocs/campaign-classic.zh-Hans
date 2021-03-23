---
solution: Campaign Classic
product: campaign
title: 了解投放失败
description: 了解如何理解投放故障
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: d1b38acc5209a5c96ab7a35fe9640159141b110f
workflow-type: tm+mt
source-wordcount: '2580'
ht-degree: 14%

---


# 了解投放失败{#understanding-delivery-failures}

## 关于投放失败{#about-delivery-failures}

当消息（电子邮件、短信、推送通知）无法发送到用户档案时，远程服务器自动发送错误消息，该消息由Adobe Campaign平台拾取并经资格确定是否应隔离电子邮件地址或电话号码。 请参阅[弹回邮件管理](#bounce-mail-management)。

>[!NOTE]
>
>**电子邮件**&#x200B;错误消息（或“退件”）由 Enhanced MTA（同步退回）或 inMail 进程（异步退回）进行鉴别。
>
>**短信**&#x200B;错误消息（或“状态报告”的“SR”）由 MTA 进行鉴别。

发送消息后，投放日志允许您视图每个用户档案的投放状态以及关联的故障类型和原因。

如果地址被隔离或投放处于隔离状态，则还可以在用户档案准备过程中排除阻止列表消息。 排除的消息列在投放仪表板中。

**相关主题：**

* [投放日志和历史](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)
* [失败状态](../../delivery/using/delivery-performances.md#failed-status)
* [投放失败类型和原因](#delivery-failure-types-and-reasons)

## 投放失败类型和原因{#delivery-failure-types-and-reasons}

消息失败时有三种类型的错误。 每种错误类型都决定是否将地址发送给隔离。 有关详细信息，请参阅[将地址发送到隔离](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)的条件

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
   <td> 软/硬 </td> 
   <td> 4 </td> 
   <td> 链接到地址的帐户不再处于活动状态。 当Internet访问提供商(IAP)检测到长时间的不活动时，它可以关闭用户帐户。 投放到用户地址将不可能。 如果帐户因为六个月的不活动而暂时禁用，并且仍然可以激活，则将分配状态“有错误”，并将再次尝试该帐户，直到错误计数器达到5。 如果错误表明帐户已永久停用，则将直接将其设置为隔离。<br /> </td> 
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
   <td> 没有为收件人提供地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 质量差的地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此地址的质量等级太低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 列入阻止列表 </td> 
   <td> 硬 </td> 
   <td> 8 </td> 
   <td> 地址已在发送阻止列表时添加到。 此状态用于将数据从外部列表和外部系统导入Adobe Campaign隔离列表。<br /> </td> 
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
   <td> 地址在允许列表。 因此，将忽略该错误，并将发送一封电子邮件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 仲裁后排除 </td> 
   <td> 已忽略 </td> 
   <td> 12 </td> 
   <td> 收件人被“仲裁”类型活动类型规则排除。<br /> </td> 
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
   <td> 此用户的邮箱已满，无法接受更多邮件。 此用户档案将被重新定向，直到错误计数达到 5 为止。此后，该记录将设置为隔离状态，并且以后不会再进行重试。<br /> 此类错误由清理进程管理，地址在30天后设置为有效状态。<br /> 警告：为了从隔离地址的列表中自动删除地址，必须启动数据库清理技术工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未连接 </td> 
   <td> 已忽略 </td> 
   <td> 6 </td> 
   <td> 发送消息时，收件人的移动电话已关闭或未连接到网络。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定义 </td> 
   <td> 未定义 </td> 
   <td> 0 </td> 
   <td> 地址已被限定，因为错误尚未递增。 当服务器发送新的错误消息时，会发生此类错误： 这可能是一个孤立的错误，但如果再次发生，则错误计数会增加，从而提醒技术团队。然后，他们可以执行消息分析并通过树结构中的<span class="uicontrol">管理</span> / <span class="uicontrol">活动管理</span> / <span class="uicontrol">非可交付项管理</span>节点确认此错误。<br /> </td> 
  </tr> 
  <tr> 
   <td> 没有资格获得优惠 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 该收件人没有资格获得投放中的优惠。<br /> </td> 
  </tr> 
  <tr> 
   <td> 拒绝 </td> 
   <td> 软/硬 </td> 
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
   <td> 邮政地址未限定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不可到达 </td> 
   <td> 软/硬 </td> 
   <td> 3 </td> 
   <td> 消息投放链中发生错误。 它可能是SMTP中继上的事件、临时不可到达的域等。 根据错误，地址将再次尝试，直到错误计数器达到5，或直接发送给隔离。<br /> </td> 
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

如果消息由于&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;错误而失败，则在投放期间将执行重试。

>[!NOTE]
>
>临时未传送的消息只能与&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;错误相关，而不能与&#x200B;**Hard**&#x200B;错误(请参阅[投放失败类型和原因](#delivery-failure-types-and-reasons))相关。

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md)，则投放中的重试设置不再由活动使用。 软跳出重试和软跳出时间长度由增强的MTA根据邮件电子邮件域返回的跳出响应的类型和严重性决定。

对于使用旧版活动 MTA的内部部署安装和托管/混合安装，要修改投放的持续时间，请转到投放或投放模板的高级参数，然后在相应字段中指定所需的持续时间。 请参阅[定义有效期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

默认配置允许以一小时间隔进行5次重试，然后每天重试4天。 可以全局更改重试数(与Adobe技术管理员联系)或针对每个投放或投放模板(请参阅[配置重试](../../delivery/using/steps-sending-the-delivery.md#configuring-retries))。

## 同步和异步错误{#synchronous-and-asynchronous-errors}

消息在发送后可能立即失败（同步错误），或稍后失败（异步错误）。

* 同步错误：由Adobe Campaign投放服务器联系的远程邮件服务器立即返回错误消息，不允许将投放发送到用户档案服务器。 Adobe Campaign确认了每个错误，以确定相关电子邮件地址是否应被隔离。 请参阅[退回邮件鉴别](#bounce-mail-qualification)。
* 异步错误：接收服务器会在迟些时间发送退回邮件或重新发送 SR。此邮件加载到应用程序用于标记有错误消息的技术邮箱中。 最晚的异步错误，可能发生在发送投放的一周之后。

   >[!NOTE]
   >
   >弹回邮箱的配置详见[本节](../../installation/using/deploying-an-instance.md#managing-bounced-emails)。

   [反馈循环](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)的操作类似于弹回电子邮件。 当用户将电子邮件归为垃圾邮件时，您可以在Adobe Campaign中配置电子邮件规则以阻止对此用户的所有投放。 发送给已将电子邮件限定为垃圾邮件的用户的邮件会自动重定向到专门为此目的创建的电子邮件框。 这些用户的地址处于状阻止列表态，即使他们未单击退订链接。 地址在阻止列表(**NmsAddress**)隔离表中，而不在(**NmsRecipient**)收件人表中。

   >[!NOTE]
   >
   >投诉管理详见[可交付性管理](../../delivery/using/about-deliverability.md)部分。

## 弹回邮件管理{#bounce-mail-management}

Adobe Campaign平台使您能够通过弹回邮件功能管理电子邮件投放失败。

当无法将电子邮件发送给收件人时，远程消息服务器会自动将错误消息（弹回邮件）返回到专为此目的而设计的技术收件箱。

对于使用旧版活动 MTA的内部部署安装和托管/混合安装，错误消息由Adobe Campaign平台收集并由inMail流程进行限定，以丰富电子邮件管理规则的列表。

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md)，则大多数电子邮件管理规则不再使用。 有关更多信息，请参阅[此章节](#email-management-rules)。

### 退回邮件鉴别{#bounce-mail-qualification}

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md):
>
>* **[!UICONTROL Delivery log qualification]**&#x200B;表中的跳出资格不再用于&#x200B;**同步**&#x200B;投放失败错误消息。 增强的MTA可确定跳出类型和资格，并将该信息发回给活动。
   >
   >
* ****&#x200B;异步退回仍然由 inMail 流程通过 **[!UICONTROL Inbound email]** 规则进行鉴别。有关此的详细信息，请参阅[电子邮件管理规则](#email-management-rules)。
   >
   >
* 对于使用不带Webhooks/EFS **的增强MTA**&#x200B;的实例，**[!UICONTROL Inbound email]**&#x200B;规则还将用于处理来自增强MTA的同步弹回电子邮件，使用与异步弹回电子邮件相同的电子邮件地址。


对于使用传统活动 MTA的本地安装和托管/混合安装，当电子邮件投放失败时，Adobe Campaign投放服务器从消息服务器或远程DNS服务器接收错误消息。 错误列表由远程服务器返回的消息中包含的字符串组成。 故障类型和原因被分配给每个错误消息。

此列表可通过&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;节点使用。 它包含Adobe Campaign用来确定投放失败的所有规则。 它非穷尽的，并由Adobe Campaign定期更新，也可以由用户管理。

![](assets/tech_quarant_rules_qualif.png)

远程服务器在第一次出现此错误类型时返回的消息显示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表的&#x200B;**[!UICONTROL First text]**&#x200B;列中。 如果未显示此列，请单击列表右下方的&#x200B;**[!UICONTROL Configure list]**&#x200B;按钮以选择它。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign过滤器此消息以删除变量内容（如ID、日期、电子邮件地址、电话号码等） 并在&#x200B;**[!UICONTROL Text]**&#x200B;列中显示筛选结果。 变量将替换为&#x200B;**`#xxx#`**，但替换为&#x200B;**`*`**&#x200B;的地址除外。

此过程允许汇总相同类型的所有故障，并避免在投放日志资格表中出现类似错误时出现多个条目。

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]**&#x200B;字段显示消息在列表中的出现次数。 限于10万次。 例如，如果您希望重置字段，可以编辑该字段。

弹回邮件可能具有以下资格状态：

* **[!UICONTROL To qualify]** :无法验证弹回邮件。必须向交付能力团队分配资格，以保证有效的平台交付能力。 只要邮件不符合条件，反弹邮件就不会用来丰富电子邮件管理规则的列表。
* **[!UICONTROL Keep]** :弹回邮件已得到验证，将由“刷新 **以交付** 能力”工作流与现有电子邮件管理规则进行比较，丰富列表。
* **[!UICONTROL Ignore]** :活动MTA会忽略弹回邮件，这意味着此弹回不会导致收件人地址被隔离。**Refresh for deliverability**&#x200B;工作流将不使用它，它将不会发送到客户端实例。

![](assets/deliverability_qualif_status.png)

### 电子邮件管理规则{#email-management-rules}

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md)，则大多数电子邮件管理规则不再使用。 有关详细信息，请参阅以下各节。

通过&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;节点访问邮件规则。 电子邮件管理规则显示在窗口的下半部分。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的默认参数是在部署向导中配置的。 有关详细信息，请参阅[本节](../../installation/using/deploying-an-instance.md)。

默认规则如下。

>[!IMPORTANT]
>
>* 如果参数已更改，则必须重新启动投放服务器(MTA)。
>* 管理规则的修改或创建仅适用于专家用户。


#### 入站电子邮件{#inbound-email}

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md)，并且您的实例具有&#x200B;**Webhooks/EFS**&#x200B;功能，则&#x200B;**[!UICONTROL Inbound email]**&#x200B;规则不再用于同步投放失败错误消息。 有关更多信息，请参阅[此章节](#bounce-mail-qualification)。

对于使用旧版活动 MTA的本地安装和托管/混合安装，这些规则包含可由远程服务器返回的字符串列表，并允许您限定错误（**Hard**、**Soft**&#x200B;或&#x200B;**Ignored**）。

当电子邮件失败时，远程服务器将返回一条弹回消息到平台参数中指定的地址。 Adobe Campaign将每个弹回邮件的内容与规则列表中的字符串进行比较，然后将其分配为三种[错误类型之一](#delivery-failure-types-and-reasons)。

>[!NOTE]
>
>用户可以创建自己的规则。 在导入包时以及通过&#x200B;**刷新以获得交付性**&#x200B;工作流更新数据时，将覆盖用户创建的规则。

有关弹回邮件资格的详细信息，请参阅[本节](#bounce-mail-qualification)。

#### 域管理{#domain-management}

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md)，则不再使用&#x200B;**[!UICONTROL Domain management]**&#x200B;规则。 所有域名的所有消息，其 **DKIM（域名识别邮件）**&#x200B;电子邮件身份验证签名均由 Enhanced MTA 进行。除非在 Enhanced MTA 中专门说明，否则不会使用 **Sender ID**、**DomainKeys** 或 **S/MIME** 进行签名。

对于使用旧版活动 MTA的本地安装和托管/混合安装，Adobe Campaign消息服务器将单个&#x200B;**域管理**&#x200B;规则应用于所有域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 可以选择是否激活某些标识标准和加密密钥以检查域名，如&#x200B;**发件人ID**、**域密钥**、**DKIM**&#x200B;和&#x200B;**S/MIME**。
* 通过&#x200B;**SMTP relay**&#x200B;参数，可以配置特定域的中继服务器的IP地址和端口。 有关更多信息，请参阅[此章节](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果您的邮件在Outlook中以&#x200B;**[!UICONTROL on behalf of]**&#x200B;的发件人地址显示，请确保您没有使用&#x200B;**发件人ID**（来自Microsoft的过时的专有电子邮件身份验证标准）对电子邮件进行签名。 如果&#x200B;**[!UICONTROL Sender ID]**&#x200B;选项处于启用状态，请取消选中相应的框，并与[Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)联系。 您的可交付性不会受到影响。

#### MX管理{#mx-management}

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md)，则不再使用&#x200B;**[!UICONTROL MX management]**&#x200B;投放吞吐量规则。 增强的MTA使用其自己的MX规则，允许它根据您自己的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，按域自定义您的吞吐量。

对于使用旧版活动 MTA的本地安装和托管/混合安装：

* MX管理规则用于管理特定域的传出电子邮件的流。 他们对弹回消息进行采样，并在适当时阻止发送。

* Adobe Campaign消息服务器应用特定于域的规则，然后在规则列表中使用星号表示的一般情况规则。

* 要配置MX管理规则，只需设置一个阈值并选择某些SMTP参数。 **threshold**&#x200B;是计算为错误百分比的限制，超过该百分比，将阻止向特定域发送的所有消息。 例如，在一般情况下，如果错误率达到90%，则至少300封邮件的发送将被阻止3小时。

有关MX管理的详细信息，请参阅[本节](../../installation/using/email-deliverability.md#mx-configuration)。
