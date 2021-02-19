---
solution: Campaign Classic
product: campaign
title: 技术工作流
description: 进一步了解Campaign Classic包中的技术工作流。
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: f57f52d8807eb771e2416b6648e1d746a206fa96
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 6%

---


# 技术工作流{#about-technical-workflows}

## 关于技术工作流 {#overview}

本节中详细介绍的工作流随不同的Adobe Campaign内置包一起安装。 这些包和相关技术工作流取决于您的许可协议。 内置软件包详见[本节](../../installation/using/installing-campaign-standard-packages.md)。

默认情况下，技术工作流位于以下节点的子文件夹中：**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**。

>[!NOTE]
>
>默认情况下，**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]**&#x200B;节点中提供与消息中心模块相关的技术工作流。

有关如何监视技术工作流的详细信息，请参阅[专用部分](../../workflow/using/monitoring-technical-workflows.md)。

## 技术工作流的列表{#list-technical-workflows}

| 技术工作流 | 包 | 说明 |
|------|--------|-----------|
| **别名清理** （别名清洗） | 投放 | 此工作流程实现了明细列表价值的标准化。 默认情况下，每天凌晨3点触发。 |
| **帐单** （帐单） | 投放 | 此工作流通过电子邮件将系统活动报告发送给“付费”操作员。 默认情况下每月25日触发。 |
| **计算Twitter统计信息** （统计信息Twitter） | 社交网络（社交营销） | 此工作流会计算与Twitter上的转推和访问关联的统计信息。 |
| **活动作业** (operationMgt) | 营销活动(活动) | 此工作流管理营销活动(启动项定位、文件提取等)的作业。 它还创建与循环和周期活动相关的工作流。 |
| **为HeatMap服务收集数据** (collectDataHeatMapService) | 默认安装 | 此工作流检索HeatMap服务所需的数据。 |
| **收集隐私请求** (collectPrivacyRequests) | 隐私数据保护规定 | 此工作流会生成存储在Adobe Campaign中的收件人数据，并使其可在隐私请求的屏幕中进行下载。 |
| **成本计算** (budgetMgt) | 营销活动(活动) | 此工作流开始了预算、计划、项目、活动、投放和任务中费用和成本行的计算。 |
| **数据库清理** （清理） | 投放 | 此工作流是数据库维护工作流：它根据部署助手中定义的配置从数据库中删除过时的数据，从而与统计数据和进程进行不同的计算。 默认情况下，每天凌晨4点触发。 有关详细信息，请参见[此页面](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic)。 |
| **删除阻止的LINE** 用户(deleteBlockedLineUsersV2) | LINE 渠道 | 此工作流确保在LINE V2用户阻止LINE官方帐户180天后删除他们的数据。 |
| **删除隐私请求数据** (deletePrivacyRequestsData) | 隐私数据保护规定 | 此工作流将删除收件人存储在Adobe Campaign中的数据。 |
| **投放指示器** (deliveryIndicators) | 中间源平台 | 此工作流更新投放的投放跟踪指示器。 默认情况下，每小时触发一次此工作流。 |
| **讨论论坛流程** (newsgroupMgt) | 营销资源语(MRM) | 此工作流管理来自论坛的通知的投放。 当收到批准信号时触发 |
| **分布式营销流程** (centralLocalMgt) | 中央/本地营销(分布式营销) | 此工作流将处理与使用分布式营销模块相关的开始。 它启动本地活动的创建并管理与订单和活动包可用性相关的通知。 |
| **事件清除** (webAnalyticsPurgeWebEvents) | Web分析连接器 | 通过此工作流，您可以根据在“寿命”字段中配置的期间从数据库字段中删除每个事件。 |
| **将受众导出到Adobe Experience Cloud** (exportSharedAudience) | 与Adobe Experience Cloud集成 | 此工作流将受众导出为共享受众/区段。 这些受众可用于您使用的不同Adobe Experience Cloud解决方案。 |
| **预测** （预测） | 投放 | 此工作流会分析保存在临时日历中的投放（创建临时日志）。 默认情况下，每天凌晨1点触发。 |
| **完整聚合计算(propositionrcp多维数据集)** (agg_nmspropositionrcp_full) | 优惠引擎（交互） | 此工作流会更新优惠建议多维数据集的完整聚合。 默认情况下，每天早上6点触发。 此聚合捕获以下维：渠道、投放、营销优惠和日期。 然后，优惠建议多维数据集用于生成基于优惠的报表。 您可以在[本节](../../reporting/using/about-cubes.md)中进一步了解多维数据集。 |
| **已转换联系人的标** 识(webAnalyticsFindConverted) | Web分析连接器 | 此工作流对在再营销活动后完成购买的站点访客进行索引。 此工作流恢复的数据可在再营销效率报表中访问（请参阅此页）。 |
| **从Adobe Experience Cloud导入受众** (importSharedAudience) | 与Adobe Experience Cloud集成 | 此工作流允许您将不同Adobe Experience Cloud解决方案中的受众/区段导入Adobe Campaign。 |
| **活动中投放的作业** (deliveryMgt) | 营销活动(活动) | 此工作流会触发已批准的投放和开始对外部投放的服务提供商进行后处理。 它还会发送批准通知和提醒。 |
| **服务提供商上的任** 务(supplierMgt) | 营销活动(活动) | 批准投放后，此工作流将开始处理提供商（向路由器发送电子邮件并进行后处理）。 |
| **LINE V2访问令牌更新** (updateLineV2AccessToken) | LINE 渠道 | 此工作流将访问令牌刷新为LINE V2。 |
| **MID到LineUserID迁移** (MIDToUserIDMigration) | LINE 渠道 | 此工作流生成LINE V2用户ID，用于从LINE V1迁移到LINE V2。 |
| **营销资源通知** (assetMgt) | 营销资源语(MRM) | 此工作流管理链接到营销资源审批和发布的通知。 |
| **消息中 &lt;external_account_name>** 心(mcSynch_&lt;external_account_name>) | 事务性消息控制（消息中心 — 控制） | 此工作流： <ul><li>恢复由操作处理的事件的列表。</li><li>与NmsBroadLogMsg表同步以恢复投放消息资格。</li><li>一旦完成与NmsBroadLogMsg表的同步，将恢复事件投放日志。</li><li>与NmsTrackingUrl表同步，以恢复对投放URL的跟踪。</li><li>完成与NmsTrackingUrl表的同步后，立即恢复事件跟踪URL。</li><li>允许您在发送投放后每三小时恢复放入隔离的所有电子邮件地址。</li></ul> |
| **MessageCenter完整聚合计算** (agg_messageCenter_full) | 事务性消息控制（消息中心 — 控制） | 此工作流将更新“消息中心”多维数据集的“完整聚合”。 默认情况下，每天凌晨3点触发。 此聚合捕获以下维：渠道、日期、状态和事件类型。 然后，消息中心多维数据集用于根据事件生成报表。 您可以在[本节](../../reporting/using/about-cubes.md)中进一步了解多维数据集 |
| **中间源(投放计数器** )(defaultMidSourcingDlv) | 传输到中间源 | 此工作流收集中间源服务器上投放的计数信息。 计数信息包括一般投放指示器，如发送的投放数等。 不包括打开等跟踪信息。 默认情况下，每10分钟触发一次。 |
| **中间源(投放日志)** (defaultMidSourcingLog) | 传输到中间源 | 此工作流会收集中间源服务器上的投放日志。 默认情况下，每小时触发一次。 |
| **NMAC退出管理** (mobileAppOptOutMgt) | 移动应用程序渠道 | 此工作流更新移动设备上的通知退订。 每6小时从凌晨1点到午夜触发一次。 有关详细信息，请参阅[此部分](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)。 |
| **有效账单用户档案数** (billingActiveContactCount) | 投放 | 此工作流会计算活动用户档案的数量。 默认情况下，每晚1点触发。 “用户档案”是指代表最终客户或潜在客户的信息记录（例如 nmsRecipient 表或外部表中的记录，包含 cookie ID、客户 ID、移动标识符或与特定渠道相关的其他信息）。计费仅涉及“活动”的用户档案。 如果用户档案在过去12个月内通过任何渠道成为目标或传达信息，则用户档案被视为“活动”。 Facebook 和 Twitter 渠道不包含在內。您可从 Administration > Campaign Management > Customer metrics 菜单中获得 Number of active profiles 的概要。 |
| **优惠通知** (offerMgt) | 投放 | 此工作流将经过批准的优惠部署到在线环境以及优惠目录中包含的每个类别上。 |
| **暂停的工作流清理** (cleanupPausedWorkflows) | 投放 | 此工作流会分析严重性设置为正常的已暂停工作流，并在暂停过长时触发警告和通知。 一个月后，暂停的技术工作流将无条件停止。 默认情况下，每周一早上5点触发。 有关详细信息，请参阅[处理暂停的工作流](../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows)。 |
| **隐私请求清理** (cleanupPrivacyRequests) | 隐私数据保护规定 | 此工作流会清除90天以前的访问请求文件。 |
| **处理批次事件** (batchEventsProcessing) | 事务性消息执行（消息中心 — 执行） | 通过此工作流，您可以在将批次事件与消息模板关联之前，将其置于队列中。 |
| **处理实时事件** (rtEventsProcessing) | 事务性消息执行（消息中心 — 执行） | 通过此工作流，您可以在将实时事件与消息模板关联之前，将它们放入队列中。 |
| **命题同步** （命题同步） | 优惠引擎的执行实例控制 | 此工作流将营销实例和用于交互的执行实例之间的建议同步。 |
| **Web事件的恢复** (webAnalyticsGetWebEvents) | Web分析连接器 | 每小时，此工作流都会下载给定站点的Internet用户行为细分，将其放入Adobe Campaign数据库并启动再营销工作流。 |
| **报告聚合** (reportingAggroges) | 投放 | 此工作流更新报表中使用的聚合。 默认情况下，每天凌晨2点触发。 |
| **发送指示符和活动属性** (webAnalyticsSendMetrics) | Web分析连接器 | 通过此工作流，您可以通过Adobe® 活动连接器将电子邮件Genesis指示器从Adobe Campaign发送到Adobe Experience Cloud Suite。 相关指示符如下：已发送(iSent)、打开总数(iTotalRecipientOpen)、单击收件人总数(iTotalRecipientClick)、错误(iError)、退出（选择退出）(iOptOut)。 |
| **股票：订单和警报** (stockMgt) | 营销活动(活动) | 此工作流将启动订单行上的库存计算并管理警告警报阈值。 |
| **同步Facebook粉丝** （syncFacebook粉丝） | 社交网络（社交营销） | 此工作流将Facebook粉丝每天早上7点导入Adobe Campaign。 |
| **同步Facebook页面** (syncFacebook) | 社交网络（社交营销） | 此工作流每天早7点将Facebook页面与Adobe Campaign同步。 |
| **同步Twitter页面** (syncTwitter) | 社交网络（社交营销） | 此工作流每天早上7点将Twitter关注者导入Adobe Campaign。 |
| **任务通知** (taskMgt) | 营销资源语(MRM) | 通过此工作流，您可以发送与营销活动中的任务相关的通知消息。 |
| **跟踪** (跟踪 | 投放 | 此工作流执行跟踪信息的恢复和合并。 它还可以确保重新计算跟踪和投放统计，特别是消息中心归档工作流使用的统计。 默认情况下，每小时触发一次。 |
| **更新事件状态** (updateEventsStatus) | 事务性消息执行（消息中心 — 执行） | 通过此工作流，您可以为事件分配状态。 事件状态如下：<ul><li>待定：事件在队列中。 尚未与其关联消息模板。</li><li>待处理投放:事件在队列中，消息模板已与其关联，当前正由投放处理。</li><li>已发送：此状态将从投放日志中复制。 这意味着投放已发送。</li><li>被投放忽略：此状态将从投放日志中复制。 这意味着投放被忽略了。</li><li>投放错误：此状态将从投放日志中复制。 这意味着投放失败了。</li><li>事件未涵盖：事件未能与消息模板关联。 不会重新处理事件。</li></ul> |
| **可交付性更新** （可交付性更新） | 投放 | 安装“可交付性”监控（“电子邮件可交付性”）包后，此工作流将在夜间运行，并管理弹回的电子邮件资格规则以及域和MX的列表。 这要求在平台上打开HTTPS端口 |
| **更新收件箱渲染的种子网** 络(updateRenderingSeeds) | 收件箱渲染(IR) | 此工作流更新用于收件箱呈现的电子邮件地址，并且仅在HTTPS端口为deliverability.neolane.net打开时才有效。 |
