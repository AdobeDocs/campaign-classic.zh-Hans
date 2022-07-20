---
product: campaign
title: 数据库清理工作流
description: 了解如何自动清理过时的数据
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 56e9fcc4240649f53239b12f1390dea041602e79
workflow-type: tm+mt
source-wordcount: '2823'
ht-degree: 0%

---

# 数据库清理工作流{#database-cleanup-workflow}

![](../../assets/v7-only.svg)

## 简介 {#introduction}

的 **[!UICONTROL Database cleanup]** 可通过 **[!UICONTROL Administration > Production > Technical workflows]** 节点，用于删除过时的数据以避免数据库的指数增长。 工作流会自动触发，无需用户干预。

![cleanup](assets/ncs_cleanup_workflow.png)

## 配置 {#configuration}

数据库清理在两个级别上配置：在工作流计划程序和部署向导中。

### 工作流调度程序 {#the-scheduler}

>[!NOTE]
>
>有关调度程序的详细信息，请参阅 [此部分](../../workflow/using/scheduler.md).

默认情况下， **[!UICONTROL Database cleanup]** 工作流配置为每天凌晨4点启动。 调度程序允许您更改工作流触发频率。 可用频率如下：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![调度程序](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>为了 **[!UICONTROL Database cleanup]** 工作流要在调度程序中定义的日期和时间启动，必须启动工作流引擎(wfserver)。

### 部署向导 {#deployment-wizard}

的 **[!UICONTROL Deployment wizard]**，通过 **[!UICONTROL Tools > Advanced]** 菜单，可配置保存数据的时长。 值以天表示。 如果没有更改这些值，工作流将使用默认值。

![](assets/ncs_cleanup_deployment-wizard.png)

的字段 **[!UICONTROL Purge of data]** 窗口与以下选项一致。 这些任务将由执行的某些任务使用 **[!UICONTROL Database cleanup]** 工作流：

* 整合的跟踪： **NmsCleanup_TrackingStatPurgeDelay** (请参阅 [清理跟踪日志](#cleanup-of-tracking-logs))
* 投放日志： **NmsCleanup_BroadLogPurgeDelay** (请参阅 [清理投放日志](#cleanup-of-delivery-logs))
* 跟踪日志： **NmsCleanup_TrackingLogPurgeDelay** (请参阅 [清理跟踪日志](#cleanup-of-tracking-logs))
* 已删除的投放： **NmsCleanup_RecycledDeliveryPurgeDelay** (请参阅 [清理要删除或回收的投放](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 导入拒绝： **NmsCleanup_RejectsPurgeDelay** (请参阅 [清除导入生成的拒绝](#cleanup-of-rejects-generated-by-imports-))
* 访客配置文件： **NmsCleanup_VisitorPurgeDelay** (请参阅 [清理访客](#cleanup-of-visitors))
* 提供建议： **NmsCleanup_CompationPurgeDelay** (请参阅 [清理命题](#cleanup-of-propositions))

   >[!NOTE]
   >
   >的 **[!UICONTROL Offer propositions]** 字段 **互动** 已安装模块。

* 事件： **NmsCleanup_EventPurgeDelay** (请参阅 [清理过期事件](#cleansing-expired-events))
* 存档事件： **NmsCleanup_EventHistoPurgeDelay** (请参阅 [清理过期事件](#cleansing-expired-events))

   >[!NOTE]
   >
   >的 **[!UICONTROL Events]** 和 **[!UICONTROL Archived events]** 字段仅在 **消息中心** 已安装模块。

* 审核跟踪： **XtkCleanup_AuditTrailPurgeDelay** (请参阅 [清理审核跟踪](#cleanup-of-audit-trail))

执行的所有任务 **[!UICONTROL Database cleanup]** 以下部分介绍了工作流。

## 由数据库清理工作流执行的任务 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流计划程序中定义的日期和时间(请参阅 [调度程序](#the-scheduler))，工作流引擎将启动数据库清理进程。 数据库清理连接到数据库，并按照如下所示的顺序执行任务。

>[!IMPORTANT]
>
>如果其中一个任务失败，则不会执行下一个任务。
>
>SQL查询 **限制** 属性会重复执行，直到所有信息都被处理。


### 要删除清理的列表 {#lists-to-delete-cleanup}

由执行的第一个任务 **[!UICONTROL Database cleanup]** 工作流删除 **deleteStatus != 0** 属性 **NmsGroup**. 链接到这些组的记录以及存在于其他表中的记录也会被删除。

1. 将使用以下SQL查询恢复要删除的列表：

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每个列表都有多个指向其他表的链接。 使用以下查询批量删除所有这些链接：

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   where `$(relatedTable)` 是与 **NmsGroup** 和 `$(l)` 是列表标识符。

1. 当该列表为“List”类型列表时，将使用以下查询删除关联的表：

   ```sql
   DROP TABLE grp$(l)
   ```

1. 每 **选择** 使用以下查询删除操作恢复的类型列表：

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   where `$(l)` 是列表标识符

### 清理要删除或回收的投放 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任务会清除所有要删除或回收的投放。

1. 的 **[!UICONTROL Database cleanup]** 工作流会选择其 **deleteStatus** 字段的值 **[!UICONTROL Yes]** 或 **[!UICONTROL Recycled]** 且其删除日期早于 **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**)字段。 有关更多信息，请参阅 [部署向导](#deployment-wizard). 此时段是相对于当前服务器日期计算的。
1. 对于每个中间源服务器，任务会选择要删除的投放列表。
1. 的 **[!UICONTROL Database cleanup]** 工作流会删除投放日志、附件、镜像页面信息和所有其他相关数据。
1. 在删除永久投放之前，工作流会从下表中清除链接的信息：

   * 在投放排除表(**NmsDlvExclusion**)，则会使用以下查询：

      ```sql
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      where **$(l)** 是投放的标识符。

   * 在优惠券表(**NmsCouponValue**)，则会使用以下查询（包含批量删除）：

      ```sql
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      where `$(l)` 是投放的标识符。

   * 在投放日志表(**NmsBroadlogXxx**)，则批量删除会以20,000条记录的批次执行。
   * 在优惠建议表(**NmsCampationXxx**)，则批量删除会以20,000条记录的批次执行。
   * 在跟踪日志表(**NmsTrackinglogXxx**)，则批量删除会以20,000条记录的批次执行。
   * 在投放片段表(**NmsDeliveryPart**)，则批量删除会以500,000条记录的批次执行。 此表包含有关要投放的其余消息的个性化信息。
   * 在镜像页面数据片段表中(**NmsMirrorPageInfo**)，则批量删除会以20,000条记录的批次执行，以获取过期的提交部件以及已完成或已取消的部件。 此表包含有关用于生成镜像页面的所有消息的个性化信息。
   * 在镜像页面搜索表(**NmsMirrorPageSearch**)，则批量删除会以20,000条记录的批次执行。 此表是一个搜索索引，用于访问存储在 **NmsMirrorPageInfo** 表。
   * 在批处理日志表中(**XtkJobLog**)，则批量删除会以20,000条记录的批次执行。 此表包含要删除的投放日志。
   * 在投放URL跟踪表中(**NmsTrackingUrl**)，则会使用以下查询：

      ```sql
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      where `$(l)` 是投放的标识符。

      此表包含在要删除的投放中找到的URL，以启用其跟踪。

1. 将从投放表格(**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   where `$(l)` 是投放的标识符。

#### 使用中间源的投放 {#deliveries-using-mid-sourcing}

的 **[!UICONTROL Database cleanup]** 工作流还会删除中间源服务器上的投放。

1. 为此，工作流会检查每个投放是否处于非活动状态（根据其状态）。 如果投放处于活动状态，则会在删除之前停止该投放。 通过执行以下查询来执行检查：

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   where **$(l)** 是投放的标识符。

1. 如果状态的值为 **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** 或 **[!UICONTROL Paused]** （值51、55、61、62、71、72、75），停止投放并清除链接信息。

### 清理过期的投放 {#cleanup-of-expired-deliveries}

此任务会停止有效期已过期的投放。

1. 的 **[!UICONTROL Database cleanup]** 工作流会创建已过期的投放列表。 此列表包含状态不为 **[!UICONTROL Finished]** ，以及最近停止的包含超过10,000条未处理消息的投放。 使用以下查询：

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   where `delivery mode 1` 匹配 **[!UICONTROL Mass delivery]** 模式， `state 51` 匹配 **[!UICONTROL Start pending]** 州， `state 85` 匹配 **[!UICONTROL Stopped]** 状态，且投放服务器上批量更新的投放日志的最大数量等于10,000。

1. 然后，该工作流包含使用中间源的最近过期投放的列表。 尚未通过中间源服务器恢复投放日志的投放将被排除。

   使用以下查询：

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 以下查询用于检测外部帐户是否仍处于活动状态，以便按日期筛选投放：

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在已过期投放的列表中，状态为 **[!UICONTROL Pending]** ，切换到 **[!UICONTROL Delivery cancelled]** ，且此列表中的所有投放将切换为 **[!UICONTROL Finished]** .

   使用以下查询：

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   where `$(curdate)`是数据库服务器的当前日期， `$(bl)` 是投放日志消息的标识符， `$(dl)` 是投放标识符， `delivery status 6` 匹配 **[!UICONTROL Pending]** 状态和 `delivery status 7` 匹配 **[!UICONTROL Delivery cancelled]** 状态。

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   where `delivery state 95` 匹配 **[!UICONTROL Finished]** 状态和 `$(dl)` 是投放的标识符。

1. 所有片段(**deliveryParts**)，并删除正在进行的通知投放的所有过时片段。 批量删除功能同时适用于这两个任务。

   使用以下查询：

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   where `delivery state 95` 匹配 **[!UICONTROL Finished]** 状态， `delivery state 85` 匹配 **[!UICONTROL Stopped]** 状态和 `$(curDate)` 是当前服务器日期。

### 清理镜像页面 {#cleanup-of-mirror-pages}

此任务会删除投放使用的Web资源（镜像页面）。

1. 首先，使用以下查询恢复要清除的投放列表：

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   where `$(curDate)` 是当前服务器日期。

1. 的 **NmsMirrorPageInfo** 然后，如果需要，使用先前恢复的投放的标识符清除表。 批量删除用于生成以下查询：

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   where `$(dl)` 是投放的标识符。

1. 然后，将条目添加到投放日志。
1. 然后识别已清除的投放，以避免以后必须重新处理它们。 将执行以下查询：

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   where `$(strIn)` 是投放标识符的列表。

### 清理工作表 {#cleanup-of-work-tables}

此任务将从数据库中删除与状态为 **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** 或 **[!UICONTROL Deleted]** .

1. 名称以开头的表列表 **wkDlv_** 将首先通过以下查询(postgresql)恢复：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然后，将排除正在进行的工作流使用的表。 为此，可使用以下查询恢复正在进行的投放列表：

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   where `0` 是与 **[!UICONTROL Being edited]** 投放状态， `85` 匹配 **[!UICONTROL Stopped]** 状态和 `100` 匹配 **[!UICONTROL Deleted]** 状态。

1. 将使用以下查询删除不再使用的表：

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### 清除导入生成的拒绝 {#cleanup-of-rejects-generated-by-imports-}

通过此步骤，您可以删除在导入过程中未处理所有数据的记录。

1. 对 **XtkReject** 表中包含以下查询：

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   where `$(curDate)` 是当前服务器日期，我们从中减去为 **NmsCleanup_RejectsPurgeDelay** 选项(请参阅 [部署向导](#deployment-wizard))和 `$(l)` 是要批量删除的最大记录数。

1. 然后，将使用以下查询删除所有孤立拒绝：

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清理工作流实例 {#cleanup-of-workflow-instances}

此任务使用其标识符清除每个工作流实例(**lWorkflowId**)和历史记录(**lHistory**)。 它通过再次运行工作表清理任务来删除非活动表。 清理还会删除已删除工作流的所有孤立工作表（wkf%和wkfhisto%）。

>[!NOTE]
>
>在 **以天为单位的历史记录** 字段（默认值为30天）。 此字段可在 **执行** 选项卡。 如需详细信息，请参阅[此部分](../../workflow/using/workflow-properties.md#execution)。

1. 要恢复要删除的工作流列表，可使用以下查询：

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查询会生成工作流列表，工作流将使用以下查询删除所有链接的日志、已完成的任务和已完成事件：

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   where `$(lworkflow)` 是工作流的标识符，并且 `$(lhistory)` 是历史记录的标识符。

1. 所有未使用的表都将被删除。 为此，将通过 **wkf%** 使用以下查询键入掩码(postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然后，将排除挂起的工作流实例使用的所有表。 可使用以下查询恢复活动工作流的列表：

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然后，恢复每个工作流标识符，以查找正在进行的工作流所使用的表的名称。 这些名称将从以前恢复的表列表中排除。
1. 使用以下查询排除“增量查询”类型的活动历史记录表：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   where `$(strcondition)` 是与 **wkfhisto%** 蒙版。

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

此任务将删除链接到组的孤立工作表。 的 **NmsGroup** 表存储要清除的组（类型不同于0）。 表名的前缀为 **grp**. 要确定要清理的组，可使用以下查询：

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 清理访客 {#cleanup-of-visitors}

此任务使用批量删除功能从访客表中删除过时的记录。 过时记录是指上次修改时间早于部署向导中定义的保护期的记录(请参阅 [部署向导](#deployment-wizard))。 使用以下查询：

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

where `$(tsDate)` 是当前服务器日期，从中我们减去为 **NmsCleanup_VisitorPurgeDelay** 选项。

### NPAI的清理 {#cleanup-of-npai}

此任务允许您从 **NmsAddress** 表。 以下查询用于执行批量删除：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

where `status 2` 匹配 **[!UICONTROL Valid]** 状态， `$(tsDate1)` 是当前服务器日期，并且 `$(tsDate2)` 匹配 **NmsCleanup_LastCleanup** 选项。

### 清理订阅 {#cleanup-of-subscriptions-}

此任务将从 **NmsSubscription** 表，使用批量删除。 使用以下查询：

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清理跟踪日志 {#cleanup-of-tracking-logs}

此任务从跟踪和Web跟踪日志表中删除过时的记录。 过时记录是指早于部署向导中定义的保护期的记录(请参阅 [部署向导](#deployment-wizard))。

1. 首先，使用以下查询恢复跟踪日志表的列表：

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 批量删除用于清除以前恢复的表列表中的所有表。 使用以下查询：

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   where `$(tsDate)` 是当前服务器日期，我们从中减去为 **NmsCleanup_TrackingLogPurgeDelay** 选项。

1. 使用批量删除功能清除跟踪统计信息表。 使用以下查询：

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   where `$(tsDate)` 是当前服务器日期，我们从中减去为 **NmsCleanup_TrackingStatPurgeDelay** 选项。

### 清理投放日志 {#cleanup-of-delivery-logs}

此任务允许您清除存储在各种表中的投放日志。

1. 为此，可使用以下查询恢复投放日志架构的列表：

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中间源时， **NmsBroadLogMid** 投放映射中未引用表。 的 **nms:broadLogMid** 架构会添加到由上一个查询恢复的列表。
1. 的 **数据库清理** 然后，工作流从以前恢复的表中清除过时的数据。 使用以下查询：

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   where `$(tableName)` 是架构列表中每个表的名称，以及 `$(option)` 是为 **NmsCleanup_BroadLogPurgeDelay** 选项(请参阅 [部署向导](#deployment-wizard))。

1. 最后，工作流检查 **NmsProviderMsgId** 表存在。 如果是，则使用以下查询删除所有过时的数据：

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   where `$(option)` 与为 **NmsCleanup_BroadLogPurgeDelay** 选项(请参阅 [部署向导](#deployment-wizard))。

### 清理NmsEmailErrorStat表 {#cleanup-of-the-nmsemailerrorstat-table-}

此任务会清除 **NmsEmailErrorStat** 表。 主程序(**coalesceErrors**)定义了两个日期：

* **开始日期**:与 **NmsLastErrorStatCoalesce** 选项或表中最近的日期。
* **结束日期**:当前服务器日期。

如果开始日期大于或等于结束日期，则不会进行任何流程。 在本例中， **coalesceUpToDate** 消息。

如果开始日期早于结束日期，则 **NmsEmailErrorStat** 已清理表。

中的错误总数 **NmsEmailErrorStat** 在开始日期和结束日期之间，使用以下查询恢复表：

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

where `$end` 和 `$start` 是先前定义的开始和结束日期。

如果总计大于0:

1. 执行以下查询是为了仅将错误保留在超出特定阈值（等于20）之外：

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. 的 **coalescingErrors** 消息。
1. 将创建新连接，以删除在开始日期和结束日期之间发生的所有错误。 使用以下查询：

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. 每个错误都保存在 **NmsEmailErrorStat** 表：

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   其中每个变量与由上一个查询恢复的值匹配。

1. 的 **开始** 变量将使用上一个进程的值进行更新，以完成循环。

循环和任务停止。

清理在 **NmsEmailError** 和 **cleanupNmsMxDomain** 表格。

### 清除NmsEmailError表 {#cleanup-of-the-nmsemailerror-table-}

使用以下查询：

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询将删除 **NmsEmailErrorStat** 从 **NmsEmailError** 表。

### 清理NmsMxDomain表 {#cleanup-of-the-nmsmxdomain-table-}

使用以下查询：

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询将删除 **NmsEmailErrorStat** 表格 **NmsMxDomain** 表。

### 清理命题 {#cleanup-of-propositions}

如果 **互动** 已安装模块，执行此任务以清除 **NmsCampationXxx** 表格。

通过以下查询，可恢复命题表列表并对每个命题表进行批量删除：

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

where `$(option)` 是为 **NmsCleanup_CompationPurgeDelay** 选项(请参阅 [部署向导](#deployment-wizard))。

### 清理模拟表 {#cleanup-of-simulation-tables}

此任务可清除孤立项模拟表（不再链接到选件模拟或投放模拟）。

1. 要恢复需要清理的模拟列表，请使用以下查询：

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要删除的表的名称由 **wkSimu_** 前缀后跟模拟的标识符(例如： **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### 清理审核跟踪 {#cleanup-of-audit-trail}

使用以下查询：

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

where **$(tsDate)** 是为 **XtkCleanup_AuditTrailPurgeDelay** 选项。

### 清除Nmsaddress {#cleanup-of-nmsaddress}

使用以下查询：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

此查询将删除与iOS和Android相关的所有条目。

### 统计更新和存储优化 {#statistics-update}

的 **XtkCleanup_NoStats** 选项允许您控制清理工作流中存储优化步骤的行为。

如果 **XtkCleanup_NoStats** 选项不存在，或者如果其值为0，则将在PostgreSQL上以详细模式(VAFU VERBOSE ANALYZE)执行存储优化，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 VAVUUM将输出以下格式的行： `INFO: vacuuming "public.nmsactivecontact"` 和分析将输出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`.

如果选项的值为1，则不会在任何数据库上执行统计信息更新。 工作流日志中将显示以下日志行： `Option 'XtkCleanup_NoStats' is set to '1'`.

如果选项的值为2，则将在PostgreSQL上以详细模式(ANALYZE VERBOSE)执行存储分析，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 分析将输出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`.

### 订阅清理(NMAC) {#subscription-cleanup--nmac-}

此任务会删除与已删除的服务或移动设备应用程序相关的所有订阅。

要恢复broadlog架构列表，请使用以下查询：

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

然后，该任务会取回链接到 **appSubscription** 链接并删除这些表。

此清理工作流还会删除自 **NmsCleanup_AppSubscriptionRcpPurgeDelay** 选项。

### 清理会话信息 {#cleansing-session-information}

此任务会清除 **sessionInfo** 表中，将使用以下查询：

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清理过期事件 {#cleansing-expired-events}

此任务可清除在执行实例上接收和存储的事件以及在控制实例上存档的事件。

### 清理反应 {#cleansing-reactions}

此任务可清除反应（表） **NmsRemaMatchRcp**)，其中假设本身已被删除。
