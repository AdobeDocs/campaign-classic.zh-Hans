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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---


# 关于分布式营销{#about-distributed-marketing}

## 简介 {#introduction}

Adobe Campaign分布式营销 **** ,优惠申请在中央实体（总部、营销部门等）之间实施合作活动 和本地实体（销售点、地区代理等）。 此协作基于称为的共享工作区，在该 **[!UICONTROL list of campaign packages]**&#x200B;共享工作区中，集中创建的活动模板和实例提供给本地实体。

中央实体提供本地实体可使用的活动。 活动由表示本地或协作活动的包实现。 要使用活动,本地实体必须订购该订单，并且该订单必须获得批准。

>[!CAUTION]
>
>分布式营销模块是一个 **活动** 选项。 请核实您的许可协议。

## 术语 {#terminology}

### 中央实体 {#central-entities}

中央实体由负责指定通信和协助本地实体执行其营销活动的营销运营商组成。

分布式营销模块允许中央实体:

* 为本地实体设置营销活动包，
* 提高本地实体在客户/潜在客户沟通、定位、内容等方面的自主性。
* 管理和控制成本，
* 处理代理网络。

### 本地实体 {#local-entities}

本地实体可以是特定本地运营商（国家或地区经理、品牌经理等）的代理、商店或组。

分布式营销允许本地实体在优化执行成本的同时拥有更多自主权。

### 本地化 {#localization}

本地化是本地实体修改活动的目标和内容的能力。 本地化的可能级别取决于活动的类型及其实施。

### 列表活动包 {#list-of-campaign-packages}

活动包的列表包含可供本地实体使用的活动。

### 活动包 {#campaign-package}

由中央实体创建的模板(或活动实例)，并提供给一组本地实体。

### 本地活动 {#local-campaign}

本地活动是使用特定执行计划在列表中引用的模 **[!UICONTROL campaign packages]** 板创 **建的实例**。 其目标是使用由活动模板设置和配置的中央实体满足本地通信需求。

本地实体的自主程度取决于所使用的执行。

请参阅 [创建本地活动](../../campaign/using/creating-a-local-campaign.md)。

### 协作活动 {#collaborative-campaign}

协作活动是由计划定 **义执行的活动** ,本地实体可以使用该中央实体。 每个本地实体的内容保持不变，但费用是共享的。 要参与，本地实体订阅协作活动。

* **[!UICONTROL Collaborative campaign (by form)]**:建议活动最多300名本地实体。 本地实体可以在Web表单中输入用于定位和内容个性化的预定义参数。 表单可以是Adobe Campaign表单或外部表单（外部客户端）。 职能管理员可以根据集成商定义的表单模板定义和配置表单。 要订购活动,本地实体只需要Web访问。
* **[!UICONTROL Collaborative campaign (by campaign)]**:推荐给活动，目标是几十个本地实体。 此类活动为每个本地实体创建子活动。 中央实体 **[!UICONTROL collaborative campaign (by campaign)]** 批准后，活动便可供本地实体使用，他们可以修改它。 执行在父活动和子代数据之间自动同步。 本地实体必须有权访问实例，才能订购活动并参与其中。
* **[!UICONTROL Collaborative campaign (by target approval)]**:推荐给活动，目标是数千本地实体。 本地实体接收由中央实体预定义的联系列表。 本地实体根据活动内容，通过Web表单决定是否保留某些联系人。 本地实体由选定接触的列表推导出。 要参与活动,本地实体只需要Web访问。
* **[!UICONTROL Collaborative campaign (simple)]**:此模式确保与先前版本的特定执行进程兼容。

请参阅 [创建协作活动](../../campaign/using/creating-a-collaborative-campaign.md)。

### 订购活动包 {#ordering-campaign-packages}

如果本地实体注册活动，则按重组与活动本地化相关的所有信息的顺序进行。

## 工作区{#workspace}

活动包的列表可从活动 **世界** :单击链 **[!UICONTROL Campaign packages]** 接。

![](assets/mkg_dist_home_local_op.png)

此窗口允许所有本地操作员视图其本地代理可用的活动。

对于中央机构，此窗口显示活动包列表中可用的所有包，并优惠用于编辑列表的其他链接。

## 运营商和实体 {#operators-and-entities}

开始，方法是通过文件夹指定中心运算符和本地实体运 **[!UICONTROL Access management]** 算符。

![](assets/s_advuser_mkg_dist_tree.png)

### 运算符 {#operators}

您需要创建中央和本地运算符。

中心运算符必须属于运 **[!UICONTROL Central management]** 算符组或具有命 **[!UICONTROL CENTRAL]** 名权限。

本地运算符必须属于运 **[!UICONTROL Local management]** 算符组或具有命 **[!UICONTROL LOCAL]** 名权限。 他们还必须与本地实体联系。

![](assets/s_advuser_mkg_dist_local_create.png)

### 组织实体 {#organizational-entities}

要创建组织实体，请单 **[!UICONTROL Administration > Access management > Organizational entities]** 击节点，并单 **[!UICONTROL New]** 击实体列表上方的图标。

![](assets/s_advuser_mkg_dist_local_list.png)

每个组织实体都包含标识信息（标签、内部名称、联系信息等） 和订单批准流程中涉及的组。 这些属性在选项卡 **[!UICONTROL Notifications and approvals]** 中的章节中 **[!UICONTROL General]** 定义。

* 定义包通知组：每次向活动包列表添加新包以及每次活动可用时，此组中的操作员都会收到通知。
* 选择负责批准订单的审阅者组，即负责批准本地实体所订购活动的审阅者组。
* 最后，选择负责批准本地活动(目标、内容、预算等)的审阅者组。 根据模板，在对活动进行排序时可以添加此组。

>[!NOTE]
>
>审批流程显示在审批 [流程部分](../../campaign/using/creating-a-local-campaign.md#approval-process) 。

## 实施 {#implementation}

分布式营销活动由中央实体创建和发布。 它们可以根据需要由本地和中央实体使用。

实施过程取决于所使用的活动包类型和本地实体委托级别。

### 集成商端 {#integrator-side}

1. 创建本地实体。
1. 将收件人与管理本地实体的运算符关联。

   ![](assets/mkg_dist_local_entity_association.png)

1. 指定本地实体的权限和浏览规则
1. 指定活动本地化所需的字段集：

   * 目标定义和最大大小，
   * 内容定义，
   * 执行计划(联系日期和提取日期)，仅 **适用于本地运营商**,
   * 扩展订单模式，并包含所有必要的附加字段。

1. 创建Web表单(Adobe或外联网)，它允许您显示本地化参数、评估目标和预算，以及预览内容和批准订单。

   对 **于协作活动(通过目标批准)**，请创建表格，其中将保存每个本地实体的批准。

### 功能管理员端 {#functional-administrator-side}

创建每个活动时必须执行这些步骤。

1. 使用用于活动本地化的字段更新表单。
1. 从相应的活动模板(协作活动)或重复活动模板(本地活动)创建实例。
1. 使用活动字段和表单引用配置本地化。
1. 发布活动。

### 本地操作员端 {#local-operator-side}

必须对每个活动执行这些步骤。

1. 收到活动包可用性通知后，请指定活动的位置（可选）。
1. 评估目标、预算等。
1. 预览活动内容。
1. 订购活动。

