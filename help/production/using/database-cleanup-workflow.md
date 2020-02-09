---
title: 数据库清除工作流
seo-title: 数据库清除工作流
description: 数据库清除工作流
seo-description: null
page-status-flag: never-activated
uuid: a7478641-cdf6-4bd4-9dd7-0c84416c9de6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 6b188d78-abb4-4f03-80b9-051ce960f43c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5813af76e3cad16d9094a19509dcb855e36c01f

---


# 数据库清除工作流{#database-cleanup-workflow}

## 简介 {#introduction}

通过 **[!UICONTROL Database cleanup]** 该节点可访问的工 **[!UICONTROL Administration > Production > Technical workflows]** 作流，可让您删除过时的数据以避免数据库的指数级增长。 该工作流会自动触发，无需用户干预。

![](assets/ncs_cleanup_workflow.png)

## 配置 {#configuration}

数据库清理配置在两个级别上：在工作流调度程序和部署向导中。

### 调度程序 {#the-scheduler}

>[!NOTE]
>
>For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

默认情况下，工 **[!UICONTROL Database cleanup]** 作流配置为每天凌晨4点开始。 调度程序允许您更改工作流触发频率。 可用频率如下：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!CAUTION]
>
>要使工作流 **[!UICONTROL Database cleanup]** 在调度程序中定义的日期和时间开始，必须启动工作流引擎(wfserver)。 如果情况不是这样，则直到下次启动工作流引擎时，才会进行数据库清理。

### 部署向导 {#deployment-wizard}

通过 **[!UICONTROL Deployment wizard]** 菜单访问的“ **[!UICONTROL Tools > Advanced]** 数据”允许您配置保存数据的时长。 值以天数表示。 如果这些值未更改，则工作流将使用默认值。

![](assets/ncs_cleanup_deployment-wizard.png)

窗口的字段 **[!UICONTROL Purge of data]** 与以下选项一致。 这些任务由工作流执行的一些任务使 **[!UICONTROL Database cleanup]** 用：

* 统一跟踪： **NmsCleanup_TrackingStatPurgeDelay** (请参阅 [跟踪日志的清理](#cleanup-of-tracking-logs))
* 交付日志：NmsCleanup_ **BroadLogPurgeDelay** (请参 [阅清除交付日志](#cleanup-of-delivery-logs))
* 跟踪日志： **NmsCleanup_TrackingLogPurgeDelay** (请参 [阅跟踪日志的清理](#cleanup-of-tracking-logs))
* 已删除的提交：NmsCleanup_RecycledDeliveryPurgeDelay **(请参** 阅清除要删除或回收的交付 [](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 导入拒绝：NmsCleanup_RejicesPurgeDelay **(请参** 阅Cleanup of rejects生成的拒绝 [](#cleanup-of-rejects-generated-by-imports-))
* 访客资料：NmsCleanup_ **VisitorPurgeDelay** (请参 [阅Cleanup of visitors](#cleanup-of-visitors))
* 优惠建议：NmsCleanup_ **CompationPurgeDelay** (请参 [阅命令清除](#cleanup-of-propositions))

   >[!NOTE]
   >
   >该 **[!UICONTROL Offer propositions]** 字段仅在安装交互模 **块时** 可用。

* 活动：NmsCleanup_ **EventPurgeDelay** (请参 [阅清除过期事件](#cleansing-expired-events))
* 存档的活动：NmsCleanup_EventHistoPurgeDelay **(请参** 阅清除过期事件 [](#cleansing-expired-events))

   >[!NOTE]
   >
   >只有在 **[!UICONTROL Events]** 安装了 **[!UICONTROL Archived events]** 消息中心模块时，和 **** 字段才可用。

* 审计跟踪： **XtkCleanup_AuditTrailPurgeDelay** (请参阅 [审核跟踪清理](#cleanup-of-audit-trail))

以下部分介绍了由工 **[!UICONTROL Database cleanup]** 作流执行的所有任务。

## 由数据库清除工作流执行的任务 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流调度程序中定义的日期和时间(请参 [阅调度程序](#the-scheduler))，工作流引擎启动数据库清除进程。 数据库清理连接到数据库，并按如下所示的顺序执行任务。

>[!CAUTION]
>
>如果这些任务之一失败，将不执行以下任务。\
>具有 **LIMIT** 属性的SQL查询将重复执行，直到所有信息都得到处理。

>[!NOTE]
>
>以下描述由数据库清除工作流执行的任务的部分是为数据库管理员或熟悉SQL语言的用户保留的。

### 要删除清除的列表 {#lists-to-delete-cleanup}

由工作流执行的第一个任 **[!UICONTROL Database cleanup]** 务将删除具有deleteStatus ！的 **所有组=** 0属 **性**。 链接到这些组的记录以及其他表中存在的记录也被删除。

1. 将使用以下SQL查询恢复要删除的列表：

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每个列表都有多个指向其他表的链接。 所有这些链接都将使用以下查询批量删除：

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   其 **中$(relatedTable)** 是与 **NmsGroup相关的表** , **$(l)** 是列表标识符。

1. 当列表为“列表”类型列表时，将使用以下查询删除关联的表：

   ```
   DROP TABLE grp$(l)
   ```

1. 此操作 **恢复的每个“选择** ”类型列表都会使用以下查询删除：

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   其中 **$(l)** 是列表标识符

### 清除要删除或回收的交货 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任务会清除所有要删除或回收的交货。

1. 该工 **[!UICONTROL Database cleanup]** 作流选择其deleteStatus **字段具有值或其删除日期早于部署向导的** ( **[!UICONTROL Yes]****[!UICONTROL Recycled]****[!UICONTROL Deleted deliveries]****** NmsCleanup_RecycledDelayDelayPurgeDelayDelayDelayDelayDelayField)字段中定义的期间的所有交付。 For more on this, refer to [Deployment wizard](#deployment-wizard). 此期间是根据当前服务器日期计算的。
1. 对于每个中间采购服务器，任务将选择要删除的提交列表。
1. 该工 **[!UICONTROL Database cleanup]** 作流会删除交付日志、附件、镜像页面信息和所有其他相关数据。
1. 在永久删除传送之前，工作流会从以下表格中清除链接的信息：

   * 在交付排除表(**NmsDlvExclusion**)中，使用以下查询：

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      其中 **$(l)** 是交付的标识符。

   * 在优惠券表(**NmsCouponValue**)中，将使用以下查询（含成批删除）:

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      其中 **$(l)** 是交付的标识符。

   * 在交付日志表(**NmsBroadlogXxx**)中，以10,000条记录的批量删除被执行。
   * 在优惠提议表(**NmsCompatitionXxx**)中，批量删除以10,000条记录批量执行。
   * 在跟踪日志表(**NmsTrackinglogXxx**)中，成批执行成批删除（5,000条记录）。
   * 在交付片段表(**NmsDeliveryPart**)中，以5,000条记录的批量执行成批删除。 此表包含有关要传送的其余消息的个性化信息。
   * 在镜像页面数据片段表(**NmsMirrorPageInfo**)中，成批执行成批删除（5,000条记录）。 此表包含有关用于生成镜像页面的所有消息的个性化信息。
   * 在镜像页面搜索表(**NmsMirrorPageSearch**)中，成批执行成批删除（5,000条记录）。 此表是一个搜索索引，它提供对存储在 **NmsMirrorPageInfo表中的个性化信息的访问** 。
   * 在批处理日志表(**XtkJobLog**)中，成批删除以5,000条记录执行。 此表包含要删除的分发日志。
   * 在交付URL跟踪表(**NmsTrackingUrl**)中，使用以下查询：

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      其中 **$(l)** 是交付的标识符。

      此表包含要删除的提交中的URL，以启用其跟踪。

1. 将从交付表(**NmsDelivery**)中删除交付：

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   其中 **$(l)** 是交付的标识符。

#### 使用中间采购的交货 {#deliveries-using-mid-sourcing}

该 **[!UICONTROL Database cleanup]** 工作流还会删除中间采购服务器上的交付。

1. 为此，工作流会检查每个交付是否处于非活动状态（基于其状态）。 如果某个交付处于活动状态，则在删除它之前将停止它。 通过执行以下查询执行检查：

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   其中 **$(l)** 是交付的标识符。

1. 如果状态的值为 **[!UICONTROL Start pending]** 、 **[!UICONTROL In progress]** 、 **[!UICONTROL Recovery pending]** 、、 **[!UICONTROL Recovery in progress]** 、、 **[!UICONTROL Pause requested]****[!UICONTROL Pause in progress]****[!UICONTROL Paused]** 、或（值51、55、61、62、71、72、75），则停止传送并且任务清除链接的信息。

### 清除过期的交付 {#cleanup-of-expired-deliveries}

此任务将停止有效期已过的分发。

1. 此工 **[!UICONTROL Database cleanup]** 作流会创建已过期的分发列表。 此列表包括所有状态为非以下状态的已过期交付 **[!UICONTROL Finished]** ，以及最近停止的包含超过10,000条未处理消息的交付。 使用以下查询：

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   如果 **传送模式** ，则状态51与 **[!UICONTROL Mass delivery]** 该模式匹配 **，状态51与状态匹配，状态5****[!UICONTROL Start pending]********[!UICONTROL Stopped]** 与状态8匹配，并且在传送服务器上更新的最大质量等于10,000。

1. 然后，该工作流包括使用中间采购的最近过期交货的列表。 不包括尚未通过中间采购服务器恢复的交付日志的交付。

   使用以下查询：

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 以下查询用于检测外部帐户是否仍处于活动状态，以按日期筛选分发：

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在已过期的分发列表中，状态为、切换到 **[!UICONTROL Pending]** 、的分发日志 **[!UICONTROL Delivery cancelled]** ，此列表中的所有分发都切换到 **[!UICONTROL Finished]** 。

   使用以下查询：

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   其中 **$(curdate)** 是数据库服务器的当前日期， **$(bl)** 是发送日志的当前日期， **$(bl)消息是发送日志，** $( **$)是发送状态6，发送状态7与发送状态7匹配，****[!UICONTROL Pending]********[!UICONTROL Delivery cancelled]** dl与状态标识符匹配。

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   其中 **传送状态** 95与状态 **[!UICONTROL Finished]** 匹配， **$(dl)** 是传送的标识符。

1. 将删除过时&#x200B;**交付的所有片段**(deliveryParts)，并删除正在进行的通知交付的所有过时片段。 这两个任务都使用批量删除。

   使用以下查询：

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   其中 **交付状态** 95与状态 **[!UICONTROL Finished]** 匹配 **，交付状态85** , **[!UICONTROL Stopped]** 且 **** $(curDate)与当前服务器日期匹配。

### 清除镜像页面 {#cleanup-of-mirror-pages}

此任务将删除提交使用的Web资源（镜像页面）。

1. 首先，将使用以下查询恢复要清除的提交列表：

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   其 **中$(curDate)** 是当前服务器日期。

1. 然后， **根据需要，使用先前恢复的传送的标识符清除NmsMirrorPageInfo** 表。 批量删除用于生成以下查询：

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   其中 **$(dl)** 是交付的标识符。

1. 然后，将一个条目添加到交付日志。
1. 然后识别已清除的提交，以避免以后必须重新处理它们。 将执行以下查询：

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   其中 **$(strIn)** 是传送标识符的列表。

### 清除工作表 {#cleanup-of-work-tables}

此任务将从数据库(所有与状态为、或的提交匹配的工作表 **[!UICONTROL Being edited]** )中 **[!UICONTROL Stopped]** 删除 **[!UICONTROL Deleted]** 。

1. 首先使用以下查询( **postgresql)恢复名称以** wkDlv_开头的表列表：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然后，将排除进行中的工作流使用的表。 为此，将使用以下查询恢复进行中的提交列表：

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   其中0是与交付状态匹配的 **[!UICONTROL Being edited]** 值，85匹配状态， **[!UICONTROL Stopped]** 100匹配状态 **[!UICONTROL Deleted]** 。

1. 不再使用的表将使用以下查询删除：

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### 清除导入生成的废品 {#cleanup-of-rejects-generated-by-imports-}

通过此步骤，您可以删除在导入过程中未处理所有数据的记录。

1. 对 **XtkReject表执行成批删除** ，查询如下：

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   其中 **$(curDate)** 是当前服务器日期，从中我们减去为 **NmsCleanup_RejicesPurgeDelay** 选项定义的期间(请参阅“部署向导 [”),](#deployment-wizard)**** $(l)是要删除的最大记录数。

1. 然后，使用以下查询删除所有孤立拒绝：

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清除工作流实例 {#cleanup-of-workflow-instances}

此任务使用其标识符(**lWorkflowId**)和历史记录(**lHistory**)清除每个工作流实例。 它通过再次运行工作台清理任务来删除不活动的表。

>[!NOTE]
>
>历史记录的清除频率在“历史记录（以天为单位）”字 **段中为每个工作流指定** （默认值为30天）。 可以在工作流属性的“执 **行** ”选项卡中找到此字段。 如需详细信息，请参阅[此部分](../../workflow/using/workflow-properties.md#execution)。

1. 要恢复要删除的工作流列表，请使用以下查询：

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查询生成工作流列表，该列表将用于删除所有链接的日志、完成的任务和完成的事件，并使用以下查询：

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   其 **中$(lworkflow)** 是工作流的标识符， **$(lhistory)** 是历史的标识符。

1. 将删除所有未使用的表。 为此，由于使用以下查询(postgresql) **wkf%** type mask，所有表都会被收集：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然后，将排除待定工作流实例使用的所有表。 活动工作流列表会使用以下查询来恢复：

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然后，将恢复每个工作流标识符以查找正在进行的工作流所使用的表的名称。 这些名称将从以前恢复的表列表中排除。
1. 使用以下查询将排除“增量查询”类型的活动历史记录表：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   其 **中$(strcondition)** ，是与wkfhisto%遮罩相 **匹配的表列表** 。

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

此任务将删除链接到组的孤立工作表。 NmsGroup **表存储要清除的组** （类型不同于0）。 表名的前缀是 **grp**。 要标识要清除的组，请使用以下查询：

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 清除访客 {#cleanup-of-visitors}

此任务使用成批删除功能从访客表中删除过时的记录。 过时记录是指上次修改时间早于部署向导中定义的保存期(请参阅部署向 [导](#deployment-wizard))的记录。 使用以下查询：

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < $(tsDate) LIMIT 5000)
```

其 **中$(tsDate)** 是当前服务器日期，从中我们减去为 **NmsCleanup_VisitorPurgeDelay选项定义的时段** 。

### NPAI的清除 {#cleanup-of-npai}

此任务允许您从 **NmsAddress表中删除与有效地址匹配的记** 录。 以下查询用于执行成批删除：

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

其中 ******[!UICONTROL Valid]** 状态与状态匹配， **$(tsDate1)** ，是当前服务器日期， **$(tsDate2)****** 匹配NmsCleanup_LastCleanup选项。

### 清除订阅 {#cleanup-of-subscriptions-}

此任务使用成批删除功能从 **NmsSubscription** 表中清除用户删除的所有订阅。 使用以下查询：

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清除跟踪日志 {#cleanup-of-tracking-logs}

此任务将从跟踪日志表和Web跟踪日志表中删除过时的记录。 过时记录是指早于部署向导中定义的保存期(请参阅部署 [向导](#deployment-wizard))的记录。

1. 首先，使用以下查询恢复跟踪日志表列表：

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 成批删除用于清除先前恢复的表列表中的所有表。 使用以下查询：

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   其 **中$(tsDate)** 是当前服务器日期，从中我们减去为 **NmsCleanup_TrackingLogPurgeDelay选项定义的期间** 。

1. 使用成批删除功能清除跟踪统计数据表。 使用以下查询：

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   其 **中$(tsDate)** 是当前服务器日期，从中我们减去为 **NmsCleanup_TrackingStatPurgeDelay选项定义的期间** 。

### 清除交付日志 {#cleanup-of-delivery-logs}

通过此任务，您可以清除存储在各种表中的交付日志。

1. 为此，将使用以下查询恢复交付日志架构列表：

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中间采购时， **NmsBroadLogMid** 表在传送映射中未引用。 将 **nms:broadLogMid** 架构添加到由上一个查询恢复的列表。
1. 然后， **** 数据库清除工作流会清除先前恢复的表中废弃的数据。 使用以下查询：

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   其 **中$(Name)** ($(Name))是架构列表中每个表的名称， **$(option)** (是为 **NmsBroadLogPurgeDelay** 选项(请参阅 [](#deployment-wizard)DeploymentDiscleant向导)定义的日期)。

1. 最后，该工作流检查 **NmsProviderMsgId表是否存在** 。 如果是，则使用以下查询删除所有废弃的数据：

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   其中 **$(option)** 匹配为 **NmsCleanup_BroadLogPurgeDelay选项定义的日期** (请参阅“部 [署向导”](#deployment-wizard))。

### 清除NmsEmailErrorStat表 {#cleanup-of-the-nmsemailerrorstat-table-}

此任务清除 **NmsEmailErrorStat** 表。 主程序(coalesceErrors ****)定义两个日期：

* **开始日期**:与 **NmsLastErrorStatCoalesce选项匹配的下一个进程的日期** ，或表中的最近日期。
* **结束日期**:当前服务器日期。

如果开始日期大于或等于结束日期，则不会进行任何进程。 在这种情况下，将显 **示coalesceUpToDate** 消息。

如果开始日期早于结束日期，则清 **除NmsEmailErrorStat** 表。

NmsEmailErrorStat表中在开始和结 **束日期之间的错误总数** ，使用以下查询来恢复：

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

其中 **$end** 和 **** $start是之前定义的开始和结束日期。

如果总数大于0:

1. 执行以下查询以仅使错误超出特定阈值（等于20）:

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. 将显 **示coalescingErrors** 消息。
1. 将创建新连接，以删除在开始日期和结束日期之间发生的所有错误。 使用以下查询：

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. 每个错误都使用以下 **查询保存在NmsEmailErrorStat** 表中：

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   其中每个变量与前一查询恢复的值相匹配。

1. 使 **用上一** 进程的值更新开始变量以完成循环。

循环和任务停止。

清除操作会在 **NmsEmailError** 和 **cleanupNmsMxDomain表上执行** 。

### 清除NmsEmailError表 {#cleanup-of-the-nmsemailerror-table-}

使用以下查询：

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询从NmsEmailError表中删除 **NmsEmailErrorStat** (NmsEmailErrorStat中没有链接记录的所 **有行** )。

### 清除NmsMxDomain表 {#cleanup-of-the-nmsmxdomain-table-}

使用以下查询：

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询将从 **NmsMxDomain表中删除NmsEmailErrorStat** 表中没有链接记录的所 **** 有行。

### 清除命题 {#cleanup-of-propositions}

如果安 **装了Interaction** Module，则执行此任务以清除 **NmsCompationXxx表** 。

通过以下查询，可以恢复命题表列表，并对每个表执行成批删除：

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

其中 **$(option)** 是为NmsCleanup_CompationPurgeDelay选项定义的日期 **(请参阅** 部署向导 [](#deployment-wizard))。

### 清理模拟表 {#cleanup-of-simulation-tables}

此任务可清除孤立的模拟表（不再链接到选件模拟或交付模拟）。

1. 要恢复需要清除的模拟列表，请使用以下查询：

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要删除的表的名称由 **wkSimu_** prefix后跟模拟的标识符组成(例如： **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### 统计数据更新和存储优化 {#statistics-update}

使用 **XtkCleanup_NoStats** 选项可以控制清除工作流中存储优化步骤的行为。

如果 **XtkCleanup_NoStats** 选项不存在，或其值为0，则将在PostgreSQL上以冗余模式(VAFUMO VERBOSE ANALYZE)执行存储优化，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 VAMUC将输出以下格式的行：而 `INFO: vacuuming "public.nmsactivecontact"` ANALYZE将输出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`.

如果选项的值为1，则不会对任何数据库执行统计信息更新。 工作流日志中将显示以下日志行： `Option 'XtkCleanup_NoStats' is set to '1'`.

如果选项的值为2，则它将在PostgreSQL上以详细模式(ANALYZE VERBOSE)执行存储分析，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 ANALYZE将输出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`.

### 订阅清理(NMAC) {#subscription-cleanup--nmac-}

此任务将删除与已删除的服务或移动应用程序相关的所有订阅。

1. 要恢复广播架构列表，请使用以下查询：

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
   ```

1. 然后，该任务会恢复链接到appSubscription链接的表 **的名称** ，并删除这些表。

### 清理会话信息 {#cleansing-session-information}

此任务清除 **sessionInfo** 表中的信息，使用以下查询：

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清理过期事件 {#cleansing-expired-events}

此任务可清除在执行实例上接收和存储的事件以及在控制实例上归档的事件。

### 清洁反应 {#cleansing-reactions}

此任务清除已删除假 **设的反应(表NmsRemaMatchRcp**)。

### 清除审计跟踪 {#cleanup-of-audit-trail}

使用以下查询：

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

其 **中$(tsDate)** 是当前服务器日期，从该日期起，将为 **** XtkCleanup_AuditTrailPurgeDelay选项定义的期间提交到该日期。
