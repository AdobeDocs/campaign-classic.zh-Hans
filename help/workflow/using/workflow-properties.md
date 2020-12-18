---
solution: Campaign Classic
product: campaign
title: 工作流属性
description: 了解有关活动工作流属性的更多信息
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---


# 工作流属性{#workflow-properties}

## 执行选项卡{#execution-tab}

工作流中&#x200B;**[!UICONTROL Properties]**&#x200B;窗口的&#x200B;**[!UICONTROL Execution]**&#x200B;选项卡分为3个部分：

![](assets/wf_execution_tab.png)

### 调度程序 {#scheduler}

此部分仅以活动工作流显示。

* **[!UICONTROL Priority]**

   工作流引擎根据此字段中定义的优先级标准处理要执行的工作流。 例如，具有&#x200B;**[!UICONTROL Average]**&#x200B;优先级的所有工作流将在具有&#x200B;**[!UICONTROL Low]**&#x200B;优先级的之前执行。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此选项将工作流开始延迟到较不繁忙的时段。 某些工作流在数据库引擎的资源方面可能成本高昂。 我们建议将执行时间安排在低活动时（例如在夜间）。 在&#x200B;**[!UICONTROL Processes on campaigns]**&#x200B;技术工作流中定义低活动期。

### 执行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安装包含多个工作流服务器，请使用此字段选择将执行该工作流的计算机。 如果此字段中定义的值在任何服务器上都不存在，则工作流将保持挂起状态。

   请参阅此[部分](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

* **[!UICONTROL History in days]**

   数据库的工作表保留执行(任务、事件、日志)的历史记录。 您可以在此定义要存档此工作流的天数：清除过程将每天删除最旧的存档一次。 如果此字段中的值为零，则永远不会删除存档。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能为高级用户保留。 它涉及包含定位活动(查询、合并、交叉点等)的工作流。 选中此选项后，在工作流执行期间发送到查询库的SQLAdobe Campaign将以显示：这意味着您可以分析查询或诊断问题。

   查询显示在&#x200B;**[!UICONTROL SQL logs]**&#x200B;选项卡中，该选项卡添加到工作流(活动工作流除外)和启用选项时添加到&#x200B;**[!UICONTROL Properties]**&#x200B;活动。 **[!UICONTROL Audit]**&#x200B;选项卡还包含SQL查询。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此选项只能用于调试，不能用于生产。 启用该工作流后，该工作流将优先处理，所有其他工作流将停止，直到此工作流完成。

### 错误管理{#error-management}

* **[!UICONTROL Troubleshooting]**

   此字段允许您定义在工作流任务有错误时要执行的操作。 有两种可能的选项：

   * **[!UICONTROL Stop the process]**:工作流会自动暂停。工作流状态变为&#x200B;**[!UICONTROL Failed]**。 问题解决后，使用&#x200B;**[!UICONTROL Start]**&#x200B;或&#x200B;**[!UICONTROL Restart]**&#x200B;按钮重新启动工作流。
   * **[!UICONTROL Ignore]**:触发错误的任务的状态将更改为， **[!UICONTROL Failed]**&#x200B;但工作流会保留 **[!UICONTROL Started]** 状态。此配置与重复任务相关：如果分支包含调度程序，则下次执行工作流时，它将正常开始。

* **[!UICONTROL Consecutive errors]**

   当在&#x200B;**[!UICONTROL In case of errors]**&#x200B;字段中选择&#x200B;**[!UICONTROL Ignore]**&#x200B;值时，此字段变为可用。 您可以指定在停止进程之前可以忽略的错误数。 到达此编号后，工作流状态将变为&#x200B;**[!UICONTROL Failed]**。 如果此字段的值为0，则无论出现多少错误，工作流都不会停止。

* **[!UICONTROL Template]**

   此字段允许您选择当工作流监管器的状态变为&#x200B;**[!UICONTROL Failed]**&#x200B;时要发送给该工作流监管的通知模板。

   如果相关运营商的用户档案有电子邮件地址，则会通过电子邮件通知相关运营商。 要定义工作流监管者，请转到属性的&#x200B;**[!UICONTROL Supervisor(s)]**&#x200B;字段（**[!UICONTROL General]**&#x200B;选项卡）。

   ![](assets/wf-properties_select-supervisors.png)

   **[!UICONTROL Notification to a workflow supervisor]**&#x200B;默认模板包含一个链接，用于通过Web访问Adobe Campaign控制台，以便收件人在登录后可以处理该问题。

   要创建个性化模板，请转到&#x200B;**[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**。

