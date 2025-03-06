---
product: campaign
title: 高级参数
description: 高级参数
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 5%

---

# 高级参数{#advanced-parameters}



活动的属性屏幕中有一个&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡，通过该选项卡可以定义发生错误时的行为、活动的执行时段以及输入初始化脚本。 此选项卡有两个版本：

* 简化版本（针对实例的&#x200B;**[!UICONTROL Start]**&#x200B;和&#x200B;**[!UICONTROL End]**&#x200B;活动）

  ![](assets/wf-advanced-basic.png)

* 更详细的版本（例如&#x200B;**[!UICONTROL Query]**&#x200B;活动的）

  ![](assets/wf-advanced-full.png)

以下各节详细介绍了要在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中输入的字段。

## 名称 {#name}

此字段包含活动的内部名称。

## 图像 {#image}

此字段允许您更改链接到活动的图像。 有关详细信息，请参阅[更改活动图像](managing-activity-images.md)。

## 执行 {#execution}

利用此字段，可定义在触发任务时要执行的操作。 有三种可能的选项：

通常可通过右键单击活动在购物车中选择这些选项。

* **[!UICONTROL Normal]**：活动照常执行。
* **[!UICONTROL Do not activate]**：不执行此任务和以下所有任务（在同一分支中）。
* **[!UICONTROL Activate but do not execute]**：此任务和以下所有任务（在同一分支中）将自动停止。 如果希望在任务启动时到达该位置，此功能会很有用。 要手动执行任务，请右键单击该活动并选择&#x200B;**[!UICONTROL Normal execution]**。

## 关联 {#affinity}

您可以选择在特定计算机上强制执行工作流或工作流活动。 要实现此目的，必须在工作流或相关活动的级别定义一个或多个属性。

高可用性工作流配置在此[部分](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)中有详细说明。


## 最大 执行期 {#max--execution-period}

利用此字段，可设置任务耗时过长的警告。 它不会影响工作流操作。 如果任务在&#x200B;**[!UICONTROL Max. execution period]**&#x200B;结束前未完成，则&#x200B;**[!UICONTROL Instance monitoring]**&#x200B;页面将显示此工作流的警告。 通过主页的&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡访问此页面。

## 行为 {#behavior}

利用此字段，可定义要应用于使用异步任务的行为。 提供了两个可能的选项：

* **[!UICONTROL Several tasks authorized]**：可以同时执行多个任务，即使第一个任务未完成。
* **[!UICONTROL The current task has priority]**：进行中的任务优先。 只要任务正在进行中，就不会执行其他任务。

## 时区 {#time-zone}

此字段允许您选择活动的时区。 有关详情： [管理时区](managing-time-zones.md)。

## 发生错误时 {#in-case-of-errors}

利用此字段，可定义活动出错时要执行的操作。 提供了两个可能的选项：

* **[!UICONTROL Suspend the process]**：工作流自动停止。 其状态更改为&#x200B;**[!UICONTROL Failed]**。 问题解决后，请重新启动工作流。
* **[!UICONTROL Ignore]**：不执行此任务和以下所有任务（在同一分支中）。 这对于周期性任务可能很有用。 如果分支具有置于上游的调度程序，则它将在下一个执行日期正常启动。
* **[!UICONTROL Abort on error]**：工作流已自动停止，无法重新启动。 其状态更改为&#x200B;**[!UICONTROL Failed]**。

## 初始化脚本 {#initialization-script}

此字段允许您初始化变量或修改活动属性。 有关详细信息，请参阅[JavaScript脚本和模板](javascript-scripts-and-templates.md)。

## 注释 {#comment}

**[!UICONTROL Comment]**&#x200B;字段是一个可让您添加说明的空闲字段。
