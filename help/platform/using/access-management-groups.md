---
product: campaign
title: 创建和管理操作员组
description: 了解如何授予操作员组访问权限
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 4e99ec73f99264e91ca427542e29bd42da88a3f9
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 1%

---

# 创建和管理操作员组 {#operator-groups}



操作员组是通过 **[!UICONTROL Administration > Access management > Operator groups]** 树中的节点。

## 创建新的操作员组 {#creating-a-new-operator-group}

要创建新的运算符组，请应用以下步骤：

1. 单击 **[!UICONTROL New]** 按钮进行编辑，或者右键单击列表并选择 **[!UICONTROL New]**.
1. 在下部窗口中，从 **[!UICONTROL General]** 选项卡，在相应字段中输入此组的名称和说明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 单击 **[!UICONTROL Content]** 选项卡定义此组的授权。
1. 单击 **[!UICONTROL Add]** 按钮以选择要与组关联的指定权限或操作员。
1. 单击下拉列表或 **[!UICONTROL Folder]** 用于查找要与此组关联的指定权限或操作员的字段。
1. 选择要添加的权限或运算符，然后单击 **[!UICONTROL OK]** 进行验证。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重复此操作以添加其他权限或操作员。

1. 单击 **[!UICONTROL Save]** 按钮以将组添加到列表。

## 默认组 {#default-groups}

默认运算符组为：

1. **[!UICONTROL Administrator]**

   此组中的操作员具有实例的完全访问权限。 管理员是可以访问界面中技术含量最高的部分的用户。 他们持有 **[!UICONTROL Administration]** 角色并确保平台已全部设置。

   此组包含以下已命名权限：

   * **[!UICONTROL ADMINISTRATION]**：有权执行/创建/编辑/删除任何对象，例如工作流、投放、脚本等

1. **[!UICONTROL Delivery operators]**

   此组中的操作员负责管理投放：他们可访问创建和准备投放所需的主要资源（活动类型、投放映射、默认模板、个性化块等）。

   此组包含以下已命名权限：

   * **[!UICONTROL PREPARE DELIVERIES]**：有权创建、编辑和开始投放分析，
   * **[!UICONTROL START DELIVERIES]**：有权批准之前分析的投放。

1. **[!UICONTROL Campaign managers]**

   此组中的操作员可以管理营销活动：通过此组，您可以访问链接到营销活动的对象（计划、项目、工作流、预算等） 在 **[!UICONTROL Campaign]** (可选Adobe Campaign模块)。

   此组包含以下已命名权限：

   * **[!UICONTROL INSERT FOLDERS]**：有权将文件夹插入Adobe Campaign树（前提是您对有关分支具有编辑权限），
   * **[!UICONTROL WORKFLOW]**：使用工作流的权限。

   >[!NOTE]
   >
   >此组不允许操作员开始投放。

1. **[!UICONTROL Content contributors]**

   此组中的操作员可在的框架内访问内容文件夹 **[!UICONTROL Content management]** (可选Adobe Campaign模块)。 此组不授予任何其他权限。

1. **[!UICONTROL Access to reports]**

   此组为外部操作员保留，用于为特定操作员启用营销活动功能板中的报表、计划和论坛图标。

1. **[!UICONTROL Workflow execution]**

   通过此组，您可以分配操作员以管理与营销活动无关的工作流。

1. **[!UICONTROL Workflow supervisors]**

   如果出现有关活动工作流的警报，此组中的操作员会收到电子邮件通知。

1. 本地/中央管理

   这些组允许您使用 **[!UICONTROL Distributed marketing]** (可选Adobe Campaign模块)。

1. **[!UICONTROL Offer managers]**

   此组中的操作员可以创建和维护选件。 有关详细信息，请参阅此 [页面](../../interaction/using/operator-profiles.md).
此组包含以下已命名权限：

   * **[!UICONTROL INSERT FOLDERS]**：有权将文件夹插入Adobe Campaign树（前提是您对有关分支具有编辑权限），
   * **[!UICONTROL EDIT FOLDERS]**：有权更改文件夹属性，如内部名称、标签、关联的图像、子文件夹顺序等。
