---
title: 全局报告
seo-title: 全局报告
description: 全局报告
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c4e6a9273c920c9d125ec3fb18a0628109475a4e

---


# 全局报告 {#global-reports}

这些报告涉及整个数据库中数据的活动。 要查看报告功能板，请转到选 **[!UICONTROL Reports]** 项卡。

![](assets/s_ncs_user_report_delivery_link.png)

要显示报告，请单击其名称。 默认情况下，以下报告可用：

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>此部分仅显示链接到交付的报表。

* **[!UICONTROL Delivery throughput]** :请参阅交 [付吞吐量](#delivery-throughput)。
* **[!UICONTROL Browsers]** :请参阅浏 [览器](#browsers)。
* **[!UICONTROL Sharing to social networks]** :请参阅 [共享到社交网络](#sharing-to-social-networks)。
* **[!UICONTROL Statistics on sharing activities]** :请参阅有 [关共享活动的统计信息](#statistics-on-sharing-activities)。
* **[!UICONTROL Operating systems]** :请参阅操 [作系统](#operating-systems)。
* **[!UICONTROL URLs and click streams]** :引用URL [并单击流](#urls-and-click-streams)。
* **[!UICONTROL Tracking indicators]** :请参阅跟 [踪指示器](#tracking-indicators)。
* **[!UICONTROL Non-deliverables and bounces]** :请参阅 [非可交付产品和弹回](#non-deliverables-and-bounces)。
* **[!UICONTROL User activities]** :请参阅用 [户活动](#user-activities)。
* **[!UICONTROL Subscription tracking]** :请参阅 [订阅跟踪](#subscription-tracking)。
* **[!UICONTROL Delivery summary]** :请参阅 [交付摘要](#delivery-summary)。
* **[!UICONTROL Delivery statistics]** :请参阅交 [付统计信息](#delivery-statistics)。
* **[!UICONTROL Breakdown of opens]** :请参阅打 [开的细分](#breakdown-of-opens)。

## 投放吞吐量 {#delivery-throughput}

此报告包含有关给定时间段内整个平台的交付吞吐量的信息。 为了测量消息的传送速度，标准是每小时发送的消息数和消息的大小（以位／秒为单位）。 在以下示例中，第一个图以蓝色显示成功交付，以橙色显示错误交付的数量。

![](assets/s_ncs_user_report_toolbar.png)

您可以通过更改时间刻度来配置显示的值：1小时视图、3小时视图、24小时视图等。 单击 **[!UICONTROL Refresh]** 以确认您的选择。

## 用户活动 {#user-activities}

此报告以图表形式显示每半小时、小时或天的打开次数、点击次数和事务处理数的细分。

![](assets/s_ncs_user_user_report.png)

可以使用以下选项：

* **[!UICONTROL Opens]** :已打开消息的总数。 不考虑文本格式的电子邮件。 有关跟踪打开的详细信息，请参阅 [跟踪打开](#tracking-opens-)。
* **[!UICONTROL Clicks]** :提交中链接的总点击次数。 取消订阅链接和镜像页面上的点击量不会被考虑在内。
* **[!UICONTROL Transactions]** :收到消息后的事务总数。 要考虑事务，必须将事务类型Web跟踪标记插入到匹配的网页中。 本节介绍Web跟踪 [配置](../../configuration/using/about-web-tracking.md)。

## 无法投放项和退回 {#non-deliverables-and-bounces}

此报告显示了非交付项的细分，以及每个Internet域的弹回的细分。

表示 **[!UICONTROL Number of messages processed]** 由交付服务器处理的消息总数。 此值低于在某些传送已停止或暂停（在由服务器处理之前）时要传送的消息数。

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>此报告中显示的错误会触发隔离过程。 有关隔离管理的详细信息，请参阅隔 [离管理](../../delivery/using/understanding-quarantine-management.md)。

此报告的第一部分以值表和图表的形式显示非交付项的细分。

对于每个错误类型，我们都有：

* 此类错误消息的数量，
* 此类错误消息与有错误消息总数的百分比，
* 与处理的消息总数相比，此类型错误消息的百分比。

使用以下指示符：

* **[!UICONTROL User unknown]** :发送过程中生成的错误类型，指示电子邮件地址无效。
* **[!UICONTROL Invalid domain]** :发送分发时生成的错误类型，用于指示电子邮件地址的域错误或不存在。
* **[!UICONTROL Inbox full]** :在五次发送尝试后生成的错误类型，以指示收件人的收件箱包含的邮件过多。
* **[!UICONTROL Account disabled]** :发送传送时生成的错误类型，以指示地址不再存在。
* **[!UICONTROL Rejected]** :IAP（Internet访问提供商）拒绝地址时生成的错误类型，例如，在应用安全规则（防垃圾邮件软件）之后。
* **[!UICONTROL Unreachable]** :消息分发字符串中出现的错误类型：SMTP中继事件、域暂时不可访问等
* **[!UICONTROL Not connected]** :指示发送时收件人的移动电话已关闭或已与网络断开连接的错误类型。

   >[!NOTE]
   >
   >此指示器仅涉及移动渠道上的交付。 如需详细信息，请参阅[此部分](../../delivery/using/sms-channel.md)。

   单击符号可打开值表的每行 `[+]` 。 对于每个错误类型，您可以按域显示错误消息的细分。

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

此报告的第二部分以值表和图表的形式显示每个Internet域的错误细目。

对于每个域名，我们都有：

* 此域有错误的消息数，
* 与此域处理的消息总数相比，此域有错误的消息百分比，
* 此域的错误消息与错误消息总数的百分比。

单击+符号可打开值表的每 [行] 。 对于每个域类型，您可以按错误类型显示错误消息的细分。

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>此报告中显示的域名在立方级别定义。 要更改这些值，请编辑立 **[!UICONTROL Delivery logs (broadlogrcp)]** 方。 如需详细信息，请参阅[此部分](../../reporting/using/about-cubes.md)。该 **[!UICONTROL Others]** 类别包括不属于特定类的域名。

## 浏览器 {#browsers}

此报告显示交付接收方在相关期间使用的因特网浏览器的细分。

>[!NOTE]
>
>本报告所示值为估计：将只考虑已单击传送的收件人。

**全球统计**

浏览器使用的全局统计信息以值表和图表的形式显示。

![](assets/dlv_explorers_report.png)

使用以下指示符：

* **[!UICONTROL Visitors]** :目标收件人（每个Internet浏览器）和已至少单击一次分发的收件人总数。
* **[!UICONTROL Pages viewed]** :所有分发中（每个Internet浏览器）分发中链接的总点击次数。
* **[!UICONTROL Usage rate]** :此比率表示与访客总数相关的访客（每个Internet浏览器）细分。

**每浏览器的统计信息**

在全局统计信息值表中，您可以单击每个浏览器名称来查看其使用统计信息。

![](assets/s_ncs_user_explorers_report2.png)

统计信息以曲线、图表和值表的形式呈现。

该曲 **[!UICONTROL History]** 线表示此浏览器每天的出席率。 此比率是每日（在此浏览器上）访客数与当天以最高出席率测量的访客数的比率。

该图 **[!UICONTROL Breakdown per version]** 表显示了与访客总数（在此浏览器上）相比，每个版本的访客细分数。

值表使用以下指示器：

* **[!UICONTROL Global rate]** :此比率表示与所有浏览器上的访客总数相比，每个版本的访客细分数。
* **[!UICONTROL Relative rate]** :此比率表示与访客总数（在此浏览器上）相比，每个版本的访客细分数。

### 共享到社交网络 {#sharing-to-social-networks}

病毒式营销使递送收件人能够与其联系网络共享信息：他们可以添加指向其个人资料的链接（Facebook、Twitter等）或者给朋友发消息。 在分发中跟踪每个共享和对共享信息的每次访问。 For more information on viral marketing, refer to [this section](../../delivery/using/viral-and-social-marketing.md).

此报告显示每个社交网络（Facebook、Twitter等）的共享和已打开消息的细分和／或每封电子邮件。

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

在电子邮件发送统计信息中，显示两个值：

* **[!UICONTROL Number of messages to be delivered]** :在交付分析过程中处理的消息总数。
* **[!UICONTROL Number of successful deliveries]** :成功处理的消息数。

**[!UICONTROL Sharing activities and mail open statistics]**

中央表格显示了电子邮件共享和打开情况的统计信息。

在该列 **[!UICONTROL Shares]** 中，我们有以下指示器：

* **[!UICONTROL No. of sharing activities]** :每个社交网络上共享的消息总数。 此值等于对匹配个性化块图标的总点击 **[!UICONTROL Links for sharing to social networks]** 次数。
* **[!UICONTROL Breakdown]** :此比率表示每个社交网络的股份细分，与股份总数有关。
* **[!UICONTROL Sharing rate]** :此比率表示与要传送的消息数有关的每个社交网络的共享细分。

在该列 **[!UICONTROL Opens]** 中，我们有以下指示器：

* **[!UICONTROL No. of opens]** :被转发给的人（通过个性化块）所打开的消 **[!UICONTROL Links for sharing to social networks]** 息总数。 此值等于显示镜像页面的次数。 不会考虑交付收件人打开的问题。
* **[!UICONTROL Breakdown]** :此比率表示每个社交网络的打开次数与打开总数的关系。
* **[!UICONTROL Rate of opens]** :此比率表示每个社交网络的打开次数与共享总数的关系。

**[!UICONTROL Breakdown of sharing activities and opens]**

本节包括两个图表，它们表示共享活动的细分，并按社交网络打开。

## 关于共享活动的统计数据 {#statistics-on-sharing-activities}

此报告显示了社交网络（Facebook、Twitter、电子邮件等）的共享演变时间。

For more information on viral marketing, refer to [this section](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

统计信息以值表和图表的形式显示。

使用以下指示符：

* **[!UICONTROL New contacts]** :收到通过电子邮件共享的消息后新订阅的数量。 此值与收到通过电子邮件共享的消息、单击该消息并填写订阅表 **[!UICONTROL Subscription link]** 单的人数相匹配。
* **[!UICONTROL Opens]** :消息被传输到的人员（通过个性化块）打开的消 **[!UICONTROL Link for sharing to social networks]** 息总数。 此值等于显示镜像页面的次数。 不会考虑交付收件人打开的问题。
* **[!UICONTROL Sharing activities]** :通过社交网络共享的消息总数。 此值与个性化块图标的总点击 **[!UICONTROL Links for sharing to social networks]** 次数匹配。

## 操作系统 {#operating-systems}

此报告显示交付收件人在有关期间使用的操作系统细分。

>[!NOTE]
>
>本报告所示值为估计：将只考虑已单击传送的收件人。

**全球统计**

操作系统的全局使用统计信息以值表和图表的形式呈现。

![](assets/s_ncs_user_os_report.png)

使用以下指示符：

* **[!UICONTROL Visitors]** :点击交付的目标收件人（每个操作系统）总数的每日平均值，至少一次。
* **[!UICONTROL Pages viewed]** :所有分发的分发链接（每个操作系统）的每日总点击次数平均数。
* **[!UICONTROL Rate of use]** :此比率表示与访客总数相关的访客（每个操作系统）细分。

**每个操作系统的统计数据**

在全局统计信息值表中，单击每个操作系统的名称以查看每个操作系统的统计信息。

![](assets/s_ncs_user_os_report2.png)

统计信息以曲线、图表和值表的形式呈现。

曲 **[!UICONTROL History]** 线表示此操作系统每天的使用率。 此比率是每天（在此操作系统上）访客数与当天访问量最高的访客数之比。

该图 **[!UICONTROL Breakdown by version]** 表表示每个版本的访客与此操作系统上访客总数的关系。

值表使用以下指示器：

* **[!UICONTROL Global rate]** :此比率表示与整个操作系统中的访客总数（每个版本）相关的访客细分。
* **[!UICONTROL Relative rate]** :此比率表示与此操作系统的访客总数相关的访客（每个版本）细分。

## 订阅跟踪 {#subscription-tracking}

通过此报告，您可以监视对信息服务的订阅。 它显示订阅和取消订阅。

![](assets/s_ncs_user_services_report.png)

单击主页的节点或资源管理器可 **[!UICONTROL Profiles and targets > Services and subscriptions]** 以显示订阅的订阅。 选择所需的订阅，然后单击选 **[!UICONTROL Reports]** 项卡。 默 **[!UICONTROL Subscriptions tracking]** 认情况下报告可用。 它允许您查看订阅和取消订阅趋势以及一段时间内的忠诚度率。 您可以通过下拉列表配置此数据的表示形式。 单击 **[!UICONTROL Refresh]** 以验证选定的配置。

如需详细信息，请参阅[此页面](../../delivery/using/managing-subscriptions.md)。

它 **[!UICONTROL Number subscribed to date]** 表示当前订阅的总人数。

**[!UICONTROL Overall evolution of subscriptions]**

值表使用以下指示器：

* **[!UICONTROL Subscribers]** :有关期间的订户总数。
* **[!UICONTROL Subscriptions]** :有关期间的订阅数。
* **[!UICONTROL Unsubscriptions]** :有关期间的取消订阅数。
* **[!UICONTROL Evolution]** :取消订阅数减去订阅数。 该速率是根据用户总数计算的。
* **[!UICONTROL Loyalty]** :相关期间的订阅者忠诚度比率。

**[!UICONTROL Subscription evolution curves]**

此图表显示了相关期间订阅和取消订阅的演变。

## 交付统计 {#delivery-statistics}

此报告按Internet域、处理和发送的所有消息、硬弹回、打开次数、单击次数和取消订阅次数显示细分。

![](assets/s_ncs_user_broadcast_report.png)

使用以下指示符：

* **[!UICONTROL Emails processed]** :传送服务器处理的消息总数。
* **[!UICONTROL Delivered]** :成功处理的消息数与已处理消息总数的百分比。
* **[!UICONTROL Hard bounces]** :“硬”弹回数与已处理消息总数的百分比。
* **[!UICONTROL Soft bounces]** :“软”弹回次数与已处理消息总数的百分比。

   >[!NOTE]
   >
   >有关硬弹回和软弹回的详细信息，请参阅 [隔离管理](../../delivery/using/understanding-quarantine-management.md)。

* **[!UICONTROL Opens]** :至少打开一次消息的目标收件人数与成功处理的消息数的百分比。
* **[!UICONTROL Clicks]** :与成功处理的消息数相比，至少单击一次分发的人数百分比。
* **[!UICONTROL Unsubscription]** :取消订阅链接上的点击次数与成功处理的消息数的百分比。

## 打开次数细分 {#breakdown-of-opens}

此报告按操作系统、设备和浏览器显示有关期间的打开情况细分。 对于每个类别，使用两个图表。 第一个显示有关计算机和移动设备上打开情况的统计信息。 第二个显示仅与移动设备上的打开有关的统计信息。

打开次数与已打开的消息总数相对应。 不会计算文本格式电子邮件。 有关“跟踪”打开的详细信息，请参阅“跟 [踪打开](#tracking-opens-) ”部分。

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>浏览器和操作系统名称构成浏览器用户代理发送的已打开指甲的信息的一部分。 Adobe Campaign使用设备信息推断出设备类型。