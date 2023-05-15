---
product: campaign
title: 工作流属性
description: 了解有关Campaign工作流属性的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 38%

---

# 工作流属性{#workflow-properties}



## “执行”选项卡 {#execution-tab}

的 **[!UICONTROL Execution]** 选项卡 **[!UICONTROL Properties]** 窗口，可划分为3个部分：

![](assets/wf_execution_tab.png)

### 调度程序 {#scheduler}

此部分仅显示在营销活动工作流中。

* **[!UICONTROL Priority]**

   工作流引擎根据此字段中定义的优先级条件处理要执行的工作流。 例如，所有使用 **[!UICONTROL Average]** 优先级将在具有 **[!UICONTROL Low]** 优先级。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此选项可将工作流的开始时间推迟到不太忙的时段。 某些工作流在数据库引擎的资源方面可能成本高昂。 我们建议将执行时间安排在活动较少的时间（例如在夜间）。 低活动期限在 **[!UICONTROL Processes on campaigns]** 技术工作流。

### 执行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安装包括多个工作流服务器，请使用此字段选择将要执行工作流的计算机。如果此字段中定义的值在任何服务器上都不存在，则工作流将保持待处理状态。

   请参阅 [Campaign Classicv7安装指南](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL History in days]**

   数据库的工作表保留执行的历史记录（任务、事件、日志）。 您可以在此处定义此工作流的存档天数：清理过程将每天删除一次最旧的存档。如果此字段中的值为零，则绝不会删除存档。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能是为高级用户保留的。它涉及包含定位活动（查询、并集、交集等）的工作流。选中此选项后，在工作流执行期间发送到数据库的 SQL 查询将显示在 Adobe Campaign 中：这意味着您可以分析它们以优化查询或诊断问题。

   查询显示在 **[!UICONTROL SQL logs]** 选项卡，可添加到工作流（营销活动工作流除外）和 **[!UICONTROL Properties]** 活动。 的 **[!UICONTROL Audit]** 选项卡还包含SQL查询。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此选项只能用于调试，而不能用于生产。 启用该工作流后，将优先考虑该工作流，并停止所有其他工作流，直到该工作流完成。

### 错误管理 {#error-management}

* **[!UICONTROL Troubleshooting]**

   此字段可让您定义在工作流任务出错时要执行的操作。提供了两个可能的选项：

   * **[!UICONTROL Stop the process]**:工作流会自动暂停。 工作流状态更改为 **[!UICONTROL Failed]**. 解决问题后，请使用 **[!UICONTROL Start]** 或 **[!UICONTROL Restart]** 按钮。
   * **[!UICONTROL Ignore]**:触发错误的任务的状态更改为 **[!UICONTROL Failed]**，但工作流会将 **[!UICONTROL Started]** 状态。 此配置与定期任务相关：如果分支包含调度程序，它将在下次执行工作流时正常启动。

* **[!UICONTROL Consecutive errors]**

   当 **[!UICONTROL Ignore]** 值 **[!UICONTROL In case of errors]** 字段。 您可以指定在流程停止前可忽略的错误的数量。达到此数字后，工作流状态将更改为 **[!UICONTROL Failed]**. 如果此字段的值为 0，则无论错误数量是多少，工作流都绝不会停止。

* **[!UICONTROL Template]**

   利用此字段，可选择要在工作流主管的状态更改为 **[!UICONTROL Failed]**.

   如果相关操作员的用户档案中有电子邮件地址，则会通过电子邮件通知相关操作员。 要定义工作流主管，请转到 **[!UICONTROL Supervisor(s)]** 属性的字段(**[!UICONTROL General]** 选项卡。

   ![](assets/wf-properties_select-supervisors.png)

   的 **[!UICONTROL Notification to a workflow supervisor]** 默认模板包含一个用于通过Web访问Adobe Campaign控制台的链接，以便收件人在登录后即可处理该问题。

   要创建个性化模板，请转到 **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**.
