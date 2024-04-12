---
product: campaign
title: 数据库清理工作流
description: 了解如何自动清理过时的数据
feature: Monitoring, Workflows
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2827'
ht-degree: 0%

---

# 数据库清理工作流{#database-cleanup-workflow}



## 简介 {#introduction}

此 **[!UICONTROL Database cleanup]** 工作流可通过以下网址访问： **[!UICONTROL Administration > Production > Technical workflows]** 节点，用于删除过时的数据，以避免数据库呈指数增长。 工作流将自动触发，无需用户干预。

![cleanup](assets/ncs_cleanup_workflow.png)

## 配置 {#configuration}

数据库清理可在两个级别上配置：在工作流计划程序中，以及在部署向导中。

### 工作流计划程序 {#the-scheduler}

>[!NOTE]
>
>有关调度程序的详细信息，请参阅 [本节](../../workflow/using/scheduler.md).

默认情况下， **[!UICONTROL Database cleanup]** 工作流配置为每天凌晨4点启动。 调度程序允许您更改工作流触发频率。 可以使用以下频率：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![调度程序](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>为了 **[!UICONTROL Database cleanup]** 工作流要在计划程序中定义的日期和时间启动，必须启动工作流引擎(wfserver)。

### 部署向导 {#deployment-wizard}

此 **[!UICONTROL Deployment wizard]**，访问方式： **[!UICONTROL Tools > Advanced]** 菜单，用于配置保存数据的时间。 值以天为单位表示。 如果未更改这些值，工作流将使用默认值。

![](assets/ncs_cleanup_deployment-wizard.png)

的字段 **[!UICONTROL Purge of data]** 窗口与以下选项一致。 它们由执行的一些任务使用 **[!UICONTROL Database cleanup]** 工作流：

* 整合跟踪： **NmsCleanup_TrackingStatPurgeDelay** (请参阅 [清理跟踪日志](#cleanup-of-tracking-logs))
* 投放日志： **NmsCleanup_BroadLogPurgeDelay** (请参阅 [投放日志清理](#cleanup-of-delivery-logs))
* 跟踪日志： **NmsCleanup_TrackingLogPurgeDelay** (请参阅 [清理跟踪日志](#cleanup-of-tracking-logs))
* 已删除的投放： **NmsCleanup_RecycledDeliveryPurgeDelay** (请参阅 [清理要删除或回收的投放](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 导入拒绝： **NmsCleanup_RejectsPurgeDelay** (请参阅 [清理导入生成的拒绝](#cleanup-of-rejects-generated-by-imports-))
* 访客资料： **NmsCleanup_VisitorPurgeDelay** (请参阅 [访客清理](#cleanup-of-visitors))
* 优惠建议： **NmsCleanup_PropositionPurgeDelay** (请参阅 [建议清理](#cleanup-of-propositions))

  >[!NOTE]
  >
  >此 **[!UICONTROL Offer propositions]** 字段仅在 **互动** 模块已安装。

* 事件： **NmsCleanup_EventPurgeDelay** (请参阅 [清除过期事件](#cleansing-expired-events))
* 已存档事件： **NmsCleanup_EventHistoPurgeDelay** (请参阅 [清除过期事件](#cleansing-expired-events))

  >[!NOTE]
  >
  >此 **[!UICONTROL Events]** 和 **[!UICONTROL Archived events]** 字段仅在 **消息中心** 模块已安装。

* 审核记录： **XtkCleanup_AuditTrailPurgeDelay** (请参阅 [审核记录清理](#cleanup-of-audit-trail))

由执行的所有任务 **[!UICONTROL Database cleanup]** 下节将介绍此工作流。

## 数据库清理工作流执行的任务 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流调度程序中定义的日期和时间(请参阅 [计划程序](#the-scheduler))，工作流引擎将启动数据库清理过程。 数据库清理将连接到数据库并按下面显示的顺序执行任务。

>[!IMPORTANT]
>
>如果其中一个任务失败，则不执行下一个任务。
>
>SQL查询 **限制** 属性会重复执行，直到处理完所有信息为止。


### 要删除清理的列表 {#lists-to-delete-cleanup}

由执行的第一个任务 **[!UICONTROL Database cleanup]** 工作流删除具有以下 **删除状态！= 0** 属性来自 **NmsGroup**. 链接到这些组并存在于其他表中的记录也会被删除。

1. 使用以下SQL查询恢复要删除的列表：

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每个列表都有多个指向其他表的链接。 使用以下查询批量删除所有这些链接：

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   位置 `$(relatedTable)` 是相关表 **NmsGroup** 和 `$(l)` 是列表标识符。

1. 当列表是“列表”类型列表时，将使用以下查询删除关联的表：

   ```sql
   DROP TABLE grp$(l)
   ```

1. 每 **选择** 使用以下查询删除通过操作恢复的类型列表：

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   位置 `$(l)` 是列表标识符

### 清理要删除或回收的投放 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任务会清除要删除或回收的所有投放。

1. 此 **[!UICONTROL Database cleanup]** 工作流选择满足以下条件的所有投放： **deleteStatus** 字段具有值 **[!UICONTROL Yes]** 或 **[!UICONTROL Recycled]** 且其删除日期早于 **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**)字段。 有关详细信息，请参见 [部署向导](#deployment-wizard). 此时间段根据当前服务器日期计算。
1. 对于每个中间源服务器，该任务会选择要删除的投放列表。
1. 此 **[!UICONTROL Database cleanup]** 工作流会删除投放日志、附件、镜像页面信息和所有其他相关数据。
1. 永久删除投放之前，工作流会清除下表中的链接信息：

   * 在投放排除表中(**NmsDlv排除**)，则使用以下查询：

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     位置 **$(l)** 是投放的标识符。

   * 在优惠券表中(**NmsCouponValue**)，则使用以下查询（包含批量删除）：

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     位置 `$(l)` 是投放的标识符。

   * 在投放日志表中(**NmsBroadlogXxx**)，批量删除以20,000条记录的批次执行。
   * 在优惠建议表中(**NmsPropositionXxx**)，批量删除以20,000条记录的批次执行。
   * 在跟踪日志表中(**NmsTrackinglogXxx**)，批量删除以20,000条记录的批次执行。
   * 在投放片段表中(**NmsDeliveryPart**)，批量删除是以500,000条记录的批次执行。 此表包含有关要投放的其余消息的个性化信息。
   * 在镜像页面数据片段表中(**NmsMirrorPageInfo**)，批量删除会以20,000条记录的形式针对过期的投放部分以及已完成或已取消的投放部分执行。 此表包含有关用于生成镜像页面的所有消息的个性化信息。
   * 在镜像页面搜索表中(**NmsMirrorPageSearch**)，批量删除以20,000条记录的批次执行。 此表是一个搜索索引，它提供对存储在中的个性化信息的访问 **NmsMirrorPageInfo** 表格。
   * 在批处理日志表中(**XtkJobLog**)，批量删除以20,000条记录的批次执行。 此表包含要删除的投放的日志。
   * 在投放URL跟踪表中(**NmsTrackingUrl**)，则使用以下查询：

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     位置 `$(l)` 是投放的标识符。

     此表包含在要删除的投放中找到的URL以启用其跟踪。

1. 该投放将从投放表中删除(**NmsDelivery**)：

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   位置 `$(l)` 是投放的标识符。

#### 使用中间源的投放 {#deliveries-using-mid-sourcing}

此 **[!UICONTROL Database cleanup]** 工作流还会删除中间源服务器上的投放。

1. 为此，工作流会检查每个投放是否处于不活动状态（根据其状态）。 如果投放处于活动状态，则会在删除之前将其停止。 通过执行以下查询来执行检查：

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   位置 **$(l)** 是投放的标识符。

1. 如果状态的值为 **[!UICONTROL Start pending]** ， **[!UICONTROL In progress]** ， **[!UICONTROL Recovery pending]** ， **[!UICONTROL Recovery in progress]** ， **[!UICONTROL Pause requested]** ， **[!UICONTROL Pause in progress]** ，或 **[!UICONTROL Paused]** （值为51、55、61、62、71、72、75），停止投放并且任务清除链接的信息。

### 清理过期的投放 {#cleanup-of-expired-deliveries}

此任务将停止有效期已过期的投放。

1. 此 **[!UICONTROL Database cleanup]** 工作流会创建已过期的投放列表。 此列表包含状态不是的所有过期投放 **[!UICONTROL Finished]** 以及最近停止的投放，其中超过10,000条未处理的消息。 使用以下查询：

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   位置 `delivery mode 1` 匹配 **[!UICONTROL Mass delivery]** 模式， `state 51` 匹配 **[!UICONTROL Start pending]** 省/州 `state 85` 匹配 **[!UICONTROL Stopped]** 状态，则投放服务器上批量更新的投放日志的最大数量等于10,000。

1. 然后，该工作流会包含使用中间源的最近过期的投放列表。 将排除尚未通过中间源服务器恢复投放日志的投放。

   使用以下查询：

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 以下查询用于检测外部帐户是否仍处于活动状态，以按日期筛选投放：

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在已过期投放列表中，状态为的投放日志 **[!UICONTROL Pending]** ，切换到 **[!UICONTROL Delivery cancelled]** ，并且此列表中的所有投放都会切换到 **[!UICONTROL Finished]** .

   使用以下查询：

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   位置 `$(curdate)`是数据库服务器的当前日期， `$(bl)` 是投放日志消息的标识符， `$(dl)` 是投放标识符， `delivery status 6` 匹配 **[!UICONTROL Pending]** 状态和 `delivery status 7` 匹配 **[!UICONTROL Delivery cancelled]** 状态。

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   位置 `delivery state 95` 匹配 **[!UICONTROL Finished]** 状态，和 `$(dl)` 是投放的标识符。

1. 所有片段(**deliveryParts**)，并删除正在进行的通知投放的所有过时片段。 批量删除用于这两个任务。

   使用以下查询：

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   位置 `delivery state 95` 匹配 **[!UICONTROL Finished]** 状态， `delivery state 85` 匹配 **[!UICONTROL Stopped]** 状态，和 `$(curDate)` 是当前服务器日期。

### 镜像页面的清理 {#cleanup-of-mirror-pages}

此任务会删除投放使用的Web资源（镜像页面）。

1. 首先，使用以下查询恢复要清除的投放列表：

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   位置 `$(curDate)` 是当前服务器日期。

1. 此 **NmsMirrorPageInfo** 之后，如有必要，使用先前恢复的投放的标识符清除表。 批量删除用于生成以下查询：

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   位置 `$(dl)` 是投放的标识符。

1. 然后，将条目添加到投放日志中。
1. 然后识别清除的投放，以避免以后必须重新处理它们。 执行以下查询：

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   位置 `$(strIn)` 是投放标识符的列表。

### 工作表的清理 {#cleanup-of-work-tables}

此任务从数据库中删除与其状态为的投放匹配的所有工作表 **[!UICONTROL Being edited]** ， **[!UICONTROL Stopped]** 或 **[!UICONTROL Deleted]** .

1. 名称以开头的表的列表 **wkDlv_** 首先使用以下查询(postgresql)恢复：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 随后将排除正在进行的工作流使用的表。 为此，使用以下查询可恢复正在进行的投放列表：

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   位置 `0` 是与 **[!UICONTROL Being edited]** 投放状态， `85` 匹配 **[!UICONTROL Stopped]** 状态和 `100` 匹配 **[!UICONTROL Deleted]** 状态。

1. 将使用以下查询删除不再使用的表：

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### 清理导入生成的拒绝 {#cleanup-of-rejects-generated-by-imports-}

此步骤允许您删除导入期间未处理其所有数据的记录。

1. 对执行批量删除 **XtkReject** 包含以下查询的表：

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   位置 `$(curDate)` 是当前服务器日期，将从此日期减去为定义的期间。 **NmsCleanup_RejectsPurgeDelay** 选项(请参阅 [部署向导](#deployment-wizard))和 `$(l)` 是要成批删除的最大记录数。

1. 然后，使用以下查询删除所有孤立拒绝：

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清理工作流实例 {#cleanup-of-workflow-instances}

此任务使用其标识符(**Workflowid**)和历史记录(**lHistory**)。 它通过再次运行工作表清理任务来删除非活动表。 该清理还会删除已删除工作流的所有孤立的工作表（wkf%和wkfhisto%）。

>[!NOTE]
>
>为中的每个工作流指定历史记录的清除频率 **历史记录（天）** 字段（默认值为30天）。 此字段可在以下位置找到 **执行** 选项卡中列出的工作流属性。 如需详细信息，请参阅[此小节](../../workflow/using/workflow-properties.md#execution)。

1. 要恢复要删除的工作流列表，请使用以下查询：

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查询生成工作流列表，工作流列表将用于使用以下查询删除所有链接的日志、已完成的任务和已完成的事件：

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   位置 `$(lworkflow)` 是工作流的标识符，并且 `$(lhistory)` 是历史记录的标识符。

1. 删除所有未使用的表。 为此，收集所有表格要归功于 **wkf%** 使用以下查询(postgresql)键入蒙版：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然后，将排除挂起工作流实例使用的所有表。 使用以下查询可恢复活动工作流的列表：

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然后，恢复每个工作流标识符以查找正在进行的工作流使用的表的名称。 这些名称将从以前恢复的表列表中排除。
1. 使用以下查询排除“增量查询”类型的活动历史记录表：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   位置 `$(strcondition)` 是与 **wkfhisto%** 面具。

1. 剩余的表将使用以下查询删除：

   ```sql
   DROP TABLE wkf15487_12;
   ```

### 清理工作流登录 {#cleanup-of-workflow-logins}

此任务使用以下查询删除工作流登录：

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 清理孤立工作表 {#cleanup-of-orphan-work-tables}

此任务删除链接到组的孤立工作表。 此 **NmsGroup** 表存储要清理的组（类型不同于0）。 表名的前缀为 **grp**. 要标识要清理的组，请使用以下查询：

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 访客清理 {#cleanup-of-visitors}

此任务使用批量删除从访客表中删除过时的记录。 过时记录是指最后一次修改早于部署向导中定义的保留期的记录(请参阅 [部署向导](#deployment-wizard))。 使用以下查询：

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

位置 `$(tsDate)` 是当前服务器日期，将从当前服务器日期中减去为 **NmsCleanup_VisitorPurgeDelay** 选项。

### NPAI清理 {#cleanup-of-npai}

此任务允许您从 **NmsAddress** 表格。 以下查询用于执行成批删除：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

位置 `status 2` 匹配 **[!UICONTROL Valid]** 状态， `$(tsDate1)` 是当前服务器日期，并且 `$(tsDate2)` 匹配 **NmsCleanup_LastCleanup** 选项。

### 订阅清理 {#cleanup-of-subscriptions-}

此任务会清除用户从 **NmsSubscription** 表，使用批量删除。 使用以下查询：

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清理跟踪日志 {#cleanup-of-tracking-logs}

此任务从跟踪和Web跟踪日志表中删除过时的记录。 过时记录是指早于部署向导中定义的保留期的记录(请参阅 [部署向导](#deployment-wizard))。

1. 首先，使用以下查询恢复跟踪日志表的列表：

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 批量删除用于清除先前恢复的表列表中的所有表。 使用以下查询：

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   位置 `$(tsDate)` 是当前服务器日期，将从此日期减去为定义的期间。 **NmsCleanup_TrackingLogPurgeDelay** 选项。

1. 使用批量删除清除跟踪统计信息表。 使用以下查询：

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   位置 `$(tsDate)` 是当前服务器日期，将从此日期减去为定义的期间。 **NmsCleanup_TrackingStatPurgeDelay** 选项。

### 投放日志清理 {#cleanup-of-delivery-logs}

此任务允许您清除存储在各种表中的投放日志。

1. 为此，使用以下查询可恢复投放日志架构列表：

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中间源时， **NmsBroadLogMid** 表未在投放映射中引用。 此 **nms：broadLogMid** 架构将添加到由上一个查询恢复的列表中。
1. 此 **数据库清理** 然后，工作流会清除先前恢复的表中的过时数据。 使用以下查询：

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   位置 `$(tableName)` 是架构列表中每个表的名称，并且 `$(option)` 是为定义的日期 **NmsCleanup_BroadLogPurgeDelay** 选项(请参阅 [部署向导](#deployment-wizard))。

1. 最后，工作流会检查 **NmsProviderMsgId** 表存在。 如果是，则使用以下查询删除所有过时数据：

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   位置 `$(option)` 匹配为定义的日期 **NmsCleanup_BroadLogPurgeDelay** 选项(请参阅 [部署向导](#deployment-wizard))。

### 清理NmsEmailErrorStat表 {#cleanup-of-the-nmsemailerrorstat-table-}

此任务将清除 **NmsEmailErrorStat** 表格。 主程序(**coalesceErrors**)定义了两个日期：

* **开始日期**：与 **NmsLastErrorStatCoalesce** 选项或表中最近的日期。
* **结束日期**：当前服务器日期。

如果开始日期晚于或等于结束日期，则不会执行任何进程。 在本例中， **coalesceUpToDate** 出现消息。

如果开始日期早于结束日期，则 **NmsEmailErrorStat** 表格已清除。

中的错误总数 **NmsEmailErrorStat** 表在开始日期和结束日期之间使用以下查询恢复：

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

位置 `$end` 和 `$start` 是以前定义的开始日期和结束日期。

如果总计大于0：

1. 执行以下查询以仅保留超过特定阈值（等于20）的错误：

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. 此 **coalescingErrors** 将显示消息。
1. 将创建一个新连接，以删除在开始日期和结束日期之间发生的所有错误。 使用以下查询：

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. 每个错误都保存在中 **NmsEmailErrorStat** 使用以下查询的表：

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   其中每个变量与上一个查询恢复的值匹配。

1. 此 **开始** 变量会使用上一个进程的值更新以完成循环。

循环和任务停止。

清除操作是在 **NmsEmailError** 和 **cleanupNmsMxDomain** 表格。

### 清理NmsEmailError表 {#cleanup-of-the-nmsemailerror-table-}

使用以下查询：

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询将删除 **NmsEmailErrorStat** 从 **NmsEmailError** 表格。

### 清理NmsMxDomain表 {#cleanup-of-the-nmsmxdomain-table-}

使用以下查询：

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询将删除 **NmsEmailErrorStat** 表格来自 **NmsMxDomain** 表格。

### 建议清理 {#cleanup-of-propositions}

如果 **互动** 安装模块后，执行此任务以清除 **NmsPropositionXxx** 表格。

使用以下查询恢复建议表列表并对每个建议表执行批量删除：

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

位置 `$(option)` 是为定义的日期 **NmsCleanup_PropositionPurgeDelay** 选项(请参阅 [部署向导](#deployment-wizard))。

### 模拟表的清理 {#cleanup-of-simulation-tables}

此任务会清除孤立的模拟表（这些表不再链接到优惠模拟或投放模拟）。

1. 要恢复需要清理的模拟列表，请使用以下查询：

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要删除的表的名称由 **西姆岛_** 前缀，后跟模拟的标识符(例如： **wkSimu_456831_aggr**)：

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### 审核记录清理 {#cleanup-of-audit-trail}

使用以下查询：

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

位置 **$(tsDate)** 为定义的期间的当前服务器日期 **XtkCleanup_AuditTrailPurgeDelay** 选项将被减去。

### Nmsaddress的清理 {#cleanup-of-nmsaddress}

使用以下查询：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

此查询删除与iOS和Android相关的所有条目。

### 统计更新和存储优化 {#statistics-update}

此 **XtkCleanup_NoStats** 选项允许您控制清理工作流的存储优化步骤的行为。

如果 **XtkCleanup_NoStats** 选项不存在或其值为0时，将在PostgreSQL上以详细模式执行存储优化(VACUUM VERBOSE ANALYZE)并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 VACUUM将以下列格式输出行： `INFO: vacuuming "public.nmsactivecontact"` 和ANALYZE将以下列格式输出行： `INFO: analyzing "public.nmsactivecontact"`.

如果该选项的值是1，则不会在任何数据库上执行统计信息更新。 以下日志行将显示在工作流日志中： `Option 'XtkCleanup_NoStats' is set to '1'`.

如果选项值为2，这将在PostgreSQL上以详细模式执行存储分析(ANALYZE VERBOSE)，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 ANALYZE将以下列格式输出行： `INFO: analyzing "public.nmsactivecontact"`.

### 订阅清理(NMAC) {#subscription-cleanup--nmac-}

此任务将删除与已删除的服务或移动应用程序相关的任何订阅。

要恢复broadlog模式的列表，请使用以下查询：

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

然后，该任务将恢复链接到 **appSubscription** 链接并删除这些表。

此清理工作流还会删除idisabled = 1且自中设定的时间以来未更新的所有条目 **NmsCleanup_AppSubscriptionRcpPurgeDelay** 选项。

### 清除会话信息 {#cleansing-session-information}

此任务会从 **sessionInfo** 表，使用以下查询：

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清除过期事件 {#cleansing-expired-events}

此任务会清除在执行实例上接收并存储的事件，以及在控制实例上存档的事件。

### 清除反应 {#cleansing-reactions}

此任务清除反应(表 **NmsRemaMatchRcp**)，其中删除了假设本身。
