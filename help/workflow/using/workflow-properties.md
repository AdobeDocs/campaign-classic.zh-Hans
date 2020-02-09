---
title: 工作流属性
seo-title: 工作流属性
description: 工作流属性
seo-description: null
page-status-flag: never-activated
uuid: bd576cc0-2db8-4519-bcb5-52bf5c811f42
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 71969b30-cc01-4358-9597-f17939720684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 工作流属性{#workflow-properties}

## “执行”选项卡 {#execution-tab}

工作流 **[!UICONTROL Execution]** 中窗口的 **[!UICONTROL Properties]** 选项卡分为三个部分：

![](assets/wf_execution_tab.png)

### 调度程序 {#scheduler}

此部分仅在营销活动工作流中显示。

* **[!UICONTROL Priority]**

   工作流引擎根据此字段中定义的优先级标准处理要执行的工作流。 例如，所有具有优先级的工 **[!UICONTROL Average]** 作流将在具有优先级的工作流之前执 **[!UICONTROL Low]** 行。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此选项可将工作流的开始时间推迟到较少的繁忙时间。 某些工作流程在数据库引擎的资源方面可能代价高昂。 我们建议将执行时间安排在活动量较低的时间（例如在夜间）。 低活动期限在技术工作流中 **[!UICONTROL Processes on campaigns]** 定义。

### 执行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安装包括多个工作流服务器，则使用此字段选择要执行该工作流的计算机。 如果此字段中定义的值在任何服务器上都不存在，则该工作流将保持挂起状态。

   请参阅此 [部分](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

* **[!UICONTROL History in days]**

   数据库的工作表保留执行（任务、事件、日志）的历史记录。 您可以在此定义要为此工作流存档的天数：清除过程将每天删除最旧的存档一次。 如果此字段中的值为零，则永远不会删除存档。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能为高级用户保留。 它涉及包含定位活动（查询、联合、交叉等）的工作流。 选中此选项后，Adobe Campaign中将显示在工作流执行期间发送到数据库的SQL查询：这意味着您可以分析查询或诊断问题。

   查询显示在选 **[!UICONTROL SQL logs]** 项卡中，该选项卡添加到工作流（营销活动工作流除外）和活 **[!UICONTROL Properties]** 动（启用此选项时）。 该选 **[!UICONTROL Audit]** 项卡还包括SQL查询。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此选项只能用于调试，绝不能用于生产。 启用该工作流后，该工作流将优先处理，所有其他工作流将停止，直到此工作流完成。

### 错误管理 {#error-management}

* **[!UICONTROL Troubleshooting]**

   此字段允许您定义在工作流任务有错误时要执行的操作。 有两种可能的选项：

   * **[!UICONTROL Stop the process]**:工作流会自动暂停。 工作流状态将更改为 **[!UICONTROL Failed]**。 解决问题后，使用或按钮重新启动工 **[!UICONTROL Start]** 作流 **[!UICONTROL Restart]** 程。
   * **[!UICONTROL Ignore]**:触发错误的任务的状态将更改为 **[!UICONTROL Failed]**，但工作流会保留状 **[!UICONTROL Started]** 态。 此配置与重复任务相关：如果分支包括调度程序，则下次执行该工作流时，该调度程序将正常启动。

* **[!UICONTROL Consecutive errors]**

   在字段中选择值后， **[!UICONTROL Ignore]** 此字段将变为可 **[!UICONTROL In case of errors]** 用。 您可以指定在进程停止之前可以忽略的错误数。 到达此编号后，工作流状态将更改为 **[!UICONTROL Failed]**。 如果此字段的值为0，则无论出现多少错误，都不会停止工作流。

* **[!UICONTROL Template]**

   通过此字段，您可以选择在工作流主管的状态变为时发送给其的通知模板 **[!UICONTROL Failed]**。

   如果相关运营商的个人资料中有电子邮件地址，他们将收到电子邮件通知。 要定义工作流监管者，请转到属 **[!UICONTROL Supervisor(s)]** 性（选项卡）的字&#x200B;**[!UICONTROL General]** 段。

   ![](assets/wf-properties_select-supervisors.png)

   默 **[!UICONTROL Notification to a workflow supervisor]** 认模板包括通过Web访问Adobe Campaign控制台的链接，以便收件人在登录后可以处理该问题。

   要创建个性化模板，请访问 **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**。

