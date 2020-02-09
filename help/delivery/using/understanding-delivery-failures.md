---
title: 了解投放失败
seo-title: 了解投放失败
description: 了解投放失败
seo-description: null
page-status-flag: never-activated
uuid: 03a91f84-77fe-40a9-8be9-a6a35a873ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 78b58a7a-b387-4d5d-80d5-01c06f83d759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 211556bbf023731ffeab2e90692410a852ab3555

---


# 了解投放失败{#understanding-delivery-failures}

## 关于交付失败 {#about-delivery-failures}

当消息（电子邮件、SMS、推送通知）无法发送到配置文件时，远程服务器会自动发送错误消息，该消息由Adobe Campaign平台选取并经资格确定是否应隔离电子邮件地址或电话号码。 请参阅 [弹回邮件管理](#bounce-mail-management)。

>[!NOTE]
>
>电子邮件错误消息（或“弹回次数”）由inMail进程限定。 MTA进程会确认SMS错误消息（或“状态报告”的“SR”）。

发送消息后，传送日志允许您查看每个配置文件的传送状态以及关联的失败类型和原因。

如果地址被隔离或配置文件被列入黑名单，则还可以在准备传送期间排除消息。 排除的消息列在传送功能板中。

**相关主题：**

* [交付日志和历史记录](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)
* [失败状态](../../delivery/using/monitoring-a-delivery.md#failed-status)
* [交付失败类型和原因](#delivery-failure-types-and-reasons)

## 交付失败类型和原因 {#delivery-failure-types-and-reasons}

消息失败时有三种类型的错误。 每个错误类型确定是否将地址发送到隔离。 有关详细信息，请参 [阅发送地址到隔离的条件](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **硬**:“硬”错误表示地址无效。 这涉及一条错误消息，明确声明地址无效，例如：“未知用户”。
* **软**:这可能是一个临时错误，或者是无法分类的错误，例如：“无效域”或“邮箱已满”。
* **忽略**:这是一个已知为临时错误（如“办公室外”）或技术错误（例如，如果发送者类型为“postmaster”）。

交付失败的可能原因包括：

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
   <td> 链接到该地址的帐户不再处于活动状态。 当Internet访问提供商(IAP)检测到长时间的不活动时，它可以关闭用户帐户。 然后，将无法将内容发送到用户地址。 如果帐户因为六个月的非活动状态而暂时禁用，并且仍可激活，则将分配“有错误”状态，并将再次尝试该帐户，直到错误计数器达到5。 如果错误表明帐户已永久停用，则将直接设置为“隔离”。<br /> </td> 
  </tr> 
  <tr> 
   <td> 隔离中的地址 </td> 
   <td> 硬 </td> 
   <td> 9 </td> 
   <td> 地址被隔离。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未指定地址 </td> 
   <td> 硬 </td> 
   <td> 7 </td> 
   <td> 没有为收件人提供地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 质量不佳的地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此地址的质量等级太低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 黑名单地址 </td> 
   <td> 硬 </td> 
   <td> 8 </td> 
   <td> 地址在发送时被列入黑名单。 此状态用于在将数据导入Adobe Campaign隔离列表时从外部列表和外部系统导入数据。<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制地址 </td> 
   <td> 已忽略 </td> 
   <td> 127 </td> 
   <td> 收件人的地址是控制组的一部分。<br /> </td> 
  </tr> 
  <tr> 
   <td> Double </td> 
   <td> 已忽略 </td> 
   <td> 10 </td> 
   <td> 收件人的地址已在此分发中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 忽略错误 </td> 
   <td> 无错误 </td> 
   <td> 25 </td> 
   <td> 地址列在白名单中。 因此，该错误会被忽略，并将发送电子邮件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 仲裁后排除 </td> 
   <td> 已忽略 </td> 
   <td> 12 </td> 
   <td> “仲裁”类型的活动类型规则排除接收方。<br /> </td> 
  </tr> 
  <tr> 
   <td> 由SQL规则排除 </td> 
   <td> 已忽略 </td> 
   <td> 11 </td> 
   <td> 收件人被“SQL”类型的营销活动类型规则排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 域无效 </td> 
   <td> 柔和 </td> 
   <td> 2 </td> 
   <td> 电子邮件地址的域不正确或不再存在。 此配置文件将再次定位，直到错误计数达到5。 此后，记录将设置为“隔离”状态，之后不会重试。<br /> </td> 
  </tr> 
  <tr> 
   <td> 邮箱已满 </td> 
   <td> 柔和 </td> 
   <td> 5 </td> 
   <td> 此用户的邮箱已满，无法接受更多消息。 此配置文件将再次定位，直到错误计数达到5。 此后，记录将设置为“隔离”状态，之后不会重试。<br /> 此类错误由清理进程管理，地址在30天后设置为有效状态。<br /> 警告：要从隔离地址列表中自动删除地址，必须启动数据库清理技术工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未连接 </td> 
   <td> 已忽略 </td> 
   <td> 6 </td> 
   <td> 当发送消息时，接收方的移动电话关闭或未连接到网络。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定义 </td> 
   <td> 未定义 </td> 
   <td> 0 </td> 
   <td> 该地址已确定，因为错误尚未递增。 当服务器发送新的错误消息时，会发生此类错误：这可能是一个孤立的错误，但如果再次发生，错误计数器会增加，这将提醒技术团队。 然后，他们可以通过树结构中的“管理 <span class="uicontrol">/营销活动管理</span> /非交付 <span class="uicontrol"></span><span class="uicontrol"></span> 产品管理”节点来分析消息并确定此错误。<br /> </td> 
  </tr> 
  <tr> 
   <td> 没有资格获得选件 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 收件人没有资格获得分发中的选件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 拒绝 </td> 
   <td> 软／硬 </td> 
   <td> 20 </td> 
   <td> 由于安全反馈作为垃圾邮件报告，该地址已被置于隔离状态。 根据错误，地址将再次尝试，直到错误计数器达到5，否则将直接发送到隔离。<br /> </td> 
  </tr> 
  <tr> 
   <td> 目标大小受限 </td> 
   <td> 已忽略 </td> 
   <td> 17 </td> 
   <td> 已达到收件人的最大交付大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不合格地址 </td> 
   <td> 已忽略 </td> 
   <td> 15 </td> 
   <td> 邮政地址不符合条件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 无法访问 </td> 
   <td> 软／硬 </td> 
   <td> 3 </td> 
   <td> 消息传送链中发生错误。 这可能是SMTP中继上的事件，可能是临时无法访问的域，等等。 根据错误，地址将再次尝试，直到错误计数器达到5，否则将直接发送到隔离。<br /> </td> 
  </tr> 
  <tr> 
   <td> 用户未知 </td> 
   <td> 硬 </td> 
   <td> 1 </td> 
   <td> 地址不存在。 不会尝试对此配置文件进行进一步提交。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 交付临时失败后重试 {#retries-after-a-delivery-temporary-failure}

如果消息因为“软 **** ”或“忽略 **”错误而失败** ，则在交付期间将重试。

>[!NOTE]
>
>临时未传送的消息只能与 **Soft** 或 **Ignored** （软错误）或Ingored（忽略）错误相关，但不能与 **Hard** （硬错误）相关(请参阅 [](#delivery-failure-types-and-reasons)Delivery failure types and reasons（传送失败类型和原因）)。

要修改传送的持续时间，请转至传送或传送模板的高级参数，然后在相应字段中指定所需的持续时间。 本节将介绍高级交付 [属性](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

默认配置允许在一小时间隔内重试五次，然后在四天内每天重试一次。 可以全局更改重试次数（与Adobe技术管理员联系），也可以更改每个交付或交付模板的重试次数(请参 [阅此部分](../../delivery/using/steps-sending-the-delivery.md#configuring-retries))。

## 同步和异步错误 {#synchronous-and-asynchronous-errors}

消息在发送后可能立即失败（同步错误），或稍后失败（异步错误）。

* 同步错误：由Adobe Campaign交付服务器联系的远程邮件服务器会立即返回错误消息，不允许将分发发送到配置文件的服务器。 Adobe Campaign确定了每个错误的有效性，以确定相关电子邮件地址是否应被隔离。 请参阅 [弹回邮件资格](#bounce-mail-qualification)。
* 异步错误：接收服务器稍后会重新发送弹回邮件或SR。 此邮件加载到应用程序用来标记消息的技术邮箱中，该邮箱存在错误。 异步错误最多可能发生到发送交付后的一周。

   >[!NOTE]
   >
   >弹回邮箱的配置在本节中有 [详细说明](../../installation/using/deploying-an-instance.md#managing-bounced-emails)。

   反馈循环的运行方式与弹回电子邮件类似。 当用户将电子邮件归为垃圾邮件时，您可以在Adobe Campaign中配置电子邮件规则以阻止向此用户发送的所有邮件。 发送给符合电子邮件垃圾邮件资格的用户的邮件会自动重定向到专门为此目的创建的邮箱。 这些用户的地址被列入黑名单，即使他们没有单击取消订阅链接。 地址列在(**NmsAddress**)隔离表中，而不是(**NmsRecipient**)收件人表中。

   >[!NOTE]
   >
   >投诉管理详见“可交付性 [管理”部分](../../delivery/using/about-deliverability.md) 。

## 弹回邮件管理 {#bounce-mail-management}

通过Adobe Campaign平台，您可以通过弹回邮件功能管理电子邮件发送失败。 当电子邮件无法发送给收件人时，远程消息传递服务器会自动将错误消息（弹回邮件）返回到专为此目的设计的技术收件箱。 错误消息由Adobe Campaign平台收集，并由inMail流程确定，以丰富电子邮件管理规则列表

### 退回邮件资格 {#bounce-mail-qualification}

当电子邮件发送失败时，Adobe Campaign交付服务器会从消息服务器或远程DNS服务器收到错误消息。 错误列表由远程服务器返回的消息中包含的字符串组成。 故障类型和原因将分配给每个错误消息。

此列表可通过节点获 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** 得。 它包含Adobe Campaign用来确定交付失败的所有规则。 它不是穷尽的，并且由Adobe Campaign定期更新，也可以由用户管理。

![](assets/tech_quarant_rules_qualif.png)

* 远程服务器在第一次出现此错误类型时返回的消息显示在表 **[!UICONTROL First text]** 的列中 **[!UICONTROL Delivery log qualification]** 。 如果未显示此列，请单击 **[!UICONTROL Configure list]** 列表右下方的按钮以选择它。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign会过滤此消息以删除变量内容（如ID、日期、电子邮件地址、电话号码等）并在列中显示筛选结 **[!UICONTROL Text]** 果。 变量将替换为 **`#xxx#`**&#x200B;地址，但替换为的地址除外 **`*`**。

此过程允许汇总相同类型的所有故障，并避免在“交付日志”资格表中出现类似错误时出现多个条目。

>[!NOTE]
>
>该字 **[!UICONTROL Number of occurrences]** 段显示消息在列表中的出现次数。 该数字限制为100 000次。 例如，如果您希望重置字段，可以编辑该字段。

弹回邮件可能具有以下资格状态：

* **[!UICONTROL To qualify]** :弹回邮件无法合格。 必须为交付能力团队分配资格，以确保有效的平台交付能力。 只要邮件不符合条件，弹回邮件就不会用来丰富电子邮件管理规则列表。
* **[!UICONTROL Keep]** :弹回邮件符合条件，将由“刷新”使用，以便与现有电子邮件管理规则进行 **比较** ，并丰富列表。
* **[!UICONTROL Ignore]** :弹回邮件已得到验证，但“刷新”将不会用于 **交付性工作流** 。 它不会发送到客户端实例。

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>对于托管或混合安装，如果您已升级到增强的MTA，则不再使用表中 **[!UICONTROL Delivery log qualification]** 的弹出资格。 增强的MTA将确定退回类型和资格，并将该信息发回营销活动。
>
>有关Adobe Campaign增强型MTA的详细信息，请参阅本 [文档](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)。

### 电子邮件管理规则 {#email-management-rules}

邮件规则通过节点 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 访问。 电子邮件管理规则显示在窗口的下半部分。

这些规则包含可由远程服务器返回的字符串列表，您可以通过该列表确定错误(**硬**、软 **或** 忽略 ****)。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的默认参数是在部署向导中配置的。 For further information, refer to [this section](../../installation/using/deploying-an-instance.md).

默认规则如下：

* **入站电子邮件**

   当电子邮件失败时，远程服务器会返回一条弹回消息至平台参数中指定的地址。 Adobe Campaign会将每封弹回邮件的内容与规则列表中的字符串进行比较，然后为其分配三个错误类型之一。

   用户可以创建自己的规则。

   >[!CAUTION]
   >
   >在导入包时以及通过刷新以实现可交付性工作 **流更新数据时** ，将覆盖用户创建的规则。

* **域管理**

   域管理规则用于调节特定域的传出电子邮件的流。 他们对弹回消息进行采样，并在适当时阻止发送。 Adobe Campaign消息传递服务器应用特定于域的规则，然后应用规则列表中以星号表示的一般大小写规则。 默认情况下，Adobe Campaign中提供Hotmail和MSN域的规则。

   单击图 **[!UICONTROL Detail]** 标可访问规则配置。

   ![](assets/tech_quarant_domain_rules_02.png)

   要配置域管理规则，只需设置阈值并选择某些SMTP参数。 阈 **值** (Threshold)是计算为错误百分比的限制，超过该百分比，向特定域的所有消息都被阻止。

   例如，在一般情况下，如果错误率达到90%，则至少300条邮件的发送将被阻止3小时。

   SMTP参 **数用作应用于阻止规则的过滤器** 。

   * 您可以选择是否激活某些标识标准和加密密钥以检查域名，如 **Sender ID**、 **DomainKeys**、 **DKIM**&#x200B;和 **** S/MIMEConnect。
   * **SMTP中继**:允许您为特定域配置IP地址和中继服务器的端口。

* **MX管理**

   For more on MX management, refer to [this section](../../installation/using/email-deliverability.md#mx-configuration).

   >[!NOTE]
   >
   >对于托管或混合安装，如果您已升级到增强的MTA，则不再使 **[!UICONTROL MX management]** 用交付吞吐量规则。 增强的MTA使用其自己的MX规则，该规则允许它根据您自己的历史电子邮件信誉以及来自您发送电子邮件的域的实时反馈，按域自定义您的吞吐量。
   >
   >有关Adobe Campaign增强型MTA的详细信息，请参阅本 [文档](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)。

>[!CAUTION]
>
>* 如果参数已更改，则必须重新启动交付服务器(MTA)。
>* 管理规则的修改或创建仅适用于专家用户。

