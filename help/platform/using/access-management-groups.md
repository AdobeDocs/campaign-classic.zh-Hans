---
product: campaign
title: 创建和管理操作员组
description: 了解如何授予对操作员组的访问权限
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 创建和管理操作员组 {#operator-groups}

![](../../assets/common.svg)

运算符组通过 **[!UICONTROL Administration > Access management > Operator groups]** 树中的节点。

## 创建新运算符组 {#creating-a-new-operator-group}

要创建新的运算符组，请应用以下步骤：

1. 单击 **[!UICONTROL New]** 按钮或右键单击列表并选择 **[!UICONTROL New]**.
1. 在下部窗口中，从 **[!UICONTROL General]** 选项卡，在相应字段中输入此组的名称和说明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 单击 **[!UICONTROL Content]** 选项卡来定义此群组的授权。
1. 单击 **[!UICONTROL Add]** 按钮选择要与组关联的指定权限或运算符。
1. 单击下拉列表或右侧文件夹上的 **[!UICONTROL Folder]** 字段，找到要与此组关联的指定权限或运算符。
1. 选择要添加的权限或运算符，然后单击 **[!UICONTROL OK]** 验证。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重复此操作可添加其他权限或运算符。

1. 单击 **[!UICONTROL Save]** 按钮将群组添加到列表。

## 默认组 {#default-groups}

默认的运算符组为：

1. **[!UICONTROL Administrator]**

   此组中的运算符对实例具有完全访问权限。 管理员可以访问界面中技术含量最高的部分。 他们握着 **[!UICONTROL Administration]** 角色，并确保平台已全部设置。

   此组包含以下命名权限：

   * **[!UICONTROL ADMINISTRATION]**:有权执行/创建/编辑/删除任何对象，如工作流、交付、脚本等。

1. **[!UICONTROL Delivery operators]**

   此组中的运算符负责管理投放：利用这些资源，可访问创建和准备投放所需的主要资源（营销活动分类、投放映射、默认模板、个性化块等）。

   此组包含以下命名权限：

   * **[!UICONTROL PREPARE DELIVERIES]**:有权创建、编辑和启动投放分析，
   * **[!UICONTROL START DELIVERIES]**:有权批准之前分析的投放。

1. **[!UICONTROL Campaign managers]**

   此组中的操作员可以管理营销活动：它允许您访问链接到营销策划的对象（计划、项目、工作流、预算等） 在 **[!UICONTROL Campaign]** (可选的Adobe Campaign模块)。

   此组包含以下命名权限：

   * **[!UICONTROL INSERT FOLDERS]**:将文件夹插入Adobe Campaign树的权限（前提是您拥有相关分支的编辑权限），
   * **[!UICONTROL WORKFLOW]**:有权使用工作流。
   >[!NOTE]
   >
   >此组不允许运算符开始投放。

1. **[!UICONTROL Content contributors]**

   此组中的运算符可以访问 **[!UICONTROL Content management]** (可选的Adobe Campaign模块)。 此组不授予任何其他权限。

1. **[!UICONTROL Access to reports]**

   此组为外部操作员保留，用于通过Web访问访问投放报告。

1. **[!UICONTROL Workflow execution]**

   通过此组，您可以为操作员分配管理与营销活动无关的工作流的权限。

1. **[!UICONTROL Workflow supervisors]**

   如果收到与营销活动工作流有关的警报，此组中的操作员会收到电子邮件通知。

1. 本地/中央管理

   这些组允许您使用 **[!UICONTROL Distributed marketing]** (可选的Adobe Campaign模块)。

1. **[!UICONTROL Offer managers]**

   此组中的运算符可以创建和维护选件。 有关此内容的更多信息，请参阅此内容 [页面](../../interaction/using/operator-profiles.md).
此组包含以下命名权限：

   * **[!UICONTROL INSERT FOLDERS]**:将文件夹插入Adobe Campaign树的权限（前提是您拥有相关分支的编辑权限），
   * **[!UICONTROL EDIT FOLDERS]**:有权更改文件夹属性，如内部名称、标签、关联图像、子文件夹顺序等。
