---
solution: Campaign Classic
product: campaign
title: 全局报告
description: 全局报告
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 2%

---


# 全局报告 {#global-reports}

这些报告涉及整个数据库中数据的活动。 要视图报表仪表板，请转到&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡。

![](assets/s_ncs_user_report_delivery_link.png)

要显示报表，请单击其名称。 默认情况下可使用以下报告：

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>此部分仅显示链接到投放的报表。

* **[!UICONTROL Delivery throughput]** :请参阅 [投放吞吐量](#delivery-throughput)。
* **[!UICONTROL Browsers]** :请参阅 [浏览器](#browsers)。
* **[!UICONTROL Sharing to social networks]** :请参阅 [共享到社交网络](#sharing-to-social-networks)。
* **[!UICONTROL Statistics on sharing activities]** :请参阅 [共享活动统计](#statistics-on-sharing-activities)。
* **[!UICONTROL Operating systems]** :请参阅 [操作系统](#operating-systems)。
* **[!UICONTROL URLs and click streams]** :请参阅 [URL并单击流](../../reporting/using/delivery-reports.md#urls-and-click-streams)。
* **[!UICONTROL Tracking indicators]** :请参阅 [跟踪指示器](../../reporting/using/delivery-reports.md#tracking-indicators)。
* **[!UICONTROL Non-deliverables and bounces]** :请参阅 [非可交付项和弹回](#non-deliverables-and-bounces)。
* **[!UICONTROL User activities]** :请参阅 [用户活动](#user-activities)。
* **[!UICONTROL Subscription tracking]** :请参阅 [订阅跟踪](#subscription-tracking)。
* **[!UICONTROL Delivery summary]** :请参阅 [投放摘要](../../reporting/using/delivery-reports.md#delivery-summary)。
* **[!UICONTROL Delivery statistics]** :请参阅 [投放统计](#delivery-statistics)。
* **[!UICONTROL Breakdown of opens]** :请参阅打 [开的划分](#breakdown-of-opens)。

## 投放吞吐量 {#delivery-throughput}

此报表包含有关给定时间段内整个平台的投放吞吐量的信息。 要测量消息的传送速度，标准是每小时发送的消息数和消息的大小（以位/秒为单位）。 在以下示例中，第一个图以蓝色显示成功的投放，以橙色显示错误投放的数量。

![](assets/s_ncs_user_report_toolbar.png)

您可以通过更改时间刻度来配置显示的值：1小时视图、3小时视图、24小时视图等 单击 **[!UICONTROL Refresh]** 以确认您的选择。

## 用户活动{#user-activities}

此报表以图表形式显示每半小时、小时或一天的打开次数、点击次数和事务处理数的细目。

![](assets/s_ncs_user_user_report.png)

可以使用以下选项：

* **[!UICONTROL Opens]** :已打开邮件的总数。不会考虑文本格式的电子邮件。 有关跟踪打开的详细信息，请参阅[跟踪打开](../../reporting/using/indicator-calculation.md#tracking-opens-)。
* **[!UICONTROL Clicks]** :投放中链接的点击总数。单击退订链接和镜像页面时不考虑在内。
* **[!UICONTROL Transactions]** :接收消息后的事务总数。要考虑事务，必须将事务类型Web跟踪标记插入到匹配的网页中。 Web跟踪配置显示在[此部分](../../configuration/using/about-web-tracking.md)中。

## 无法投放项和退回 {#non-deliverables-and-bounces}

此报告显示非可交付项的细目，以及每个Internet域的弹回细目。

**[!UICONTROL Number of messages processed]**&#x200B;表示投放服务器处理的消息总数。 此值低于某些投放停止或暂停（在服务器处理之前）时要传送的消息数。

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>此报表中显示的错误会触发隔离进程。 有关隔离管理的详细信息，请参阅[隔离管理](../../delivery/using/understanding-quarantine-management.md)。

此报表的第一部分以值表和图表的形式显示非交付项的细分。

对于每个错误类型，我们都有：

* 此类型的错误消息数，
* 此类型错误的消息与出错消息总数的百分比，
* 此类型的错误消息与处理的邮件总数的百分比。

使用以下指示符：

* **[!UICONTROL User unknown]** :在投放过程中生成的错误类型，指示电子邮件地址无效。
* **[!UICONTROL Invalid domain]** :发送投放以指示电子邮件地址的域错误或不存在时生成的错误类型。
* **[!UICONTROL Inbox full]** :在五次投放尝试指示收件人的收件箱包含过多邮件后生成的错误类型。
* **[!UICONTROL Account disabled]** :发送投放以指示地址不再存在时生成的错误类型。
* **[!UICONTROL Rejected]** :当IAP（Internet访问提供程序）拒绝地址时(例如在应用安全规则（防垃圾邮件软件）之后)生成的错误类型。
* **[!UICONTROL Unreachable]** :消息分发字符串中出现的错误类型：SMTP中继事件、域临时不可到达等
* **[!UICONTROL Not connected]** :错误类型，指示收件人的移动电话在发送时已关闭或断开与网络的连接。

   >[!NOTE]
   >
   >此指标仅涉及移动渠道上的投放。 如需详细信息，请参阅[此部分](../../delivery/using/sms-channel.md)。

   单击`[+]`符号可打开值表的每行。 对于每个错误类型，您可以按域显示错误消息的划分。

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

此报告的第二部分以值表和图表的形式显示每个Internet域的错误细分。

对于每个域名，我们都有：

* 此域有错误的消息数，
* 与此域处理的消息总数相比，此域有错误的消息的百分比，
* 此域的错误消息与错误消息总数的百分比。

单击[+]符号可打开值表的每行。 对于每个域类型，您可以按错误类型显示错误消息的划分。

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>此报表中显示的域名在多维数据集级别定义。 要更改这些值，请编辑&#x200B;**[!UICONTROL Delivery logs (broadlogrcp)]**&#x200B;多维数据集。 如需详细信息，请参阅[此部分](../../reporting/using/about-cubes.md)。**[!UICONTROL Others]**&#x200B;类别包含不属于特定类的域名。

## 浏览器 {#browsers}

此报告显示了投放收件人在有关期间使用的Internet浏览器的细目。

>[!NOTE]
>
>此报表中显示的值是估计值：将只考虑单击某个投放的收件人。

**全球统计**

有关浏览器使用的全局统计信息以值表和图表的形式显示。

![](assets/dlv_explorers_report.png)

使用以下指示符：

* **[!UICONTROL Visitors]** :目标收件人（每个Internet浏览器）和已至少单击一次投放的总数。
* **[!UICONTROL Pages viewed]** :所有投放（每个Internet浏览器）中链接的总点击量。
* **[!UICONTROL Usage rate]** :此比率表示访客（每个因特网浏览器）与总访客数的划分。

**每个浏览器的统计信息**

在全局统计值表中，您可以单击每个浏览器名称以视图其使用情况统计。

![](assets/s_ncs_user_explorers_report2.png)

统计数据以曲线、图表和值表的形式呈现。

**[!UICONTROL History]**&#x200B;曲线表示此浏览器每天的出席率。 此比率是每天（在此浏览器上）的访客数与当天以最高出席率测量的访客数的比率。

**[!UICONTROL Breakdown per version]**&#x200B;图表表示与（在此浏览器上）访客总数相比，每个版本的访客细分。

值表使用以下指示符：

* **[!UICONTROL Global rate]** :此比率表示与总访客数（在所有浏览器上）相比，每个版本的访客细分。
* **[!UICONTROL Relative rate]** :此比率表示与总访客数（在此浏览器上）相比，每个版本的访客细分。

### 共享到社交网络{#sharing-to-social-networks}

病毒式营销使投放收件人能够与其联系网络共享信息：他们可以添加指向其用户档案（Facebook、Twitter等）的链接 或者给朋友发个信息。 在该投放内跟踪每个共享和对共享信息的每次访问。 有关病毒式营销的详细信息，请参阅[本节](../../delivery/using/viral-and-social-marketing.md)。

此报告显示每个社交网络（Facebook、Twitter等）的共享和已打开消息的细分 和/或每封电子邮件。

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

在电子邮件投放统计信息中，显示两个值：

* **[!UICONTROL Number of messages to be delivered]** :在投放分析期间处理的邮件总数。
* **[!UICONTROL Number of successful deliveries]** :已成功处理的邮件数。

**[!UICONTROL Sharing activities and mail open statistics]**

中央表格显示有关电子邮件共享和打开情况的统计信息。

在&#x200B;**[!UICONTROL Shares]**&#x200B;列中，我们有以下指示器：

* **[!UICONTROL No. of sharing activities]** :每个社交网络上共享的消息总数。此值等于对匹配的&#x200B;**[!UICONTROL Links for sharing to social networks]**&#x200B;个性化块图标的总点击量。
* **[!UICONTROL Breakdown]** :该比率表示每个社会网络的份额与股份总数的划分。
* **[!UICONTROL Sharing rate]** :该比率表示按社交网络分列的每个共享数，与要传递的消息数有关。

在&#x200B;**[!UICONTROL Opens]**&#x200B;列中，我们有以下指示器：

* **[!UICONTROL No. of opens]** :被转发邮件的人（通过个性化块）打开的 **[!UICONTROL Links for sharing to social networks]** 邮件总数。此值等于显示镜像页面的次数。 未考虑投放收件人打开。
* **[!UICONTROL Breakdown]** :此比率表示每个社交网络的打开次数与打开总数的关系。
* **[!UICONTROL Rate of opens]** :此比率表示每个社交网络的开放次数与总份数的关系。

**[!UICONTROL Breakdown of sharing activities and opens]**

本节包含两个图表，它们表示共享活动的划分，并按社交网络打开。

## 共享活动{#statistics-on-sharing-activities}的统计信息

此报告显示了共享到社交网络（Facebook、Twitter、电子邮件等）的演变 时间。

有关病毒式营销的详细信息，请参阅[本节](../../delivery/using/viral-and-social-marketing.md)。

![](assets/s_ncs_user_social_report2.png)

统计数据以值表和图表的形式显示。

使用以下指示符：

* **[!UICONTROL New contacts]** :接收通过电子邮件共享的消息后新订阅的数量。此值与收到通过电子邮件共享的消息、单击&#x200B;**[!UICONTROL Subscription link]**&#x200B;并填写了订阅表单的人数匹配。
* **[!UICONTROL Opens]** :消息被传输到的人员（通过个性化块）打开的 **[!UICONTROL Link for sharing to social networks]** 消息总数。此值等于显示镜像页面的次数。 未考虑投放收件人打开。
* **[!UICONTROL Sharing activities]** :通过社交网络共享的消息总数。此值与对&#x200B;**[!UICONTROL Links for sharing to social networks]**&#x200B;个性化块图标的总点击量匹配。

## 操作系统 {#operating-systems}

此报告显示了投放收件人在有关期间使用的操作系统的细目。

>[!NOTE]
>
>此报表中显示的值是估计值：将只考虑单击某个投放的收件人。

**全球统计**

操作系统的全局使用统计以值表和图表的形式显示。

![](assets/s_ncs_user_os_report.png)

使用以下指示符：

* **[!UICONTROL Visitors]** :在收件人中至少单击一次的目标投放（每个操作系统）的每日平均数。
* **[!UICONTROL Pages viewed]** :所有投放（每个操作系统）上的点击总数的每日平均值。
* **[!UICONTROL Rate of use]** :此比率表示访客（每个操作系统）与访客总数的划分。

**每个操作系统的统计**

在全局统计信息值表中，单击每个操作系统的名称以视图每个操作系统的统计信息。

![](assets/s_ncs_user_os_report2.png)

统计数据以曲线、图表和值表的形式呈现。

**[!UICONTROL History]**&#x200B;曲线表示此操作系统每天的使用率。 此比率是每天（在此操作系统上）访客数与当日测量的出席率最高的访客数之比。

**[!UICONTROL Breakdown by version]**&#x200B;图表表示每个版本的访客与此操作系统上的访客总数的划分。

值表使用以下指示符：

* **[!UICONTROL Global rate]** :此比率表示访客（每个版本）与整个操作系统中访客总数的细分。
* **[!UICONTROL Relative rate]** :此比率表示与此操作系统的访客总数相关的访客（每个版本）细分。

## 订阅跟踪{#subscription-tracking}

此报表可让您监视订阅与信息服务。 它显示订阅和退订。

![](assets/s_ncs_user_services_report.png)

单击订阅或浏览器的&#x200B;**[!UICONTROL Profiles and targets > Services and subscriptions]**&#x200B;节点可显示主页。 选择所需的订阅，然后单击&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡。 默认情况下，**[!UICONTROL Subscriptions tracking]**&#x200B;报告可用。 它可让您查看订阅和退订趋势以及一段时间内的忠诚度率。 您可以通过下拉列表配置此数据的表示形式。 单击&#x200B;**[!UICONTROL Refresh]**&#x200B;验证所选配置。

如需详细信息，请参阅[此页面](../../delivery/using/managing-subscriptions.md)。

**[!UICONTROL Number subscribed to date]**&#x200B;表示当前订阅的总人数。

**[!UICONTROL Overall evolution of subscriptions]**

值表使用以下指示符：

* **[!UICONTROL Subscribers]** :有关期间的订户总数。
* **[!UICONTROL Subscriptions]** :有关期间的订阅数。
* **[!UICONTROL Unsubscriptions]** :有关期间的退订数。
* **[!UICONTROL Evolution]** :退订数减去订阅数。该速率是根据用户总数计算的。
* **[!UICONTROL Loyalty]** :相关期间的用户忠诚度。

**[!UICONTROL Subscription evolution curves]**

此图表显示了相关时段的订阅和退订的演变。

## 投放统计{#delivery-statistics}

此报表显示按Internet域、处理和发送的所有邮件、硬弹回、打开、点击和退订的细分。

![](assets/s_ncs_user_broadcast_report.png)

使用以下指示符：

* **[!UICONTROL Emails processed]** :由投放服务器处理的消息总数。
* **[!UICONTROL Delivered]** :成功处理的邮件数与处理的邮件总数的百分比。
* **[!UICONTROL Hard bounces]** :“硬”弹回数与处理邮件总数的百分比。
* **[!UICONTROL Soft bounces]** :“软”弹回次数与已处理邮件总数的百分比。

   >[!NOTE]
   >
   >有关硬弹回和软弹回的详细信息，请参阅[隔离管理](../../delivery/using/understanding-quarantine-management.md)。

* **[!UICONTROL Opens]** :至少打开一次消息的目标收件人与成功处理的消息数的百分比。
* **[!UICONTROL Clicks]** :在投放中至少单击一次的人数与成功处理的消息数的百分比。
* **[!UICONTROL Unsubscription]** :与成功处理的消息数相比，退订链接上的点击次数百分比。

## 打开的划分{#breakdown-of-opens}

此报表显示了在相关期间按操作系统、设备和浏览器划分的打开次数。 对于每个类别，使用两个图表。 第一个显示有关在计算机和移动设备上打开的统计信息。 第二个显示仅与移动设备上的打开有关的统计信息。

打开次数与已打开的邮件总数相对应。 不计算文本格式电子邮件。 有关“跟踪”打开的详细信息，请参阅[“跟踪”打开](../../reporting/using/indicator-calculation.md#tracking-opens-)部分。

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>浏览器和操作系统名称构成浏览器用户代理发送的已打开消息的部分信息。 Adobe Campaign利用设备信息推断设备类型。