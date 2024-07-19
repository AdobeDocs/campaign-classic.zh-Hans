---
product: campaign
title: 了解隔离管理
description: 了解隔离管理
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '2987'
ht-degree: 8%

---

# 了解隔离管理{#understanding-quarantine-management}

Adobe Campaign 管理了一个隔离地址列表。在投放分析时，默认情况下会将其地址已被隔离的收件人排除在外，不会将其设为目标。例如，当邮箱已满或地址不存在时，可以隔离电子邮件地址。 无论如何，隔离程序都符合下述具体规则。

>[!NOTE]
>
>本节适用于在线渠道：电子邮件、短信、推送通知。

## 通过隔离管理优化投放 {#optimizing-your-delivery-through-quarantines}

在准备消息时，电子邮件地址或电话号码处于隔离状态的用户档案将被自动排除（请参阅[识别投放的隔离地址](#identifying-quarantined-addresses-for-a-delivery)）。 这样可加快投放速度，因为错误率对投放速度有显著的影响。

如果无效地址率过高，某些互联网访问提供商会自动将电子邮件判断为垃圾邮件。因此，隔离可让您避免被这些提供商添加到阻止列表。

此外，隔离还可避免向错误的电话号码投放短信，有助于降低短信发送成本。

有关安全防护和优化投放之最佳做法的更多信息，请参阅[此页面](delivery-best-practices.md)。

### 隔离与阻止列表 {#quarantine-vs-denylist}

隔离和阻止列表不适用于同一对象：

* **隔离**&#x200B;仅应用于&#x200B;**地址**（或电话号码等），不适用于配置文件本身。 例如，其电子邮件地址被隔离的用户档案可以更新其用户档案并输入新地址，然后再次被投放操作定向。 同样，如果两个用户档案碰巧拥有相同的电话号码，那么隔离该号码将会同时影响这两个用户档案。

  隔离的地址或电话号码显示在[排除日志](#identifying-quarantined-addresses-for-a-delivery)（针对投放）或[隔离列表](#identifying-quarantined-addresses-for-the-entire-platform)（针对整个平台）中。

* 另一方面，如果位于&#x200B;**阻止列表**，则会导致&#x200B;**用户档案**&#x200B;不再被投放定位，例如在取消订阅（选择退出）给定渠道后。 例如，如果电子邮件渠道阻止列表上的用户档案有两个电子邮件地址，则这两个地址都将排除在投放之外。

  您可以在配置文件的&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL No longer contact]**&#x200B;部分中检查配置文件是否正在阻止列表一个或多个渠道。 请参阅[此小节](../../platform/using/editing-a-profile.md#general-tab)。

>[!NOTE]
>
>隔离包括&#x200B;**[!UICONTROL Denylisted]**&#x200B;状态，当收件人将您的邮件报告为垃圾邮件或回复带有“STOP”等关键字的短信邮件时，将应用该状态。 在这种情况下，会将用户档案中涉及的地址或电话号码添加到隔离，并显示&#x200B;**[!UICONTROL Denylisted]**&#x200B;状态。 有关管理STOP SMS消息的更多信息，请参阅[此章节](../../delivery/using/sms-send.md#processing-inbound-messages)。

## 确定隔离的地址 {#identifying-quarantined-addresses}

可以针对特定投放或整个平台列出隔离的地址。

### 确定投放的隔离地址 {#identifying-quarantined-addresses-for-a-delivery}

在投放准备阶段期间，投放仪表板的投放日志中会列出特定投放的隔离地址（请参阅[投放日志和历史记录](delivery-dashboard.md#delivery-logs-and-history)）。

### 确定整个平台的隔离地址 {#identifying-quarantined-addresses-for-the-entire-platform}

管理员可以列出&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;节点中整个平台的隔离地址。

>[!NOTE]
>
>此菜单列出了&#x200B;**电子邮件**、**短信**&#x200B;和&#x200B;**推送通知**&#x200B;渠道的隔离元素。

每个地址均提供以下信息：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>隔离数量的增加是正常的，这与数据库的“磨损”有关。 例如，如果将电子邮件地址的生命周期视为三年，并且收件人表每年增加50%，则隔离的增加可以按如下方式计算：
>
>第1年年末： (1&#42;0.33)/(1+0.5)=22%。
>
第2年年末：((1.22&#42;0.33)+0.33)/(1.5+0.75)=32.5%。

### 在投放报告中确定隔离的地址 {#identifying-quarantined-addresses-in-delivery-reports}

以下报告提供了有关隔离地址的信息：

* 对于每次投放，**[!UICONTROL Delivery summary]**&#x200B;报告都会显示投放目标中隔离的地址数。 它显示：

   * 投放分析期间被隔离的地址数，

   * 投放操作后放置到隔离区的地址数。

* **[!UICONTROL Non-deliverables and bounces]**&#x200B;报告显示有关隔离地址、遇到的错误类型等以及按域划分的失败的信息。

您可以查找平台(**[!UICONTROL Home page > Reports]**)的所有投放或特定投放的此类信息。 您还可以创建自定义报告并选择要显示的信息。

### 确定收件人的隔离地址 {#identifying-quarantined-addresses-for-a-recipient}

您可以查找任何收件人的电子邮件地址的状态。 为此，请选择收件人配置文件，然后单击&#x200B;**[!UICONTROL Deliveries]**&#x200B;选项卡。 对于发送给该收件人的所有投放，您可以查明地址是否出现故障，在分析期间是否被隔离等。 对于每个文件夹，您只能显示其电子邮件地址处于隔离状态的收件人。 为此，请使用&#x200B;**[!UICONTROL Quarantined email address]**&#x200B;应用程序筛选器。

![](assets/tech_quarant_recipients_filter.png)


## 将地址添加到隔离的条件 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign根据投放失败类型和错误消息鉴别期间分配的原因管理隔离（请参阅[退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification)和[投放失败类型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)）。

* **已忽略的错误**：已忽略的错误不会将地址添加到隔离。
* **硬错误**：相应的电子邮件地址会立即添加到隔离。
* **软错误**：软错误不会立即将地址添加到隔离，但会增加错误计数。有关此内容的详细信息，请参阅[软错误管理](#soft-error-management)。

如果用户将电子邮件标记为垃圾邮件（[反馈循环](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)），则该邮件会自动重定向到由Adobe管理的技术邮箱。 随后，该用户的电子邮件地址会自动添加到隔离，并附加 **[!UICONTROL Denylisted]** 状态。此状态仅适用于地址，用户档案不在阻止列表上，因此用户可继续接收短信和推送通知。

>[!NOTE]
>
Adobe Campaign 中的隔离会区分大小写字母。请确保以小写方式导入电子邮件地址，这样以后就不会重新定向这些地址。

在隔离地址列表中（请参阅[确定整个平台的隔离地址](#identifying-quarantined-addresses-for-the-entire-platform)），**[!UICONTROL Error reason]**&#x200B;字段指示将选定地址置于隔离状态的原因。

![](assets/tech_quarant_error_reasons.png)

### 软错误管理 {#soft-error-management}

与硬错误相反，软错误不会立即将地址添加到隔离，而是会增加错误计数。

将在[投放持续时间](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)期间执行重试。 当错误计数达到限制阈值时，即会将地址添加到隔离。有关详细信息，请参阅投放临时失败后[重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。

如果最后一次重大错误发生在10天之前，则重新初始化错误计数器。 然后，地址状态更改为&#x200B;**有效**，并由[数据库清理](../../production/using/database-cleanup-workflow.md)工作流从隔离列表中将其删除。


对于托管或混合安装，如果您已升级到[增强型MTA](sending-with-enhanced-mta.md)，则在&#x200B;**[!UICONTROL Erroneous]**&#x200B;状态的情况下要执行的最大重试次数和重试之间的最小延迟现在取决于IP在给定域名的历史和当前表现如何。

对于使用旧版Campaign MTA的内部部署和托管/混合安装，您可以修改错误数以及两个错误之间的时间间隔。 为此，请更改[部署向导](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**)或投放级别](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)的[中的相应设置。


## 从隔离中删除地址 {#removing-a-quarantined-address}

### 自动更新 {#unquarantine-auto}

符合特定条件的地址会由[数据库清理](../../production/using/database-cleanup-workflow.md)工作流自动从隔离列表中删除。

在以下情况下，地址会自动从隔离列表中删除：

* 成功投放后，将从隔离列表中删除处于&#x200B;**[!UICONTROL With errors]**&#x200B;状态的地址。
* 如果最后一次软退回发生在10天之前，则会从隔离列表中删除处于&#x200B;**[!UICONTROL With errors]**&#x200B;状态的地址。 有关软错误管理的详细信息，请参阅[此部分](#soft-error-management)。
* 状态为&#x200B;**[!UICONTROL With errors]**&#x200B;且出现&#x200B;**[!UICONTROL Mailbox full]**&#x200B;错误退回的地址将在30天后从隔离列表中删除。

其状态随后更改为&#x200B;**[!UICONTROL Valid]**。

>[!IMPORTANT]
>
不会移除地址处于&#x200B;**[!UICONTROL Quarantine]**&#x200B;或&#x200B;**[!UICONTROL Denylisted]**&#x200B;状态的收件人，即使他们收到电子邮件也是如此。

### 手动更新 {#unquarantine-manual}

您还可以手动取消隔离地址。 要从隔离列表中手动删除地址，请将其状态从&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;节点更改为&#x200B;**[!UICONTROL Valid]**。

![](assets/tech_quarant_error_status.png)

### 批量更新 {#unquarantine-bulk}

您可能需要对隔离列表执行批量更新，例如，在ISP中断的情况下。 在这种情况下，电子邮件会错误地标记为跳出，因为它们无法成功传递给收件人。 必须从隔离列表中删除这些地址。

要执行此操作，请创建工作流并在隔离表上添加&#x200B;**[!UICONTROL Query]**&#x200B;活动以过滤掉所有受影响的收件人。 确定后，可以从隔离列表中删除它们，并将其包含在将来的Campaign电子邮件投放中。

以下是此查询的建议准则：

* 对于在隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含入站电子邮件规则信息的Campaign Classicv7环境：

   * **错误文本（隔离文本）**&#x200B;包含“Momen_Code10_InvalidRecipient”
   * **电子邮件域(@domain)**&#x200B;等于domain1.com或&#x200B;**电子邮件域(@domain)**&#x200B;等于domain2.com或&#x200B;**电子邮件域(@domain)**&#x200B;等于domain3.com
   * **更新状态(@lastModified)**&#x200B;在`MM/DD/YYYY HH:MM:SS AM`或之后
   * **在`MM/DD/YYYY HH:MM:SS PM`或之前更新状态(@lastModified)**

* 对于隔离列表的&#x200B;**[!UICONTROL Error text]**&#x200B;字段中包含SMTP退回响应信息的Campaign Classicv7实例：

   * **错误文本（隔离文本）**&#x200B;包含“550-5.1.1”且&#x200B;**错误文本（隔离文本）**&#x200B;包含“support.ISP.com”

  其中“support.ISP.com”可以是：例如“support.apple.com”或“support.google.com”

   * **更新状态(@lastModified)**&#x200B;在`MM/DD/YYYY HH:MM:SS AM`或之后
   * **在`MM/DD/YYYY HH:MM:SS PM`或之前更新状态(@lastModified)**

获得受影响的收件人列表后，添加&#x200B;**[!UICONTROL Update data]**&#x200B;活动以将其电子邮件地址状态设置为&#x200B;**[!UICONTROL Valid]**，以便&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流将其从隔离列表中删除。 也可以直接从隔离表中删除它们。

## 推送通知隔离 {#push-notification-quarantines}

推送通知的隔离机制与常规流程全局相同。 但是，对于推送通知，某些错误的管理方式有所不同。 例如，对于某些软错误，不会在同一投放中执行重试。 下面列出了推送通知的特性。 重试机制（重试次数、频率）与电子邮件的机制相同。

被隔离的项目是设备令牌。

### iOS隔离 {#ios-quarantine}

HTTP/V2协议允许直接反馈每个推送投放的状态。 如果使用HTTP/V2协议连接器，**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流将不再调用反馈服务。 卸载或重新安装移动应用程序时，令牌被视为已注销。

同时，如果APN为消息返回“未注册”状态，则目标令牌将立即被隔离。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>方案</strong><br /> </td> 
   <td> <strong>状态</strong><br /> </td> 
   <td> <strong>错误消息</strong><br /> </td> 
   <td> <strong>失败类型</strong><br /> </td> 
   <td> <strong>失败原因</strong><br /> </td> 
   <td> <strong>重试</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 目标设备已打开<br /> </td> 
   <td> 确定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 目标设备已关闭<br /> </td> 
   <td> 确定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 用户禁用应用程序<br />的通知 </td> 
   <td> 确定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段 — 有效负载太大<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 有效负载过长<br /> </td> 
   <td> 软<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段 — 意外的内容格式问题<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 根据错误<br />显示各种错误消息 </td> 
   <td> 软<br /> </td> 
   <td> 未定义<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 证书问题（密码、损坏等） 并测试与APNs问题<br />的连接 </td> 
   <td> 失败<br /> </td> 
   <td> 根据错误<br />显示各种错误消息 </td> 
   <td> 软<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送期间网络连接丢失<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 连接错误<br /> </td> 
   <td> 未定义<br /> </td> 
   <td> 无法访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs消息拒绝：取消注册<br />用户已删除应用程序或令牌已过期<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 已取消注册<br /> </td> 
   <td> 硬<br /> </td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs消息拒绝：所有其他错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 错误消息<br />中将显示错误拒绝原因 </td> 
   <td> 软<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔离 {#android-quarantine}

用于Android V1 **的**

对于每个通知，Adobe Campaign都会直接从FCM服务器接收同步错误。 Adobe活动会即时处理这些错误，并根据错误的严重性生成硬错误或软错误，并且可以执行重试：

* 已超出有效负载长度，连接问题，服务可用性问题：已执行重试，软错误，失败原因为&#x200B;**[!UICONTROL Refused]**。
* 超出设备配额：无重试、软错误、失败原因为&#x200B;**[!UICONTROL Refused]**。
* 无效或未注册的令牌，意外错误，发件人帐户问题：无重试，硬错误，失败原因为&#x200B;**[!UICONTROL Refused]**。

**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流每6小时运行一次，以更新&#x200B;**AppSubscriptionRcp**&#x200B;表。 对于声明为未注册或不再有效的令牌，字段&#x200B;**Disabled**&#x200B;设置为&#x200B;**True**，并且将来投放时将自动排除链接到该设备令牌的订阅。

在投放分析期间，从目标中排除的所有设备都会自动添加到&#x200B;**excludeLogAppSubRcp**&#x200B;表中。

>[!NOTE]
>
对于使用百度连接器的客户，以下是不同类型的错误：
>
* 投放开始时的连接问题：失败类型&#x200B;**[!UICONTROL Undefined]**，失败原因&#x200B;**[!UICONTROL Unreachable]**，已执行重试。
* 传递期间连接丢失：软错误，失败原因&#x200B;**[!UICONTROL Refused]**，执行重试。
* 百度在发送期间返回的同步错误：硬错误，失败原因&#x200B;**[!UICONTROL Refused]**，不执行重试。
>
Adobe Campaign每10分钟联系百度服务器以检索发送消息的状态，并更新broadlog。 如果消息被声明为已发送，则broadlogs中该消息的状态将设置为&#x200B;**[!UICONTROL Received]**。 如果百度声明错误，则状态设置为&#x200B;**[!UICONTROL Failed]**。

用于Android V2 **的**

Android V2隔离机制使用与Android V1相同的过程，该过程同样适用于订阅和排除项更新。 有关详细信息，请参阅[Android V1](#android-quarantine)部分。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>方案</strong><br /> </td> 
   <td> <strong>状态</strong><br /> </td> 
   <td> <strong>错误消息</strong><br /> </td> 
   <td> <strong>失败类型</strong><br /> </td> 
   <td> <strong>失败原因</strong><br /> </td> 
   <td> <strong>重试</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段：自定义字段<br />中使用的关键字不合法 </td> 
   <td> 失败<br /> </td> 
   <td> 不能使用以下关键字： {1}<br /> </td> 
   <td> 软<br /> </td> 
   <td> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段：有效负载太大<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 通知过重： {1}位，而只有{2}是授权的<br /> </td> 
   <td> 软<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送期间网络连接丢失<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 地址上的Firebase Cloud Messaging服务没有响应： {1}<br /> </td> 
   <td> 软<br /> </td> 
   <td> 无法访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝： FCM服务器暂时不可用（例如，超时）。<br /> </td> 
   <td> 失败<br /> </td> 
   <td> Firebase Cloud Messaging服务暂时不可用<br /> </td> 
   <td> 软<br /> </td> 
   <td> 无法访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：验证发件人帐户时出错<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 无法识别开发人员帐户，请检查您的ID和密码<br /> </td> 
   <td> 软<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：超出设备配额<br /> </td> 
   <td> 失败<br /> </td> 
   <td> </td> 
   <td> 软<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：注册无效/未注册<br /> </td> 
   <td> 失败<br /> </td> 
   <td> </td> 
   <td> 硬<br /> </td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：所有其他错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> Firebase Cloud Messaging Server返回了意外错误代码： {1} </td> 
   <td> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM消息拒绝：无效参数<br /> </td> 
   <td> 失败<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> 已忽略</td> 
   <td> 未定义<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒绝：第三方身份验证错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒绝：发件人ID不匹配<br /> </td> 
   <td> 失败<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> 柔光</td>
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒绝：已取消注册<br /> </td> 
   <td> 失败<br /> </td>
   <td> 未注册 </td> 
   <td> 硬</td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒绝：内部<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 内部 </td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒绝：不可用<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 不可用</td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒绝：意外的错误代码<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 意外错误代码</td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
  <tr> 
   <td> 身份验证：连接问题<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 无法连接到身份验证服务器 </td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：请求中的客户端或作用域未获授权。<br /> </td> 
   <td> 失败<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：客户端无权使用此方法检索访问令牌，或者客户端无权使用请求的任何作用域。<br /> </td> 
   <td> 失败<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：访问被拒绝<br /> </td> 
   <td> 失败<br /> </td>
   <td> access_denied</td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：无效的电子邮件<br /> </td> 
   <td> 失败<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证： JWT<br />无效 </td> 
   <td> 失败<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证： JWT签名无效<br /> </td> 
   <td> 失败<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：提供的OAuth范围或ID令牌受众无效<br /> </td> 
   <td> 失败<br /> </td> 
   <td> unauthorized_client</td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证： OAuth客户端已禁用<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 已禁用客户端</td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
 </tbody> 
</table>

## 短信隔离 {#sms-quarantines}

**对于标准连接器**

SMS消息的隔离机制在全局上与常规流程相同。 请参阅[关于隔离](#about-quarantines)。 下面列出了短信的特性。

>[!NOTE]
>
**[!UICONTROL Delivery log qualification]**&#x200B;表不适用于&#x200B;**扩展通用SMPP**&#x200B;连接器。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>方案</strong><br /> </td> 
   <td> <strong>状态</strong><br /> </td> 
   <td> <strong>错误消息</strong><br /> </td> 
   <td> <strong>失败类型</strong><br /> </td> 
   <td> <strong>失败原因</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 已发送给提供程序<br /> </td> 
   <td> 已发送<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 已在移动设备<br />上收到 </td> 
   <td> 已接收<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 提供程序<br />返回的错误 </td> 
   <td> 失败<br /> </td> 
   <td> 接收数据（SR或MO）时出错<br /> </td> 
   <td> 软<br /> </td> 
   <td> 无法访问<br /> </td> 
  </tr> 
  <tr> 
   <td> MT确认<br />无效 </td> 
   <td> 失败<br /> </td> 
   <td> 处理发送查询<br />的确认帧时出错“{1}” </td> 
   <td> 软<br /> </td> 
   <td> 无法访问<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送MT<br />时出错 </td> 
   <td> 失败<br /> </td> 
   <td> 发送消息时出错<br /> </td> 
   <td> 软<br /> </td> 
   <td> 无法访问<br /> </td> 
  </tr> 
 </tbody> 
</table>

扩展通用SMPP连接器的&#x200B;****

使用SMPP协议发送短信消息时，错误管理的处理方式不同。 有关扩展通用SMPP连接器的详细信息，请参阅[此页面](sms-set-up.md#creating-an-smpp-external-account)。

SMPP连接器从使用正则表达式（正则表达式）返回的SR（状态报告）消息中检索数据，以筛选其内容。 然后，此数据与&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表中的信息匹配（通过&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**&#x200B;菜单提供）。

在限定新类型的错误之前，默认情况下失败原因始终设置为&#x200B;**已拒绝**。

>[!NOTE]
>
失败类型和失败原因与电子邮件相同。 请参阅[投放失败类型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
>
请向您的提供商索取状态和错误代码列表，以便在投放日志资格表中设置正确的失败类型和失败原因。

生成的消息示例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有错误消息均以&#x200B;**SR**&#x200B;开头，以区分短信错误代码和电子邮件错误代码。
* 错误消息的第二部分（**Generic**，在此示例中为）引用SMSC实现的名称，如SMS外部帐户的&#x200B;**[!UICONTROL SMSC implementation name]**&#x200B;字段中定义的名称。 请参阅[此页](sms-set-up.md#creating-an-smpp-external-account)。

  由于对于每个提供程序而言，相同的错误代码可能具有不同的含义，因此此字段允许您知道是哪个提供程序生成了错误代码。 然后，您可以在相关提供商的文档中查找错误。

* 错误消息的第三部分(**DELIVRD**)对应于使用SMS外部帐户中定义的状态提取正则表达式从SR检索到的状态代码。

  此正则表达式在外部帐户的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;选项卡中指定。 请参阅[此页](sms-set-up.md#creating-an-smpp-external-account)。

  ![](assets/tech_quarant_error_regex.png)

  默认情况下，正则表达式提取&#x200B;**SMPP 3.4规范**&#x200B;的&#x200B;**附录B**&#x200B;部分定义的&#x200B;**stat：**&#x200B;字段。

* 错误消息的第四部分(**000**)对应于使用SMS外部帐户中定义的错误代码提取正则表达式从SR提取的错误代码。

  此正则表达式在外部帐户的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;选项卡中指定。 请参阅[此页](sms-set-up.md#creating-an-smpp-external-account)。

  默认情况下，正则表达式提取&#x200B;**SMPP 3.4规范**&#x200B;的&#x200B;**附录B**&#x200B;部分定义的&#x200B;**err：**&#x200B;字段。

* 管道符号(|)之后的所有内容仅显示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表的&#x200B;**[!UICONTROL First text]**&#x200B;列中。 在消息规范化后，此内容始终被&#x200B;**#MESSAGE#**&#x200B;替换。 此过程避免因类似错误而出现多个条目，与电子邮件的情况相同。 有关此内容的详细信息，请参阅[退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification)。

扩展通用SMPP连接器应用启发式来查找合理的默认值：如果状态以&#x200B;**DELIV**&#x200B;开头，则被视为成功，因为它与大多数提供商使用的通用状态&#x200B;**DELIVRD**&#x200B;或&#x200B;**DELIVERED**&#x200B;匹配。 任何其他状态都会导致硬故障。
