---
product: campaign
title: 工作流属性
description: 了解有关Campaign工作流属性的更多信息
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---

# 工作流属性{#workflow-properties}

## “执行”选项卡{#execution-tab}

工作流中&#x200B;**[!UICONTROL Properties]**&#x200B;窗口的&#x200B;**[!UICONTROL Execution]**&#x200B;选项卡分为3个部分：

![](assets/wf_execution_tab.png)

### 调度程序 {#scheduler}

此部分仅显示在营销活动工作流中。

* **[!UICONTROL Priority]**

   工作流引擎根据此字段中定义的优先级条件处理要执行的工作流。 例如，所有具有&#x200B;**[!UICONTROL Average]**&#x200B;优先级的工作流都将在执行具有&#x200B;**[!UICONTROL Low]**&#x200B;优先级的工作流之前执行。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此选项可将工作流的开始时间推迟到不太忙的时段。 某些工作流在数据库引擎的资源方面可能成本高昂。 我们建议将执行时间安排在活动较少的时间（例如在夜间）。 在&#x200B;**[!UICONTROL Processes on campaigns]**&#x200B;技术工作流中定义低活动期。

### 执行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安装包含多个工作流服务器，请使用此字段选择要执行工作流的计算机。 如果此字段中定义的值在任何服务器上都不存在，则工作流将保持挂起状态。

   请参阅此[部分](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

* **[!UICONTROL History in days]**

   数据库的工作表保留执行的历史记录（任务、事件、日志）。 在此，您可以定义要为此工作流存档的天数：清理过程将每天删除最早的存档一次。 如果此字段中的值为零，则永远不会删除存档。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能为高级用户保留。 它涉及包含定向活动（查询、并集、交集等）的工作流。 选中此选项后，工作流执行期间发送到数据库的SQL查询将显示在Adobe Campaign中：这意味着您可以分析查询以优化查询或诊断问题。

   查询显示在&#x200B;**[!UICONTROL SQL logs]**&#x200B;选项卡中，该选项卡在启用选项时添加到工作流（营销活动工作流除外）和&#x200B;**[!UICONTROL Properties]**&#x200B;活动。 **[!UICONTROL Audit]**&#x200B;选项卡还包含SQL查询。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此选项只能用于调试，而不能用于生产。 启用该工作流后，将优先考虑该工作流，并停止所有其他工作流，直到该工作流完成。

### 错误管理{#error-management}

* **[!UICONTROL Troubleshooting]**

   利用此字段，可定义在工作流任务出错时要执行的操作。 有两种可能的选项：

   * **[!UICONTROL Stop the process]**:工作流会自动暂停。工作流状态更改为&#x200B;**[!UICONTROL Failed]**。 解决问题后，请使用&#x200B;**[!UICONTROL Start]**&#x200B;或&#x200B;**[!UICONTROL Restart]**&#x200B;按钮重新启动工作流。
   * **[!UICONTROL Ignore]**:触发错误的任务的状态将更改为，但 **[!UICONTROL Failed]**&#x200B;工作流会保留状 **[!UICONTROL Started]** 态。此配置与定期任务相关：如果分支包含调度程序，则下次执行工作流时将正常启动该调度程序。

* **[!UICONTROL Consecutive errors]**

   在&#x200B;**[!UICONTROL In case of errors]**&#x200B;字段中选择&#x200B;**[!UICONTROL Ignore]**&#x200B;值后，此字段将变为可用。 您可以指定在进程停止前可忽略的错误数。 达到此数字后，工作流状态将变为&#x200B;**[!UICONTROL Failed]**。 如果此字段的值为0，则无论出现多少错误，工作流都将永远不会停止。

* **[!UICONTROL Template]**

   利用此字段，可选择要在工作流主管的状态变为&#x200B;**[!UICONTROL Failed]**&#x200B;时发送给其的通知模板。

   如果相关操作员的用户档案中有电子邮件地址，则会通过电子邮件通知相关操作员。 要定义工作流监管者，请转到属性的&#x200B;**[!UICONTROL Supervisor(s)]**&#x200B;字段（**[!UICONTROL General]**&#x200B;选项卡）。

   ![](assets/wf-properties_select-supervisors.png)

   **[!UICONTROL Notification to a workflow supervisor]**&#x200B;默认模板包含用于通过Web访问Adobe Campaign控制台的链接，以便收件人在登录后即可处理此问题。

   要创建个性化模板，请转到&#x200B;**[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**。
