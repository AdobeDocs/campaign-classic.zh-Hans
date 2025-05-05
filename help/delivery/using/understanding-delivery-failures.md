---
product: campaign
title: 了解投放失败
description: 了解如何了解投放失败
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '2567'
ht-degree: 12%

---

# 了解投放失败{#understanding-delivery-failures}

## 关于投放失败 {#about-delivery-failures}

当消息（电子邮件、短信、推送通知）无法发送到用户档案时，远程服务器会自动发送错误消息，该消息会被Adobe Campaign平台拾取并进行鉴别，从而确定是否应隔离电子邮件地址或电话号码。 请参阅[退回邮件管理](#bounce-mail-management)。

>[!NOTE]
>
>**电子邮件**&#x200B;错误消息（或“退件”）由 Enhanced MTA（同步退回）或 inMail 进程（异步退回）进行鉴别。
>
>**短信**&#x200B;错误消息（或“状态报告”的“SR”）由 MTA 进行鉴别。

发送消息后，投放日志允许您查看每个用户档案的投放状态以及相关失败的类型和原因。

如果地址被隔离或用户档案阻止列表，也可以在投放准备期间排除消息。 排除的消息将列在投放仪表板中。

**相关主题：**

* [投放日志和历史记录](delivery-dashboard.md#delivery-logs-and-history)
* [失败状态](delivery-performances.md#failed-status)
* [投放失败类型和原因](#delivery-failure-types-and-reasons)

## 投放失败类型和原因 {#delivery-failure-types-and-reasons}

当消息失败时，有三种类型的错误。 每种错误类型都会确定地址是否被发送到隔离区。 有关详情，请参阅[将地址发送到隔离区的条件](understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

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
   <td> 帐户被禁用 </td> 
   <td> 软/硬 </td> 
   <td> 4 </td> 
   <td> 链接到地址的帐户不再有效。 当互联网访问提供商(IAP)检测到长时间不活动时，它可以关闭用户的帐户。 之后，将无法投放到用户的地址。 如果帐户因6个月不活动而被暂时禁用，且仍可激活，则将分配状态有错误并重试帐户，直到错误计数达到5。 如果错误信号表明帐户已永久停用，则直接将其设置为“隔离”。<br /> </td> 
  </tr> 
  <tr> 
   <td> 隔离地址 </td> 
   <td> 硬 </td> 
   <td> 9 </td> 
   <td> 地址被隔离。<br /> </td> 
  </tr> 
  <tr> 
   <td> 地址未指定 </td> 
   <td> 硬 </td> 
   <td> 7 </td> 
   <td> 没有给收件人地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 低质量地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此地址的质量等级太低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已列入阻止列表的地址 </td> 
   <td> 硬 </td> 
   <td> 8 </td> 
   <td> 发送时地址已添加到阻止列表。 此状态用于将外部列表和外部系统的数据导入Adobe Campaign隔离列表。<br /> </td> 
  </tr> 
  <tr> 
   <td> 对照地址 </td> 
   <td> 已忽略 </td> 
   <td> 127 </td> 
   <td> 收件人的地址是控制组的一部分。<br /> </td> 
  </tr> 
  <tr> 
   <td> 两次 </td> 
   <td> 已忽略 </td> 
   <td> 10 </td> 
   <td> 收件人的地址已在此投放中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 错误已忽略 </td> 
   <td> 已忽略 </td> 
   <td> 25 </td> 
   <td> 地址在允许列表上。 因此，该错误将被忽略，并将发送电子邮件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 仲裁后排除 </td> 
   <td> 已忽略 </td> 
   <td> 12 </td> 
   <td> 收件人已被“仲裁”类型营销活动类型规则排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 由 SQL 规则排除 </td> 
   <td> 已忽略 </td> 
   <td> 11 </td> 
   <td> 收件人已被“SQL”类型营销活动类型规则排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 无效域 </td> 
   <td> 柔光 </td> 
   <td> 2 </td> 
   <td> 电子邮件地址的域不正确或不再存在。 此用户档案将被重新定向，直到错误计数达到 5 为止。之后，该记录将设置为隔离状态，以后不会再重试。<br /> </td> 
  </tr> 
  <tr> 
   <td> 邮箱已满 </td> 
   <td> 柔光 </td> 
   <td> 5 </td> 
   <td> 此用户的邮箱已满，无法接收更多邮件。 此用户档案将被重新定向，直到错误计数达到 5 为止。此后，该记录将设置为隔离状态，并且以后不会再进行重试。<br />此类错误由清理进程管理，地址在30天后设置为有效状态。<br />警告：为了自动从隔离地址列表中移除地址，必须启动数据库清理技术工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未连接 </td> 
   <td> 已忽略 </td> 
   <td> 6 </td> 
   <td> 发送消息时，收件人的手机已关闭或未连接到网络。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定义 </td> 
   <td> 未定义 </td> 
   <td> 0 </td> 
   <td> 地址正在进行鉴别，因为错误尚未递增。 当服务器发送新错误消息时，会发生此类错误：它可能是孤立的错误，但如果再次发生，错误计数会增加，这会提醒技术团队。 然后，他们可以通过树结构中的<span class="uicontrol">管理</span> / <span class="uicontrol">Campaign Management</span> / <span class="uicontrol">不可交付结果管理</span>节点执行消息分析并限定此错误。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不符合优惠资格 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 收件人不符合投放优惠的条件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒绝 </td> 
   <td> 软/硬 </td> 
   <td> 20 </td> 
   <td> 由于安全反馈为垃圾邮件报告，该地址已被隔离。 根据错误，将再次尝试该地址，直到错误计数达到5，否则将直接将其发送到隔离区。<br /> </td> 
  </tr> 
  <tr> 
   <td> 目标大小受限 </td> 
   <td> 已忽略 </td> 
   <td> 17 </td> 
   <td> 已达到收件人的最大传递大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不合格地址 </td> 
   <td> 已忽略 </td> 
   <td> 15 </td> 
   <td> 邮寄地址不合格。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不可到达 </td> 
   <td> 软/硬 </td> 
   <td> 3 </td> 
   <td> 消息投放链中发生错误。 可能是SMTP中继上的事件、暂时无法访问的域等。 根据错误，将再次尝试该地址，直到错误计数达到5，否则将直接将其发送到隔离区。<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户未知 </td> 
   <td> 硬 </td> 
   <td> 1 </td> 
   <td> 地址不存在。 不再尝试针对此用户档案进行投放。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 投放临时失败后重试 {#retries-after-a-delivery-temporary-failure}

如果消息因临时的&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;错误而失败，则在投放持续期间将执行重试。

>[!NOTE]
>
>临时未送达的消息只能与&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;错误相关，而不是&#x200B;**Hard**&#x200B;错误（请参阅[传递失败类型和原因](#delivery-failure-types-and-reasons)）。

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign将不再使用投放中的重试设置。 软退回重试次数以及它们之间的时间长度由Enhanced MTA根据从消息的电子邮件域返回的退回响应的类型和严重性确定。

对于使用旧版Campaign MTA的内部部署和托管/混合安装，要修改投放的持续时间，请转至投放或投放模板的高级参数，并在相应的字段中指定所需的持续时间。 请参阅[定义有效期](steps-sending-the-delivery.md#defining-validity-period)。

默认配置允许每小时间隔重试五次，然后每天重试一次，持续四天。 重试次数可以全局更改(请联系您的Adobe技术管理员)，也可以针对每个投放或投放模板进行更改。 请参阅[配置重试](steps-sending-the-delivery.md#configuring-retries)。

## 同步和异步错误 {#synchronous-and-asynchronous-errors}

消息在发送后可能会立即失败（同步错误），或稍后失败（异步错误）。

* 同步错误：Adobe Campaign投放服务器联系的远程邮件服务器立即返回错误消息，不允许将投放发送到用户档案服务器。 Adobe Campaign会对每个错误进行鉴别，以确定是否应隔离相关的电子邮件地址。 请参阅[退回邮件鉴别](#bounce-mail-qualification)。
* 异步错误：接收服务器稍后会重新发送退回邮件或重新发送SR。 此邮件已加载到应用程序用来标记有错误邮件的技术邮箱中。 最晚的异步错误，可能发生在发送投放的一周之后。

  >[!NOTE]
  >
  >[此部分](../../installation/using/deploying-an-instance.md#managing-bounced-emails)中详细描述了退回邮箱的配置。

  [反馈循环](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=zh-Hans#feedback-loops)的运行方式与退回电子邮件类似。 当用户将电子邮件标记为垃圾邮件时，您可以在Adobe Campaign中配置电子邮件规则以阻止投放给此用户的所有邮件。 发送给确定电子邮件为垃圾邮件的用户的邮件会自动重定向到为此目的专门创建的电子邮件框。 这些用户的地址处于阻止列表状态，即使他们未单击退订链接。 地址在(**NmsAddress**)隔离表中阻止列表，而不是在(**NmsRecipient**)收件人表中。

  >[!NOTE]
  >
  >投诉管理在[可投放性管理](about-deliverability.md)部分中有详细介绍。

## 退回邮件管理 {#bounce-mail-management}

Adobe Campaign平台允许您通过退回邮件功能管理电子邮件投放失败。

当电子邮件无法发送给收件人时，远程消息服务器会自动将错误消息（退回邮件）返回到为此目的而设计的技术收件箱。

对于使用旧版Campaign MTA的内部部署安装和托管/混合安装，Adobe Campaign平台会收集错误消息，inMail流程会对其进行限定，以扩充电子邮件管理规则的列表。

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到[增强型MTA](sending-with-enhanced-mta.md)，则不再使用大多数电子邮件管理规则。 有关更多信息，请参阅[此小节](#email-management-rules)。

### 退回邮件鉴别 {#bounce-mail-qualification}

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到[增强型MTA](sending-with-enhanced-mta.md)：
>
>* **[!UICONTROL Delivery log qualification]**&#x200B;表中的退回限定不再用于&#x200B;**同步**&#x200B;投放失败错误消息。 增强型MTA可确定退回类型并进行鉴别，然后将该信息发回至Campaign。
>
>* **异步**&#x200B;退回仍由inMail进程通过&#x200B;**[!UICONTROL Inbound email]**&#x200B;规则进行鉴别。 有关详细信息，请参阅[电子邮件管理规则](#email-management-rules)。
>
>* 对于使用增强型MTA **但不使用Webhook**&#x200B;的实例，**[!UICONTROL Inbound email]**&#x200B;规则还将用于处理来自增强型MTA的同步退回电子邮件，使用的电子邮件地址与异步退回电子邮件相同。

对于使用旧版Campaign MTA的内部部署和托管/混合安装，当电子邮件投放失败时，Adobe Campaign投放服务器会收到来自消息传送服务器或远程DNS服务器的错误消息。 错误列表由远程服务器返回的消息中包含的字符串组成。 为每个错误消息指定失败类型和原因。

此列表可通过&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;节点使用。 它包含Adobe Campaign用于限定投放失败的所有规则。 此文档并非详尽无遗，由Adobe Campaign定期更新，用户也可以对其进行管理。

![](assets/tech_quarant_rules_qualif.png)

远程服务器第一次出现此错误类型时返回的消息显示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表的&#x200B;**[!UICONTROL First text]**&#x200B;列中。 如果未显示此列，请单击列表右下方的&#x200B;**[!UICONTROL Configure list]**&#x200B;按钮将其选定。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign过滤此消息以删除变量内容（如ID、日期、电子邮件地址、电话号码等） 并在&#x200B;**[!UICONTROL Text]**&#x200B;列中显示过滤的结果。 变量已替换为&#x200B;**`#xxx#`**，但地址已替换为&#x200B;**`*`**。

此流程允许汇总相同类型的所有故障，并避免投放日志鉴别表中出现多个类似错误条目。

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]**&#x200B;字段显示消息在列表中的出现次数。 限制为100 000次。 例如，如果您希望重置该字段，则可以对其进行编辑。

退回邮件可以具有以下资格状态：

* **[!UICONTROL To qualify]** ：无法限定退回邮件。 必须向可交付性团队分配资格以确保高效的平台可交付性。 只要不满足条件，就不会使用退回邮件来丰富电子邮件管理规则的列表。
* **[!UICONTROL Keep]** ：退回邮件已限定，将由&#x200B;**刷新以进行可投放性**&#x200B;工作流使用，以与现有电子邮件管理规则进行比较并扩充列表。
* **[!UICONTROL Ignore]** ：退回邮件被Campaign MTA忽略，这意味着此退回不会导致隔离收件人的地址。 **刷新可投放性**&#x200B;工作流不会使用此项，并且不会将其发送到客户端实例。

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>如果ISP发生中断，通过Campaign发送的电子邮件将被错误地标记为退回。 要更正此问题，您需要更新退回鉴别。 有关更多信息，请参阅[此页面](update-bounce-qualification.md)。

### 电子邮件管理规则 {#email-management-rules}

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到[增强型MTA](sending-with-enhanced-mta.md)，则不再使用大多数电子邮件管理规则。 有关更多详细信息，请参阅以下部分。

通过&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;节点访问邮件规则。 电子邮件管理规则显示在窗口的下部。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的默认参数是在部署向导中配置的。 有关详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md)。

默认规则如下。

>[!IMPORTANT]
>
>* 如果更改了参数，则必须重新启动投放服务器(MTA)。
>* 管理规则的修改或创建仅供专家用户使用。

#### 入站电子邮件 {#inbound-email}

<!--
STATEMENT ONLY TRUE with Momentum and EFS+:
For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](sending-with-enhanced-mta.md), and if your instance has **Webhooks** functionality, the **[!UICONTROL Inbound email]** rules are no longer used for synchronous delivery failure error messages. For more on this, see [this section](#bounce-mail-qualification).

For on-premise installations and hosted/hybrid installations using the legacy Campaign MTA, these rules contain the list of character strings which can be returned by remote servers and which let you qualify the error (**Hard**, **Soft** or **Ignored**).-->

**[!UICONTROL Inbound email]**&#x200B;规则包含可由远程服务器返回的字符串列表，可让您鉴别错误（**Hard**、**Soft**&#x200B;或&#x200B;**Ignored**）。

当电子邮件失败时，远程服务器将向[平台参数](../../installation/using/deploying-an-instance.md)中指定的地址返回退回消息。 Adobe Campaign将每个退回邮件的内容与规则列表中的字符串进行比较，然后为其分配三种[错误类型](#delivery-failure-types-and-reasons)之一。

>[!NOTE]
>
>用户可以创建自己的规则。 在导入包和通过&#x200B;**刷新可投放性**&#x200B;工作流更新数据时，用户创建的规则将被覆盖。

有关退回邮件鉴别的详细信息，请参阅[此部分](#bounce-mail-qualification)。

#### 域管理 {#domain-management}

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到[增强型MTA](sending-with-enhanced-mta.md)，则不再使用&#x200B;**[!UICONTROL Domain management]**&#x200B;规则。 所有域名的所有消息，其 **DKIM（域名识别邮件）**&#x200B;电子邮件身份验证签名均由 Enhanced MTA 进行。除非在 Enhanced MTA 中专门说明，否则不会使用 **Sender ID**、**DomainKeys** 或 **S/MIME** 进行签名。

对于使用旧版Campaign MTA的内部部署安装和托管/混合安装，Adobe Campaign消息服务器会将单个&#x200B;**域管理**&#x200B;规则应用于所有域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以选择是否激活某些标识标准和加密密钥以检查域名，如&#x200B;**发件人ID**、**DomainKeys**、**DKIM**&#x200B;和&#x200B;**S/MIME**。
* **SMTP中继**&#x200B;参数允许您为特定域配置中继服务器的IP地址和端口。 有关更多信息，请参阅[此小节](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果邮件显示在发件人地址为&#x200B;**[!UICONTROL on behalf of]**&#x200B;的Outlook中，请确保您未使用&#x200B;**发件人ID**&#x200B;签署电子邮件，这是Microsoft过时的专有电子邮件身份验证标准。 如果已启用&#x200B;**[!UICONTROL Sender ID]**&#x200B;选项，请取消选中相应的框并联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 您的可投放性不会受到影响。

#### MX管理 {#mx-management}

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[增强型MTA](sending-with-enhanced-mta.md)，则不再使用&#x200B;**[!UICONTROL MX management]**&#x200B;投放吞吐量规则。 Enhanced MTA会使用自己的MX规则，根据您自己的历史电子邮件信誉以及来自您发送电子邮件之域名的实时反馈，按域自定义您的吞吐量。

对于使用旧版Campaign MTA的内部部署和托管/混合安装：

* MX管理规则用于管理特定域的传出电子邮件流程。 它们会对退回消息进行采样，并在适当时阻止发送。

* Adobe Campaign消息服务器应用特定于域的规则，然后应用规则列表中用星号表示的一般用例的规则。

* 要配置MX管理规则，只需设置阈值并选择某些SMTP参数即可。 **阈值**&#x200B;是按错误百分比计算的限制，超过该限制将阻止向特定域发送的所有消息。 例如，在一般情况下，对于至少300条消息，如果错误率达到90%，则电子邮件发送将阻塞三个小时。

有关MX管理的详细信息，请参阅[此部分](../../installation/using/email-deliverability.md#mx-configuration)。
