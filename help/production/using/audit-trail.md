---
product: campaign
title: 审核跟踪
description: 了解如何使用Campaign审核记录监控实例
feature: Audit Trail, Monitoring, Workflows
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 4%

---

# 审核跟踪{#audit-trail}



在Adobe Campaign中 **[!UICONTROL Audit trail]** 允许您访问在实例中所做更改的完整历史记录。

**[!UICONTROL Audit trail]** 可实时捕获您的Adobe Campaign实例中发生的操作和事件的全面列表。 它提供了一种访问数据历史的自助方式，可帮助回答以下问题：您的工作流发生了什么情况、上次更新这些工作流的人员或者您的用户在实例中做了什么。

>[!NOTE]
>
>Adobe Campaign不会审核在用户权限、模板、个性化或营销活动中所做的更改。\
>审核记录只能由实例的管理员管理。

审核记录包括三个组件：

* **架构审核跟踪**：检查活动和对架构进行的最后修改。

  有关架构的详细信息，请参阅此 [页面](../../configuration/using/data-schemas.md).

* **工作流审核跟踪**：检查活动和上次对工作流进行的修改，以及工作流的状态，例如：

   * 开始
   * 暂停
   * 停止
   * 重新启动
   * 清除等于操作清除历史记录
   * 模拟在模拟模式下等于操作“开始”的项
   * 唤醒等于操作立即执行待处理任务
   * 无条件停止

  有关工作流的详细信息，请参阅此 [页面](../../workflow/using/about-workflows.md).

  有关如何监测工作流的详细信息，请参阅 [专用部分](../../workflow/using/monitoring-workflow-execution.md).

* **选项审核跟踪**：检查活动和上次对选项进行的修改。

  有关选项的更多信息，请参阅此 [页面](../../installation/using/configuring-campaign-options.md).

## 访问审核记录 {#accessing-audit-trail}

访问实例的 **[!UICONTROL Audit trail]** ：

1. 访问 **[!UICONTROL Explorer]** 实例菜单。
1. 在 **[!UICONTROL Administration]** 菜单，选择 **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. 此 **[!UICONTROL Audit trail]** 此时将打开一个窗口，其中包含实体列表。 Adobe Campaign将审核工作流、选项和架构的创建、编辑和删除操作。

   选择其中一个实体以了解有关上次修改的更多信息。

   ![](assets/audit_trail_2.png)

1. 此 **[!UICONTROL Audit entity]** 窗口提供了有关所选实体的更多详细信息，例如：

   * **[!UICONTROL Type]** ：工作流、选项或架构。
   * **[!UICONTROL Entity]** ：活动的内部名称。
   * **[!UICONTROL Modified by]** ：上次修改此实体的人的用户名。
   * **[!UICONTROL Action]** ：对此实体执行的最后一个操作，即已创建、已编辑或已删除。
   * **[!UICONTROL Modification date]** ：对此实体执行上次操作的日期。

   代码块为您提供了有关实体中确切更改的更多信息。

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>默认情况下，保留期设置为180天 **[!UICONTROL Audit logs]** . 要了解有关如何更改保留期的更多信息，请参阅此 [页面](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## 启用/禁用审核跟踪 {#enable-disable-audit-trail}

例如，如果您想在数据库上节省一些空间，则可以轻松地为特定活动激活或停用审核跟踪。

为实现此操作，请执行以下步骤：

1. 访问 **[!UICONTROL Explorer]** 实例菜单。
1. 在 **[!UICONTROL Administration]** 菜单，选择 **[!UICONTROL Platform]** 则 **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. 根据要激活/取消激活的实体，选择以下选项之一：

   * 对于工作流： **[!UICONTROL XtkAudit_Workflows]**
   * 对于架构： **[!UICONTROL XtkAudit_DataSchema]**
   * 对于选项： **[!UICONTROL XtkAudit_Option]**
   * 对于每个实体： **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. 更改 **[!UICONTROL Value]** 1表示要启用实体，0表示要禁用实体。

   ![](assets/audit_trail_6.png)

1. 单击 **[!UICONTROL Save]** .
