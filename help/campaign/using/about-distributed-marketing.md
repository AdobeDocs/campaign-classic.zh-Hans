---
solution: Campaign Classic
product: campaign
title: 关于分布式营销
description: 关于分布式营销
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 1%

---


# 关于分布式营销{#about-distributed-marketing}

## 简介 {#introduction}

Adobe Campaign优惠&#x200B;**分布式营销**&#x200B;应用程序，以在中央实体（总部、营销部门等）之间实施协作活动 和本地实体（销售点、区域代理等）。 此协作基于称为&#x200B;**[!UICONTROL list of campaign packages]**&#x200B;的共享工作区，在该共享工作区中，集中创建的活动模板和实例将提供给本地实体。

该中央实体提供了本地实体可能使用的活动。 活动由表示本地或协作活动的包实现。 要使用活动,本地实体必须订购该订单，并且订单必须获得批准。

>[!CAUTION]
>
>分布式营销模块是&#x200B;**活动**&#x200B;选项。 请核实您的许可协议。

## 术语 {#terminology}

### 中央实体{#central-entities}

中央实体由负责指定通信和协助本地实体执行其营销活动的营销运营商组成。

分布式营销模块使中央实体能够：

* 为本地实体设置营销活动包，
* 提高本地实体在客户/潜在客户沟通、定位、内容等方面的自主性。
* 管理和控制成本，
* 处理一个机构网络。

### 本地实体{#local-entities}

本地实体可以是特定本地运营商（国家或地区经理、品牌经理等）的代理、商店或组。

分布式营销使本地实体在优化执行成本的同时拥有更多自主权。

### 本地化{#localization}

本地化是本地实体修改活动目标和内容的能力。 本地化的可能级别取决于活动的类型及其实现。

### 列表活动包{#list-of-campaign-packages}

活动包的列表包含可用于本地实体的活动。

### 活动包{#campaign-package}

由中央实体创建的模板(或活动实例)，并可用于一组本地实体。

### 本地活动{#local-campaign}

本地活动是从&#x200B;**[!UICONTROL campaign packages]**&#x200B;列表中引用的具有&#x200B;**特定执行计划**&#x200B;的模板创建的实例。 其目标是使用由中央实体设置和配置的活动模板来满足本地通信需求。

本地实体的自主程度取决于所使用的实施。

请参阅[创建本地活动](../../campaign/using/creating-a-local-campaign.md)。

### 协作活动{#collaborative-campaign}

协作活动是活动，其&#x200B;**执行计划由中央实体定义**,本地实体可使用该。 每个本地实体的内容保持不变，但成本是共享的。 要参与，本地实体订阅协作活动。

* **[!UICONTROL Collaborative campaign (by form)]**:建议用于涉及多达300个活动的本地实体。本地实体可以在Web表单中输入用于定位和内容个性化的预定义参数。 表单可以是Adobe Campaign表单或外部表单（外部客户端）。 职能管理员可以根据集成商定义的表单模板定义和配置表单。 要订购活动,本地实体只需要Web访问。
* **[!UICONTROL Collaborative campaign (by campaign)]**:推荐针对数十种活动的本地实体。此类活动为每个本地实体创建子活动。 中央实体批准&#x200B;**[!UICONTROL collaborative campaign (by campaign)]**&#x200B;后，活动便可供本地实体使用，由谁修改。 执行在父活动和子应用程序之间自动同步。 本地实体必须有权访问某个实例，才能订购活动并参与其中。
* **[!UICONTROL Collaborative campaign (by target approval)]**:建议活动针对几千个本地实体。本地实体接收由中央实体预定义的联系列表。 本地实体根据活动内容，通过Web表单决定是否保留某些联系人。 本地实体由所选接触的列表导出。 要参与活动,本地实体只需要Web访问。
* **[!UICONTROL Collaborative campaign (simple)]**:此模式可确保与先前版本的特定执行进程兼容。

请参阅[创建协作活动](../../campaign/using/creating-a-collaborative-campaign.md)。

### 对活动包{#ordering-campaign-packages}排序

如果本地实体注册活动，则按重组与活动本地化相关的所有信息的顺序进行。

## 工作区{#workspace}

活动包的列表可以从&#x200B;**活动**&#x200B;选项卡访问：单击&#x200B;**[!UICONTROL Campaign packages]**&#x200B;链接。

![](assets/mkg_dist_home_local_op.png)

此窗口允许所有本地运营商视图其本地代理可用的活动。

对于中央机构，此窗口显示活动包列表中所有可用的包，并优惠用于编辑列表的其他链接。

## 运算符和实体{#operators-and-entities}

开始，方法是通过&#x200B;**[!UICONTROL Access management]**&#x200B;文件夹指定central和本地实体运算符。

![](assets/s_advuser_mkg_dist_tree.png)

### 运算符 {#operators}

您需要创建中心和本地运算符。

中心运算符必须属于&#x200B;**[!UICONTROL Central management]**&#x200B;运算符组，或具有&#x200B;**[!UICONTROL CENTRAL]**&#x200B;的命名权限。

本地运算符必须属于&#x200B;**[!UICONTROL Local management]**&#x200B;运算符组，或具有&#x200B;**[!UICONTROL LOCAL]**&#x200B;的命名权限。 它们还必须与本地实体联系。

![](assets/s_advuser_mkg_dist_local_create.png)

### 组织实体{#organizational-entities}

要创建组织实体，请单击&#x200B;**[!UICONTROL Administration > Access management > Organizational entities]**&#x200B;节点，然后单击实体列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

![](assets/s_advuser_mkg_dist_local_list.png)

每个组织实体都包含标识信息（标签、内部名称、联系信息等） 和订单批准流程中涉及的组。 这些定义在&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL Notifications and approvals]**&#x200B;部分中。

* 定义包通知组：每次向活动包的列表添加新包和每次活动可用时，此组中的运算符都将收到通知。
* 选择负责批准订单的审阅人组，即负责批准本地实体所订购活动的审阅人组。
* 最后，选择负责批准本地活动(目标、内容、预算等)的审阅者组。 根据模板的不同，在订购活动时可以添加此组。

>[!NOTE]
>
>审批流程显示在[审批流程](../../campaign/using/creating-a-local-campaign.md#approval-process)部分。

## 实现{#implementation}

分布式营销活动由中央实体创建和发布。 它们可以根据需要由本地和中央实体使用。

实施过程取决于所使用的活动包类型和本地实体委派级别。

### 集成商端{#integrator-side}

1. 创建本地实体。
1. 将收件人与管理本地实体的运算符关联。

   ![](assets/mkg_dist_local_entity_association.png)

1. 指定本地实体的权限和浏览规则
1. 指定活动本地化所需的字段集：

   * 目标定义和最大大小，
   * 内容定义，
   * 执行计划(联系日期和提取日期),**（仅针对本地运算符**），
   * 扩展订单模式，并包含所有必需的其他字段。

1. 创建一个Web表单(Adobe或外联网)，它允许您显示本地化参数、评估目标和预算、预览内容和批准订单。

   对于&#x200B;**协作活动(通过目标批准)**，创建保存每个本地实体批准的表。

### 功能管理员端{#functional-administrator-side}

创建每个活动时必须执行这些步骤。

1. 使用用于活动本地化的字段更新表单。
1. 从适当的活动模板(协作活动)或重复活动模板(本地活动)创建实例。
1. 使用本地化字段和表单引用配置活动。
1. 发布活动。

### 本地运算符端{#local-operator-side}

必须对每个活动执行这些步骤。

1. 收到活动包可用性通知后，请指定活动的位置（可选）。
1. 评估目标、预算等
1. 预览活动内容。
1. 订购活动。

