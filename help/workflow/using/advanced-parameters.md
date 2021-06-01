---
product: campaign
title: 高级参数
description: 高级参数
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 6c90ac2f-0d2b-48b0-9245-3e5e3a3d027c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%

---

# 高级参数{#advanced-parameters}

活动的属性屏幕中有一个&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡，利用该选项卡，可定义出错时的行为，即活动的执行期；和允许您输入初始化脚本。 此选项卡有两个版本：

* 简化版本（例如，**[!UICONTROL Start]**&#x200B;和&#x200B;**[!UICONTROL End]**&#x200B;活动）

   ![](assets/wf-advanced-basic.png)

* 更详细的版本（例如，对于&#x200B;**[!UICONTROL Query]**&#x200B;活动）

   ![](assets/wf-advanced-full.png)

以下各节详细介绍了在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中输入的字段。

## 名称 {#name}

此字段包含活动的内部名称。

## 图像 {#image}

利用此字段，可更改链接到活动的图像。 有关更多信息，请参阅：[管理活动图像](../../workflow/using/managing-activity-images.md)。

## 执行 {#execution}

利用此字段，可定义在触发任务时要执行的操作。 有三种可能的选项：

这些选项通常通过右键单击活动在购物车中进行选择。

* **[!UICONTROL Normal]**:与往常一样，执行活动。
* **[!UICONTROL Do not activate]**:不会执行此任务和以下所有任务（在同一分支中）。
* **[!UICONTROL Activate but do not execute]**:此任务和以下所有任务（在同一分支中）将自动停止。如果您希望在任务启动时存在该位置，则此选项会非常有用。 要手动执行任务，请右键单击活动并选择&#x200B;**[!UICONTROL Normal execution]**。

## 亲和度 {#affinity}

您可以选择在特定计算机上强制执行工作流或工作流活动。 为此，您必须在工作流或相关活动的级别定义一个或多个倾向性。

此[部分](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)中详细描述了高可用性工作流配置。


## Max。 执行期{#max--execution-period}

利用此字段，可在任务过长时设置警告。 它不会影响工作流操作。 如果任务在&#x200B;**[!UICONTROL Max. execution period]**&#x200B;结束时尚未完成，则&#x200B;**[!UICONTROL Instance monitoring]**&#x200B;页面将显示此工作流的警告。 可通过主页的&#x200B;**[!UICONTROL Monitoring]**&#x200B;选项卡访问此页面。

## 行为 {#behavior}

利用此字段，可定义要使用异步任务应用的行为。 有两种可能的选项：

* **[!UICONTROL Several tasks authorized]**:即使第一个任务未完成，也可以同时执行多个任务。
* **[!UICONTROL The current task has priority]**:正在进行的任务优先处理。只要任务正在进行中，就不会执行其他任务。

## 时区 {#time-zone}

利用此字段，可选择活动的时区。 有关此内容的更多信息：[管理时区](../../workflow/using/managing-time-zones.md)。

## 出现错误{#in-case-of-errors}时

利用此字段，可定义在活动出错时要执行的操作。 有两种可能的选项：

* **[!UICONTROL Stop the process]**:工作流将自动停止。其状态将变为&#x200B;**[!UICONTROL Failed]**。 解决问题后，重新启动工作流。
* **[!UICONTROL Ignore]**:不会执行此任务和以下所有任务（在同一分支中）。这对于定期任务很有用。 如果分支具有上游调度程序，则该调度程序将像往常一样在下一个执行日期开始。

## 初始化脚本{#initialization-script}

利用此字段，可初始化变量或修改活动属性。 有关更多信息，请参阅：[JavaScript脚本和模板](../../workflow/using/javascript-scripts-and-templates.md)。

## 注释 {#comment}

**[!UICONTROL Comment]**&#x200B;字段是可添加说明的自由字段。
