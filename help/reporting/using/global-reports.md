---
product: campaign
title: 全局报告
description: 全局报告
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 6839fd7e-ecf4-4504-90a8-0207bc3991e4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 2%

---

# 全局报告 {#global-reports}

这些报告涉及整个数据库中数据的活动。 要查看报表功能板，请转到&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡。

![](assets/s_ncs_user_report_delivery_link.png)

要显示报表，请单击其名称。 默认情况下，可以使用以下报表：

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>此部分仅显示链接到投放的报表。

* **[!UICONTROL Delivery throughput]** :请参阅投 [放吞吐量](#delivery-throughput)。
* **[!UICONTROL Browsers]** :请参阅浏 [览器](#browsers)。
* **[!UICONTROL Sharing to social networks]** :请参阅 [共享到社交网络](#sharing-to-social-networks)。
* **[!UICONTROL Statistics on sharing activities]** :请参阅 [共享活动的统计信息](#statistics-on-sharing-activities)。
* **[!UICONTROL Operating systems]** :请参阅操 [作系统](#operating-systems)。
* **[!UICONTROL URLs and click streams]** :请参阅 [URL并单击流](../../reporting/using/delivery-reports.md#urls-and-click-streams)。
* **[!UICONTROL Tracking indicators]** :请参阅跟 [踪指示器](../../reporting/using/delivery-reports.md#tracking-indicators)。
* **[!UICONTROL Non-deliverables and bounces]** :请参阅 [无法交付项和退回](#non-deliverables-and-bounces)。
* **[!UICONTROL User activities]** :请参阅用 [户活动](#user-activities)。
* **[!UICONTROL Subscription tracking]** :请参阅 [订阅跟踪](#subscription-tracking)。
* **[!UICONTROL Delivery summary]** :请参阅 [投放摘要](../../reporting/using/delivery-reports.md#delivery-summary)。
* **[!UICONTROL Delivery statistics]** :请参阅投 [放统计信息](#delivery-statistics)。
* **[!UICONTROL Breakdown of opens]** :请参阅打 [开的划分](#breakdown-of-opens)。

## 投放吞吐量 {#delivery-throughput}

此报表包含有关给定时段内整个平台的投放吞吐量的信息。 为了测量消息的传送速度，标准是每小时发送的消息数和消息的大小（以位/秒为单位）。 在以下示例中，第一个图表以蓝色显示成功投放，以橙色显示错误投放的数量。

![](assets/s_ncs_user_report_toolbar.png)

您可以通过更改时间刻度来配置显示的值：1小时查看、3小时查看、24小时查看等。 单击 **[!UICONTROL Refresh]** 以确认您的选择。

## 用户活动{#user-activities}

此报表以图表形式显示每半小时、每小时或每天的打开数、点击数和交易记录的细分。

![](assets/s_ncs_user_user_report.png)

可以使用以下选项：

* **[!UICONTROL Opens]** :已打开的消息总数。未考虑文本格式的电子邮件。 有关跟踪打开的更多信息，请参阅[跟踪打开](../../reporting/using/indicator-calculation.md#tracking-opens-)。
* **[!UICONTROL Clicks]** :投放中链接的总点击次数。取消订阅链接和镜像页面的点击量不会被考虑在内。
* **[!UICONTROL Transactions]** :收到消息后的交易总数。为了考虑交易，必须在匹配的网页中插入交易类型Web跟踪标记。 Web跟踪配置请参见[此部分](../../configuration/using/about-web-tracking.md)。

## 无法投放项和退回 {#non-deliverables-and-bounces}

此报表显示了无法交付项的细分以及每个互联网域的退回细分。

**[!UICONTROL Number of messages processed]**&#x200B;表示投放服务器处理的消息总数。 此值小于停止或暂停某些投放时（服务器处理之前）要投放的消息数。

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>此报表中显示的错误会触发隔离过程。 有关隔离管理的更多信息，请参阅[隔离管理](../../delivery/using/understanding-quarantine-management.md)。

此报表的第一部分以值表和图表的形式显示无法交付项的划分。

对于每种错误类型，我们都有：

* 此类型的错误消息数，
* 出现此类型错误的消息数与出现错误的消息总数的百分比，
* 此类型的错误消息与已处理消息总数的百分比。

使用以下指标：

* **[!UICONTROL User unknown]** :投放期间生成的错误类型，用于指示电子邮件地址无效。
* **[!UICONTROL Invalid domain]** :发送投放以指示电子邮件地址的域错误或不存在时生成的错误类型。
* **[!UICONTROL Inbox full]** :5次投放尝试表明收件人的收件箱包含过多邮件后，生成的错误类型。
* **[!UICONTROL Account disabled]** :发送投放时生成的错误类型，用于指示地址不再存在。
* **[!UICONTROL Rejected]** :当地址被IAP（互联网访问提供商）拒绝时(例如，在应用安全规则（防垃圾邮件软件）之后)生成的错误类型。
* **[!UICONTROL Unreachable]** :消息分发字符串中发生的错误类型：SMTP中继事件、域名临时不可到达等
* **[!UICONTROL Not connected]** :表示发送时收件人的手机已关闭或断开与网络的连接的错误类型。

   >[!NOTE]
   >
   >此指标仅涉及移动渠道上的投放。 如需详细信息，请参阅[此部分](../../delivery/using/sms-channel.md)。

   单击`[+]`符号可打开值表的每一行。 对于每种错误类型，您可以按域显示错误消息的划分。

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

此报告的第二部分以值表和图表的形式显示每个Internet域的错误细分。

对于每个域名，我们具有：

* 此域中出错的消息数，
* 与针对此域处理的消息总数相比，此域出错的消息百分比，
* 此域的错误消息与错误消息总数的百分比。

可通过单击[+]符号打开值表的每一行。 对于每种域类型，您可以按错误类型显示错误消息的划分。

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>此报表中显示的域名在多维数据集级别定义。 要更改这些值，请编辑&#x200B;**[!UICONTROL Delivery logs (broadlogrcp)]**&#x200B;多维数据集。 如需详细信息，请参阅[此部分](../../reporting/using/about-cubes.md)。**[!UICONTROL Others]**&#x200B;类别包含不属于特定类的域名。

## 浏览器 {#browsers}

此报表显示投放收件人在相关时段使用的Internet浏览器的细目。

>[!NOTE]
>
>此报表中显示的值是估计值：将只考虑已单击投放的收件人。

**全局统计**

有关浏览器使用情况的全局统计信息以值表和图表的形式呈现。

![](assets/dlv_explorers_report.png)

使用以下指标：

* **[!UICONTROL Visitors]** :已定向并且已至少点击一次投放的收件人总数（每个Internet浏览器）。
* **[!UICONTROL Pages viewed]** :投放中（每个Internet浏览器）所有投放的链接总点击次数。
* **[!UICONTROL Usage rate]** :此比率表示访客（每个Internet浏览器）与访客总数之间的关联。

**每个浏览器的统计信息**

在全局统计值表中，您可以单击每个浏览器名称以查看其使用情况统计信息。

![](assets/s_ncs_user_explorers_report2.png)

统计数据以曲线、图表和值表的形式呈现。

**[!UICONTROL History]**&#x200B;曲线表示此浏览器每天的出席率。 比率是每日（在此浏览器上）访客数与当天以最高出勤率测量的访客数之比。

**[!UICONTROL Breakdown per version]**&#x200B;图表表示与访客总数（在此浏览器上）相比，每个版本的访客的细分情况。

值表使用以下指标：

* **[!UICONTROL Global rate]** :此比率表示与所有浏览器上的访客总数相比，每个版本的访客的细分情况。
* **[!UICONTROL Relative rate]** :此比率表示与访客总数（在此浏览器上）相比，每个版本的访客的细分情况。

### 共享到社交网络{#sharing-to-social-networks}

病毒式营销让投放收件人与其联系网络共享信息：他们可以添加指向其配置文件(Facebook、Twitter等)的链接 或者给朋友发个信息。 在投放中跟踪每次共享和每次访问共享信息。 有关病毒式营销的更多信息，请参阅[此部分](../../delivery/using/viral-and-social-marketing.md)。

此报表显示每个社交网络(Facebook、Twitter等)的共享和打开消息的划分 和/或每封电子邮件。

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

在电子邮件投放统计信息中，显示了两个值：

* **[!UICONTROL Number of messages to be delivered]** :在投放分析期间处理的消息总数。
* **[!UICONTROL Number of successful deliveries]** :成功处理的消息数。

**[!UICONTROL Sharing activities and mail open statistics]**

中央表格显示有关电子邮件共享和打开次数的统计资料。

在&#x200B;**[!UICONTROL Shares]**&#x200B;列中，我们有以下指示器：

* **[!UICONTROL No. of sharing activities]** :每个社交网络上共享的消息总数。此值等于对匹配&#x200B;**[!UICONTROL Links for sharing to social networks]**&#x200B;个性化块图标的总点击次数。
* **[!UICONTROL Breakdown]** :此比率表示每个社交网络的分享次数与分享总数的关系。
* **[!UICONTROL Sharing rate]** :此比率表示每个社交网络的分享次数与要发送的消息数量的关系。

在&#x200B;**[!UICONTROL Opens]**&#x200B;列中，我们有以下指示器：

* **[!UICONTROL No. of opens]** :将消息转发到的人员（通过个性化块）打开的消 **[!UICONTROL Links for sharing to social networks]** 息总数。此值等于镜像页面的显示次数。 未考虑投放收件人打开的次数。
* **[!UICONTROL Breakdown]** :此比率表示每个社交网络的打开次数相对于总打开次数的细分。
* **[!UICONTROL Rate of opens]** :此比率表示每个社交网络的打开数与共享总数的关系。

**[!UICONTROL Breakdown of sharing activities and opens]**

本节包括两个图表，它们表示共享活动的细分，并按社交网络打开。

## 共享活动的统计资料{#statistics-on-sharing-activities}

此报表显示了共享到社交网络(Facebook、Twitter、电子邮件等)的演变 及时。

有关病毒式营销的更多信息，请参阅[此部分](../../delivery/using/viral-and-social-marketing.md)。

![](assets/s_ncs_user_social_report2.png)

统计资料以值表和图表的形式呈现。

使用以下指标：

* **[!UICONTROL New contacts]** :接收通过电子邮件共享的消息后的新订阅数。此值匹配通过电子邮件共享消息、单击&#x200B;**[!UICONTROL Subscription link]**&#x200B;并填写订阅表单的人数。
* **[!UICONTROL Opens]** :消息被传输到的人员（通过个性化块）打开的 **[!UICONTROL Link for sharing to social networks]** 消息总数。此值等于镜像页面的显示次数。 未考虑投放收件人打开的次数。
* **[!UICONTROL Sharing activities]** :通过社交网络共享的消息总数。此值与&#x200B;**[!UICONTROL Links for sharing to social networks]**&#x200B;个性化块图标的总点击次数匹配。

## 操作系统 {#operating-systems}

此报表显示了投放收件人在有关期间使用的操作系统的细目。

>[!NOTE]
>
>此报表中显示的值是估计值：将只考虑已单击投放的收件人。

**全局统计**

操作系统的全局使用统计数据以值表和图表的形式呈现。

![](assets/s_ncs_user_os_report.png)

使用以下指标：

* **[!UICONTROL Visitors]** :点击投放至少一次的目标收件人（每个操作系统）总数的每日平均值。
* **[!UICONTROL Pages viewed]** :所有投放的投放链接（每个操作系统）的每日平均点击次数。
* **[!UICONTROL Rate of use]** :此比率表示访客（每个操作系统）与访客总数之间的关联。

**每个操作系统的统计信息**

在全局统计信息值表中，单击每个操作系统的名称以查看每个操作系统的统计信息。

![](assets/s_ncs_user_os_report2.png)

统计数据以曲线、图表和值表的形式呈现。

**[!UICONTROL History]**&#x200B;曲线表示此操作系统每天的使用率。 此比率是每日（在此操作系统上）访客数与在出勤率最高的当天测量的访客数之比。

**[!UICONTROL Breakdown by version]**&#x200B;图表表示每个版本的访客数与此操作系统上的访客总数之间的关系。

值表使用以下指标：

* **[!UICONTROL Global rate]** :此比率表示访客（每个版本）与整个操作系统中的访客总数之间的细分。
* **[!UICONTROL Relative rate]** :此比率表示访客（每个版本）与此操作系统的访客总数之间的关系。

## 订阅跟踪{#subscription-tracking}

此报告可让您监控信息服务订阅情况。 它显示订阅和退订。

![](assets/s_ncs_user_services_report.png)

通过单击主页或资源管理器的&#x200B;**[!UICONTROL Profiles and targets > Services and subscriptions]**&#x200B;节点，可为订阅显示该节点。 选择所需的订阅，然后单击&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡。 默认情况下， **[!UICONTROL Subscriptions tracking]**&#x200B;报表可用。 它允许您查看订阅和退订趋势以及一段时间内的忠诚度比率。 您可以通过下拉列表配置此数据的表示形式。 单击&#x200B;**[!UICONTROL Refresh]**&#x200B;以验证所选配置。

如需详细信息，请参阅[此页面](../../delivery/using/managing-subscriptions.md)。

**[!UICONTROL Number subscribed to date]**&#x200B;表示当前订阅的总人数。

**[!UICONTROL Overall evolution of subscriptions]**

值表使用以下指标：

* **[!UICONTROL Subscribers]** :有关期间的订户总数。
* **[!UICONTROL Subscriptions]** :有关期间的订阅数。
* **[!UICONTROL Unsubscriptions]** :有关期间的退订次数。
* **[!UICONTROL Evolution]** :取消订阅数减去订阅数。该速率基于订阅者总数计算。
* **[!UICONTROL Loyalty]** :相关时段的订阅者忠诚度比率。

**[!UICONTROL Subscription evolution curves]**

此图表显示了相关期间订阅和退订的演变情况。

## 投放统计数据{#delivery-statistics}

此报表显示按互联网域、处理和发送的所有消息、硬退回和软退回、打开、点击和退订的细分。

![](assets/s_ncs_user_broadcast_report.png)

使用以下指标：

* **[!UICONTROL Emails processed]** :投放服务器处理的消息总数。
* **[!UICONTROL Delivered]** :成功处理的消息数量与已处理消息总数的百分比。
* **[!UICONTROL Hard bounces]** :“硬”退回次数与已处理消息总数的百分比。
* **[!UICONTROL Soft bounces]** :“软”退回次数与已处理消息总数的百分比。

   >[!NOTE]
   >
   >有关硬退回和软退回的更多信息，请参阅[隔离管理](../../delivery/using/understanding-quarantine-management.md)。

* **[!UICONTROL Opens]** :与成功处理消息的数量相比，至少打开一次消息的目标收件人数量的百分比。
* **[!UICONTROL Clicks]** :与成功处理的消息数量相比，点击投放至少一次的人数百分比。
* **[!UICONTROL Unsubscription]** :退订链接的点击次数与成功处理消息数的百分比。

## 打开次数{#breakdown-of-opens}的划分

此报表显示了在相关时段内，操作系统、设备和浏览器的打开次数的细分情况。 对于每个类别，使用两个图表。 第一个报表显示有关计算机和移动设备上打开次数的统计信息。 第二个显示仅与移动设备上的打开次数相关的统计信息。

打开次数对应于已打开的消息总数。 不会计算文本格式电子邮件。 有关“跟踪”打开次数的更多信息，请参阅[跟踪打开次数](../../reporting/using/indicator-calculation.md#tracking-opens-)一节。

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>浏览器和操作系统名称构成了浏览器用户代理发送的已打开消息的信息的一部分。 Adobe Campaign利用其设备信息推导设备类型。
