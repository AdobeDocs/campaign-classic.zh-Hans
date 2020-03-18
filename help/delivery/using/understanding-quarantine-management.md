---
title: 了解隔离管理
seo-title: 了解隔离管理
description: 了解隔离管理
seo-description: null
page-status-flag: never-activated
uuid: 9421e26c-bdcc-4588-8e44-fa6f31051081
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 56cbf48a-eb32-4617-8f80-efbfd05976ea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 527d2dd2296d18c8ca26745b9f87d65c6fdf480a

---


# 了解隔离管理{#understanding-quarantine-management}

## 关于检疫 {#about-quarantines}

Adobe Campaign 管理了一个隔离地址列表。在投放分析时，默认情况下会将其地址已被隔离的收件人排除在外，不会将其设为目标。举例来说，信箱已满或地址不存在时，可以隔离某个电子邮件地址。无论如何，隔离程序都符合下述特定规则。

>[!NOTE]
>
>本条适用于在线渠道：电子邮件、短信、推送通知。

### 通过隔离优化您的交付 {#optimizing-your-delivery-through-quarantines}

邮件准备过程中，将自动排除其电子邮件地址或电话号码处于隔离状态的配置文件(请参阅 [识别传送的隔离地址](#identifying-quarantined-addresses-for-a-delivery))。 这将加快交付速度，因为错误率对交付速度有显着影响。

如果无效地址的速率太高，某些Internet访问提供商会自动将电子邮件视为垃圾邮件。 因此，隔离功能可以避免这些提供商的黑名单。

此外，隔离可以排除发送错误的电话号码，从而帮助降低短信发送成本。 有关保护和优化交付的最佳实践的更多信息，请参阅 [本页](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)。

### 隔离与黑名单 {#quarantine-vs-blacklisting}

**隔离** (Quarantine)仅适用于地址，而不适用于配置文件本身。 这意味着，如果两个配置文件具有相同的电子邮件地址，则在地址被隔离时，这两个配置文件都会受到影响。

同样，其电子邮件地址被隔离的配置文件也可以更新其配置文件并输入新地址，然后可以通过提交操作再次定位。

**另一方面**，黑名单将导致任何分发不再瞄准配置文件，例如在取消订阅（选择退出）后。

>[!NOTE]
>
>当用户用诸如“STOP”的关键字回复SMS消息以选择退出SMS分发时，其个人资料不会像在电子邮件选择退出过程中那样被列入黑名单。 配置文件电话号码将发送到隔离，以便用户继续接收电子邮件。

## 识别隔离地址 {#identifying-quarantined-addresses}

可以为特定交付或整个平台列出隔离的地址。

### 识别传送的隔离地址 {#identifying-quarantined-addresses-for-a-delivery}

特定传送的隔离地址在传送准备阶段的传送控制板的传送日志中列出(请参阅传送 [日志和历史记录](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history))。

### 识别整个平台的隔离地址 {#identifying-quarantined-addresses-for-the-entire-platform}

管理员可以从节点为整个平台列出隔离中的地 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 址。

>[!NOTE]
>
>此菜单列出了电子邮件、 **SMS和推送通**&#x200B;知渠道 **的隔** 离元素 **** 。

每个地址都有以下信息：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>检疫数量的增加是正常的，与数据库的“磨损”有关。 例如，如果电子邮件地址的有效期被认为是三年，收件人表格每年增加50%，那么隔离的增加可以计算如下：
>
>年末1:(1*0.33)/(1+0.5)=22%。
年末2:((1.22*0.33)+0.33)/(1.5+0.75)=32.5%。

### 在传送报告中识别隔离地址 {#identifying-quarantined-addresses-in-delivery-reports}

以下报告提供了有关隔离中地址的信息：

* 对于每个传送，报 **[!UICONTROL Delivery summary]** 告会显示传送目标中隔离的地址数。 它显示：

   * 在交付分析过程中，隔离的地址数，

   * 在传送操作后置于隔离中的地址数。

* 报 **[!UICONTROL Non-deliverables and bounces]** 告显示有关隔离中地址的信息、遇到的错误类型等，以及按域划分的故障细目。

您可以查找平台的所有交付(主页>报&#x200B;**告**)或特定交付的此信息。 您还可以创建自定义报告并选择要显示的信息。

### 识别收件人的隔离地址 {#identifying-quarantined-addresses-for-a-recipient}

您可以查找任何收件人的电子邮件地址的状态。 为此，请选择收件人配置文件，然后单击选 **[!UICONTROL Deliveries]** 项卡。 对于发送给该收件人的所有分发，您可以了解地址是否失败、是否在分析过程中被隔离等。 对于每个文件夹，只能显示电子邮件地址处于隔离状态的收件人。 为此，请使用应用程 **[!UICONTROL Quarantined email address]** 序过滤器。

![](assets/tech_quarant_recipients_filter.png)

### 删除隔离地址 {#removing-a-quarantined-address}

如果需要从隔离中删除地址，请手动将其状态更改为 **[!UICONTROL Valid]**。

![](assets/tech_quarant_error_status.png)

如果将状态更改为， **[!UICONTROL Whitelisted]**&#x200B;则即使遇到错误，每次都会系统地定位地址。

>[!CAUTION]
列入黑名单的地址不受隔离系统的关注，并且不是目标地址，即使您更改了地址的状态。

您还可以更改错误数和错误之间的句点。 为此，请更改部署向导的设置（电子邮件渠道／高级设置）。 有关部署向导的详细信息，请参阅 [此部分](../../installation/using/deploying-an-instance.md)。

## 发送地址到隔离的条件 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign会根据发送失败类型和在错误消息资格(请参阅弹回邮件资格 [)期间分配的原因以及发送失败类](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)型和原因管理隔离 [](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

* **忽略的错误**:忽略的错误不会发送地址进行隔离。
* **硬错误**:相应的电子邮件地址会立即发送到隔离区。
* **软错误**:软错误不会立即发送要隔离的地址，但会增加一个错误计数器。 有关此方面的详细信息，请参 [阅软错误管理](#soft-error-management)。

如果用户将电子邮件归为垃圾邮件(**反馈循环**)，则该邮件会自动重定向到由Adobe管理的技术邮箱。 随后，用户的电子邮件地址会自动发送到隔离区。

在隔离地址列表中，字段 **[!UICONTROL Error reason]** 指示将选定地址置于隔离中的原因。 Adobe Campaign中的隔离区区分大小写。 确保以小写形式导入电子邮件地址，以便以后不会重新定位。

![](assets/tech_quarant_error_reasons.png)

### 软错误管理 {#soft-error-management}

与硬错误相反，软错误不会立即发送要隔离的地址，而是会增加一个错误计数器。

* 当错误计数器达到限制阈值时，地址将进入隔离。
* 在默认配置中，阈值设置为5个错误，其中，如果两个错误间隔至少24小时，则它们会显着。 地址在第五个错误时被隔离。
* 可以修改错误计数器阈值。 有关详细信息，请参阅“在临时 [交付失败后重试”](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。

如果上次出现重大错误的时间超过10天，则错误计数器将重新初始化。 然后，地址状态将更改为“ **有效** ”，并且数据库清除工作流会从隔离列 **表中删除该状态** 。

## 推送通知隔离 {#push-notification-quarantines}

推送通知的隔离机制与常规进程在全局上相同。 请参 [阅关于检疫](#about-quarantines)。 但是，对于推送通知，某些错误的管理方式不同。 例如，对于某些软错误，在同一交付内不执行重试。 推送通知的特性如下所列。 重试机制（重试次数、频率）与电子邮件的重试机制相同。

被隔离的项目是设备令牌。

### iOS隔离 {#ios-quarantine}

**对于iOS —— 二进制连接器**

对于每个通知，Adobe Campaign会从APNS服务器接收同步和异步错误。 对于以下同步错误，Adobe Campaign会生成软错误：

* 负载长度问题：无重试，失败原因为 **[!UICONTROL Unreachable]**。
* 证书过期问题：无重试，失败原因为 **[!UICONTROL Unreachable]**。
* 交付过程中连接丢失：已执行重试，失败原因为 **[!UICONTROL Unreachable]**。
* 服务配置问题（证书无效、证书密码无效、证书无效）:无重试，失败原因为 **[!UICONTROL Unreachable]**。

APNS服务器异步通知Adobe Campaign设备令牌已取消注册（当用户卸载了移动应用程序时）。 该工 **[!UICONTROL mobileAppOptOutMgt]** 作流每6小时运行一次，以与APNS反馈服务联系以更新 **AppSubscriptionRcp** 表。 对于所有已停用的令牌， **“禁用** ”字段将设置为 **True** ，并且链接到该设备令牌的订阅将自动从将来的分发中排除。

**对于iOS - HTTP/2连接器**

http/2协议允许每个推送交付的直接反馈和状态。 如果使用http/2协议连接器，则工作流不再调用反馈服 **[!UICONTROL mobileAppOptOutMgt]** 务。 未注册的令牌在iOS二进制连接器和iOS http/2连接器之间处理方式不同。 卸载或重新安装手机应用程序时，代号被视为未注册。

同步地，如果APNS为消息返回“未注册”状态，则目标令牌将立即被隔离。

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
   <td> 目标设备已开启<br /> </td> 
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
   <td> 用户禁用应用程序通知<br /> </td> 
   <td> 确定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 消息创建／分析阶段——有效负荷过大<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 负载过长<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建／分析阶段——意外的内容格式问题<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 根据错误发送的各种错误消息<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 未定义<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 证书问题（密码、损坏等）并测试与APNS问题的连接<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 根据错误发送的各种错误消息<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送过程中网络连接丢失<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 连接错误<br /> </td> 
   <td> 未定义<br /> </td> 
   <td> 无法访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> APNS消息拒绝：取消注册<br /> ，用户已删除应用程序或令牌已过期<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 未注册<br /> </td> 
   <td> 硬<br /> </td> 
   <td> 用户未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APNS消息拒绝：所有其他错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 错误消息中将显示错误拒绝原因<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔离 {#android-quarantine}

**对于Android V1**

对于每个通知，Adobe Campaign会直接从FCM服务器接收同步错误。 Adobe Campaign会根据错误的严重性动态处理这些错误并生成硬错误或软错误，并可以执行重试：

* 超出负载长度，连接问题，服务可用性问题：已执行重试、软错误、失败原因 **[!UICONTROL Refused]**&#x200B;为。
* 超出设备配额：无重试、软错误、失败原因 **[!UICONTROL Refused]**&#x200B;为。
* 无效或未注册的令牌，意外错误，发送者帐户问题：无重试、硬错误、失败原因 **[!UICONTROL Refused]**&#x200B;为。

该工 **[!UICONTROL mobileAppOptOutMgt]** 作流每6小时运行一次，以更新 **AppSubscriptionRcp** 表。 对于声明为未注册或不再有效的令牌， **Disabled** （禁用）字段设置为 **True** ，链接到该设备令牌的订阅将自动从将来的分发中排除。

在分发分析过程中，从目标中排除的所有设备都会自动添加到 **excludeLogAppSubRcp** 表中。

>[!NOTE]
对于使用Baidu连接器的客户，以下是不同类型的错误：
* 交付开始时的连接问题：失败类 **[!UICONTROL Undefined]**&#x200B;型、失败原因 **[!UICONTROL Unreachable]**、重试被执行。
* 交付过程中连接丢失：软错误、失败原因 **[!UICONTROL Refused]**、重试被执行。
* Baidu在发送过程中返回的同步错误：硬错误、失败原 **[!UICONTROL Refused]**&#x200B;因、不执行重试。

Adobe Campaign每10分钟与Baidu服务器联系，以检索已发送消息的状态并更新广播。 如果消息被声明为已发送，则广播中消息的状态将设置为 **[!UICONTROL Received]**。 如果百度声明错误，则状态将设置为 **[!UICONTROL Failed]**。

**对于Android V2**

Android V2隔离机制使用与Android V1相同的进程，同样的进程也适用于订阅和排除更新。 有关详细信息，请参阅 [Android V1部分](#android-quarantine) 。

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
   <td> 消息创建／分析阶段：自定义字段中使用的非法关键字<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 不能使用以下关键字：{1}<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息创建／分析阶段：负载过大<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 通知过重：{1} bits, while only {2} authorized<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送过程中网络连接丢失<br /> </td> 
   <td> 失败<br /> </td> 
   <td> Firebase Cloud Messaging服务在以下地址上没有响应：{1}<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 无法访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：FCM服务器暂时不可用（例如超时）。 <br /> </td> 
   <td> 失败<br /> </td> 
   <td> Firebase Cloud Messaging服务暂时不可用<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 无法访问<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：验证发送者帐户时出错<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 无法识别开发人员帐户，请检查您的ID和密码<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒绝：超出设备配额<br /> </td> 
   <td> 失败<br /> </td> 
   <td> </td> 
   <td> 柔和<br /> </td> 
   <td> 拒绝<br /> </td> 
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
   <td> Firebase Cloud Messaging服务器返回意外的错误代码：{1} </td> 
   <td> </td> 
   <td> 拒绝<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

## SMS隔离 {#sms-quarantines}

**对于标准连接器**

SMS消息的隔离机制与一般过程在全局上是相同的。 请参 [阅关于检疫](#about-quarantines)。 SMS的特性如下。

>[!NOTE]
该表 **[!UICONTROL Delivery log qualification]** 不适用于扩展的通 **用SMPP连接器** 。

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
   <td> 提供者返回的错误<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 接收数据时出错（SR或MO）<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 无法访问<br /> </td> 
  </tr> 
  <tr> 
   <td> 无效MT确认<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 处理发送查询的确认帧时出错“{1}”<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 无法访问<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送MT时出错<br /> </td> 
   <td> 失败<br /> </td> 
   <td> 发送消息时出错<br /> </td> 
   <td> 柔和<br /> </td> 
   <td> 无法访问<br /> </td> 
  </tr> 
 </tbody> 
</table>

**对于扩展的通用SMPP连接器**

当使用SMPP协议发送SMS消息时，错误管理会以不同方式处理。 有关扩展通用SMPP连接器的详细信息，请参 [阅本页](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

SMPP连接器从SR（状态报告）消息中检索数据，该SR（状态报告）消息使用正则表达式(regexes)返回以过滤其内容。 然后，将根据表中的信息匹配此数 **[!UICONTROL Delivery log qualification]** 据(可通过 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** >菜单 **[!UICONTROL Non deliverables Management]** 访问)。

在限定新类型的错误之前，默认情况下，失败原因始终设置为“ **拒绝** ”。

>[!NOTE]
失败类型和失败原因与电子邮件相同。 请参 [阅交付失败类型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
请向提供商索取状态和错误代码列表，以便在“交付日志”资格表中设置正确的失败类型和失败原因。

生成的消息示例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有错误消息都以 **SR开头** ，以区分SMS错误代码和电子邮件错误代码。
* 错误消息的第二部分(**本例中的通用** )引用SMSC实现的名称，如在SMS外部帐户的字 **[!UICONTROL SMSC implementation name]** 段中定义的名称。 请参 [阅此页](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   由于同一错误代码可能对每个提供者具有不同的含义，因此此字段允许您了解生成错误代码的提供者。 然后，您可以在相关提供商的文档中找到该错误。

* 错误消息的第三部分(**本例中的DELIVRD** )与使用在SMS外部帐户中定义的状态提取正则表达式从SR检索到的状态代码相对应。

   此正则表达式在外部帐户 **[!UICONTROL SMSC specificities]** 的选项卡中指定。 请参 [阅此页](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   ![](assets/tech_quarant_error_regex.png)

   默认情况下，正则表达式会提取 **stat:** 字段(如 **SMPP 3.4规范的附录B****部分所定义)**。

* 该错误消息的第四部分(**000** )与使用在SMS外部帐户中定义的错误代码提取正则表达式从SR提取的错误代码相对应。

   此正则表达式在外部帐户 **[!UICONTROL SMSC specificities]** 的选项卡中指定。 请参 [阅此页](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   默认情况下，正则表达式会提取 **错误：** 字段(如 **SMPP 3.4规范的附录B****部分所定义)**。

* 管道符号(|)之后的所有内容只显示在 **[!UICONTROL First text]** 表的列中 **[!UICONTROL Delivery log qualification]** 。 此内容始终由 **#MESSAGE#** After the message is normalized替换。 此过程可避免为类似错误设置多个条目，并且与电子邮件相同。 有关此问题的详细信息，请参 [阅弹回邮件资格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)。

扩展的通用SMPP连接器应用启发式方法来查找合理的默认值：如果状态以 **DELIV开头**，则它被视为成功，因为它与大多数提供商使用的常见状态 **DELIVRD** 或 **DELIVERED** 相匹配。 任何其他状态都会导致硬失败。
