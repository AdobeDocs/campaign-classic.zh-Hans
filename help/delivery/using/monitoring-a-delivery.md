---
title: 监控投放
seo-title: 监控投放
description: 监控投放
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 51bbf50a1e9b00c25fca8e1e86ca21c314c18313
workflow-type: tm+mt
source-wordcount: '2597'
ht-degree: 2%

---


# 监控投放{#monitoring-a-delivery}

投放 **仪表板** 是监控投放以及发送消息时遇到的最终问题的关键。

**相关主题：**

* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [了解隔离管理](../../delivery/using/understanding-quarantine-management.md)
* [投放最佳实践](../../delivery/using/delivery-best-practices.md)
* [管理投放能力](../../delivery/using/about-deliverability.md)

## 投放仪表板 {#delivery-dashboard}

要视图投放上的信息，请编辑该信息，视图仪表板并单击可用的选项卡。

一旦发送投放，选项卡内容便不再更改。

![](assets/s_ncs_user_del_details.png)

### 投放摘要 {#delivery-summary}

选 **[!UICONTROL Summary]** 项卡包含投放的特性： 投放状态、渠道已使用、发送方信息、主题、执行信息。 有关详细信息，请参 [阅发送的消息数](#number-of-messages-sent)。

通过 **[!UICONTROL reports]** 该链接，您可以查看一组与投放操作相关的报告： 一般投放报告、详细报告、投放报告、失败消息的分发、打开率、点击量和交易等。 此选项卡的内容可以根据您的要求进行配置。 有关更多信息，请参见[此章节](../../reporting/using/delivery-reports.md)。

### 投放日志和历史 {#delivery-logs-and-history}

该选 **[!UICONTROL Delivery]** 项卡提供此投放中发生事件的历史记录。 它包含投放日志，即已发送消息的列表、消息的状态和关联的消息。

对于投放，您只能显示（例如）投放失败或隔离中地址为收件人的。 为此，请单击按 **[!UICONTROL Filters]** 钮并选择 **[!UICONTROL By state]**。 然后在下拉列表中选择状态。

![](assets/s_ncs_user_delivery_delivery_tab.png)

此页上列出了 [各种状态](#delivery-statuses)。

>[!NOTE]
>
>通 **[!UICONTROL Display the mirror page for this message...]** 过链接，您可以在新窗口中视图从列表中选择的投放的内容。 该镜像页面仅适用于已定义HTML内容的投放。 有关此内容的详细信息，请参 [阅生成镜像页面](../../delivery/using/sending-messages.md#generating-the-mirror-page)。

### Tracking logs {#tracking-logs}

该选 **[!UICONTROL Tracking]** 项卡列表此投放的跟踪历史记录。 此选项卡显示所发送邮件的跟踪数据，即所有受Adobe Campaign跟踪的URL。 跟踪数据每小时更新一次。

>[!NOTE]
>
>如果未为投放启用跟踪，则不显示此选项卡。

跟踪配置在投放向导的相应阶段执行。 请参 [阅如何配置跟踪的链接](../../delivery/using/how-to-configure-tracked-links.md)。

**[!UICONTROL Tracking]** 数据在投放报告中解释。 请参阅[此章节](../../reporting/using/delivery-reports.md)。

![](assets/s_ncs_user_delivery_tracking_tab.png)

### 投放审核 {#delivery-audit-}

该选 **[!UICONTROL Audit]** 项卡包含投放日志和与验证相关的所有消息。 通过 **[!UICONTROL Refresh]** 该按钮可更新数据。 使用按 **[!UICONTROL Filters]** 钮可定义数据上的筛选器。

通过特殊图标可识别错误或警告。 请参 [阅分析投放](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

通过 **[!UICONTROL Proofs]** 子选项卡可以视图已发送的验证的列表。

![](assets/s_ncs_user_delivery_log_tab.png)

通过选择要显示的列，可以修改此窗口中显示的 **[!UICONTROL Delivery]** 信 **[!UICONTROL Tracking]** 息（以及选项卡和选项卡的信息）。 为此，请单 **[!UICONTROL Configure list]** 击右下角的图标。 有关配置列表显示的详细信息，请参 [阅此部分](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

### 投放仪表板同步 {#delivery-dashboard-synchronization}

从投放仪表板中，您需要检查已处理的消息和投放日志，以确保已成功发送投放。

某些指示器或状态可能不正确或不是最新，这可以通过以下解决方案解决：

* 如果您的投放状态不正确，请检查是否已为此投放完成所有必要的批准，或者是否正在运行 **[!UICONTROL operationMgt]** 和 **[!UICONTROL deliveryMgt]** 工作流并且没有错误。 这也可能是由于投放在发送实例上使用未配置的关联。
* 如果您的投放指示器仍为零，并且您处于中间源配置中，请检查技术 **[!UICONTROL Mid-sourcing (delivery counters)]** 工作流。 开始它，如果它的状态不 **[!UICONTROL Started]**&#x200B;是。 然后，您可以尝试重新计算指示器，方法是右键单击投放浏览器中的相关Adobe Campaign，然后选择 **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**。 For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* 如果投放计数器与投放不匹配，请尝试重新计算指示器，方法是右键单击Adobe Campaign资源管理器中的相关投放，然后选择 **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** 重新同步。 For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* 如果您的投放计数器不是中间源部署的最新状态，请检查技术工 **[!UICONTROL Mid-Sourcing (Delivery counters)]** 作流是否正在运行。 有关详细信息，请参见此 [ 页面](../../installation/using/mid-sourcing-deployment.md)。

您还可以通过投放仪表板，通过不同的报告跟踪投放。 有关更多信息，请参阅此](../../reporting/using/delivery-reports.md)章节[。

## 性能问题 {#performance-issues}

### 清单 {#checklist-}

如果投放性能不佳，您可以检查：

* **投放的大小**: 大型投放可能需要更长的时间才能完成。 MTA子项配置为处理默认的批大小，这适用于大多数情况，但当投放速度持续变慢时，需要检查该大小。
* **投放的目标**: 投放性能禁止受软跳出错误影响，软跳出错误根据重试配置进行处理。 错误数越多，需要的重试就越多。
* **整个平台负载**: 当发送多个大型投放时，整个平台可能会受到影响。 您还可以检查IP信誉和可交付性问题。 有关此内容的详细信息，请参 [阅Adobe Campaign交付性最佳](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 实践指 [南和本页](../../delivery/using/about-deliverability.md)。

平台和投放库维护也会影响数据发送性能。 有关详细信息，请参见[此页面](../../production/using/database-performances.md)。

### 慢速投放 {#slow-deliveries}

单击该按 **[!UICONTROL Send]** 钮后，投放的时间似乎比往常长。 这可能由不同元素引起：

* 某些电子邮件提供商可能已将您的IP地址添加到阻止列表。 在这种情况下，请检查广告并参 [阅此部分](../../delivery/using/about-deliverability.md)。
* 您的投放可能太大，无法快速处理，高JavaScript个性化可能会发生这种情况，或者如果您的投放重量超过60kbytes。 请参阅Adobe Campaign [投放最佳实践](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html) ，了解内容指南。
* Adobe CampaignMTA中可能已发生限制。 这是由以下原因造成的：

   * 已暂停的消息&#x200B;**[!UICONTROL quotas met]** （消息）: 已满足在活动中定义的声明性MX规则声明的配额。 For more information about this message, refer to [this page](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ). 要进一步了解MX规则，请参 [阅本页](../../delivery/using/technical-recommendations.md#mx-rules)。
   * 已暂停的消息&#x200B;**[!UICONTROL dynamic flow control]** （消息）: 活动MTA在尝试为给定ISP发送消息时遇到错误，这会导致延迟以避免错误密度过大，从而面临潜在阻止列表。

* 系统问题可能会阻止服务器进行交互： 这会减慢整个发送过程。 检查服务器，以确保在获取个性化数据的过程中不存在可能影响活动的内存或资源问题。

### 性能最佳实践 {#best-practices-performance}

* 请勿在实例上使投放处于失败状态，因为这会维护临时表并影响性能。

* 删除不再需要的投放。

* 过去12个月中将从数据库中删除的非活动收件人，以保持地址质量。

* 不要试着计划大投放。 有5-10分钟的时间间隔，可将负载均匀地分布在系统上。 与团队中的其他成员协调投放安排以确保最佳性能。 当营销服务器同时处理许多不同的任务时，它会降低性能。

* 尽可能减少电子邮件的大小。 建议的电子邮件最大大小约为35KB。 电子邮件投放的大小会在发送服务器中生成一定数量的卷。

* 大型投放(如超过100万收件人的投放)需要在发送队列中留出空间。 单单这一点对服务器来说并不是问题，但是，如果与其他许多大型投放一起同时出现，就会引起发送延迟。

* 电子邮件中的个性化会为每个收件人从数据库中提取数据。 如果存在许多个性化元素，则会增加准备投放所需的数据量。

* 索引地址。 要优化应用程序中使用的SQL查询的性能，可以从数据模式的主元素中声明索引。

>[!NOTE]
>
>ISP会在非活动状态持续一段时间后禁用地址。 退回邮件会发送给发送方，以告知他们此新状态。

## 投放状态 {#delivery-statuses}

发送投放时，您可能会在投放仪表板上面临以下状态：

<table> 
 <thead> 
  <tr> 
   <th> 状态<br /> </th> 
   <th> 定义和解决方案<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 不适用<br /> </td> 
   <td> 服务器(MTA)已考虑投放，但未处理。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 由于投放地址出错，该收件人未被发送到该地址。 它已添加到阻止列表、隔离、未提供或重复。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 已发送<br /> </td> 
   <td> 投放已正确发送给消息提供者(但收件人未必收到消息)。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失败<br /> </td> 
   <td> 例如，由于地址无效或收件箱已满，投放无法到达收件人。 它还可以链接到个性化块的问题，因为当模式与投放映射不匹配时，这些数据可能会生成错误。 查看 <a href="#failed-status" target="_blank">失败状态</a><br /> </td> 
  </tr> 
  <tr> 
   <td> 服务提供商考虑<br /> </td> 
   <td> 短信服务提供商收到投放。<br /> </td> 
  </tr> 
  <tr> 
   <td> 在移动设备上接收<br /> </td> 
   <td> 收件人在其移动设备上收到SMS。<br /> </td> 
  </tr> 
  <tr> 
   <td> 待定<br /> </td> 
   <td> 投放已准备好发送，并将由投放服务器(MTA)处理。 请参阅 <a href="#pending-status" target="_blank">待定状态</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放已取消<br /> </td> 
   <td> 投放被操作员取消。<br /> </td> 
  </tr> 
  <tr> 
   <td> 准备<br /> </td> 
   <td> 中间状态仅用于外部连接器，如移动渠道。 它遵循“待定”状态，是将确定以下状态的外部连接器。<br /> </td> 
  </tr> 
  <tr> 
   <td> 发送到服务提供商<br /> </td> 
   <td> 投放已发送到SMS服务提供商，但尚未收到。<br /> </td> 
  </tr> 
 </tbody> 
</table>

要了解如何优化Adobe Campaign电子邮件的可交付性，请参阅Adobe Campaign可 [交付性最佳实践指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) ，以 [及本页](../../delivery/using/about-deliverability.md)。

### 待定状态 {#pending-status}

确认投放后，您可以看到投放的状态为 **[!UICONTROL Pending]**。 此状态意味着执行进程正在等待某些资源的可用性。

状 **[!UICONTROL Pending]** 态可以首先表示投放已计划，并且在指定日期之前一直处于待定状态。 For more on this, refer to the [Delivery scheduling](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) section.

如果投放未发送，且其状态 **[!UICONTROL Pending]**&#x200B;保持不变，则可能是以下结果：

* 在投放服务器上运行模块和进程并管理电子邮件发送的MTA（邮件传输代理）可能尚未启动，或需要重新启动。 要检查此项并在必要时开始模块，请应用以下步骤：

   * 检查您的 `mta@<instance>` 模块是否已在MTA服务器上启动。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * 如果未列出MTA，请使用以下命令开始它：

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >替换 `<INSTANCENAME>` 为实例的名称（生产、开发等）。 实例名称通过配置文件进行标识： `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* 投放可能使用在发送服务器上未配置的关联。 在这种情况下，请检查流量管理(IP关联)的配置，并使用 **[!UICONTROL Managing affinities with IP addresses]** 该字段将投放链接到管理关联的MTA。 For more information on affinities, refer to [this section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* 当投放准备处于挂起状态时，可能运行的活动过多，从而阻止了投放的状态更新。 要解决此问题，请转 **[!UICONTROL Options]** 到并增加值( **[!UICONTROL NmsOperation_LimitConcurrency]** 默认值为10)。 不要运行比分配给此特定选项的值更多的活动。

### 失败状态 {#failed-status}

如果电子邮件投放的状 **[!UICONTROL Failed]**&#x200B;态为，则可以将其链接到个性化块的问题。 例如，个性化块中的模式与投放映射不匹配时，投放会生成错误。

投放日志是了解投放失败原因的关键。 以下是您可以从投放日志中检测到的可能错误：

* 如果收件人消息失败，并显示“不可到达”错误，说明： **编译脚本“content htmlContent”行X时出错：`[table]`未定义。 JavaScript: 评估脚本“content htmlContent**”时出错，此问题的原因几乎始终是HTML中的个性化，它们试图调用尚未在上游定位或投放目标映射中定义或映射的表或字段。

   要更正此问题，需要检查工作流和投放内容，以明确确定尝试调用该表的个性化内容以及是否可以映射该表。 从此处，在HTML中删除对此表的调用或将映射修复到投放将成为解析路径。

* 在中间源部署模型中，投放日志中可能显示以下消息： **在中间来源服务器上调用方法“AppendDeliveryPart”时出错： &#39;与服务器通信错误： 请检查此配置是否正确。 代码HTTP 408“服务暂时不可用”**。

   原因与性能问题有关。 这意味着在将数据发送到中间源服务器之前，营销实例花费了太多时间构建数据。

   为此，我们建议对数据库执行真空并重新索引。 For more information on database maintenance, refer to [this section](../../production/using/recommendations.md).

   您还应使用计划工作流重新启动所有活动，以及所有处于失败状态的工作流。 请参阅[此章节](../../workflow/using/scheduler.md) 。

* 投放失败时，投放日志中可能显示以下错误： **DLV-XXXX准备的消息计数(123)大于要发送的消息数(111)。 请联系支持人员。**

   通常，此错误意味着电子邮件中存在一个个性化字段或块，该字段或块具有多个收件人值。 正在使用个性化块，它正在为特定收件人获取多个记录。

   要解决此问题，请检查所使用的个性化目标，然后检查这些字段中有多个条目的收件人。 在活动之前，您 **[!UICONTROL Deduplication]** 还可以在定位工作流中使用投放活动，以检查一次只有一个个性化字段。 For more information on deduplication, refer to [this page](../../workflow/using/deduplication.md).

* 某些投放可能失败，并显示“不可到达”错误： “入站电子邮件弹回（规则&#39;Auto_replies&#39;已匹配此弹回）。 这意味着投放成功，但Adobe Campaign收到了来自收件人的自动回复(例如，与“Auto_replies”入站电子邮件规则匹配的“Out off”回复)。 Adobe Campaign会忽略自动回复电子邮件，收件人的地址不会发送给隔离。

**相关主题：**

* [投放日志和历史](#delivery-logs-and-history)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [投放失败类型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## Number of messages sent {#number-of-messages-sent}

您可以通过树的节点从投放 **[!UICONTROL Campaign Management > Deliveries]** 列表访问投放。

默认情况下，投放的列表包含在选定节点中创建的投放的名称和状态。 还显示成功发送、处理和发送的消息数。

* 数量与收件人 **[!UICONTROL Messages to send]** 之后和投放之前的目标分析数量相对应。
* 列中的消息数与服 **[!UICONTROL Success]** 务器发送和收件人接收的消息数相对应。
* 消息数 **[!UICONTROL Processed]** 与收到的消息数以及有错误的消息数相对应。

投放仪表板允许您跟踪发送的消息数。

>[!NOTE]
>
>对于大投放，您可能希望更新这些值。 为此，请选择相关投放，然后右键单击它。 选 **[!UICONTROL Action > Recompute delivery and tracking indicators...]** 择，然后使用向导更新此信息。

## 计划投放 {#scheduled-deliveries-}

如果投放未在确切的预定日期执行，则可能与服务器时区之间的差异有关。 中间源实例和生产实例可以位于不同的时区。

例如，如果中间源实例在布里斯班时区，生产实例在达尔文时区，两个时区彼此相距半小时，那么在审计日志中，您会清楚地看到，如果投放在11:56预定生产，则中间预定的同一投放将在12:26，这有半小时的差别。
