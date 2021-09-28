---
product: campaign
title: 技术工作流
description: 进一步了解Campaign Classic包中可用的技术工作流。
audience: workflow
content-type: reference
topic-tags: technical-workflows
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 56470602e3acf777d5b00c293060c644c1fbbc37
workflow-type: tm+mt
source-wordcount: '1712'
ht-degree: 3%

---

# 技术工作流{#about-technical-workflows}

![](../../assets/common.svg)

## 关于技术工作流 {#overview}

此部分中详细描述的工作流将随不同的Adobe Campaign内置包一起安装。 这些包及相关的技术工作流取决于您的许可协议。 [此部分](../../installation/using/installing-campaign-standard-packages.md)中详细介绍了内置软件包。

默认情况下，以下节点的子文件夹中提供了技术工作流：**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**。

请注意，只有具有管理权限的运算符才能启动和修改技术工作流。 有关权限的更多信息，请参阅此[部分](../../platform/using/access-management-groups.md#default-groups)。

>[!NOTE]
>
>默认情况下，与消息中心模块相关的技术工作流可在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]**&#x200B;节点中使用。

有关如何监控技术工作流的更多信息，请参阅[专述章节](monitoring-technical-workflows.md)。

## 技术工作流的列表 {#list-technical-workflows}

| 技术工作流 | 包 | 说明 |
|------|--------|-----------|
| **别名清理** （别名清理） | 投放 | 此工作流使枚举值标准化。 默认情况下，此工作流于每日凌晨3点触发。 |
| **帐单** （帐单） | 投放 | 此工作流会通过电子邮件将系统活动报告发送给“billing”操作员。 它于每月25日在营销实例上触发。 |
| **计算Twitter统计** (statsTwitter) | 社交网络（社交营销） — 仅限Campaign v7 | 此工作流会计算与Twitter上的转推和访问次数关联的统计资料。 |
| **促销活动作业** (operationMgt) | 营销活动（营销活动） | 此工作流可管理营销活动的作业（启动项定位、文件提取等）。 它还会创建与定期和定期营销活动相关的工作流。 |
| **为HeatMap服务收集数据** (collectDataHeatMapService) | 默认安装 | 此工作流检索HeatMap服务所需的数据。 |
| **收集隐私请求** (collectPrivacyRequests) | 隐私数据保护规定 | 此工作流会生成存储在Adobe Campaign中的收件人数据，并将其提供在隐私请求屏幕中下载。 |
| **成本计算** (budgetMgt) | 营销活动（营销活动） | 此工作流开始计算预算、计划、项目、营销策划、投放和任务中的费用和成本行。 |
| **数据库清理** （清理） | 投放 | 此工作流是数据库维护工作流：它根据部署助手中定义的配置从数据库中删除过时的数据，从而与统计和进程进行不同的计算。 默认情况下，此工作流于每日凌晨4点触发。 有关详细信息，请参见[此页面](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic)。 |
| **删除阻止的LINE用户** (deleteBlockedLineUsersV2) | LINE 渠道 | 此工作流可确保在LINE V2用户阻止LINE正式帐户180天后删除其数据。 |
| **删除隐私请求数据** (deletePrivacyRequestsData) | 隐私数据保护规定 | 此工作流会删除存储在Adobe Campaign中的收件人数据。 |
| **投放指标** (deliveryIndicators) | 中间源平台 | 此工作流可更新投放的投放跟踪指示器。 默认情况下，此工作流每小时触发一次。 |
| **讨论论坛流程** (newsgroupMgt) | 营销资源(MRM) | 此工作流用于管理论坛中通知的发送。 在收到批准信号时触发 |
| **分布式营销流程** (centralLocalMgt) | 中央/地方营销（分布式营销） | 此工作流会开始处理与使用分布式营销模块相关的问题。 它可启动本地促销活动的创建，并管理与订单和促销活动包可用性相关的通知。 |
| **事件清除** (webAnalyticsPurgeWebEvents) | Web Analytics连接器 | 利用此工作流，可根据在“有效期”(Life)字段中配置的期间，从数据库字段中删除每个事件。 |
| **将受众导出到Adobe Experience Cloud** (exportSharedAudience) | 与Adobe Experience Cloud集成 | 此工作流会将受众导出为共享的受众/区段。 这些受众可在您使用的不同Adobe Experience Cloud解决方案中使用。 |
| **预测** （预测） | 投放 | 此工作流会分析在临时日历中保存的投放（创建临时日志）。 默认情况下，此工作流于每日凌晨1点触发。 |
| **完全聚合计算（propositionrcp多维数据集）** (agg_nmspropositionrcp_full) | 优惠引擎（交互） | 此工作流更新了选件建议多维数据集的完整聚合。 默认情况下，此工作流于每日早上6点触发。 此聚合会捕获以下维度：渠道、投放、营销选件和日期。 然后，使用选件建议多维数据集来根据选件生成报告。 您可以在[此部分](../../reporting/using/about-cubes.md)中了解有关多维数据集的更多信息。 |
| **已转换的联系人的标识** (webAnalyticsFindConverted) | Web Analytics连接器 | 此工作流可为在再营销活动后完成购买的网站访客建立索引。 可通过再营销效率报表访问此工作流取回的数据（请参阅此页面）。 |
| **从Adobe Experience Cloud导入受众** (importSharedAudience) | 与Adobe Experience Cloud集成 | 利用此工作流，可将不同Adobe Experience Cloud解决方案中的受众/区段导入Adobe Campaign。 |
| **营销活动中投放的作业** (deliveryMgt) | 营销活动（营销活动） | 此工作流会触发已批准的投放，并启动外部投放的服务提供商的后处理。 它还会发送批准通知和提醒。 |
| **服务提供商的作业** (supplierMgt) | 营销活动（营销活动） | 在投放获得批准后，此工作流将开始处理提供程序（向路由器发送电子邮件并进行后处理）。 |
| **LINE V2访问令牌更新** (updateLineV2AccessToken) | LINE渠道 — 仅限Campaign v7 | 此工作流将刷新LINE V2的访问令牌。 |
| **MID到LineUserID迁移** (MIDoUserIDMigration) | LINE 渠道 | 此工作流会生成从LINE V1迁移到LINE V2的LINE V2用户ID。 |
| **营销资源通知** (assetMgt) | 营销资源(MRM) | 此工作流可管理链接到营销资源批准和发布的通知。 |
| **消息中 &lt;external_account_name>** 心(mcSynch_&lt;external_account_name>) | 事务型消息控制（消息中心 — 控制） | 此工作流： <ul><li>取回由操作处理的事件列表。</li><li>与NmsBroadLogMsg表同步，以恢复投放消息的资格。</li><li>与NmsBroadLogMsg表同步完成后，立即恢复事件投放日志。</li><li>与NmsTrackingUrl表同步，以便恢复交付URL的跟踪。</li><li>完成与NmsTrackingUrl表的同步后，会立即恢复事件跟踪URL。</li><li>允许您在发送投放后每三小时恢复隔离的所有电子邮件地址。</li></ul> |
| **MessageCenter完整聚合计算** (agg_messageCenter_full) | 事务型消息控制（消息中心 — 控制） | 此工作流更新消息中心多维数据集的完整聚合。 默认情况下，此工作流于每日凌晨3点触发。 此聚合会捕获以下维度：渠道、日期、状态和事件类型。 然后，消息中心多维数据集用于根据事件生成报告。 您可以在[此部分](../../reporting/using/about-cubes.md)中了解有关多维数据集的更多信息 |
| **中间源（投放计数器）** (defaultMidSourcingDlv) | 传输到中间源 | 此工作流会收集中间源服务器上投放的计数信息。 计数信息包括常规投放指示器，如发送的投放数量等。 不包括打开等跟踪信息。 默认情况下，每10分钟触发一次。 |
| **中间源（投放日志）** (defaultMidSourcingLog) | 传输到中间源 | 此工作流在中间源服务器上收集投放日志。 默认情况下，每小时触发一次。 |
| **NMAC选择退出管理** (mobileAppOptOutMgt) | 移动应用程序渠道 | 此工作流可更新移动设备上的取消订阅通知。 从凌晨1点到午夜之间，每6小时触发一次。 有关更多详细信息，请参见[此部分](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)。 |
| **选件通知** (offerMgt) | 投放 | 此工作流会将已批准的选件部署到在线环境，以及选件目录中包含的每个类别。 |
| **暂停的工作流清理** (cleanupPausedWorkflows) | 投放 | 此工作流会分析严重性设置为正常的暂停工作流，并在暂停过长时触发警告和通知。 一个月后，将无条件停止暂停的技术工作流。 默认情况下，此工作流于每周一早上5点触发。 有关更多信息，请参阅[处理暂停的工作流](monitoring-workflow-execution.md#handling-of-paused-workflows)。 |
| **隐私请求清理** (cleanupPrivacyRequests) | 隐私数据保护规定 | 此工作流会清除90天以前的访问请求文件。 |
| **处理批处理事件** (batchEventsProcessing) | 事务型消息执行（消息中心 — 执行） | 利用此工作流，可在将批处理事件与消息模板关联之前，先将它们放入队列中。 |
| **处理实时事件** (rtEventsProcessing) | 事务型消息执行（消息中心 — 执行） | 利用此工作流，可在将实时事件与消息模板关联之前，将它们放入队列中。 |
| **命题同步** （命题同步） | 具有执行实例的优惠引擎控制 | 此工作流可在用于交互的营销实例和执行实例之间同步建议。 |
| **Web事件的恢复** (webAnalyticsGetWebEvents) | Web Analytics连接器 | 此工作流每小时会下载给定网站上Internet用户行为的区段，并将其放入Adobe Campaign数据库并启动再营销工作流。 |
| **报表聚合** (reportingAggregates) | 投放 | 此工作流可更新报表中使用的聚合。 默认情况下，此工作流于每日凌晨2点触发。 |
| **发送指标和促销活动属性** (webAnalyticsSendMetrics) | Web Analytics连接器 | 此工作流允许您通过Analytics®连接器将电子邮件促销活动指示器从Adobe Campaign发送到Adobe Experience Cloud Suite。 相关指标如下：已发送(iSent)、打开总数(iTotalRecipientOpen)、已单击的收件人总数(iTotalRecipientClick)、错误(iError)、选择退出（选择退出）(iOptOut)。 |
| **股票：订单和警报** (stockMgt) | 营销活动（营销活动） | 此工作流会启动订单行上的库存计算并管理警告警报阈值。 |
| **同步Facebook粉丝** (syncFacebookFans) | 社交网络（社交营销） — 仅限Campaign v7 | 此工作流会在每天早上7点将Facebook粉丝导入Adobe Campaign。 |
| **同步Facebook页面** (syncFacebook) | 社交网络（社交营销） — 仅限Campaign v7 | 此工作流于每天早上7点将Facebook页面与Adobe Campaign同步。 |
| **同步Twitter页面** (syncTwitter) | 社交网络（社交营销） — 仅限Campaign v7 | 此工作流会在每天早上7点将Twitter关注者导入Adobe Campaign。 |
| **任务通知** (taskMgt) | 营销资源(MRM) — 仅限Campaign v7 | 利用此工作流，可发送与营销活动中的任务相关的通知消息。 |
| **跟踪** (跟踪 | 投放 | 此工作流可执行跟踪信息的恢复和整合。 它还可确保重新计算跟踪和投放统计信息，特别是消息中心归档工作流使用的跟踪和投放统计信息。 默认情况下，每小时触发一次。 |
| **更新事件状态** (updateEventsStatus) | 事务型消息执行（消息中心 — 执行） | 利用此工作流，可为事件分配状态。 事件状态如下所示：<ul><li>待定：事件在队列中。 尚未关联消息模板。</li><li>待定投放：事件在队列中，消息模板已与其关联，且投放当前正在处理该事件。</li><li>已发送：此状态复制于投放日志。 这意味着投放已发送。</li><li>被投放忽略：此状态复制于投放日志。 这意味着投放已被忽略。</li><li>投放错误：此状态复制于投放日志。 这意味着投放失败。</li><li>未涵盖的事件：事件未能与消息模板关联。 将不会重新处理该事件。</li></ul> |
| **可投放性更新** (deliverabilityUpdate) | 投放 | 安装可投放性监控（电子邮件可投放性）包后，此工作流将在夜间运行，并管理退回电子邮件鉴别规则以及域和MX列表。 这要求在平台上打开HTTPS端口 |