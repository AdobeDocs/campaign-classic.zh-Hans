---
solution: Campaign Classic
product: campaign
title: 了解隔离管理
description: 了解隔离管理
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2799'
ht-degree: 14%

---


# 了解隔离管理{#understanding-quarantine-management}

## 关于隔离{#about-quarantines}

Adobe Campaign 管理了一个隔离地址列表。在投放分析时，默认情况下会将其地址已被隔离的收件人排除在外，不会将其设为目标。举例来说，信箱已满或地址不存在时，可以隔离某个电子邮件地址。无论如何，隔离程序都符合下面描述的特定规则。

>[!NOTE]
>
>本条适用于在线渠道:电子邮件、短信、推送通知。

### 通过隔离优化投放{#optimizing-your-delivery-through-quarantines}

在准备消息时，电子邮件地址或电话号码处于隔离状态的用户档案会被自动被排除（请参阅[确定投放的隔离地址](#identifying-quarantined-addresses-for-a-delivery)）。这样可加快投放速度，因为错误率对投放速度有显著的影响。

如果无效地址率过高，某些互联网访问提供商会自动将电子邮件判断为垃圾邮件。因此，隔离允许您避免被这阻止列表些提供商添加到。

此外，隔离还可避免向错误的电话号码投放短信，有助于降低短信发送成本。有关安全防护和优化投放之最佳做法的更多信息，请参阅[此页面](../../delivery/using/delivery-best-practices.md)。

### 隔离与阻止列表{#quarantine-vs-denylist}

**隔离**&#x200B;仅适用于地址，而不适用于用户档案本身。这意味着，如果两个用户档案具有相同的电子邮件地址，那么隔离该地址会同时影响这两个用户档案。

同样，其电子邮件地址被隔离的用户档案可以更新其用户档案并输入新地址，然后即可再次被投放操作定向。

另一方面，位于&lt;a0/阻止列表>**上将导致用户档案不再为任何投放所针对，例如在退订（退出）之后。**

>[!NOTE]
>
>当用户用诸如“STOP”的关键字回复SMS消息以从SMS投放中选择退出时，其用户档案不会像在电子邮件选择退出阻止列表过程中那样添加到该中。 用户档案电话号码被发送给隔离，以便用户继续接收电子邮件。

## 确定隔离的地址{#identifying-quarantined-addresses}

可以针对特定投放或整个平台列出隔离的地址。

### 确定投放的隔离地址{#identifying-quarantined-addresses-for-a-delivery}

特定投放的隔离地址在投放准备阶段列在投放仪表板的投放日志中(请参阅[投放日志和历史记录](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history))。

### 确定整个平台的隔离地址{#identifying-quarantined-addresses-for-the-entire-platform}

管理员可以从&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;节点列表整个平台的隔离地址。

>[!NOTE]
>
>此菜单列出了&#x200B;**电子邮件**、**短信**&#x200B;和&#x200B;**推送通知**&#x200B;渠道的隔离元素。

每个地址都有以下信息：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>隔离数量的增加是正常的，与数据库的&quot;磨损&quot;有关。 例如，如果将电子邮件地址的使用期视为三年，并且收件人表每年增加50%，则隔离的增加可以按如下方式计算：
>
>年末1:(1*0.33)/(1+0.5)=22%。
第 2 年年末：((1.22*0.33)+0.33)/(1.5+0.75)=32.5%。

### 在投放报告{#identifying-quarantined-addresses-in-delivery-reports}中标识隔离地址

以下报告提供有关隔离中地址的信息：

* 对于每个投放,**[!UICONTROL Delivery summary]**&#x200B;报告显示投放目标中隔离的地址数。 它显示：

   * 在隔离分析内放置的地址数，

   * 在隔离操作后放置投放的地址数。

* **[!UICONTROL Non-deliverables and bounces]**&#x200B;报告按域显示有关隔离中地址、遇到错误类型等的信息以及故障细分。

您可以查找平台的所有投放(**[!UICONTROL Home page > Reports]**)或特定投放的此信息。 您还可以创建自定义报告并选择要显示的信息。

### 识别收件人{#identifying-quarantined-addresses-for-a-recipient}的隔离地址

您可以查找任何收件人的电子邮件地址的状态。 为此，请选择收件人用户档案，然后单击&#x200B;**[!UICONTROL Deliveries]**&#x200B;选项卡。 对于该收件人的所有投放，您可以了解该地址是否失败、是否在分析期间被隔离等。 对于每个文件夹，您只能显示其电子邮件地址处于隔离的收件人。 为此，请使用&#x200B;**[!UICONTROL Quarantined email address]**&#x200B;应用程序过滤器。

![](assets/tech_quarant_recipients_filter.png)

### 删除隔离地址{#removing-a-quarantined-address}

如果需要，您可以从隔离列表中手动删除地址。 此外，符合特定条件的地址也会由&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流自动从隔离列表中删除。

要手动从隔离列表中删除地址，请执行以下操作：

* 可以从&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;节点将其状态更改为&#x200B;**[!UICONTROL Valid]**。

   ![](assets/tech_quarant_error_status.png)

* 您还可以将其状态更改为&#x200B;**[!UICONTROL Allowlisted]**。 在这种情况下，地址仍保留在隔离列表中，但系统化地址将被定位，即使遇到错误也是如此。

在以下情况下，地址会自动从隔离列表中删除：

* 处于&#x200B;**[!UICONTROL With errors]**&#x200B;状态的地址将在成功隔离后从列表中删除。
* 如果上次软弹出发生时间超过10天，处于&#x200B;**[!UICONTROL With errors]**&#x200B;状态的地址将从隔离列表中删除。 有关软错误管理的详细信息，请参阅[此部分](#soft-error-management)。
* 处于&#x200B;**[!UICONTROL With errors]**&#x200B;状态且因&#x200B;**[!UICONTROL Mailbox full]**&#x200B;错误退回的地址将在30天后从隔离列表中删除。

状态随后变为&#x200B;**[!UICONTROL Valid]**。

>[!IMPORTANT]
地址为&#x200B;**[!UICONTROL Quarantine]**&#x200B;或&#x200B;**[!UICONTROL On denylist]**&#x200B;的收件人将永远不会被删除，即使他们收到电子邮件也是如此。

您可以修改错误数以及两个错误之间的时间段。 为此，请更改部署向导中的相应设置(**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**)。 有关部署向导的详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md)。

## 将地址加入隔离的条件{#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign根据投放故障类型和在错误消息限定期间分配的原因（请参阅[弹回邮件限定](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)）和[投放故障类型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)管理隔离。

* **已忽略的错误**：已忽略的错误不会将地址添加到隔离。
* **硬错误**：相应的电子邮件地址会立即添加到隔离。
* **软错误**：软错误不会立即将地址添加到隔离，但会增加错误计数。有关详细信息，请参阅[软错误管理](#soft-error-management)。

如果用户将电子邮件归为垃圾邮件（[反馈循环](../../delivery/using/technical-recommendations.md#feedback-loop)），则该消息将自动重定向到由Adobe管理的技术邮箱。 随后，用户的电子邮件地址会自动发送到隔离。

在隔离地址的列表中，**[!UICONTROL Error reason]**&#x200B;字段指示选定地址置于隔离的原因。 Adobe Campaign 中的隔离会区分大小写字母。请确保以小写方式导入电子邮件地址，这样以后就不会重新定向这些地址。

![](assets/tech_quarant_error_reasons.png)

### 软错误管理{#soft-error-management}

与硬错误相反，软错误不会立即向隔离发送地址，而是增加一个错误计数器。

* 当错误计数器达到限制阈值时，地址将进入隔离。
* 在默认配置中，阈值被设置为 5 次错误，其中如果两次错误间隔至少 24 小时，则会将其突出显示。在第 5 次出错后，即会将地址添加到隔离。
* 可修改错误计数阈值。有关详细信息，请参阅投放临时故障后的[重试](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。

如果上一个重大错误在10天前发生，则错误计数器将重新初始化。 然后，地址状态将变为&#x200B;**Valid**，并由&#x200B;**数据库清理**&#x200B;工作流从隔离列表中删除。

## 推送通知隔离{#push-notification-quarantines}

推送通知的隔离机制与一般流程在全局上相同。 请参阅[关于隔离](#about-quarantines)。 但是，对于推送通知，某些错误的管理方式不同。 例如，对于某些软错误，不会在同一重试内执行任何投放。 下面列出了推送通知的特性。 重试机制(重试数、频率)与电子邮件的重试机制相同。

放入隔离的项是设备令牌。

### iOS隔离{#ios-quarantine}

**对于iOS —— 二进制连接器**

>[!NOTE]
从 Campaign 20.3 版本开始，弃用 iOS 旧版二进制连接器。如果您使用的是此连接器，则需要相应地调整实施。[了解详情](https://helpx.adobe.com/cn/campaign/kb/migrate-to-apns-http2.html)

对于每个通知，Adobe Campaign从APNs服务器接收同步和异步错误。 对于以下同步错误，Adobe Campaign会生成软错误：

* 负载长度问题：无重试，失败原因为&#x200B;**[!UICONTROL Unreachable]**。
* 证书过期问题：无重试，失败原因为&#x200B;**[!UICONTROL Unreachable]**。
* 在投放期间连接丢失：重试，失败原因为&#x200B;**[!UICONTROL Unreachable]**。
* 服务配置问题（证书无效、证书密码无效、证书无效）:无重试，失败原因为&#x200B;**[!UICONTROL Unreachable]**。

APNs服务器异步通知Adobe Campaign设备令牌已注册（当用户卸载了移动应用程序时）。 **[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流每6小时运行一次，以联系APNs反馈服务以更新&#x200B;**AppSubscriptionRcp**&#x200B;表。 对于所有已取消激活的令牌，字段&#x200B;**Disabled**&#x200B;设置为&#x200B;**True**，链接到该设备令牌的订阅将自动从将来的投放中排除。

**对于iOS - HTTP/V2连接器**

HTTP/V2协议允许直接反馈和每个推送投放的状态。 如果使用HTTP/V2协议连接器，则&#x200B;**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流不再调用反馈服务。 未注册的令牌在iOS二进制连接器和iOS HTTP/V2连接器之间以不同方式处理。 卸载或重新安装手机应用程序时，令牌被视为未注册。

同步地，如果APNs返回消息的“未注册”状态，则目标令牌将立即置入隔离。

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
   <td> 打开<br />的目标设备 </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 关闭目标设备<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 用户禁用应用程序<br />的通知 </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段——负载太大<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 负载过长<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段——意外的内容格式问题<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 根据错误<br />显示各种错误消息 </td> 
   <td> Soft<br /> </td> 
   <td> 未定义<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 证书问题（密码、损坏等） 并测试与APNs问题的连接<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 根据错误<br />显示各种错误消息 </td> 
   <td> Soft<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送<br />期间网络连接丢失 </td> 
   <td> 失败<br /> </td> 
   <td> 连接错误<br /> </td> 
   <td> 未定义<br /> </td> 
   <td> 不可到达<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs消息拒绝：取消注册<br />用户已删除应用程序或令牌已过期<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 未注册<br /> </td> 
   <td> 硬<br /> </td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs消息拒绝：所有其他错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 错误消息<br />中将显示错误拒绝原因 </td> 
   <td> Soft<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔离{#android-quarantine}

**对于Android V1**

对于每个通知，Adobe Campaign直接从FCM服务器接收同步错误。 Adobe活动会立即处理这些错误，并根据错误的严重性生成硬错误或软错误，并可以执行重试:

* 超出负载长度、连接问题、服务可用性问题：重试，软错误，失败原因为&#x200B;**[!UICONTROL Refused]**。
* 超出设备配额：无重试，软错误，失败原因为&#x200B;**[!UICONTROL Refused]**。
* 无效或未注册的令牌，意外错误，发送者帐户问题：无重试，硬错误，失败原因为&#x200B;**[!UICONTROL Refused]**。

**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流每6小时运行一次以更新&#x200B;**AppSubscriptionRcp**&#x200B;表。 对于声明为未注册或不再有效的令牌，字段&#x200B;**Disabled**&#x200B;设置为&#x200B;**True**，链接到该设备令牌的订阅将自动从将来的投放中排除。

在投放分析期间，将从目标中排除的所有设备都自动添加到&#x200B;**excludeLogAppSubRcp**&#x200B;表中。

>[!NOTE]
对于使用百度连接器的客户，以下是不同类型的错误：
* 投放开始时的连接问题：失败类型&#x200B;**[!UICONTROL Undefined]**，失败原因&#x200B;**[!UICONTROL Unreachable]**，重试。
* 在投放期间连接丢失：执行软错误、失败原因&#x200B;**[!UICONTROL Refused]**、重试。
* 百度在发送过程中返回的同步错误：硬错误，失败原因&#x200B;**[!UICONTROL Refused]**，未执行重试。

Adobe Campaign每10分钟与百度服务器联系，检索发送消息的状态并更新广播。 如果消息被声明为已发送，则广播中消息的状态将设置为&#x200B;**[!UICONTROL Received]**。 如果百度声明错误，则状态将设置为&#x200B;**[!UICONTROL Failed]**。

**对于Android V2**

Android V2隔离机制与Android V1使用的过程相同，对订阅和排除更新的过程也相同。 有关详细信息，请参阅[Android V1](#android-quarantine)部分。

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
   <td> 消息创建/分析阶段：自定义字段<br />中使用的非法关键字 </td> 
   <td> 失败<br /> </td> 
   <td> 下列关键字不能使用：{1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建/分析阶段：负载过大<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 通知太重：{1} bits, while only {2} are authorized<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送<br />期间网络连接丢失 </td> 
   <td> 失败<br /> </td> 
   <td> 地址上没有来自Firebase Cloud Messaging服务的响应：{1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 不可到达<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：FCM服务器暂时不可用（例如超时）。<br /> </td> 
   <td> 失败<br /> </td> 
   <td> Firebase Cloud Messaging服务暂时不可用<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 不可到达<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：验证发件人帐户时出错<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 无法识别开发人员帐户，请检查您的ID和密码<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：超出设备配额<br /> </td> 
   <td> 失败<br /> </td> 
   <td> </td> 
   <td> Soft<br /> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：注册无效／未注册<br /> </td> 
   <td> 失败<br /> </td> 
   <td> </td> 
   <td> 硬<br /> </td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：所有其他错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> Firebase Cloud Messaging服务器返回了意外的错误代码：{1} </td> 
   <td> </td> 
   <td> 已拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM消息拒绝：参数<br />无效 </td> 
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
   <td> 柔和</td>
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒绝：未注册<br /> </td> 
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
   <td> FCM消息拒绝：意外错误代码<br /> </td> 
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
   <td> 身份验证：客户端未授权使用此方法检索访问令牌，或者客户端未对请求的任何范围授权。<br /> </td> 
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
   <td> 身份验证：JWT<br />无效 </td> 
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

## SMS隔离{#sms-quarantines}

**对于标准连接器**

短信隔离机制与一般过程是全局的。 请参阅[关于隔离](#about-quarantines)。 SMS的特性列于下面。

>[!NOTE]
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
   <td> 已发送到提供程序<br /> </td> 
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
   <td> 提供程序<br />返回的错误 </td> 
   <td> 失败<br /> </td> 
   <td> 接收数据（SR或MO）时出错<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 不可到达<br /> </td> 
  </tr> 
  <tr> 
   <td> 无效MT确认<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 处理发送查询的确认帧时出错“{1}”<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 不可到达<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送MT<br />时出错 </td> 
   <td> 失败<br /> </td> 
   <td> 发送消息<br />时出错 </td> 
   <td> Soft<br /> </td> 
   <td> 不可到达<br /> </td> 
  </tr> 
 </tbody> 
</table>

**对于扩展通用SMPP连接器**

当使用SMPP协议发送SMS消息时，错误管理的处理方式不同。 有关扩展通用SMPP连接器的详细信息，请参阅[此页](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

SMPP连接器从SR（状态报告）消息中检索数据，该消息使用常规表达式(regexes)返回以过滤其内容。 然后，将此数据与&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表中的信息进行匹配（可通过&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**&#x200B;菜单访问）。

在限定新类型的错误之前，默认情况下故障原因始终设置为&#x200B;**拒绝**。

>[!NOTE]
失败类型和失败原因与电子邮件的失败类型和原因相同。 请参阅[投放故障类型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
在投放日志资格表中，要求提供商提供状态和错误代码列表，以设置正确的故障类型和故障原因。

生成消息的示例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有错误消息以&#x200B;**SR**&#x200B;开头，以区分SMS错误代码和电子邮件错误代码。
* 错误消息的第二部分（本例中的&#x200B;**Generic**）引用SMSC实现的名称，如在SMS外部帐户的&#x200B;**[!UICONTROL SMSC implementation name]**&#x200B;字段中定义的名称。 请参阅[此页](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   由于同一错误代码可能对每个提供程序具有不同的含义，因此此字段允许您了解生成错误代码的提供程序。 然后，您可以在相关提供商的文档中找到该错误。

* 错误消息的第三部分（本例中的&#x200B;**DELIVRD**）与使用SMS外部帐户中定义的状态提取正则表达式从SR检索的状态代码相对应。

   此正则表达式在外部帐户的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;选项卡中指定。 请参阅[此页](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   ![](assets/tech_quarant_error_regex.png)

   缺省情况下，正则表达式提取&#x200B;**stat:**&#x200B;字段，该字段由&#x200B;**SMPP 3.4规范**&#x200B;的&#x200B;**附录B**&#x200B;部分定义。

* 错误消息的第四部分（本例中的&#x200B;**000**）与使用在SMS外部帐户中定义的错误代码提取正则表达式从SR提取的错误代码相对应。

   此正则表达式在外部帐户的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;选项卡中指定。 请参阅[此页](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   缺省情况下，正则表达式提取&#x200B;**err:**&#x200B;字段，该字段由&#x200B;**SMPP 3.4规范**&#x200B;的&#x200B;**附录B**&#x200B;部分定义。

* 管道符号(|)之后的所有内容仅显示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表的&#x200B;**[!UICONTROL First text]**&#x200B;列中。 在消息规范化后，此内容始终由&#x200B;**#MESSAGE#**&#x200B;替换。 此过程可避免出现多个条目，以处理类似错误，与电子邮件相同。 有关详细信息，请参阅[弹回邮件资格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)。

扩展的通用SMPP连接器应用启发式方法来查找合理的默认值：如果状态以&#x200B;**DELIV**&#x200B;开头，则它被视为成功，因为它与大多数提供商使用的常见状态&#x200B;**DELIVRD**&#x200B;或&#x200B;**DELIVERED**&#x200B;匹配。 任何其他状态都会导致硬故障。
