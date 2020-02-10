---
title: 高级参数
seo-title: 高级参数
description: 高级参数
seo-description: null
page-status-flag: never-activated
uuid: 9453d291-921b-4a03-80d1-2c8295f9a986
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f66f1ff5-3601-4eb8-b05d-6f99164890ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 高级参数{#advanced-parameters}

活动的属性屏幕有一个选项 **[!UICONTROL Advanced]** 卡，允许您在出错时定义行为，即活动的执行期；并允许您输入初始化脚本。 此选项卡有两个版本：

* 简化版本(例 **[!UICONTROL Start]** 如， **[!UICONTROL End]** 活动)

   ![](assets/wf-advanced-basic.png)

* 更详细的版本(例 **[!UICONTROL Query]** 如，针对活动)

   ![](assets/wf-advanced-full.png)

以下各节详细介绍了要在 **[!UICONTROL Advanced]** 选项卡中输入的字段。

## 名称 {#name}

此字段包含活动的内部名称。

## Image {#image}

通过此字段，可以更改链接到活动的图像。 有关详细信息，请参阅：管 [理活动图像](../../workflow/using/managing-activity-images.md)。

## 执行 {#execution}

通过此字段，您可以定义在触发任务时要执行的操作。 有三种可能的选项：

这些选项通常在购物车中通过右键单击活动来选择。

* **[!UICONTROL Normal]**:活动照常执行。
* **[!UICONTROL Do not activate]**:不执行此任务和以下所有任务（在同一分支中）。
* **[!UICONTROL Activate but do not execute]**:此任务和以下所有任务（在同一分支中）将自动停止。 如果您希望在任务启动时出现在该位置，则此选项会很有用。 要手动执行任务，请右键单击活动并选择 **[!UICONTROL Normal execution]**。

## 亲和力 {#affinity}

通过此字段，可以强制在特定计算机上执行活动。 For more on this, refer to: [Managing propensity](../../workflow/using/managing-propensity.md).

## Max. 执行期 {#max--execution-period}

此字段允许您为任务过长时设置警告。 它不会影响工作流操作。 如果任务在结束前未完成， **[!UICONTROL Max. execution period]** 则页面将 **[!UICONTROL Instance monitoring]** 显示此工作流的警告。 可通过主页的选 **[!UICONTROL Monitoring]** 项卡访问此页面。

## 行为 {#behavior}

此字段允许您定义要使用异步任务应用的行为。 有两种可能的选项：

* **[!UICONTROL Several tasks authorized]**:即使第一个任务未完成，也可以同时执行多个任务。
* **[!UICONTROL The current task has priority]**:进行中的任务优先。 只要任务正在进行中，就不会执行任何其他任务。

## 时区 {#time-zone}

通过此字段，您可以选择活动的时区。 有关此方面的更多信息：管 [理时区](../../workflow/using/managing-time-zones.md)。

## 如果出错 {#in-case-of-errors}

通过此字段，您可以定义在活动有错误时要执行的操作。 有两种可能的选项：

* **[!UICONTROL Stop the process]**:该工作流将自动停止。 其状态将更改为 **[!UICONTROL Failed]**。 问题解决后，重新启动工作流。
* **[!UICONTROL Ignore]**:不执行此任务和以下所有任务（在同一分支中）。 这对于重复任务可能很有用。 如果分支有一个调度程序放在上游，它将在下一个执行日期像往常一样开始。

## 初始化脚本 {#initialization-script}

通过此字段可初始化变量或修改活动属性。 有关详细信息，请参阅： [JavaScript脚本和模板](../../workflow/using/javascript-scripts-and-templates.md)。

## 评论 {#comment}

该字 **[!UICONTROL Comment]** 段是一个可添加说明的免费字段。
