---
product: campaign
title: 创建和管理操作员组
description: 了解如何授予对操作员组的访问权限
feature: Access Management
role: User, Admin
level: Beginner
exl-id: d5833d3d-e8ef-4f2b-8084-4ba825c79525
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# 创建和管理操作员组 {#operator-groups}

![](../../assets/common.svg)

通过树中的&#x200B;**[!UICONTROL Administration > Access management > Operator groups]**&#x200B;节点创建运算符组。

## 创建新运算符组 {#creating-a-new-operator-group}

要创建新的运算符组，请应用以下步骤：

1. 单击组列表右侧的&#x200B;**[!UICONTROL New]**&#x200B;按钮，或右键单击列表并选择&#x200B;**[!UICONTROL New]**。
1. 在下部窗口的&#x200B;**[!UICONTROL General]**&#x200B;选项卡的相应字段中，输入此组的名称和说明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 单击&#x200B;**[!UICONTROL Content]**&#x200B;选项卡以定义此组的授权。
1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择指定的权限或与组关联的运算符。
1. 单击下拉列表或&#x200B;**[!UICONTROL Folder]**&#x200B;字段右侧文件夹中的，找到要与此组关联的指定权限或运算符。
1. 选择要添加的权限或运算符，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;以验证。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重复此操作可添加其他权限或运算符。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;按钮将组添加到列表。

## 默认组 {#default-groups}

默认的运算符组为：

1. **[!UICONTROL Administrator]**

   此组中的运算符对实例具有完全访问权限。 管理员可以访问界面中技术含量最高的部分。 他们承担着&#x200B;**[!UICONTROL Administration]**&#x200B;角色，并确保平台已全部设置。

   此组包含以下命名权限：

   * **[!UICONTROL ADMINISTRATION]**:有权执行/创建/编辑/删除任何对象，如工作流、交付、脚本等。

1. **[!UICONTROL Delivery operators]**

   此组中的运算符负责管理投放：利用这些资源，可访问创建和准备投放所需的主要资源（营销活动分类、投放映射、默认模板、个性化块等）。

   此组包含以下命名权限：

   * **[!UICONTROL PREPARE DELIVERIES]**:有权创建、编辑和启动投放分析，
   * **[!UICONTROL START DELIVERIES]**:有权批准之前分析的投放。

1. **[!UICONTROL Campaign managers]**

   此组中的操作员可以管理营销活动：它允许您访问链接到营销策划的对象（计划、项目、工作流、预算等） 在&#x200B;**[!UICONTROL Campaign]**&#x200B;框架内(可选的Adobe Campaign模块)。

   此组包含以下命名权限：

   * **[!UICONTROL INSERT FOLDERS]**:将文件夹插入Adobe Campaign树的权限（前提是您拥有相关分支的编辑权限），
   * **[!UICONTROL WORKFLOW]**:有权使用工作流。
   >[!NOTE]
   >
   >此组不允许运算符开始投放。

1. **[!UICONTROL Content contributors]**

   此组中的运算符可以访问&#x200B;**[!UICONTROL Content management]**&#x200B;框架内的Content文件夹(可选的Adobe Campaign模块)。 此组不授予任何其他权限。

1. **[!UICONTROL Access to reports]**

   此组为外部操作员保留，用于通过Web访问访问投放报告。

1. **[!UICONTROL Workflow execution]**

   通过此组，您可以为操作员分配管理与营销活动无关的工作流的权限。

1. **[!UICONTROL Workflow supervisors]**

   如果收到与营销活动工作流有关的警报，此组中的操作员会收到电子邮件通知。

1. 本地/中央管理

   这些组允许您使用&#x200B;**[!UICONTROL Distributed marketing]**(可选的Adobe Campaign模块)。

1. **[!UICONTROL Offer managers]**

   此组中的运算符可以创建和维护选件。 有关此内容的详细信息，请参见此[页面](../../interaction/using/operator-profiles.md)。
此组包含以下命名权限：

   * **[!UICONTROL INSERT FOLDERS]**:将文件夹插入Adobe Campaign树的权限（前提是您拥有相关分支的编辑权限），
   * **[!UICONTROL EDIT FOLDERS]**:有权更改文件夹属性，如内部名称、标签、关联图像、子文件夹顺序等。
