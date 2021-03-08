---
solution: Campaign Classic
product: campaign
title: 创建和管理操作员组
description: 了解如何授予操作员组访问权限
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# 创建和管理运算符组{#operator-groups}

通过树中的&#x200B;**[!UICONTROL Administration > Access management > Operator groups]**&#x200B;节点创建操作符组。

## 新建一个运算符组{#creating-a-new-operator-group}

要创建新的运算符组，请应用以下步骤：

1. 单击组列表右侧的&#x200B;**[!UICONTROL New]**&#x200B;按钮或右键单击列表并选择&#x200B;**[!UICONTROL New]**。
1. 在下面窗口部分的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，在相应的字段中输入该组的名称和说明。

   ![](assets/s_ncs_user_create_operator_gp.png)

1. 单击&#x200B;**[!UICONTROL Content]**&#x200B;选项卡以定义此组的授权。
1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择指定的右侧或要与组关联的运算符。
1. 单击下拉列表或&#x200B;**[!UICONTROL Folder]**&#x200B;字段右侧的文件夹，以找到要与此组关联的指定权限或运算符。
1. 选择要添加的权限或运算符，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;进行验证。

   ![](assets/s_ncs_user_create_operator_gp03.png)

   重复此操作以添加其他权限或运算符。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;按钮将组添加到列表。

## 默认组{#default-groups}

默认运算符组为：

1. **[!UICONTROL Administrator]**

   此组中的运算符对实例具有完全访问权限。 管理员是可以访问界面中技术最强的部分的用户。 他们担任&#x200B;**[!UICONTROL Administration]**&#x200B;角色并确保平台已全部设置。

   此组包含以下命名权：

   * **[!UICONTROL ADMINISTRATION]**:执行/创建/编辑/删除任何对象(如工作流、投放、脚本等)的权利。

1. **[!UICONTROL Delivery operators]**

   此组中的运营商负责管理投放:它们允许访问创建和准备投放(活动类型、投放映射、默认模板、个性化块等)所需的主要资源。

   此组包含以下已命名权限:

   * **[!UICONTROL PREPARE DELIVERIES]**:创建、编辑和开始投放分析,
   * **[!UICONTROL START DELIVERIES]**:批准之前分析的投放。

1. **[!UICONTROL Campaign managers]**

   此组中的操作员可以管理营销活动:它允许您访问链接到活动(计划、项目、工作流、预算等)的对象 在&#x200B;**[!UICONTROL Campaign]**(可选Adobe Campaign模块)的框架中。

   此组包含以下已命名权限:

   * **[!UICONTROL INSERT FOLDERS]**:将文件夹插入Adobe Campaign树的权利（前提是您对相关分支拥有编辑权限），
   * **[!UICONTROL WORKFLOW]**:使用工作流。

   >[!NOTE]
   >
   >此组不允许运算符开始投放。

1. **[!UICONTROL Content contributors]**

   此组中的运算符可以访问&#x200B;**[!UICONTROL Content management]**(可选Adobe Campaign模块)框架中的“内容”文件夹。 此组不授予任何额外权利。

1. **[!UICONTROL Access to reports]**

   此组保留给外部操作员，以便通过Web访问访问访问投放报告。

1. **[!UICONTROL Workflow execution]**

   通过此组，您可以分配操作员管理与工作流无关的活动的权利。

1. **[!UICONTROL Workflow supervisors]**

   此组中的运算符会收到电子邮件通知，以防出现与活动工作流有关的警报。

1. 本地/中央管理

   这些组允许您使用&#x200B;**[!UICONTROL Distributed marketing]**(可选Adobe Campaign模块)。

1. **[!UICONTROL Offer managers]**

   此组中的运算符可以创建和维护优惠。 有关此的详细信息，请参阅此[页](../../interaction/using/operator-profiles.md)。
此组包含以下已命名权限:

   * **[!UICONTROL INSERT FOLDERS]**:将文件夹插入Adobe Campaign树的权利（前提是您对相关分支具有编辑权限），
   * **[!UICONTROL EDIT FOLDERS]**:有权更改文件夹属性，如内部名称、标签、关联图像、子文件夹顺序等。



