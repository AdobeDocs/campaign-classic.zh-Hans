---
product: campaign
title: 了解隔离管理
description: 了解隔离管理
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '2614'
ht-degree: 13%

---

# 了解隔离管理{#understanding-quarantine-management}

![](../../assets/common.svg)

## 关于隔离 {#about-quarantines}

Adobe Campaign 管理了一个隔离地址列表。在投放分析时，默认情况下会将其地址已被隔离的收件人排除在外，不会将其设为目标。举例来说，信箱已满或地址不存在时，可以隔离某个电子邮件地址。无论如何，隔离程序都符合下面所述的具体规则。

>[!NOTE]
>
>本节适用于在线渠道：电子邮件、短信、推送通知。

### 通过隔离优化投放 {#optimizing-your-delivery-through-quarantines}

在准备消息时，电子邮件地址或电话号码处于隔离状态的用户档案会被自动被排除（请参阅[确定投放的隔离地址](#identifying-quarantined-addresses-for-a-delivery)）。这样可加快投放速度，因为错误率对投放速度有显著的影响。

如果无效地址率过高，某些互联网访问提供商会自动将电子邮件判断为垃圾邮件。因此，隔离可让您避免被这些提阻止列表供商添加到。

此外，隔离还可避免向错误的电话号码投放短信，有助于降低短信发送成本。有关安全防护和优化投放之最佳做法的更多信息，请参阅[此页面](delivery-best-practices.md)。

### 隔离与阻止列表 {#quarantine-vs-denylist}

**隔离**&#x200B;仅适用于地址，而不适用于用户档案本身。这意味着，如果两个用户档案具有相同的电子邮件地址，那么隔离该地址会同时影响这两个用户档案。

同样，其电子邮件地址被隔离的用户档案可以更新其用户档案并输入新地址，然后可以再次被投放操作定向。

在 **阻止列表**&#x200B;另一方面，将导致用户档案不再为任何投放所定向，例如，在退订（选择退出）后。

>[!NOTE]
>
>当用户回复的短信带有“STOP”之类的关键字以选择退出短信投放时，他们的用户档案不会像电子邮件选择退出过程阻止列表中一样添加到该中。 用户档案的电话号码将添加到隔离，以便用户继续接收电子邮件。

## 确定隔离的地址 {#identifying-quarantined-addresses}

可以针对特定投放或整个平台列出隔离的地址。

### 确定投放的隔离地址 {#identifying-quarantined-addresses-for-a-delivery}

在投放准备阶段期间，投放仪表板的投放日志中会列出特定投放的隔离地址(请参阅 [投放日志和历史记录](delivery-dashboard.md#delivery-logs-and-history))。

### 确定整个平台的隔离地址 {#identifying-quarantined-addresses-for-the-entire-platform}

管理员可以从 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 节点。

>[!NOTE]
>
>此菜单列出了&#x200B;**电子邮件**、**短信**&#x200B;和&#x200B;**推送通知**&#x200B;渠道的隔离元素。

每个地址都有以下信息：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>隔离数量的增加是正常的，与数据库的“磨损”有关。 例如，如果将电子邮件地址的生命周期视为三年，而收件人表每年增加50%，则隔离的增加可以按如下方式计算：
>
>年末1:(1*0.33)/(1+0.5)=22%。
第 2 年年末：((1.22*0.33)+0.33)/(1.5+0.75)=32.5%。

### 确定投放报告中的隔离地址 {#identifying-quarantined-addresses-in-delivery-reports}

以下报告提供了有关隔离中地址的信息：

* 对于每个投放， **[!UICONTROL Delivery summary]** 报表显示投放目标中隔离的地址数。 它显示：

   * 在投放分析期间隔离的地址数，

   * 在投放操作后置于隔离中的地址数。

* 的 **[!UICONTROL Non-deliverables and bounces]** 报表显示有关隔离中的地址、遇到的错误类型等的信息，以及按域划分失败的信息。

您可以查找平台所有投放的此信息(**[!UICONTROL Home page > Reports]**)或用于特定投放。 您还可以创建自定义报表并选择要显示的信息。

### 确定收件人的隔离地址 {#identifying-quarantined-addresses-for-a-recipient}

您可以查找任何收件人的电子邮件地址状态。 要执行此操作，请选择收件人用户档案，然后单击 **[!UICONTROL Deliveries]** 选项卡。 对于发送给该收件人的所有投放，您可以了解地址是否失败、在分析期间是否被隔离等。 对于每个文件夹，您只能显示电子邮件地址处于隔离状态的收件人。 为此，请使用 **[!UICONTROL Quarantined email address]** 应用程序筛选器。

![](assets/tech_quarant_recipients_filter.png)

### 删除隔离地址 {#removing-a-quarantined-address}

如果需要，您可以从隔离列表中手动删除地址。 此外，符合特定条件的地址会由 **[!UICONTROL Database cleanup]** 工作流。

要手动从隔离列表中删除地址，请执行以下操作：

* 您可以将其状态更改为 **[!UICONTROL Valid]** 从 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 节点。

   ![](assets/tech_quarant_error_status.png)

* 您还可以将其状态更改为 **[!UICONTROL Allowlisted]**. 在这种情况下，地址仍保留在隔离列表中，但会系统地定位该地址，即使遇到错误也是如此。

在以下情况下，地址会自动从隔离列表中删除：

* 中的地址 **[!UICONTROL With errors]** 成功投放后，状态将从隔离列表中删除。
* 中的地址 **[!UICONTROL With errors]** 如果上次软退件发生在10天以前，则会从隔离列表中删除状态。 有关软错误管理的更多信息，请参阅 [此部分](#soft-error-management).
* 中的地址 **[!UICONTROL With errors]** 状态 **[!UICONTROL Mailbox full]** 30天后将从隔离列表中删除错误。

其状态随后更改为 **[!UICONTROL Valid]**.

>[!IMPORTANT]
地址在 **[!UICONTROL Quarantine]** 或 **[!UICONTROL On denylist]** 即使收到电子邮件，状态也永远不会被删除。

您可以修改错误数和两个错误之间的句点。 为此，请在部署向导中更改相应的设置(**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**)。 有关部署向导的更多信息，请参阅 [此部分](../../installation/using/deploying-an-instance.md).

## 将地址加入隔离的条件 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign根据投放失败类型和在错误消息鉴别过程中分配的原因管理隔离(请参阅 [退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification))和 [投放失败类型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

* **已忽略的错误**：已忽略的错误不会将地址添加到隔离。
* **硬错误**：相应的电子邮件地址会立即添加到隔离。
* **软错误**：软错误不会立即将地址添加到隔离，但会增加错误计数。有关此内容的更多信息，请参阅 [软错误管理](#soft-error-management).

如果用户将电子邮件标记为垃圾邮件([反馈回路](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops))时，该邮件会自动重定向到由Adobe管理的技术邮箱。 随后，用户的电子邮件地址会自动添加到隔离。

隔离地址列表中， **[!UICONTROL Error reason]** 字段指示将选定地址置于隔离中的原因。 Adobe Campaign 中的隔离会区分大小写字母。请确保以小写方式导入电子邮件地址，这样以后就不会重新定向这些地址。

![](assets/tech_quarant_error_reasons.png)

### 软错误管理 {#soft-error-management}

与硬错误相反，软错误不会立即将地址添加到隔离，而是增加错误计数。

* 当错误计数达到限制阈值时，地址将被隔离。
* 在默认配置中，阈值被设置为 5 次错误，其中如果两次错误间隔至少 24 小时，则会将其突出显示。在第 5 次出错后，即会将地址添加到隔离。
* 可修改错误计数阈值。有关更多信息，请参阅 [在投放临时失败后重试](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

如果上次出现重大错误的时间超过10天，则会重新初始化错误计数。 地址状态随后更改为 **有效** 并且会从 **数据库清理** 工作流。

## 推送通知隔离 {#push-notification-quarantines}

推送通知的隔离机制与常规流程的全局隔离机制相同。 请参阅 [关于隔离](#about-quarantines). 但是，对于推送通知，某些错误的管理方式不同。 例如，对于某些软错误，不会在同一投放内执行重试。 下面列出了推送通知的特性。 重试机制（重试次数、频率）与电子邮件的相同。

隔离的项目是设备令牌。

### iOS隔离 {#ios-quarantine}

HTTP/V2协议允许对每次推送交付进行直接反馈和状态。 如果使用HTTP/V2协议连接器，则不再由 **[!UICONTROL mobileAppOptOutMgt]** 工作流。 在卸载或重新安装移动应用程序时，令牌会被视为未注册。

同步，如果APNs为消息返回“未注册”状态，则目标令牌将立即被隔离。

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
   <td> 启用目标设备<br /> </td> 
   <td> 确定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 关闭目标设备<br /> </td> 
   <td> 确定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 用户禁用应用程序的通知<br /> </td> 
   <td> 确定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段 — 负载过大<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 负载过长<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段 — 意外的内容格式问题<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 根据错误显示的各种错误消息<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 未定义<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 证书问题（密码、损坏等） 并测试与APNs问题的连接<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 根据错误显示的各种错误消息<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送过程中网络连接丢失<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 连接错误<br /> </td> 
   <td> 未定义<br /> </td> 
   <td> 不可访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs消息拒绝：取消注册<br /> 用户已删除应用程序或令牌已过期<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 未注册<br /> </td> 
   <td> 硬<br /> </td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs消息拒绝：所有其他错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 错误消息中将存在错误拒绝原因<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔离 {#android-quarantine}

**对于Android V1**

对于每个通知，Adobe Campaign会直接从FCM服务器接收同步错误。 Adobe营销活动会即时处理错误，并根据错误的严重性生成硬错误或软错误，并可以执行重试：

* 超出负载长度、连接问题、服务可用性问题：重试，软错误，失败原因 **[!UICONTROL Refused]**.
* 超出设备配额：无重试，软错误，失败原因 **[!UICONTROL Refused]**.
* 无效或未注册的令牌、意外错误、发件人帐户问题：无重试，硬错误，失败原因 **[!UICONTROL Refused]**.

的 **[!UICONTROL mobileAppOptOutMgt]** 工作流每6小时运行一次，以更新 **AppSubscriptionRcp** 表。 对于声明为未注册或不再有效的令牌，该字段 **已禁用** 设置为 **True** 且链接到该设备令牌的订阅将自动从将来投放中排除。

在投放分析过程中，从目标中排除的所有设备都会自动添加到 **excludeLogAppSubRcp** 表。

>[!NOTE]
对于使用百度连接器的客户，以下是不同类型的错误：
* 投放开始时出现连接问题：失败类型 **[!UICONTROL Undefined]**，失败原因 **[!UICONTROL Unreachable]**，则执行重试。
* 投放期间连接丢失：软错误，失败原因 **[!UICONTROL Refused]**，则执行重试。
* 百度在发送过程中返回的同步错误：硬错误，失败原因 **[!UICONTROL Refused]**，则不执行重试。
Adobe Campaign每10分钟联系百度服务器以检索已发送消息的状态并更新广告。 如果消息声明为已发送，则广播中消息的状态将设置为 **[!UICONTROL Received]**. 如果百度声明错误，则状态将设置为 **[!UICONTROL Failed]**.

**对于Android V2**

Android V2隔离机制使用与Android V1相同的流程，这同样适用于订阅和排除项更新。 有关更多信息，请参阅 [Android V1](#android-quarantine) 中。

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
   <td> 消息创建/分析阶段：自定义字段中使用的非法关键词<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 不能使用以下关键词：{1}<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段：负载太大<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 通知过重：{1}位，而只有{2}位已授权<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送过程中网络连接丢失<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 地址上没有来自Firebase Cloud Messaging服务的响应：{1}<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 不可访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM报文拒绝：FCM服务器暂时不可用（例如超时）。 <br /> </td> 
   <td> 失败<br /> </td> 
   <td> Firebase Cloud Messaging服务暂时不可用<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 不可访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM报文拒绝：验证发件人帐户时出错<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 无法识别开发人员帐户，请检查您的ID和密码<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM报文拒绝：超出设备配额<br /> </td> 
   <td> 失败<br /> </td> 
   <td> </td> 
   <td> 柔和<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM报文拒绝：注册无效/未注册<br /> </td> 
   <td> 失败<br /> </td> 
   <td> </td> 
   <td> 硬<br /> </td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM报文拒绝：所有其他错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> Firebase Cloud Messaging服务器返回了意外的错误代码：{1} </td> 
   <td> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM报文拒绝：参数无效<br /> </td> 
   <td> 失败<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> 已忽略</td> 
   <td> 未定义<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM报文拒绝：第三方身份验证错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM报文拒绝：发件人ID不匹配<br /> </td> 
   <td> 失败<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> 柔和</td>
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM报文拒绝：未注册<br /> </td> 
   <td> 失败<br /> </td>
   <td> 未注册 </td> 
   <td> 硬</td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM报文拒绝：内部<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 内部 </td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM报文拒绝：不可用<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 不可用</td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM报文拒绝：意外错误代码<br /> </td> 
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
   <td> 身份验证：请求中的未授权客户端或范围。<br /> </td> 
   <td> 失败<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：客户端未授权使用此方法检索访问令牌，或者客户端未授权任何请求的作用域。<br /> </td> 
   <td> 失败<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：拒绝访问<br /> </td> 
   <td> 失败<br /> </td>
   <td> access_denied</td> 
   <td> 已忽略</td>
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：无效电子邮件<br /> </td> 
   <td> 失败<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：JWT无效<br /> </td> 
   <td> 失败<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份验证：JWT签名无效<br /> </td> 
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
   <td> 身份验证：已禁用OAuth客户端<br /> </td> 
   <td> 失败<br /> </td> 
   <td> disabled_client</td> 
   <td> 已忽略</td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
 </tbody> 
</table>

## 短信隔离 {#sms-quarantines}

**对于标准连接器**

短信消息的隔离机制与常规过程在全局上相同。 请参阅 [关于隔离](#about-quarantines). 以下列出了短信的特性。

>[!NOTE]
的 **[!UICONTROL Delivery log qualification]** 表不适用于 **扩展通用SMPP** 连接器。

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
   <td> 发送给提供商<br /> </td> 
   <td> 已发送<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 在移动设备上接收<br /> </td> 
   <td> 已接收<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 提供程序返回的错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 接收数据（SR或MO）时出错<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 不可访问<br /> </td> 
  </tr> 
  <tr> 
   <td> 无效的MT确认<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 处理用于发送查询的确认帧时出错“{1}”<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 不可访问<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送MT时出错<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 发送消息时出错<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 不可访问<br /> </td> 
  </tr> 
 </tbody> 
</table>

**对于扩展的通用SMPP连接器**

使用SMPP协议发送短信消息时，错误管理的处理方式不同。 有关扩展通用SMPP连接器的更多信息，请参阅 [本页](sms-set-up.md#creating-an-smpp-external-account).

SMPP连接器从SR（状态报告）消息中检索数据，该消息使用正则表达式(regex)返回以过滤其内容。 然后，将此数据与 **[!UICONTROL Delivery log qualification]** 表格(可通过 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** 菜单)。

在鉴定新类型的错误之前，失败原因始终设置为 **已拒绝** 默认情况下。

>[!NOTE]
失败类型和失败原因与电子邮件相同。 请参阅 [投放失败类型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
请向提供商提供状态和错误代码列表，以在投放日志鉴别表中设置正确的失败类型和失败原因。

生成的消息示例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有错误消息均以 **SR** 以区分短信错误代码和电子邮件错误代码。
* 第二部分(**通用** 在本示例中)的错误消息引用SMSC实施的名称，如 **[!UICONTROL SMSC implementation name]** 短信外部帐户的字段。 请参阅[此页](sms-set-up.md#creating-an-smpp-external-account)。

   由于同一错误代码对每个提供程序可能具有不同的含义，因此通过此字段，您可以了解哪个提供程序生成了错误代码。 然后，您可以在相关提供商的文档中找到该错误。

* 第三部分(**DELIVRD** 在此示例中)的错误消息对应于从SR中检索的状态代码，该代码使用SMS外部帐户中定义的状态提取正则表达式。

   此正则表达式在 **[!UICONTROL SMSC specificities]** 选项卡。 请参阅[此页](sms-set-up.md#creating-an-smpp-external-account)。

   ![](assets/tech_quarant_error_regex.png)

   默认情况下，正则表达式会提取 **stat:** 字段 **附录B** 部分 **SMPP 3.4规范**.

* 第四部分(**000** 在本例中)，错误消息对应于使用短信外部帐户中定义的错误代码提取正则表达式从SR提取的错误代码。

   此正则表达式在 **[!UICONTROL SMSC specificities]** 选项卡。 请参阅[此页](sms-set-up.md#creating-an-smpp-external-account)。

   默认情况下，正则表达式会提取 **错误：** 字段 **附录B** 部分 **SMPP 3.4规范**.

* 管道符号(|)之后的所有内容仅在 **[!UICONTROL First text]** 列 **[!UICONTROL Delivery log qualification]** 表。 此内容始终由 **#MESSAGE#** 在消息被标准化后。 此过程可避免因类似错误而包含多个条目，且与电子邮件相同。 有关此内容的更多信息，请参阅 [退回邮件鉴别](understanding-delivery-failures.md#bounce-mail-qualification).

扩展的通用SMPP连接器应用启发式来查找合理的默认值：如果状态以 **DELIV**，则会被视为成功，因为它与常用状态匹配 **DELIVRD** 或 **已交付** 由大多数提供商使用。 任何其他状态都会导致硬失败。
