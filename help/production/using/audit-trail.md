---
title: 审核跟踪
seo-title: 审核跟踪
description: 审核跟踪
seo-description: null
page-status-flag: never-activated
uuid: b96b93b6-e002-4c67-b9ce-b66cdcd395d7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: aa147a8c-9d93-45c8-bb4a-db714739f4c0
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 4%

---


# 审核跟踪{#audit-trail}

在Adobe Campaign中， **[!UICONTROL Audit trail]** 您可以访问实例中所做更改的完整历史记录。

**[!UICONTROL Audit trail]** 实时捕获在您的Adobe Campaign实例中发生的操作和事件的全面列表。 它包括一种自助方式，用于访问数据历史，以帮助回答以下问题：您的工作流发生了什么，谁上次更新了它们，或者您的用户在实例中做了什么。

>[!NOTE]
>
>Adobe Campaign不审核在用户权限、模板、个性化或活动中所做的更改。\
>审核跟踪只能由实例的管理员管理。

审核跟踪包括三个组件：

* **模式审核跟踪**:检查活动和对模式所做的最后修改。

   For more information on schemas, refer to this [page](../../configuration/using/data-schemas.md).

* **工作流审核跟踪**:检查活动和对工作流所做的最后修改，以及工作流的状态，例如：

   * 开始
   * 暂停
   * 停止
   * 重新启动
   * 清除 它等于“清除”历史记录操作
   * 在模拟模式下模拟与操作开始相等的内容
   * 唤醒操作等于立即执行挂起任务
   * 无条件停止

   For more information on workflows, refer to this [page](../../workflow/using/about-workflows.md).

   有关如何监视工作流的详细信息，请参阅专 [门的部分](../../workflow/using/monitoring-workflow-execution.md)。

* **选项审核跟踪**:检查活动和对选项所做的最后修改。

   For more information on options, refer to this [page](../../installation/using/configuring-campaign-options.md).

## 访问审核跟踪 {#accessing-audit-trail}

访问实例的 **[!UICONTROL Audit trail]** :

1. 访问 **[!UICONTROL Explorer]** 实例菜单。
1. 在菜单 **[!UICONTROL Administration]** 下，选择 **[!UICONTROL Audit]** 。

   ![](assets/audit_trail_1.png)

1. 窗 **[!UICONTROL Audit trail]** 口随图元列表打开。 Adobe Campaign将审核工作流、选项和模式的创建、编辑和删除操作。

   选择其中一个实体以进一步了解上次修改。

   ![](assets/audit_trail_2.png)

1. 该窗 **[!UICONTROL Audit entity]** 口会提供有关所选实体的更多详细信息，例如：

   * **[!UICONTROL Type]** :工作流、选项或模式。
   * **[!UICONTROL Entity]** :活动的内部名称。
   * **[!UICONTROL Modified by]** :上次修改此实体的最后一个人的用户名。
   * **[!UICONTROL Action]** :对此实体执行的上次操作，创建、编辑或删除。
   * **[!UICONTROL Modification date]** :对此实体执行的上次操作的日期。

   代码块会为您提供有关实体中确切更改的内容的更多信息。

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>默认情况下，保留期设置为180天 **[!UICONTROL Audit logs]** 。 要进一步了解如何更改保留期，请参阅本 [页](../../production/using/database-cleanup-workflow.md#deployment-wizard)。

## 启用／禁用审核跟踪 {#enable-disable-audit-trail}

例如，如果您希望在活动库上节省一些空间，则可以轻松激活或取消激活特定数据的审核跟踪。

为实现此操作，请执行以下步骤：

1. 访问 **[!UICONTROL Explorer]** 实例菜单。
1. 在菜单 **[!UICONTROL Administration]** 下，选择 **[!UICONTROL Platform]** ，然后 **[!UICONTROL Options]** 。

   ![](assets/audit_trail_4.png)

1. 根据要激活／取消激活的实体，选择以下选项之一：

   * 对于工作流： **[!UICONTROL XtkAudit_Workflows]**
   * 对于模式: **[!UICONTROL XtkAudit_DataSchema]**
   * 对于选项： **[!UICONTROL XtkAudit_Option]**
   * 对于每个实体： **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. 如果要 **[!UICONTROL Value]** 启用实体，请将其更改为1；如果要禁用实体，则将其更改为0。

   ![](assets/audit_trail_6.png)

1. 单击 **[!UICONTROL Save]** .

