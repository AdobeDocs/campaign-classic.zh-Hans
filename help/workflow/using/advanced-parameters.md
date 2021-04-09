---
solution: Campaign Classic
product: campaign
title: 高级参数
description: 高级参数
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---

# 高级参数{#advanced-parameters}

活动的属性屏幕有一个&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡，允许您在出现错误时定义行为，即活动的执行期；并允许您输入初始化脚本。 此选项卡有两个版本：

* 简化版本(例如，**[!UICONTROL Start]**&#x200B;和&#x200B;**[!UICONTROL End]**&#x200B;活动)

   ![](assets/wf-advanced-basic.png)

* 更详细的版本(例如，**[!UICONTROL Query]**&#x200B;活动)

   ![](assets/wf-advanced-full.png)

将在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中输入的字段将在以下部分中详细介绍。

## 名称 {#name}

此字段包含活动的内部名称。

## 图像 {#image}

通过此字段，可以更改链接到活动的图像。 有关详细信息，请参阅：[管理活动映像](../../workflow/using/managing-activity-images.md)。

## 执行 {#execution}

此字段允许您定义在触发任务时要执行的操作。 有三种可能的选项：

这些选项通常在购物车中通过右键单击活动来选择。

* **[!UICONTROL Normal]**:活动照常执行。
* **[!UICONTROL Do not activate]**:不执行此任务和以下所有任务（在同一分支中）。
* **[!UICONTROL Activate but do not execute]**:此任务和以下所有任务（在同一分支中）将自动停止。如果您希望在任务启动时存在，则此功能可能很有用。 要手动执行任务，请右键单击活动，然后选择&#x200B;**[!UICONTROL Normal execution]**。

## 关联{#affinity}

您可以选择强制在特定计算机上执行工作流或工作流活动。 为此，您必须在工作流或相关活动层定义一个或多个倾向性。

此[部分](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)详细介绍了高可用性工作流配置。


## Max。 执行期{#max--execution-period}

此字段允许您设置任务过长时的警告。 它不会影响工作流操作。 如果任务在&#x200B;**[!UICONTROL Max. execution period]**&#x200B;结束时尚未完成，则&#x200B;**[!UICONTROL Instance monitoring]**&#x200B;页面将显示此工作流的警告。 可通过该主页的&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡访问此页面。

## 行为{#behavior}

此字段允许您定义要使用异步任务应用的行为。 有两种可能的选项：

* **[!UICONTROL Several tasks authorized]**:可以同时执行多个任务，即使第一个尚未完成也是如此。
* **[!UICONTROL The current task has priority]**:正在进行的任务优先。只要任务在进行中，就不会执行其他任务。

## 时区 {#time-zone}

此字段允许您选择活动的时区。 有关此内容的更多信息：[管理时区](../../workflow/using/managing-time-zones.md)。

## 如果出错{#in-case-of-errors}

此字段允许您定义在活动有错误时要执行的操作。 有两种可能的选项：

* **[!UICONTROL Stop the process]**:工作流将自动停止。其状态更改为&#x200B;**[!UICONTROL Failed]**。 问题解决后，重新开始工作流。
* **[!UICONTROL Ignore]**:不执行此任务和以下所有任务（在同一分支中）。这对于循环任务非常有用。 如果分支将调度程序放在上游，它将在下一执行日期像往常一样开始。

## 初始化脚本{#initialization-script}

通过此字段，可以初始化变量或修改活动属性。 有关详细信息，请参阅：[JavaScript脚本和模板](../../workflow/using/javascript-scripts-and-templates.md)。

## 注释{#comment}

**[!UICONTROL Comment]**&#x200B;字段是可添加说明的免费字段。
