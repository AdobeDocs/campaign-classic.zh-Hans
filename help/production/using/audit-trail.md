---
solution: Campaign Classic
product: campaign
title: 审核跟踪
description: 审核跟踪
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---


# 审核跟踪{#audit-trail}

在Adobe Campaign中，**[!UICONTROL Audit trail]**&#x200B;允许您访问实例中所做更改的完整历史记录。

**[!UICONTROL Audit trail]** 实时捕获在您的Adobe Campaign实例中发生的操作和事件的全面列表。它包括一种自助方式，可访问数据历史，以帮助回答以下问题：您的工作流发生了什么，以及谁上次更新了它们，或者您的用户在实例中做了什么。

>[!NOTE]
>
>Adobe Campaign不是审核在用户权限、模板、个性化或活动中所做的更改。\
>审核跟踪只能由实例的管理员管理。

审核跟踪包括三个组件：

* **模式审计跟踪**:检查活动和对模式所做的最后修改。

   有关模式的详细信息，请参阅此[页面](../../configuration/using/data-schemas.md)。

* **工作流审核跟踪**:检查活动和对工作流所做的最后修改，此外还检查工作流的状态，例如：

   * 开始
   * 暂停
   * 停止
   * 重新启动
   * 清除 它等于“清除”历史记录
   * 在模拟模式下模拟与操作开始相等的
   * 唤醒操作等同于立即执行挂起任务
   * 无条件停止

   有关工作流的详细信息，请参阅此[页面](../../workflow/using/about-workflows.md)。

   有关如何监视工作流的详细信息，请参阅[专用部分](../../workflow/using/monitoring-workflow-execution.md)。

* **选项审核跟踪**:检查活动和对选项所做的最后修改。

   有关选项的详细信息，请参阅此[页](../../installation/using/configuring-campaign-options.md)。

## 访问审核跟踪{#accessing-audit-trail}

访问实例的&#x200B;**[!UICONTROL Audit trail]** :

1. 访问实例的&#x200B;**[!UICONTROL Explorer]**&#x200B;菜单。
1. 在&#x200B;**[!UICONTROL Administration]**&#x200B;菜单下，选择&#x200B;**[!UICONTROL Audit]**。

   ![](assets/audit_trail_1.png)

1. 将打开&#x200B;**[!UICONTROL Audit trail]**&#x200B;窗口，其中显示实体的列表。 Adobe Campaign将审核工作流、选项和模式的创建、编辑和删除操作。

   选择其中一个实体可了解有关上次修改的更多信息。

   ![](assets/audit_trail_2.png)

1. **[!UICONTROL Audit entity]**&#x200B;窗口将提供有关所选实体的更多详细信息，例如：

   * **[!UICONTROL Type]** :工作流、选项或模式。
   * **[!UICONTROL Entity]** :您的活动的内部名称。
   * **[!UICONTROL Modified by]** :上次修改此实体的最后一个人员的用户名。
   * **[!UICONTROL Action]** :对此实体执行的上次操作，创建、编辑或删除。
   * **[!UICONTROL Modification date]** :对此实体执行的上次操作的日期。

   代码块为您提供有关实体中确切更改的内容的更多信息。

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>默认情况下，**[!UICONTROL Audit logs]**&#x200B;的保留期设置为180天。 要了解有关如何更改保留期的详细信息，请参阅此[页](../../production/using/database-cleanup-workflow.md#deployment-wizard)。

## 启用/禁用审核跟踪{#enable-disable-audit-trail}

例如，如果您希望在活动库上保存一些空间，可以轻松激活或取消激活特定审核跟踪。

为实现此操作，请执行以下步骤：

1. 访问实例的&#x200B;**[!UICONTROL Explorer]**&#x200B;菜单。
1. 在&#x200B;**[!UICONTROL Administration]**&#x200B;菜单下，选择&#x200B;**[!UICONTROL Platform]**，然后选择&#x200B;**[!UICONTROL Options]**。

   ![](assets/audit_trail_4.png)

1. 根据要激活/取消激活的实体，选择以下选项之一：

   * 对于工作流：**[!UICONTROL XtkAudit_Workflows]**
   * 对于模式:**[!UICONTROL XtkAudit_DataSchema]**
   * 对于选项：**[!UICONTROL XtkAudit_Option]**
   * 对于每个实体：**[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. 如果要启用实体，请将&#x200B;**[!UICONTROL Value]**&#x200B;更改为1；如果要禁用实体，则更改为0。

   ![](assets/audit_trail_6.png)

1. 单击 **[!UICONTROL Save]**。

