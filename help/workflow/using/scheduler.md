---
product: campaign
title: 调度程序
description: 了解有关调度程序工作流活动的更多信息
feature: Workflows
exl-id: 30a9bd2a-afb1-481c-ab5f-5acebd9cbb5a
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---

# 调度程序 {#scheduler}

![](../../assets/common.svg)

的 **调度程序** 是在其计划指定的时间激活其过渡的持久任务。

**[!UICONTROL Scheduler]** 活动应视为排程开始的时间。图表中的活动定向规则与 **[!UICONTROL Start]** 活动相同。此活动不得包含集客过渡。

## 最佳实践 {#best-practices}

* 请勿将工作流安排为每15分钟运行一次以上，因为它可能会妨碍系统的整体性能并在数据库中创建块。

* 请勿使用多个 **[!UICONTROL Scheduler]** 工作流中每个分支的活动。 请参阅 [使用活动](workflow-best-practices.md#using-activities).

* 使用调度程序活动可能会导致同时运行多个工作流的执行。 例如，您可以让调度程序每小时触发一次工作流执行，但有时整个工作流的执行需要超过一小时。

   如果工作流已经运行，您可能需要跳过执行。 有关如何防止同时执行工作流的更多信息，请参阅 [本页](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

* 请注意，如果工作流正在执行长期任务（如导入），或wfserver模块已停止一段时间，则可在数小时后激活该过渡。 在这种情况下，可能需要将调度程序激活的任务的执行限制到特定的时间范围。

## 配置调度程序活动 {#configuring-scheduler-activity}

调度程序定义过渡的激活调度。 要配置对象，请双击图形对象，然后单击 **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

通过向导，您可以定义活动的频率和有效期。 配置步骤如下所示：

1. 选择激活频率并单击 **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. 提供激活时间和天数。 此步骤的参数取决于在上一步中选择的频率。 如果您选择每天多次启动活动，则配置选项将如下所示：

   ![](assets/s_user_segmentation_scheduler3.png)

1. 定义计划的有效期，或指定计划的执行次数。

   ![](assets/s_user_segmentation_scheduler4.png)

1. 检查配置并单击 **[!UICONTROL Finish]** 保存。

   ![](assets/s_user_segmentation_scheduler5.png)
