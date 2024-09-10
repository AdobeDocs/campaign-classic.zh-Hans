---
product: campaign
title: 技术工作流
description: 了解有关Campaign Classic包中可用的技术工作流的更多信息
feature: Workflows
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 1%

---

# 技术工作流{#about-technical-workflows}



## 关于技术工作流 {#overview}

此部分中详细介绍的工作流与其他Adobe Campaign内置包一起安装。 这些软件包和相关技术工作流取决于您的许可协议。 [此部分](../../installation/using/installing-campaign-standard-packages.md)中详细介绍了内置包。

默认情况下，技术工作流在以下节点的子文件夹中可用： **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**。

请注意，技术工作流只能由具有管理权限的操作员启动和修改。 有关权限的详细信息，请参阅此[部分](../../platform/using/access-management-groups.md#default-groups)。

>[!NOTE]
>
>默认情况下，**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]**&#x200B;节点中提供了与消息中心模块相关的技术工作流。

有关如何监视技术工作流的详细信息，请参阅[专用部分](monitoring-technical-workflows.md)。

## 技术工作流列表 {#list-technical-workflows}

| 技术工作流 | 包 | 说明 |
|------|--------|-----------|
| **别名清理** (aliasCleansing) | 投放 | 此工作流可标准化枚举值。 默认情况下，此工作流于每日凌晨3点触发。 |
| **帐单** （帐单） | 投放 | 此工作流会通过电子邮件将系统活动报告发送给“billing”操作员。 它在每月25日在营销实例上触发。 |
| **Twitter统计信息的计算** (statsTwitter) | 社交网络（社交营销） — 仅限Campaign v7 | 此工作流用于计算链接到X上的转推和访问(以前称为Twitter)的统计数据。 |
| **营销活动作业** (operationMgt) | 营销活动（营销活动） | 此工作流用于管理营销活动（启动项定位、文件提取等）的作业。 它还创建与循环和定期活动相关的工作流。 |
| **为HeatMap服务** (collectDataHeatMapService)收集数据 | 默认安装 | 此工作流可检索HeatMap服务所需的数据。 |
| **收集隐私请求** (collectPrivacyRequests) | 隐私数据保护条例 | 此工作流会生成存储在Adobe Campaign中的收件人数据，并在隐私请求屏幕中提供下载。 |
| **成本计算** (budgetMgt) | 营销活动（营销活动） | 此工作流可开始计算预算、计划、方案、营销策划、投放和任务中的费用和成本行。 |
| **数据库清理** （清理） | 投放 | 此工作流是数据库维护工作流：它进行的计算与统计和进程不同，并根据部署向导中定义的配置从数据库中删除过时的数据。 默认情况下，此工作流于每日凌晨4点触发。 有关详细信息，请参见[此页面](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic)。 |
| **删除阻止的LINE用户** (deleteBlockedLineUsersV2) | LINE 渠道 | 此工作流可确保在阻止LINE正式帐户180天后，删除LINE V2用户的数据。 |
| **删除隐私请求数据** (deletePrivacyRequestsData) | 隐私数据保护条例 | 此工作流会删除存储在Adobe Campaign中的收件人数据。 |
| **传递指示器** (deliveryIndicators) | 中间源平台 | 此工作流可更新投放的投放跟踪指示器。 默认情况下，此工作流每小时触发一次。 |
| **讨论论坛进程** (newsgroupMgt) | 营销资源(MRM) | 此工作流用于管理来自讨论论坛的通知投放。 在收到批准信号时触发 |
| **分布式营销流程** (centralLocalMgt) | 中央/本地营销（分布式营销） | 此工作流开始处理与使用分布式营销模块相关。 它可启动本地营销策划的创建，并管理与订单和营销策划包可用性相关的通知。 |
| **事件清除** (webAnalyticsPurgeWebEvents) | 网站分析连接器 | 利用此工作流，可根据生命周期字段中配置的时段，从数据库字段删除每个事件。 |
| **将受众导出到Adobe Experience Cloud** (exportSharedAudience) | 与Adobe Experience Cloud集成 | 此工作流可将受众作为共享受众/区段导出。 这些受众可在您使用的其他Adobe Experience Cloud解决方案中使用。 |
| **预测** （预测） | 投放 | 此工作流会分析保存在临时日历中的投放（创建临时日志）。 默认情况下，此工作流于每日凌晨1点触发。 |
| **完全聚合计算（propositionrcp多维数据集）** (agg_nmspropositionrcp_full) | 优惠引擎（交互） | 此工作流可更新优惠建议多维数据集的完全聚合。 默认情况下，此工作流于每日早上6点触发。 此聚合可捕获以下维度：渠道、投放、营销选件和日期。 然后，使用优惠建议多维数据集根据优惠生成报表。 您可以在[本节](../../reporting/using/ac-cubes.md)中了解多维数据集的更多信息。 |
| **已转换联系人的标识** (webAnalyticsFindConverted) | 网站分析连接器 | 此工作流对再营销活动后完成购买的网站访客编制索引。 可以在再营销效率报表中访问通过此工作流恢复的数据（请参阅此页面）。 |
| **从Adobe Experience Cloud导入受众** (importSharedAudience) | 与Adobe Experience Cloud集成 | 利用此工作流，可将不同Adobe Experience Cloud解决方案的受众/区段导入Adobe Campaign。 |
| 营销活动中的投放&#x200B;**作业** (deliveryMgt) | 营销活动（营销活动） | 此工作流会触发批准的投放，并开始后处理外部投放的服务提供程序。 它还会发送批准通知和提醒。 |
| 服务提供者上的&#x200B;**作业** (supplierMgt) | 营销活动（营销活动） | 在投放获得批准后，此工作流将开始处理提供程序（通过电子邮件发送到路由器并进行后处理）。 |
| **LINE V2访问令牌更新** (updateLineV2AccessToken) | LINE渠道 — 仅限Campaign v7 | 此工作流将刷新对LINE V2的访问令牌。 |
| **MID到LineUserID的迁移** (MIDToUserIDMigration) | LINE 渠道 | 此工作流会生成LINE V2用户ID，以便从LINE V1迁移到LINE V2。 |
| **营销资源通知** (assetMgt) | 营销资源(MRM) | 此工作流可管理链接到营销资源审批和发布的通知。 |
| **消息中心&lt;外部帐户名称>** （mcSynch_&lt;外部帐户名称>） | 事务性消息控制（消息中心 — 控制） | 此工作流： <ul><li>恢复操作处理的事件列表。</li><li>与NmsBroadLogMsg表同步，以恢复投放消息资格。</li><li>与NmsBroadLogMsg表的同步完成后，立即恢复事件投放日志。</li><li>与NmsTrackingUrl表同步，以恢复对投放URL的跟踪。</li><li>与NmsTrackingUrl表的同步完成后，立即恢复事件跟踪URL。</li><li>用于在发送投放后，每三小时恢复一次所有被隔离的电子邮件地址。</li></ul> |
| **MessageCenter完全聚合计算** (agg_messageCenter_full) | 事务性消息控制（消息中心 — 控制） | 此工作流可更新消息中心多维数据集的完全聚合。 默认情况下，此工作流于每日凌晨3点触发。 此聚合捕获以下维度：渠道、日期、状态和事件类型。 然后，使用消息中心多维数据集根据事件生成报告。 您可以在[本节](../../reporting/using/ac-cubes.md)中了解多维数据集的更多信息 |
| **中间源（投放计数器）** (defaultMidSourcingDlv) | 传输到中间源 | 此工作流收集中间源服务器上投放的计数信息。 计数信息包括常规投放指标，如已发送的投放数量等。 不包括打开等跟踪信息。 默认情况下，每10分钟触发一次。 |
| **中间源（投放日志）** (defaultMidSourcingLog) | 传输到中间源 | 此工作流在中间源服务器上收集投放日志。 默认情况下，每小时触发一次。 |
| **NMAC选择退出管理** (mobileAppOptOutMgt) | 移动应用程序渠道 | 此工作流可更新移动设备上的取消订阅通知。 从凌晨1点到午夜，每6小时触发一次。 有关详细信息，请参阅[此部分](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)。 |
| **优惠通知** (offerMgt) | 投放 | 此工作流可将已批准的优惠以及优惠目录中包含的每个类别部署到在线环境中。 |
| **暂停的工作流清理** (cleanupPausedWorkflows) | 投放 | 此工作流会分析严重性设置为正常的暂停工作流，并在暂停时间过长时触发警告和通知。 一个月后，暂停的技术工作流将无条件停止。 默认情况下，此工作流于每周一凌晨5点触发。 有关详细信息，请参阅[暂停工作流的处理](monitoring-workflow-execution.md#handling-of-paused-workflows)。 |
| **隐私请求清理** (cleanupPrivacyRequests) | 隐私数据保护条例 | 此工作流会清除90天以前的访问请求文件。 |
| **正在处理批次事件** (batchEventsProcessing) | 事务性消息执行（消息中心 — 执行） | 利用此工作流，可在将批量事件与消息模板关联之前将其放入队列中。 |
| **正在处理实时事件** (rtEventsProcessing) | 事务性消息执行（消息中心 — 执行） | 通过此工作流，在将实时事件与消息模板关联之前，您可以先将它们放入队列中。 |
| **建议同步** (propositionSynch) | 使用执行实例控制优惠引擎 | 此工作流在营销实例和用于交互的执行实例之间同步建议。 |
| **恢复Web事件** (webAnalyticsGetWebEvents) | 网站分析连接器 | 每小时，此工作流会下载给定网站上的Internet用户行为区段，将它们放入Adobe Campaign数据库并启动再营销工作流。 |
| **报告聚合** (reportingAggregates) | 投放 | 此工作流可更新报告中使用的聚合。 默认情况下，此工作流于每日凌晨2点触发。 |
| **发送指标和营销活动属性** (webAnalyticsSendMetrics) | 网站分析连接器 | 此工作流可让您通过Adobe® Analytics连接器，将电子邮件营销活动指标从Adobe Campaign发送到Adobe Experience Cloud套件。 相关指示器如下所示： Sent (iSent)、打开总数(iTotalRecipientOpen)、点击的收件人总数(iTotalRecipientClick)、错误(iError)、选择退出（选择退出）(iOptOut)。 |
| **Stock：订单和警报** (stockMgt) | 营销活动（营销活动） | 此工作流可启动订单行上的库存计算，并管理警告警报阈值。 |
| **同步Facebook粉丝** (syncFacebookFans) | 社交网络（社交营销） — 仅限Campaign v7 | 此工作流可在每天早上7点将Facebook粉丝导入Adobe Campaign。 |
| **同步Facebook页面** (syncFacebook) | 社交网络（社交营销） — 仅限Campaign v7 | 此工作流每天早上7:00与Adobe Campaign同步Facebook页面。 |
| **同步Twitter页面** (syncTwitter) | 社交网络（社交营销） — 仅限Campaign v7 | 此工作流每天早上7:00将X关注者导入Adobe Campaign。 |
| **任务通知** (taskMgt) | 营销资源(MRM) — 仅限Campaign v7 | 利用此工作流，可发送与营销活动中的任务相关的通知消息。 |
| **跟踪** （跟踪） | 投放 | 此工作流执行跟踪信息的恢复和整合。 它还确保重新计算跟踪和投放统计数据，特别是消息中心归档工作流使用的统计数据。 默认情况下，每小时触发一次。 |
| **更新事件状态** (updateEventsStatus) | 事务性消息执行（消息中心 — 执行） | 利用此工作流，可为事件分配状态。 事件状态如下：<ul><li>挂起：事件在队列中。 尚未为其关联任何消息模板。</li><li>待处理投放：事件处于队列中，已关联消息模板且投放当前正在处理该模板。</li><li>已发送：此状态复制于投放日志。 这意味着投放已发送。</li><li>被投放忽略：此状态复制于投放日志。 这意味着该投放已被忽略。</li><li>投放错误：此状态复制于投放日志。 这意味着投放已失败。</li><li>事件未被覆盖：该事件未能与消息模板相关联。 将不会重新处理该事件。</li></ul> |
| **刷新可投放性** (deliverabilityUpdate) | 投放 | 此工作流每夜运行并管理退回电子邮件资格规则以及域和MX的列表。 这要求在平台上打开HTTPS端口。 |