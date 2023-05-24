---
product: campaign
title: 高级参数
description: 高级参数
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 5%

---

# 高级参数{#advanced-parameters}



活动的属性屏幕具有 **[!UICONTROL Advanced]** 选项卡，用于定义出现错误时的行为、活动的执行时段以及输入初始化脚本。 此选项卡有两个版本：

* 简化版本(适用于 **[!UICONTROL Start]** 和 **[!UICONTROL End]** 例如活动)

   ![](assets/wf-advanced-basic.png)

* 更详细的版本(适用于 **[!UICONTROL Query]** 活动)

   ![](assets/wf-advanced-full.png)

要输入的字段 **[!UICONTROL Advanced]** 选项卡，详见以下部分。

## 名称 {#name}

此字段包含活动的内部名称。

## 图像 {#image}

此字段允许您更改链接到活动的图像。 有关更多信息，请参阅 [更改活动图像](managing-activity-images.md).

## 执行 {#execution}

利用此字段，可定义在触发任务时要执行的操作。 有三种可能的选项：

通常可通过右键单击活动在购物车中选择这些选项。

* **[!UICONTROL Normal]**：活动按常规方式执行。
* **[!UICONTROL Do not activate]**：不执行此任务和以下所有任务（在同一分支中）。
* **[!UICONTROL Activate but do not execute]**：此任务和以下所有任务（在同一分支中）会自动停止。 如果您希望在任务启动时到达该位置，则此功能会非常有用。 要手动执行任务，请右键单击活动并选择 **[!UICONTROL Normal execution]**.

## 关联 {#affinity}

您可以选择在特定计算机上强制执行工作流或工作流活动。 要实现此目的，必须在工作流或相关活动的级别定义一个或多个属性。

高可用性工作流配置详见本文 [部分](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).


## 最大值. 执行期 {#max--execution-period}

利用此字段，可设置任务耗时过长的警告。 它不会影响工作流操作。 如果任务在 **[!UICONTROL Max. execution period]** 结束， **[!UICONTROL Instance monitoring]** 页面将显示此工作流的警告。 可通过以下方式访问此页面： **[!UICONTROL Monitoring]** 选项卡。

## 行为 {#behavior}

利用此字段，可定义要应用于使用异步任务的行为。 提供了两个可能的选项：

* **[!UICONTROL Several tasks authorized]**：可以同时执行多个任务，即使第一个任务未完成也是如此。
* **[!UICONTROL The current task has priority]**：正在进行的任务获得优先权。 只要任务正在进行中，就不会执行其他任务。

## 时区 {#time-zone}

此字段允许您选择活动的时区。 有关此内容的更多信息： [管理时区](managing-time-zones.md).

## 发生错误时 {#in-case-of-errors}

利用此字段，可定义活动出错时要执行的操作。 提供了两个可能的选项：

* **[!UICONTROL Suspend the process]**：工作流自动停止。 其状态更改为 **[!UICONTROL Failed]**. 一旦问题得到解决，请重新启动工作流。
* **[!UICONTROL Ignore]**：不执行此任务和以下所有任务（在同一分支中）。 这对周期性任务很有用。 如果分支具有放置在上游的调度程序，则它将在下一个执行日期照常启动。
* **[!UICONTROL Abort on error]**：工作流自动停止，无法重新启动。 其状态更改为 **[!UICONTROL Failed]**.

## 初始化脚本 {#initialization-script}

此字段允许您初始化变量或修改活动属性。 有关更多信息，请参阅： [JavaScript脚本和模板](javascript-scripts-and-templates.md).

## 注释 {#comment}

此 **[!UICONTROL Comment]** 字段是一个自由字段，允许您添加描述。
