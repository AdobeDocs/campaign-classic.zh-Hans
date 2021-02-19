---
solution: Campaign Classic
product: campaign
title: 调度程序
description: 进一步了解调度程序工作流活动
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---


# 调度程序 {#scheduler}

**调度程序**&#x200B;是一个持续性任务，在其计划指定的时间激活其过渡。

**[!UICONTROL Scheduler]** 活动应视为排程开始的时间。图表中的活动定向规则与 **[!UICONTROL Start]** 活动相同。此活动不得包含集客过渡。

## 最佳做法 {#best-practices}

* 不要计划工作流超过每15分钟运行一次，因为它可能会妨碍总体系统性能并在数据库中创建块。

* 在工作流中，每个分支使用一个&#x200B;**[!UICONTROL Scheduler]**&#x200B;活动。 请参阅[使用活动](../../workflow/using/workflow-best-practices.md#using-activities)。

* 使用调度程序活动可能导致同时运行多个工作流执行。 例如，您可以让调度程序每小时触发一次工作流执行，但有时整个工作流的执行需要超过一小时。

   如果工作流已在运行，您可能希望跳过执行。 有关如何防止同时执行工作流的详细信息，请参阅[此页](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)。

* 请注意，如果工作流正在执行长期任务（如导入），或wfserver模块已停止一段时间，则可以在数小时后激活过渡。 在这种情况下，可能需要将由任务激活的调度程序的执行限制在一定的时间范围内。

## 配置调度程序活动{#configuring-scheduler-activity}

调度程序定义过渡的激活计划。 要进行配置，请按住多次键单击图形对象，然后单击&#x200B;**[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

向导允许您定义活动的频率和有效期。 配置步骤如下：

1. 选择激活频率，然后单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_scheduler2.png)

1. 给激活时间和时间。 此步骤的参数取决于在上一步中选择的频率。 如果您选择每天启动活动多次，配置选项将如下：

   ![](assets/s_user_segmentation_scheduler3.png)

1. 定义计划的有效期，或指定将执行该订阅的次数。

   ![](assets/s_user_segmentation_scheduler4.png)

1. 检查配置，然后单击&#x200B;**[!UICONTROL Finish]**&#x200B;进行保存。

   ![](assets/s_user_segmentation_scheduler5.png)
