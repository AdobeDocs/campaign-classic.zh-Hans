---
solution: Campaign Classic
product: campaign
title: 数据库清理工作流
description: 了解如何自动清理过时的数据
audience: production
content-type: reference
topic-tags: data-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2910'
ht-degree: 0%

---


# 数据库清理工作流{#database-cleanup-workflow}

## 简介 {#introduction}

可通过&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;节点访问的&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流允许您删除过时的数据，以避免数据库呈指数级增长。 工作流会自动触发，无需用户干预。

![](assets/ncs_cleanup_workflow.png)

## 配置{#configuration}

数据库清理配置在两个级别上：在工作流调度程序和部署向导中。

### 工作流调度程序{#the-scheduler}

>[!NOTE]
>
>有关调度程序的详细信息，请参阅[此部分](../../workflow/using/scheduler.md)。

默认情况下，**[!UICONTROL Database cleanup]**&#x200B;工作流配置为每天4AM开始。 该调度程序允许您更改工作流触发频率。 可用频率如下：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>要使&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流在调度程序中定义的日期和时间开始，必须启动工作流引擎(wfserver)。 如果不是这样，数据库清理直到下次启动工作流引擎时才会发生。

### 部署向导{#deployment-wizard}

通过&#x200B;**[!UICONTROL Tools > Advanced]**&#x200B;菜单访问的&#x200B;**[!UICONTROL Deployment wizard]**&#x200B;可配置数据的保存时间。 值以天表示。 如果这些值未更改，工作流将使用默认值。

![](assets/ncs_cleanup_deployment-wizard.png)

**[!UICONTROL Purge of data]**&#x200B;窗口的字段与以下选项一致。 这些任务由&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流执行的某些应用程序使用：

* 整合跟踪：**NmsCleanup_TrackingStatPurgeDelay**(请参阅[清理跟踪日志](#cleanup-of-tracking-logs))
* 投放日志:**NmsCleanup_BroadLogPurgeDelay**(请参阅[清理投放日志](#cleanup-of-delivery-logs))
* 跟踪日志:**NmsCleanup_TrackingLogPurgeDelay**(请参阅[清理跟踪日志](#cleanup-of-tracking-logs))
* 已删除投放:**NmsCleanup_RecyledDeliveryPurgeDelay**(请参阅[清除要删除或回收的投放](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 导入拒绝：**NmsCleanup_RejecsPurgeDelay**（请参阅[清除导入生成的废品](#cleanup-of-rejects-generated-by-imports-)）
* 访客用户档案:**NmsCleanup_VisitorPurgeDelay**(请参阅[清理访客](#cleanup-of-visitors))
* 优惠建议:**NmsCleanup_CompationPurgeDelay**（请参阅[清理建议](#cleanup-of-propositions)）

   >[!NOTE]
   >
   >**[!UICONTROL Offer propositions]**&#x200B;字段仅在安装&#x200B;**Interaction**&#x200B;模块时可用。

* 事件:**NmsCleanup_EventPurgeDelay**(请参阅[清理过期事件](#cleansing-expired-events))
* 存档的事件:**NmsCleanup_EventHistoPurgeDelay**(请参阅[清理过期事件](#cleansing-expired-events))

   >[!NOTE]
   >
   >**[!UICONTROL Events]**&#x200B;和&#x200B;**[!UICONTROL Archived events]**&#x200B;字段仅在安装了&#x200B;**消息中心**&#x200B;模块时可用。

* 审计跟踪：**XtkCleanup_AuditTrailPurgeDelay**（请参阅[审核跟踪的清理](#cleanup-of-audit-trail)）

以下部分介绍了由&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流执行的所有任务。

## 任务由数据库清理工作流{#tasks-carried-out-by-the-database-cleanup-workflow}执行

在工作流调度程序中定义的日期和时间(请参阅[调度程序](#the-scheduler)),工作流引擎将开始数据库清理进程。 数据库清理连接到数据库，并按如下所示的顺序执行任务。

>[!IMPORTANT]
>
>如果其中一个任务失败，则不会执行下列操作。\
>具有&#x200B;**LIMIT**&#x200B;属性的SQL查询将重复执行，直到处理所有信息。

>[!NOTE]
>
>以下描述由数据库清理工作流执行的任务的部分为数据库管理员或熟悉SQL语言的用户保留。

### 列表删除清理{#lists-to-delete-cleanup}

由&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流执行的第一个任务将删除具有&#x200B;**deleteStatus ！的所有组=** NmsGroup **中的0**&#x200B;属性。 链接到这些组的记录以及存在于其他表中的记录也将被删除。

1. 将使用以下SQL查询恢复要删除的列表:

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每个列表都有多个指向其他表的链接。 所有这些链接都将使用以下查询批量删除：

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   其中&#x200B;**$(relatedTable)**&#x200B;是与&#x200B;**NmsGroup**&#x200B;相关的表，而&#x200B;**$(l)**&#x200B;是列表标识符。

1. 当列表为“列表”类型列表时，将使用以下查询删除关联表：

   ```
   DROP TABLE grp$(l)
   ```

1. 通过以下列表删除操作恢复的每个&#x200B;**Select**&#x200B;类型查询:

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   其中&#x200B;**$(l)**&#x200B;是列表标识符

### 清除要删除或回收的投放{#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任务清除所有要删除或循环使用的投放。

1. **[!UICONTROL Database cleanup]**&#x200B;工作流选择&#x200B;**deleteStatus**&#x200B;字段的值为&#x200B;**[!UICONTROL Yes]**&#x200B;或&#x200B;**[!UICONTROL Recycled]**&#x200B;且其删除日期早于部署向导的&#x200B;**[!UICONTROL Deleted deliveries]**(**NmsCleanup_RecycledDeliveryPurgeDelay**)字段中定义的期间的所有投放。 有关详细信息，请参阅[部署向导](#deployment-wizard)。 此期间是根据当前服务器日期计算的。
1. 对于每个中间源服务器，任务选择要删除的投放的列表。
1. **[!UICONTROL Database cleanup]**&#x200B;工作流将删除投放日志、附件、镜像页面信息和所有其他相关数据。
1. 在永久删除投放之前，工作流会从以下表中清除链接信息：

   * 在投放排除表(**NmsDlvExclusion**)中，使用以下查询:

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      其中&#x200B;**$(l)**&#x200B;是投放的标识符。

   * 在优惠券表(**NmsCouponValue**)中，使用以下查询（进行批量删除）：

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      其中&#x200B;**$(l)**&#x200B;是投放的标识符。

   * 在投放日志表(**NmsBroadlogXxx**)中，成批删除以20,000条记录的批次执行。
   * 在优惠建议表(**NmsCompatitionXxx**)中，成批删除以20,000条记录执行。
   * 在跟踪日志表(**NmsTrackinglogXxx**)中，批量删除以20,000条记录的批次执行。
   * 在投放片段表(**NmsDeliveryPart**)中，成批删除以500,000条记录执行。 此表包含有关要传递的其余消息的个性化信息。
   * 在镜像页面数据片段表(**NmsMirrorPageInfo**)中，对过期的投放部件和已完成或已取消的部件，以20,000条记录的批次执行成批删除。 此表包含有关用于生成镜像页面的所有消息的个性化信息。
   * 在镜像页面搜索表(**NmsMirrorPageSearch**)中，成批删除以20,000条记录的批次执行。 此表是一个搜索索引，它提供对存储在&#x200B;**NmsMirrorPageInfo**&#x200B;表中的个性化信息的访问。
   * 在批处理日志表(**XtkJobLog**)中，成批删除以20,000条记录的批次执行。 此表包含要删除的投放日志。
   * 在投放URL跟踪表(**NmsTrackingUrl**)中，使用以下查询:

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      其中&#x200B;**$(l)**&#x200B;是投放的标识符。

      此表包含在要删除的投放中找到的URL，以启用其跟踪。

1. 投放从投放表(**NmsDelivery**)中删除：

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   其中&#x200B;**$(l)**&#x200B;是投放的标识符。

#### 投放使用中间源 {#deliveries-using-mid-sourcing}

**[!UICONTROL Database cleanup]**&#x200B;工作流还会删除中间源服务器上的投放。

1. 为此，工作流会检查每个投放是否处于非活动状态（基于其状态）。 如果投放处于活动状态，则在删除它之前将停止它。 通过执行以下查询执行检查：

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   其中&#x200B;**$(l)**&#x200B;是投放的标识符。

1. 如果状态的值为&#x200B;**[!UICONTROL Start pending]**、**[!UICONTROL In progress]**、**[!UICONTROL Recovery pending]**、**[!UICONTROL Recovery in progress]**、**[!UICONTROL Pause requested]**、**[!UICONTROL Pause in progress]**&#x200B;或&#x200B;**[!UICONTROL Paused]**（值51、55、61、62、71、72、75），则停止投放并清除链接的信息。

### 清除过期投放{#cleanup-of-expired-deliveries}

此任务停止有效期已过的投放。

1. **[!UICONTROL Database cleanup]**&#x200B;工作流会创建过期投放的列表。 此列表包括状态不为&#x200B;**[!UICONTROL Finished]**&#x200B;的所有过期投放，以及最近停止的包含超过10,000条未处理邮件的投放。 使用以下查询:

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   其中，**投放模式1**&#x200B;与&#x200B;**[!UICONTROL Mass delivery]**&#x200B;模式匹配，**状态51**&#x200B;与&#x200B;**[!UICONTROL Start pending]**&#x200B;状态匹配，**状态85**&#x200B;与&#x200B;**[!UICONTROL Stopped]**&#x200B;状态匹配，投放服务器上更新的最大投放日志数量等于10,000。

1. 然后，该工作流包括对使用中间源的最近过期投放的列表。 尚未通过中间源服务器恢复任何投放日志的投放将被排除。

   使用以下查询:

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 以下查询用于检测外部帐户是否仍处于活动状态，以按日期筛选投放:

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在过期投放的列表中，状态为&#x200B;**[!UICONTROL Pending]**&#x200B;的投放日志切换到&#x200B;**[!UICONTROL Delivery cancelled]**，此列表中的所有投放切换到&#x200B;**[!UICONTROL Finished]**。

   使用以下查询:

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   其中&#x200B;**$(curdate)**&#x200B;是投放日志库服务器的当前日期，**$(bl)**&#x200B;是投放消息的标识符，**$(dl)**&#x200B;是投放标识符，**状态6**&#x200B;与&#x200B;**[!UICONTROL Pending]**&#x200B;状态和&#x200B;**投放状态7匹配**&#x200B;与&#x200B;**[!UICONTROL Delivery cancelled]**&#x200B;状态匹配。

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   其中&#x200B;**投放状态95**&#x200B;与&#x200B;**[!UICONTROL Finished]**&#x200B;状态匹配，而&#x200B;**$(dl)**&#x200B;是投放的标识符。

1. 将删除已废弃投放的所有片段(**deliveryParts**)，并删除所有正在执行的通知投放的已废弃片段。 批量删除用于这两个任务。

   使用以下查询:

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   其中，**投放状态95**&#x200B;与&#x200B;**[!UICONTROL Finished]**&#x200B;状态匹配，**投放状态85**&#x200B;与&#x200B;**[!UICONTROL Stopped]**&#x200B;状态匹配，**$(curDate)**&#x200B;是当前服务器日期。

### 清除镜像页面{#cleanup-of-mirror-pages}

此任务将删除投放使用的Web资源(镜像页面)。

1. 首先，将使用以下列表恢复要清除的投放的查询:

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   其中&#x200B;**$(curDate)**&#x200B;是当前服务器日期。

1. 然后，如果需要，使用先前恢复的投放的标识符，清除&#x200B;**NmsMirrorPageInfo**&#x200B;表。 批量删除用于生成以下查询:

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   其中&#x200B;**$(dl)**&#x200B;是投放的标识符。

1. 然后，将一个条目添加到投放日志。
1. 然后识别已清除的投放，以避免以后必须重新处理它们。 将执行以下查询:

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   其中&#x200B;**$(strIn)**&#x200B;是投放标识符的列表。

### 清除工作表{#cleanup-of-work-tables}

此任务将从投放库中删除，所有与状态为&#x200B;**[!UICONTROL Being edited]**、**[!UICONTROL Stopped]**&#x200B;或&#x200B;**[!UICONTROL Deleted]**&#x200B;的相匹配的工作表。

1. 首先使用以下列表(postgresql)恢复名称以&#x200B;**wkDlv_**&#x200B;开头的表的查询:

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然后，将排除进行中工作流使用的表。 为此，使用以下列表恢复进行中投放的查询:

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   其中0是与&#x200B;**[!UICONTROL Being edited]**&#x200B;投放状态匹配的值，85与&#x200B;**[!UICONTROL Stopped]**&#x200B;状态匹配，100与&#x200B;**[!UICONTROL Deleted]**&#x200B;状态匹配。

1. 不再使用的表将使用以下查询删除：

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### 清除导入{#cleanup-of-rejects-generated-by-imports-}生成的拒绝

通过此步骤，可删除在导入过程中未处理所有数据的记录。

1. 对&#x200B;**XtkReject**&#x200B;表执行质量删除，具有以下查询:

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   其中&#x200B;**$(curDate)**&#x200B;是当前服务器日期，从中我们减去为&#x200B;**NmsCleanup_RejectsPurgeDelay**&#x200B;选项（参阅[部署向导](#deployment-wizard)）定义的期间，而&#x200B;**$(l)**&#x200B;是要大量删除的最大记录数。

1. 然后，使用以下查询删除所有孤立拒绝：

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清除工作流实例{#cleanup-of-workflow-instances}

此任务使用其标识符(**lWorkflowId**)和历史记录(**lHistory**)清除每个工作流实例。 它通过再次运行工作表清理任务来删除非活动表。 清除还会删除已删除工作流的所有孤立工作表（wkf%和wkfhisto%）。

>[!NOTE]
>
>在&#x200B;**History in days**（默认值30天）字段中为每个工作流指定历史记录的清除频率。 可以在工作流属性的&#x200B;**执行**&#x200B;选项卡中找到此字段。 如需详细信息，请参阅[此部分](../../workflow/using/workflow-properties.md#execution)。

1. 要恢复要删除的工作流的列表，请使用以下查询:

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查询生成工作流列表，这些将用于删除所有链接的日志、完成的任务和完成的事件，使用以下查询:

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   其中&#x200B;**$(lworkflow)**&#x200B;是工作流的标识符，**$(lhistory)**&#x200B;是历史记录的标识符。

1. 将删除所有未使用的表。 为此目的，所有表都由于使用以下查询(postgresql)的&#x200B;**wkf%**&#x200B;类型掩码而被收集：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然后，将排除挂起工作流实例使用的所有表。 活动工作流的列表使用以下查询恢复：

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然后，恢复每个工作流标识符，以查找正在进行中的工作流使用的表的名称。 这些名称将排除在以前恢复的表的列表之外。
1. “增量查询”类型活动历史记录表使用以下查询被排除：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   其中&#x200B;**$(strcondition)**&#x200B;是与&#x200B;**wkfhisto%**&#x200B;掩码匹配的表的列表。

1. 其余的表将使用以下查询删除：

   ```
   DROP TABLE wkf15487_12;
   ```

### 清除工作流登录{#cleanup-of-workflow-logins}

此任务使用以下查询删除工作流登录：

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 清除孤立工作表{#cleanup-of-orphan-work-tables}

此任务将删除链接到组的孤立工作表。 **NmsGroup**&#x200B;表存储要清除的组（类型不同于0）。 表名的前缀为&#x200B;**grp**。 要标识要清除的组，请使用以下查询:

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 清除访客{#cleanup-of-visitors}

此任务使用成批删除从访客表中删除过时记录。 过时记录是指上次修改时间早于部署向导中定义的保存期（请参阅[部署向导](#deployment-wizard)）的记录。 使用以下查询:

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

其中&#x200B;**$(tsDate)**&#x200B;是当前服务器日期，从中我们减去为&#x200B;**NmsCleanup_VisitorPurgeDelay**&#x200B;选项定义的时段。

### 清除NPAI {#cleanup-of-npai}

此任务允许您从&#x200B;**NmsAddress**&#x200B;表中删除与有效地址匹配的记录。 以下查询用于执行成批删除：

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

其中&#x200B;**status 2**&#x200B;与&#x200B;**[!UICONTROL Valid]**&#x200B;状态匹配，**$(tsDate1)**&#x200B;是当前服务器日期，**$(tsDate2)**&#x200B;与&#x200B;**NmsCleanup_LastCleanup**&#x200B;选项匹配。

### 清除订阅{#cleanup-of-subscriptions-}

此任务使用成批删除从&#x200B;**NmsSubscription**&#x200B;表中清除用户删除的所有订阅。 使用以下查询:

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清除跟踪日志{#cleanup-of-tracking-logs}

此任务将从跟踪日志表和Web跟踪日志表中删除过时记录。 过时记录是指早于部署向导中定义的保存期（请参阅[部署向导](#deployment-wizard)）的记录。

1. 首先，使用以下列表恢复跟踪日志表的查询:

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 成批删除用于清除先前恢复的表列表中的所有表。 使用以下查询:

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   其中&#x200B;**$(tsDate)**&#x200B;是当前服务器日期，从中我们减去为&#x200B;**NmsCleanup_TrackingLogPurgeDelay**&#x200B;选项定义的时段。

1. 跟踪统计信息表将使用成批删除功能清除。 使用以下查询:

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   其中&#x200B;**$(tsDate)**&#x200B;是当前服务器日期，从中我们减去为&#x200B;**NmsCleanup_TrackingStatPurgeDelay**&#x200B;选项定义的期间。

### 清除投放日志{#cleanup-of-delivery-logs}

通过此任务，可清除存储在各种表中的投放日志。

1. 为此，使用以下列表恢复投放日志模式的查询:

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中间源时，在投放映射中未引用&#x200B;**NmsBroadLogMid**&#x200B;表。 **nms:broadLogMid**&#x200B;模式将添加到由上一个查询恢复的列表。
1. 然后，**数据库清理**&#x200B;工作流会从以前恢复的表中清除过时的数据。 使用以下查询:

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   其中&#x200B;**$(tableName)**&#x200B;是模式列表中每个表的名称，**$(option)**&#x200B;是为&#x200B;**NmsCleanup_BroadLogPurgeDelay**&#x200B;选项定义的日期（请参阅[部署向导](#deployment-wizard)）。

1. 最后，该工作流检查&#x200B;**NmsProviderMsgId**&#x200B;表是否存在。 如果是，则使用以下查询删除所有过时数据：

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   其中&#x200B;**$(option)**&#x200B;与为&#x200B;**NmsCleanup_BroadLogPurgeDelay**&#x200B;选项定义的日期匹配（请参阅[部署向导](#deployment-wizard)）。

### 清理NmsEmailErrorStat表{#cleanup-of-the-nmsemailerrorstat-table-}

此任务清除&#x200B;**NmsEmailErrorStat**&#x200B;表。 主项目(**coalesceErrors**)定义两个日期：

* **开始日期**:与NmsLastErrorStatCoalesce选项或表中 **** 的最近日期相匹配的下一个进程的日期。
* **结束日期**:当前服务器日期。

如果开始日期大于或等于结束日期，则不进行任何处理。 在这种情况下，将显示&#x200B;**coalesceUpToDate**&#x200B;消息。

如果开始日期早于结束日期，则清除&#x200B;**NmsEmailErrorStat**&#x200B;表。

**NmsEmailErrorStat**&#x200B;表中在开始和结束日期之间的错误总数使用以下查询来恢复：

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

其中&#x200B;**$end**&#x200B;和&#x200B;**$开始**&#x200B;是之前定义的开始和结束日期。

如果总数大于0:

1. 执行以下查询以仅使错误超过特定阈值（等于20）：

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. 将显示&#x200B;**coalescingErrors**&#x200B;消息。
1. 将创建新连接，以删除在开始和结束日期之间发生的所有错误。 使用以下查询:

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. 每个错误都使用以下查询保存在&#x200B;**NmsEmailErrorStat**&#x200B;表中：

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   其中，每个变量都与前一个查询恢复的值匹配。

1. **开始**&#x200B;变量将使用上一个进程的值更新以完成循环。

循环和任务停止。

清除操作会在&#x200B;**NmsEmailError**&#x200B;和&#x200B;**cleanupNmsMxDomain**&#x200B;表上执行。

### 清理NmsEmailError表{#cleanup-of-the-nmsemailerror-table-}

使用以下查询:

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询将从&#x200B;**NmsEmailError**&#x200B;表中删除&#x200B;**NmsEmailErrorStat**&#x200B;中没有链接记录的所有行。

### 清理NmsMxDomain表{#cleanup-of-the-nmsmxdomain-table-}

使用以下查询:

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查询将从&#x200B;**NmsMxDomain**&#x200B;表中删除&#x200B;**NmsEmailErrorStat**&#x200B;表中没有链接记录的所有行。

### 清理{#cleanup-of-propositions}命题

如果安装了&#x200B;**Interaction**&#x200B;模块，则执行此任务以清除&#x200B;**NmsCompationXxx**&#x200B;表。

对命题表的列表进行恢复，对每个表进行质量删除，使用以下查询:

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

其中&#x200B;**$(option)**&#x200B;是为&#x200B;**NmsCleanup_CompationPurgeDelay**&#x200B;选项定义的日期（请参阅[部署向导](#deployment-wizard)）。

### 清除模拟表{#cleanup-of-simulation-tables}

此任务可清除孤立模拟表(不再链接到优惠模拟或投放模拟)。

1. 要恢复需要清理的模拟的列表，请使用以下查询:

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要删除的表名由&#x200B;**wkSimu_**&#x200B;前缀组成，后跟模拟的标识符(例如：**wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### 清理审计跟踪{#cleanup-of-audit-trail}

使用以下查询:

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

其中&#x200B;**$(tsDate)**&#x200B;是当前服务器日期，从该日期起，将为&#x200B;**XtkCleanup_AuditTrailPurgeDelay**&#x200B;选项定义的期间进行子集化。

### 清除Nmsaddress {#cleanup-of-nmsaddress}

使用以下查询:

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

此查询将删除与iOS和Android相关的所有条目。

### 统计更新和存储优化{#statistics-update}

使用&#x200B;**XtkCleanup_NoStats**&#x200B;选项，可以控制清除工作流的存储优化步骤的行为。

如果&#x200B;**XtkCleanup_NoStats**&#x200B;选项不存在，或其值为0，则将在PostgreSQL上以详细模式(VAFUO VERBOSE ANALYZE)执行存储优化，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 VAXUO将以以下格式输出行：`INFO: vacuuming "public.nmsactivecontact"`和ANALYZE将输出以下格式的行：`INFO: analyzing "public.nmsactivecontact"`。

如果选项的值为1，则不会对任何数据库执行统计信息更新。 工作流日志中将显示以下日志行：`Option 'XtkCleanup_NoStats' is set to '1'`。

如果选项的值为2，则它将在PostgreSQL上以详细模式(ANALYZE VERBOSE)执行存储分析，并更新所有其他数据库的统计信息。 要确保执行此命令，请检查PostgreSQL日志。 ANALYZE将输出以下格式的行：`INFO: analyzing "public.nmsactivecontact"`。

### 订阅清理(NMAC){#subscription-cleanup--nmac-}

此任务将删除与已删除的服务或移动应用程序相关的任何订阅。

要恢复广播模式的列表，请使用以下查询:

```
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

然后，任务恢复链接到&#x200B;**appSubscription**&#x200B;链接的表的名称，并删除这些表。

此清理工作流还会删除自&#x200B;**NmsCleanup_AppSubscriptionRcpPurgeDelay**&#x200B;选项中设置的时间以来未更新的禁用= 1的所有条目。

### 清理会话信息{#cleansing-session-information}

此任务从&#x200B;**sessionInfo**&#x200B;表中清除信息，使用以下查询:

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清理过期事件{#cleansing-expired-events}

此任务可清除在执行实例上接收和存储的事件，以及在控制实例上存档的事件。

### 清理反应{#cleansing-reactions}

此任务清除已删除假设验证的反应（表&#x200B;**NmsRemaMatchRcp**）。
