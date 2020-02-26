---
title: 调度程序
seo-title: 调度程序
description: 调度程序
seo-description: null
page-status-flag: never-activated
uuid: e814b978-2edd-442e-9334-9633bc9ec63a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 093dbe8a-494f-4fe7-8614-3bf58486e34c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# 调度程序{#scheduler}

调度 **程序** (Scheduler)是一个永久任务，在调度程序指定的时间激活其过渡。

活 **[!UICONTROL Scheduler]** 动应视为预定开始。 图表中的活动定位规则与活动的定位规 **[!UICONTROL Start]** 则相同。 此活动不得具有入站过渡。

最好不要将工作流计划为每15分钟以上运行一次，因为它可能会妨碍总体系统性能并在数据库中创建块。

在构建工作流时，每个分支不能使用 **[!UICONTROL Scheduler]** 多个活动。 For more on this, refer to: [Using activities](../../workflow/using/workflow-best-practices.md#using-activities).

调度程序定义转换的激活调度。 要进行配置，请双击图形对象，然后单击 **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

通过向导，您可以定义活动的频率和有效期。 配置步骤如下：

1. 选择激活频率并单击 **[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_scheduler2.png)

1. 请提供激活时间和天数。 此步骤的参数取决于在上一步骤中选择的频率。 如果选择每天多次启动活动，则配置选项将如下：

   ![](assets/s_user_segmentation_scheduler3.png)

1. 定义计划的有效期，或指定执行计划的次数。

   ![](assets/s_user_segmentation_scheduler4.png)

1. 检查配置并单击 **[!UICONTROL Finish]** 以保存。

   ![](assets/s_user_segmentation_scheduler5.png)

使用调度程序活动可能导致同时运行多个工作流的执行。 例如，您可以让一个调度程序每小时触发工作流执行，但有时整个工作流的执行需要超过一小时。 如果工作流已在运行，您可能希望跳过执行。 有关如何防止同时执行工作流的详细信息，请参阅 [本页](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)。

另请注意，如果工作流执行长期任务（如导入），或wfserver模块停止了一段时间，则可以在数小时后激活过渡。 在这种情况下，可能需要将由调度器激活的任务的执行限制在一定的时间范围内。
