---
solution: Campaign Classic
product: campaign
title: 关于分布式营销
description: 关于分布式营销
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: c625b4109e2cb47446331cd009ff9827c8267c93
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 1%

---


# 关于分布式营销{#about-distributed-marketing}

## 简介 {#introduction}

Adobe Campaign优惠&#x200B;**分布式营销**&#x200B;申请在中央实体（总部、营销部门等）之间实施合作活动 和本地实体（销售点、地区代理等）。 此协作基于称为&#x200B;**[!UICONTROL list of campaign packages]**&#x200B;的共享工作区，其中集中创建的活动模板和实例提供给本地实体。

中央实体提供本地实体可使用的活动。 活动由表示本地或协作活动的包实现。 要使用活动,本地实体必须订购该订单，并且该订单必须获得批准。

>[!CAUTION]
>
>分布式营销模块是&#x200B;**活动**&#x200B;选项。 请核实您的许可协议。

## 术语 {#terminology}

### 中央实体{#central-entities}

中央实体由负责指定通信和协助本地实体执行其营销活动的营销运营商组成。

分布式营销模块允许中央实体:

* 为本地实体设置营销活动包，
* 提高本地实体在客户/潜在客户沟通、定位、内容等方面的自主性。
* 管理和控制成本，
* 处理代理网络。

### 本地实体{#local-entities}

本地实体可以是特定本地运营商（国家或地区经理、品牌经理等）的代理、商店或组。

分布式营销允许本地实体在优化执行成本的同时拥有更多自主权。

### 本地化{#localization}

本地化是本地实体修改活动的目标和内容的能力。 本地化的可能级别取决于活动的类型及其实施。

### 列表活动包{#list-of-campaign-packages}

活动包的列表包含可供本地实体使用的活动。

### 活动包{#campaign-package}

由中央实体创建的模板(或活动实例)，并提供给一组本地实体。

### 本地活动{#local-campaign}

本地活动是从&#x200B;**[!UICONTROL campaign packages]**&#x200B;列表中引用的具有&#x200B;**特定执行计划**&#x200B;的模板创建的实例。 其目标是使用由活动模板设置和配置的中央实体满足本地通信需求。

本地实体的自主程度取决于所使用的执行。

请参阅[创建本地活动](../../campaign/using/creating-a-local-campaign.md)。

### 协作活动{#collaborative-campaign}

协作活动是活动，其&#x200B;**执行计划由中央实体定义**,本地实体可以使用该。 每个本地实体的内容保持不变，但费用是共享的。 要参与，本地实体订阅协作活动。

* **[!UICONTROL Collaborative campaign (by form)]**:建议活动最多300名本地实体。本地实体可以在Web表单中输入用于定位和内容个性化的预定义参数。 表单可以是Adobe Campaign表单或外部表单（外部客户端）。 职能管理员可以根据集成商定义的表单模板定义和配置表单。 要订购活动,本地实体只需要Web访问。
* **[!UICONTROL Collaborative campaign (by campaign)]**:推荐给活动，目标是几十个本地实体。此类活动为每个本地实体创建子活动。 中央实体批准&#x200B;**[!UICONTROL collaborative campaign (by campaign)]**&#x200B;后，活动便可供本地实体使用，由谁修改。 执行在父活动和子代数据之间自动同步。 本地实体必须有权访问实例，才能订购活动并参与其中。
* **[!UICONTROL Collaborative campaign (by target approval)]**:推荐给活动，目标是数千本地实体。本地实体接收由中央实体预定义的联系列表。 本地实体根据活动内容，通过Web表单决定是否保留某些联系人。 本地实体由选定接触的列表推导出。 要参与活动,本地实体只需要Web访问。
* **[!UICONTROL Collaborative campaign (simple)]**:此模式确保与先前版本的特定执行进程兼容。

请参阅[创建协作活动](../../campaign/using/creating-a-collaborative-campaign.md)。

### 对活动包{#ordering-campaign-packages}排序

如果本地实体注册活动，则按重组与活动本地化相关的所有信息的顺序进行。

## 工作区{#workspace}

活动包的列表可以从&#x200B;**活动**&#x200B;范围访问：单击&#x200B;**[!UICONTROL Campaign packages]**&#x200B;链接。

![](assets/mkg_dist_home_local_op.png)

此窗口允许所有本地操作员视图其本地代理可用的活动。

对于中央机构，此窗口显示活动包列表中可用的所有包，并优惠用于编辑列表的其他链接。

## 运算符和实体{#operators-and-entities}

开始，通过&#x200B;**[!UICONTROL Access management]**&#x200B;文件夹指定central和本地实体运算符。

![](assets/s_advuser_mkg_dist_tree.png)

### 运算符 {#operators}

您需要创建中央和本地运算符。

中心运算符必须属于&#x200B;**[!UICONTROL Central management]**&#x200B;运算符组或具有名为right的&#x200B;**[!UICONTROL CENTRAL]**。

本地运算符必须属于&#x200B;**[!UICONTROL Local management]**&#x200B;运算符组或具有名为right的&#x200B;**[!UICONTROL LOCAL]**。 他们还必须与本地实体联系。

![](assets/s_advuser_mkg_dist_local_create.png)

### 组织实体{#organizational-entities}

要创建组织实体，请单击&#x200B;**[!UICONTROL Administration > Access management > Organizational entities]**&#x200B;节点，然后单击实体列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

![](assets/s_advuser_mkg_dist_local_list.png)

每个组织实体都包含标识信息（标签、内部名称、联系信息等） 和订单批准流程中涉及的组。 这些属性在&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL Notifications and approvals]**&#x200B;部分中定义。

* 定义包通知组：每次向活动包列表添加新包以及每次活动可用时，此组中的操作员都会收到通知。
* 选择负责批准订单的审阅者组，即负责批准本地实体所订购活动的审阅者组。
* 最后，选择负责批准本地活动(目标、内容、预算等)的审阅者组。 根据模板，在对活动进行排序时可以添加此组。

>[!NOTE]
>
>审批流程显示在[审批流程](../../campaign/using/creating-a-local-campaign.md#approval-process)部分。

## 实现{#implementation}

分布式营销活动由中央实体创建和发布。 它们可以根据需要由本地和中央实体使用。

实施过程取决于所使用的活动包类型和本地实体委托级别。

### 集成商端{#integrator-side}

1. 创建本地实体。
1. 将收件人与管理本地实体的运算符关联。

   ![](assets/mkg_dist_local_entity_association.png)

1. 指定本地实体的权限和浏览规则
1. 指定活动本地化所需的字段集：

   * 目标定义和最大大小，
   * 内容定义，
   * 执行计划(联系日期和提取日期),**（仅针对本地运算符）**,
   * 扩展订单模式，并包含所有必要的附加字段。

1. 创建一个Web表单(Adobe或外联网)，它允许您显示本地化参数、评估目标和预算，以及预览内容和批准订单。

   对于&#x200B;**协作活动(通过目标批准)**，请创建表格，其中将保存每个本地实体的批准。

### 功能管理员端{#functional-administrator-side}

创建每个活动时必须执行这些步骤。

1. 使用用于活动本地化的字段更新表单。
1. 从相应的活动模板(协作活动)或重复活动模板(本地活动)创建实例。
1. 使用活动字段和表单引用配置本地化。
1. 发布活动。

### 本地运算符端{#local-operator-side}

必须对每个活动执行这些步骤。

1. 收到活动包可用性通知后，请指定活动的位置（可选）。
1. 评估目标、预算等。
1. 预览活动内容。
1. 订购活动。

