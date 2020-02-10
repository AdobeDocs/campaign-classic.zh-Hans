---
title: 关于分布式营销
seo-title: 关于分布式营销
description: 关于分布式营销
seo-description: null
page-status-flag: never-activated
uuid: 7f7ece67-c644-4072-a06c-c5b49f3acb5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 6d694f5c-1d1f-4686-b3bf-8697d919a0c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 关于分布式营销{#about-distributed-marketing}

## 简介 {#introduction}

Adobe Campaign提供一个分 **布式营销应用程序** ，用于在中央实体（总部、营销部门等）之间实施协作式营销活动地方实体（销售点、区域代理等）。 此协作基于共享工作区（称为“”） **[!UICONTROL list of campaign packages]**，在该工作区中，集中创建的营销活动模板和实例会提供给本地实体。

中央实体提供本地实体可能使用的营销活动。 营销活动由表示本地或协作营销活动的包实现。 要使用营销活动，本地实体必须对其进行订购，并且该订单必须获得批准。

>[!CAUTION]
>
>“分布式营销”模块是“营销 **活动** ”选项。 请检查您的许可协议。

## 术语 {#terminology}

### 中央实体 {#central-entities}

中央实体由负责指定通信和协助当地实体执行其营销活动的营销经营者组成。

分布式营销模块允许中心实体：

* 为本地实体设置营销活动包，
* 提高本地实体在客户／潜在客户沟通、定位、内容等方面的自主性。
* 管理和控制成本，
* 处理代理网络。

### 本地实体 {#local-entities}

本地实体可以是特定本地运营商（国家或地区经理、品牌经理等）的代理、商店或组。

分布式营销使本地实体在优化执行成本的同时拥有更大的自主权。

### 本地化 {#localization}

本地化是指本地实体修改营销活动的目标和内容的能力。 本地化的可能级别取决于营销活动的类型及其实施。

### 系列活动包列表 {#list-of-campaign-packages}

系列活动包列表包含可供本地实体使用的系列活动。

### 营销活动包 {#campaign-package}

由中央实体创建的模板（或营销活动实例），并将其提供给一组本地实体。

### 本地营销活动 {#local-campaign}

本地营销活动是从具有特定执行计划的列表中引用的模板 **[!UICONTROL campaign packages]** 创建的 **实例**。 其目标是使用由中央实体设置和配置的营销活动模板满足本地通信需求。

地方实体的自治程度取决于所采用的实施。

请参阅创 [建本地营销活动](../../campaign/using/creating-a-local-campaign.md)。

### 协作式营销活动 {#collaborative-campaign}

协作型营销活动是指其执 **行计划由中央实体定义** ，本地实体可使用该中央实体。 对于每个本地实体，内容将保持不变，但成本将共享。 要参加该活动，本地实体可订阅协作营销活动。

* **[!UICONTROL Collaborative campaign (by form)]**:建议用于涉及多达300个本地实体的营销活动。 本地实体可以在Web表单中输入用于定位和内容个性化的预定义参数。 表单可以是Adobe Campaign表单或外部表单（外部客户端）。 职能管理员可以根据集成商定义的表单模板定义和配置表单。 要对营销活动进行排序，本地实体只需要Web访问。
* **[!UICONTROL Collaborative campaign (by campaign)]**:推荐用于针对数十个当地实体的营销活动。 此类型的营销活动为每个本地实体创建子营销活动。 一旦中 **[!UICONTROL collaborative campaign (by campaign)]** 央实体批准该营销活动，该营销活动便会提供给本地实体，由本地实体进行修改。 执行在父营销活动和子营销活动之间自动同步。 本地实体必须有权访问某个实例，以对营销活动进行排序并参与其中。
* **[!UICONTROL Collaborative campaign (by target approval)]**:推荐用于针对数千个当地实体的活动。 本地实体接收由中央实体预定义的联系人列表。 本地实体根据营销活动内容，通过Web表单决定是否保留某些联系人。 从所选接触的列表推导出局部图元。 要参与营销活动，本地实体只需要Web访问。
* **[!UICONTROL Collaborative campaign (simple)]**:此模式确保与先前版本的特定执行进程兼容。

请参阅创 [建协作营销活动](../../campaign/using/creating-a-collaborative-campaign.md)。

### 订购营销活动包 {#ordering-campaign-packages}

如果本地实体注册了营销活动，则该实体将按顺序进行注册，重新分组与营销活动本地化相关的所有信息。

## 工作区 {#workspace}

可从“营销活动”范围访问营销活动包 **列表** :单击链 **[!UICONTROL Campaign packages]** 接。

![](assets/mkg_dist_home_local_op.png)

此窗口允许所有本地运营商查看其本地代理可用的营销活动。

对于中央机构，此窗口将显示营销活动包列表中所有可用的包，并提供用于编辑列表的其他链接。

## 运营商和实体 {#operators-and-entities}

首先，通过文件夹指定中心和本地实体运 **[!UICONTROL Access management]** 算符。

![](assets/s_advuser_mkg_dist_tree.png)

### 运营商 {#operators}

您需要创建中心和本地运算符。

中央运算符必须属于运 **[!UICONTROL Central management]** 算符组或具有命 **[!UICONTROL CENTRAL]** 名权限。

本地运算符必须属于运 **[!UICONTROL Local management]** 算符组或具有命 **[!UICONTROL LOCAL]** 名权限。 它们还必须与本地实体关联。

![](assets/s_advuser_mkg_dist_local_create.png)

### 组织实体 {#organizational-entities}

要创建组织实体，请单击该节 **[!UICONTROL Administration > Access management > Organizational entities]** 点，然后单击实 **[!UICONTROL New]** 体列表上方的图标。

![](assets/s_advuser_mkg_dist_local_list.png)

每个组织实体都包含标识信息（标签、内部名称、联系信息等）以及订单批准流程中涉及的组。 这些定义在选项卡 **[!UICONTROL Notifications and approvals]** 中的部分中 **[!UICONTROL General]** 定义。

* 定义包通知组：每次将新包添加到营销活动包列表以及每次营销活动可用时，此组中的运营商都会收到通知。
* 选择负责批准订单的审阅者组，即负责批准由本地实体订购的营销活动的审阅者组。
* 最后，选择负责批准本地营销活动（目标、内容、预算等）的一组审阅者。 在订购营销活动时，可以根据模板将此组添加到。

>[!NOTE]
>
>审批流程显示在审批流 [程部分](../../campaign/using/creating-a-local-campaign.md#approval-process) 。

## 实施 {#implementation}

分布式营销活动由中央实体创建和发布。 它们可以根据需要由本地实体和中央实体使用。

实施过程取决于所使用的营销活动包类型和本地实体委托级别。

### 集成商侧 {#integrator-side}

1. 创建本地实体。
1. 将收件人与管理本地实体的操作符关联。

   ![](assets/mkg_dist_local_entity_association.png)

1. 为本地实体指定权限和浏览规则
1. 指定营销活动本地化所需的字段集：

   * 目标定义和最大尺寸，
   * 内容定义，
   * 执行计划（联系日期和提取日期），仅 **适用于本地操作员**,
   * 扩展顺序架构，并包含所有必需的其他字段。

1. 创建Web表单（Adobe或外部网），它允许您显示本地化参数、评估目标和预算、预览内容和批准订单。

   对于 **协作式营销活动（通过目标批准）**，请创建保存每个本地实体的批准的表。

### 功能管理员端 {#functional-administrator-side}

创建每个营销活动时必须执行这些步骤。

1. 使用用于营销活动本地化的字段更新表单。
1. 从相应的营销活动模板（协作营销活动）创建实例或复制营销活动模板（本地营销活动）。
1. 使用本地化字段和表单引用配置营销活动。
1. 发布营销活动。

### 本地操作员端 {#local-operator-side}

必须对每个营销活动执行这些步骤。

1. 在您收到营销活动包可用性通知后，指定营销活动的位置（可选）。
1. 评估目标、预算等。
1. 预览营销活动内容。
1. 订购营销活动。

