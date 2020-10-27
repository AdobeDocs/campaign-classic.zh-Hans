---
title: 数据库清理工作流
description: 了解如何自动清理过时的数据
page-status-flag: never-activated
uuid: a7478641-cdf6-4bd4-9dd7-0c84416c9de6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 6b188d78-abb4-4f03-80b9-051ce960f43c
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '2910'
ht-degree: 0%

---


# 数据库清理工作流{#database-cleanup-workflow}

## 简介 {#introduction}

通过 **[!UICONTROL Database cleanup]** 该节点可访问的 **[!UICONTROL Administration > Production > Technical workflows]** 工作流允许您删除过时的数据，以避免数据库呈指数级增长。 工作流会自动触发，无需用户干预。

![](assets/ncs_cleanup_workflow.png)

## 配置{#configuration}

数据库清理配置在两个级别上：在工作流调度程序和部署向导中。

### 工作流调度程序 {#the-scheduler}

>[!NOTE]
>
>For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

默认情况下，该 **[!UICONTROL Database cleanup]** 工作流配置为每天凌晨4点开始。 该调度程序允许您更改工作流触发频率。 可用频率如下：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>要使工作流 **[!UICONTROL Database cleanup]** 在调度程序中定义的日期和时间开始，必须启动工作流引擎(wfserver)。 如果不是这样，数据库清理直到下次启动工作流引擎才会发生。

### 部署向导 {#deployment-wizard}

通过 **[!UICONTROL Deployment wizard]**&#x200B;菜单访问 **[!UICONTROL Tools > Advanced]** 的数据，可以配置数据的保存时间。 值以天数表示。 如果这些值未更改，工作流将使用默认值。

![](assets/ncs_cleanup_deployment-wizard.png)

窗口的字 **[!UICONTROL Purge of data]** 段与以下选项一致。 这些任务由工作流执行的一些使 **[!UICONTROL Database cleanup]** 用：

* 整合跟踪： **NmsCleanup_TrackingStatPurgeDelay** (请参阅 [跟踪日志清除](#cleanup-of-tracking-logs))
* 投放日志: **NmsCleanup_BroadLogPurgeDelay** (请参 [阅投放日志清除](#cleanup-of-delivery-logs))
* 跟踪日志: **NmsCleanup_TrackingLogPurgeDelay** (请参阅 [跟踪日志清除](#cleanup-of-tracking-logs))
* 已删除投放: **NmsCleanup_RecycledDeliveryPurgeDelay** (请参 [阅清除要删除或回收的投放](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 导入拒绝： **NmsCleanup_RejectsPurgeDelay** (请参 [阅Cleanup of rejects gerated by imports](#cleanup-of-rejects-generated-by-imports-))
* 访客用户档案: **NmsCleanup_VisitorPurgeDelay** (请参 [阅访客清除](#cleanup-of-visitors))
* 优惠建议: **NmsCleanup_CompationPurgeDelay** (请参阅 [命题清除](#cleanup-of-propositions))

   >[!NOTE]
   >
   >该 **[!UICONTROL Offer propositions]** 字段仅在安装交互模 **块时** 可用。

* 事件: **NmsCleanup_EventPurgeDelay** (请参阅 [清理过期事件](#cleansing-expired-events))
* 存档事件: **NmsCleanup_EventHistoPurgeDelay** (请参阅 [清理过期事件](#cleansing-expired-events))

   >[!NOTE]
   >
   >只有 **[!UICONTROL Events]** 安装了 **[!UICONTROL Archived events]** 消息中心模块，才 **能使用** “和”字段。

* 审核跟踪： **XtkCleanup_AuditTrailPurgeDelay** (请参阅 [审核跟踪的清除](#cleanup-of-audit-trail))

工作流执行的所 **[!UICONTROL Database cleanup]** 有任务在以下部分中有介绍。

## 任务由数据库清理工作流执行 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流调度程序中定义的日期和时间(请参 [阅调度程序](#the-scheduler)),工作流引擎将开始数据库清除过程。 数据库清理连接到数据库，并按如下所示的顺序执行任务。

>[!IMPORTANT]
>
>如果其中一个任务失败，则不会执行下列操作。\
>具有LIMIT属性 **的SQL查询** ，将重复执行，直到处理所有信息。

>[!NOTE]
>
>下面描述数据库清理工作流执行的任务的部分是为数据库管理员或熟悉SQL语言的用户保留的。

### 列表删除清除 {#lists-to-delete-cleanup}

工作流执行的第一个任务 **[!UICONTROL Database cleanup]** 将删除具有deleteStatus ！的 **所有组=** NmsGroup的0 **属性**。 链接到这些组的记录以及其他表中存在的记录也会被删除。

1. 将使用以下SQL列表恢复要删除的查询:

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每个列表都有多个指向其他表的链接。 所有这些链接都使用以下查询批量删除：

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   其 **中$(relatedTable** )是与NmsGroup相关的 **表** , **$(l)是列表标识符** 。

1. 当列表为“列表”类型列表时，将使用以下查询删除关联表：

   ```
   DROP TABLE grp$(l)
   ```

1. 操作 **恢复的** “选择类型”列表将使用以下查询删除：

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   其 **中$(l)** 是列表标识符

### 清除要删除或回收的投放 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任务清除所有要删除或回收的投放。

1. 工作 **[!UICONTROL Database cleanup]** 流选择deleteStatus字段具有值 **或删除日** 期早于部署向导(NmsRecycleapun **[!UICONTROL Yes]** _RecycledDelayPurgeDelay)字段中定义的时 **[!UICONTROL Recycled]** 间段的所 **[!UICONTROL Deleted deliveries]******&#x200B;有投放。 For more on this, refer to [Deployment wizard](#deployment-wizard). 此期间是根据当前服务器日期计算的。
1. 对于每个中间源服务器，任务选择要删除的投放的列表。
1. 该工 **[!UICONTROL Database cleanup]** 作流会删除投放日志、附件、镜像页面信息和所有其他相关数据。
1. 在删除投放之前，工作流会从以下表中清除链接信息：

   * 在投放排除表(**NmsDlvExclusion**)中，使用以下查询:

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      其中 **$(l)** 是投放的标识符。

   * 在优惠券表(**NmsCouponValue**)中，使用以下查询（进行批量删除）:

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      其中 **$(l)** 是投放的标识符。

   * 在投放日志表(**NmsBroadlogXxx**)中，成批删除以20,000条记录执行。
   * 在优惠建议表(**NmsCompatitionXxx**)中，成批删除以20,000条记录执行。
   * 在跟踪日志表(**NmsTrackinglogXxx**)中，批量删除以20,000条记录批次执行。
   * 在投放片段表(**NmsDeliveryPart**)中，成批删除以500,000条记录执行。 此表包含有关要传送的其余消息的个性化信息。
   * 在镜像页面数据片段表(**NmsMirrorPageInfo**)中，对过期的投放部件和已完成的或已取消的部件，以20,000条记录的批量方式执行成批删除。 此表包含有关用于生成镜像页面的所有消息的个性化信息。
   * 在镜像页面搜索表(**NmsMirrorPageSearch**)中，成批删除以20,000条记录执行。 此表是一个搜索索引，它提供对存储在NmsMirrorPageInfo表中的个 **性化信息** 的访问。
   * 在批处理日志表(**XtkJobLog**)中，成批删除以20,000条记录进行。 此表包含要删除的投放日志。
   * 在投放URL跟踪表(**NmsTrackingUrl**)中，使用以下查询:

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      其中 **$(l)** 是投放的标识符。

      此表包含在要删除的投放中找到的URL，以启用其跟踪。

1. 投放会从投放表(NmsDelivery ****)中删除：

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   其中 **$(l)** 是投放的标识符。

#### 投放使用中间源 {#deliveries-using-mid-sourcing}

该 **[!UICONTROL Database cleanup]** 工作流还会删除中间源服务器上的投放。

1. 为此，工作流会检查每个投放是否处于非活动状态（根据其状态）。 如果投放处于活动状态，则在删除它之前将停止它。 通过执行以下查询执行检查：

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   其中 **$(l)** 是投放的标识符。

1. 如果状态的值 **[!UICONTROL Start pending]** 为、 **[!UICONTROL In progress]** 、、、 **[!UICONTROL Recovery pending]** 、 **[!UICONTROL Recovery in progress]** 、 **[!UICONTROL Pause requested]** 或(值 **[!UICONTROL Pause in progress]****[!UICONTROL Paused]** 51、55、61、62、71、72、75)，则投放将停止，任务将清除链接的信息。

### 清除过期投放 {#cleanup-of-expired-deliveries}

此任务停止有效期已过的投放。

1. 该工 **[!UICONTROL Database cleanup]** 作流创建已过期的投放的列表。 此列表包括所有状态为非的过期投放 **[!UICONTROL Finished]** ，以及最近停止的具有超过10,000条未处理消息的投放。 使用以下查询:

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   当 **投放模式** 1与该模式 **[!UICONTROL Mass delivery]** 匹配时，状 **态51** 与状态匹配，状 **[!UICONTROL Start pending]********[!UICONTROL Stopped]** 态5匹配状态85匹配状态，在投放服务器上更新的投放日志质量的最大数目等于10,000。

1. 然后，该工作流包括使用列表的最近过期投放的中间源。 尚未通过投放服务器恢复投放日志的中间源将被排除。

   使用以下查询:

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 以下查询用于检测外部帐户是否仍处于活动状态，以按日期筛选投放:

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在过期投放的列表中，状态为、 **[!UICONTROL Pending]** 切换到的投放日志 **[!UICONTROL Delivery cancelled]** ，此列表中的所有投放都切换为 **[!UICONTROL Finished]** 。

   使用以下查询:

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   其中 **$(curdate)** 是投放日志服务器的当前日期， **(bl)** 是投放的标识符， **$(dl)********[!UICONTROL Pending]********[!UICONTROL Delivery cancelled]** 是投放,投放状态6匹配状态7和状态7匹配状态。

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   其 **中投放状** 态 **[!UICONTROL Finished]** 95与状态匹配， **$(dl)** 是投放的标识符。

1. 已过时投放&#x200B;**的所有片段**(deliveryParts)都将被删除，正在执行的通知投放的所有已过时片段将被删除。 批量删除功能同时用于这两个任务。

   使用以下查询:

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   其中 **投放状** 态 **[!UICONTROL Finished]** 95与状态匹配， **投放状态85** 与状态匹配， **[!UICONTROL Stopped]** 并且 **** $(curDate)是当前服务器日期。

### 清除镜像页面 {#cleanup-of-mirror-pages}

此任务删除投放使用的Web资源(镜像页面)。

1. 首先，使用以下列表恢复要清除的投放的查询:

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   其中 **$(curDate)** 是当前服务器日期。

1. 然 **后，如果必要** ，使用先前恢复的投放的标识符清除NmsMirrorPageInfo表。 成批删除用于生成以下查询:

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   其 **中$(dl** )是投放的标识符。

1. 然后，将一个条目添加到投放日志。
1. 然后，会识别已清除的投放，以避免以后必须重新处理它们。 将执行以下查询:

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   其中 **$(strIn** )是投放标识符的列表。

### 清除工作表 {#cleanup-of-work-tables}

此任务会从库中删除所有与状态为、或的投放匹配 **[!UICONTROL Being edited]** 的工 **[!UICONTROL Stopped]** 作表 **[!UICONTROL Deleted]** 。

1. 名称以wkDlv_开头的表 **的列表** ，首先使用以下查询(postgresql)恢复：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 进行中工作流使用的表随后将被排除。 为此，使用以下列表恢复在制投放的查询:

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   其中0是与投放状态匹配 **[!UICONTROL Being edited]** 的值，85与状态 **[!UICONTROL Stopped]** 匹配，100与状态 **[!UICONTROL Deleted]** 匹配。

1. 不再使用的表将使用以下查询删除：

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### 清除导入生成的拒绝 {#cleanup-of-rejects-generated-by-imports-}

通过此步骤，可以删除在导入过程中未处理所有数据的记录。

1. 在XtkReject表上使用以 **下查询** ，执行质量删除：

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   其 **中$(curDate)** 是当前服务器日期，从中我们减去为NmsCleanup_RejectsPurgeDelay **选项定义的期间(请参阅部署向导** ), [](#deployment-wizard)**** $(l)是要成批删除的最大记录数。

1. 然后，使用以下查询删除所有孤立拒绝：

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清除工作流实例 {#cleanup-of-workflow-instances}

此任务使用其标识符(lWorkflowId)和历史&#x200B;**记录**(lHistory)清除&#x200B;**每个工作流**&#x200B;实例。 它通过再次运行工作表清理任务来删除不活动的表。 清除还会删除已删除工作流的所有孤立工作表（wkf%和wkfhisto%）。

>[!NOTE]
>
>历史记录的清除频率在“历史记录（以天为单位）”字 **段(默认值** 30天)中为每个工作流指定。 可以在工作流属性的“执 **行** ”选项卡中找到此字段。 如需详细信息，请参阅[此部分](../../workflow/using/workflow-properties.md#execution)。

1. 要恢复要删除的列表，请使用以下查询:

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查询生成列表，这些工作流将用于删除所有链接的日志、完成的任务和完成的事件，使用以下查询:

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   其 **中$(lworkflow** )是工作流的标识符， **$(lhistory)** 是历史记录的标识符。

1. 将删除所有未使用的表。 为此目的，所有表都由于使用以下查询( **postgresql** )的wkf%type掩码而收集：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然后，将排除挂起工作流实例使用的所有表。 活动工作流的列表使用以下查询恢复：

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然后，会恢复每个工作流标识符，以查找正在进行中的工作流使用的表的名称。 这些名称将排除在以前恢复的表的列表中。
1. “增量查询”类型活动历史表使用以下查询排除：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   其 **中$(strcondition** )是与wkfhisto%mask匹配 **的表的列表** 。

1. 其余的表将使用以下查询删除：

   ```
   DROP TABLE wkf15487_12;
   ```

### 清除工作流登录 {#cleanup-of-workflow-logins}

此任务使用以下查询删除工作流登录：

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 清除孤立工作表 {#cleanup-of-orphan-work-tables}

此任务删除链接到组的孤立工作表。 NmsGroup **表存** 储要清除的组（类型不同于0）。 表名的前缀是 **grp**。 要标识要清除的组，请使用以下查询:

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 清除访客 {#cleanup-of-visitors}

此任务使用成批删除从访客表删除过时记录。 过时记录是指上次修改时间早于部署向导中定义的保存期(请参阅部 [署向导](#deployment-wizard))。 使用以下查询:

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

其 **中$(tsDate** )是当前服务器日期，从中我们减去为NmsCleanup_VisitorPurgeDelay选项 **定义的期间** 。

### NPAI的清除 {#cleanup-of-npai}

此任务允许您从NmsAddress表中删除与有效地址 **匹配的** 记录。 以下查询用于执行成批删除：

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

其中 **状态** 2与状态 **[!UICONTROL Valid]** 匹配， **$(tsDate1)** 是当前服务器日期，而 **$(tsDate2)与****** NmsCleanup_LastCleanup选项匹配。

### 清除订阅 {#cleanup-of-subscriptions-}

此任务使用成批删除从NmsSubscription表 **中清除** 用户删除的所有订阅。 使用以下查询:

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清除跟踪日志 {#cleanup-of-tracking-logs}

此任务会从跟踪日志表和Web跟踪日志表中删除过时记录。 过时记录是指早于部署向导中定义的保存期的记录(请参 [阅部署向导](#deployment-wizard))。

1. 首先，使用以下列表恢复跟踪日志表的查询:

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 成批删除用于清除先前恢复的表列表中的所有表。 使用以下查询:

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   其 **中$(tsDate** )是当前服务器日期，从中我们减去为NmsCleanup_TrackingLogPurgeDelay选项 **定义的期间** 。

1. 跟踪统计信息表将使用成批删除来清除。 使用以下查询:

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   其 **中$(tsDate** )是当前服务器日期，从中我们减去为NmsCleanup_TrackingStatPurgeDelay选项 **定义的期间** 。

### 清除投放日志 {#cleanup-of-delivery-logs}

此任务允许您清除存储在各种表中的投放日志。

1. 为此，投放日志模式的列表使用以下查询恢复：

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中间源时， **NmsBroadLogMid** 表在投放映射中未引用。 将 **nms:broadLog** Mid模式添加到由前一个查询恢复的列表。
1. 然后， **数据库清理** 工作流会从以前恢复的表中清除过时的数据。 使用以下查询:

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   其 **中$(tableName)** 是模式列表中每个表的名称，而$ **(option)是为NmsBroadPlugeLogDelay** 选项(请参阅部署向导 ****[](#deployment-wizard))定义的日期。

1. 最后，该工作流检查NmsProviderMsgId **表是否存在** 。 如果是，则使用以下查询删除所有过时的数据：

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   其中 **$(option)** 与为NmsCleanup_BroadLogPurgeDelay选项定 **义的日期相匹配** (请参阅 [部署向导](#deployment-wizard))。

### 清除NmsEmailErrorStat表 {#cleanup-of-the-nmsemailerrorstat-table-}

此任务清 **除NmsEmailErrorStat** 表。 主项目(**coalesceErrors**)定义两个日期：

* **开始日期**:与NmsLastErrorStatCoalesce选项相 **匹配的下一进程的日期** ，或表中最近的日期。
* **结束日期**:当前服务器日期。

如果开始日期大于或等于结束日期，则不进行任何流程。 在这种情况下，将 **显示coalesceUpToDate** 消息。

如果开始日期早于结束日期，则清 **除NmsEmailErrorStat** 表。

NmsEmailErrorStat表中在开始 **和结束日期之间** ，使用以下查询恢复错误总数：

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

其中 **$end****和$** 开始是先前定义的开始和结束日期。

如果总数大于0:

1. 执行以下查询以仅使错误超出特定阈值（等于20）:

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. 将显 **示coalescingErrors** 消息。
1. 将新建一个连接，以删除在开始和结束日期之间发生的所有错误。 使用以下查询:

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. 每个错误都使用以 **下查询保存** 在NmsEmailErrorStat表中：

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   其中每个变量与前一个查询恢复的值相匹配。

1. 开始 **变量** 将更新为上一个进程的值，以完成循环。

循环和任务停止。

清除操作在NmsEmailError **和cleanup** NmsMxDomain **表上执行** 。

### 清除NmsEmailError表 {#cleanup-of-the-nmsemailerror-table-}

使用以下查询:

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询从NmsEmailError表中删除NmsEmailErrorStat中 **没有链接记** 录的 **所有行** 。

### 清除NmsMxDomain表 {#cleanup-of-the-nmsmxdomain-table-}

使用以下查询:

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询从NmsMxDomain表中删除NmsEmailErrorStat表 **中没有链接记** 录的所 **有行** 。

### 清理命题 {#cleanup-of-propositions}

如果安 **装了** “交互”模块 **，则执行此任务以清除** NmsCompationXxx表。

将恢复命题表的列表，并对每个表执行质量删除，使用以下查询:

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

其 **中$(option)** 是为NmsCleanup_CompationPurgeDelay选项 **定义的日期** (请参阅 [部署向导](#deployment-wizard))。

### 清除模拟表 {#cleanup-of-simulation-tables}

此任务可清除孤立模拟表(不再链接到优惠模拟或投放模拟)。

1. 要恢复需要清理的模拟的列表，请使用以下查询:

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要删除的表的名称由wkSimu_ **prefix和模拟** (例如： **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### 清理审核跟踪 {#cleanup-of-audit-trail}

使用以下查询:

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

其 **中$(tsDate** )是为XtkCleanup_AuditTrailPurgeDelay选项定义的期 **间的当前服务器日期** 。

### 清除Nms地址 {#cleanup-of-nmsaddress}

使用以下查询:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

此查询将删除与iOS和Android相关的所有条目。

### 统计更新和存储优化 {#statistics-update}

使用 **XtkCleanup** _NoStats选项可以控制清除工作流中存储优化步骤的行为。

如果XtkCleanup **** _NoStats选项不存在，或其值为0，则将在PostgreSQL上以详细模式(VAFUM VERBOSE ANALYZE)执行存储优化，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 DAVUM将输出以下格式的行： `INFO: vacuuming "public.nmsactivecontact"` 并且ANALYZE将输出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`.

如果选项的值为1，则不对任何数据库执行统计信息更新。 工作流日志中将显示以下日志行： `Option 'XtkCleanup_NoStats' is set to '1'`.

如果选项的值为2，则将在PostgreSQL上以详细模式(ANALYZE VERBOSE)执行存储分析，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 ANALYZE将输出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`.

### 订阅清除(NMAC) {#subscription-cleanup--nmac-}

此任务将删除与已删除的服务或移动应用程序相关的任何订阅。

要恢复广播模式的列表，请使用以下查询:

```
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

然后，任务恢复链接到appSubscription链接的表 **的名称** ，并删除这些表。

此清除工作流还删除自NmsCleanup_AppSubscriptionRcpPurgeDelay选项中设置的时间以来未更新 **的idisabled = 1的所有条目** 。

### 清理会话信息 {#cleansing-session-information}

此任务从sessionInfo表 **中清除** 信息，使用以下查询:

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清理过期事件 {#cleansing-expired-events}

此任务清除接收和存储在执行实例上的事件，以及存档在控制实例上的事件。

### 清理反应 {#cleansing-reactions}

此任务清除已删 **除假设验证的反应(**&#x200B;表NmsRemaMatchRcp)。
