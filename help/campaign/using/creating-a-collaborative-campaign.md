---
title: 创建协作营销活动
seo-title: 创建协作营销活动
description: 创建协作营销活动
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 创建协作营销活动{#creating-a-collaborative-campaign-intro}

该中央实体根据“分布式营销”营销活动模 **板创建协作** 式营销活动。 请参见[此页面](../../campaign/using/about-distributed-marketing.md#collaborative-campaign)。

## 创建协作营销活动 {#creating-a-collaborative-campaign}

要配置协作式营销活动，请单击节 **[!UICONTROL Campaign management > Campaigns]** 点，然后单击图 **[!UICONTROL New]** 标。

>[!NOTE]
>
>除此之 **[!UICONTROL collaborative campaigns (by campaign)]**&#x200B;外，还可以通过Web界面配置和执行这些营销活动。

协作营销活动数据库的配置过程与本地营销活动模板的配置过程类似。 以下详细介绍了不同类型的协作营销活动的规范。

### 按表单 {#by-form}

要创建协作式营销活动（按表单），必 **[!UICONTROL Collaborative campaign (by form)]** 须选择模板。

![](assets/mkg_dist_mutual_op_form2.png)

在选项卡 **[!UICONTROL Edit]** 中，单击链接以 **[!UICONTROL Advanced campaign settings...]** 访问“分布式营 **销”选项卡** 。

选择“按 **表单** web”界面。 通过这种类型的界面，您可以创建个性化字段，这些字段将在订购营销活动时由本地实体使用。 请参阅 [创建本地营销活动（按表单）](../../campaign/using/examples.md#creating-a-local-campaign--by-form-)。

保存您的营销活动。 现在，您可以通过单击按 **钮，从****Campaign范围的“营销活动包”视图中使用该****[!UICONTROL Create]** 组件。

该视 **[!UICONTROL Campaign Package]** 图允许您使用本地营销活动模板（现成或重复的）以及协作营销活动的参考营销活动，以便为不同的组织实体创建营销活动。

![](assets/mkg_dist_mutual_op_form1b.png)

### 按营销活动 {#by-campaign}

要创建协作式营销活动（按营销活动），必 **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** 须选择模板。

![](assets/mkg_dist_mutual_op_by_op2.png)

在对营销活动进行排序时，本地实体可以完成由中心实体预定义的条件，并在对营销活动进行排序之前对其进行评估。

当协作营销活动(按 **营销活动)的订单得到中央实体批准后** ，将为本地实体创建子营销活动。 当本地实体可供他们使用后，即可修改：

* 营销活动的工作流程，
* 排版规则，
* 和个性化字段。

本地实体执行子营销活动。 中央实体执行父营销活动。

中央实体可以从此功能板中（通过链接）查看与 **Collaborative系列活动（按系列活动）关联的所有子系列****[!UICONTROL List of associated campaigns]** 系列活动。

![](assets/mkg_dist_mutual_op_by_op.png)

### 按目标批准 {#by-target-approval}

要创建协作式营销活动（通过目标批准），必 **[!UICONTROL Collaborative campaign (by target approval)]** 须选择模板。

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>在此模式中，中央实体无需指定本地实体。

营销活动工作流必须集 **成“本地批准** ”类型活动。 活动参数如下：

* **[!UICONTROL Action to perform]** :目标批准通知。
* **[!UICONTROL Distribution context]** :明确。
* **[!UICONTROL Data distribution]** :本地实体分发。

**必须创建本地实体分发** ，类型数据分发。 通过数据分发模板，您可以限制分组值列表中的记录数。 在 **[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;中，单 **[!UICONTROL New]** 击图标以创建新 **[!UICONTROL Data distribution]**。 有关数据分发的详细信息，请参阅工作 [流指南](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) 。

![](assets/mkg_dist_data_distribution.png)

选择定 **位维** 和 **[!UICONTROL Distribution field]**。 对于，选 **[!UICONTROL Assignment type]**&#x200B;择“本 **地实体”**。

在选项卡 **[!UICONTROL Distribution]** 中，为每个本地实体添加一个字段并指定值。

![](assets/mkg_dist_data_distribution2.png)

您可以在“交付类 **型** ”活动之后再添 **** 加一个Target批准，以便对其配置报告。

在营销活动创建通知消息中，本地实体接收由中央实体参数预定义的联系人列表。

![](assets/mkg_dist_mutual_op_by_valid1.png)

本地实体可以基于营销活动内容删除某些联系人。

![](assets/mkg_dist_mutual_op_by_valid2.png)

### 简单 {#simple}

要创建简单的协作营销活动，必 **[!UICONTROL Collaborative campaign (simple)]** 须选择模板。

## 创建协作式营销活动包 {#creating-a-collaborative-campaign-package}

要使营销活动可用于本地实体，中央实体必须创建营销活动包。

应用以下步骤：

1. 在“营 **[!UICONTROL Navigation]** 销活动”页面的 **部分** ，单击链 **[!UICONTROL Campaign packages]** 接。
1. Click the **[!UICONTROL Create]** button.
1. 窗口顶部的部分允许您选择模 **[!UICONTROL New collaborative package (mutualizedEmpty)]** 板。
1. 选择引用营销活动。
1. 指定系列活动包的标签、文件夹和执行计划。

### 日期 {#dates}

开始日期和结束日期定义营销活动包列表中营销活动的可见性时间段。

对于 **协作营销活动**，中央实体必须指定注册和个性化的截止日期。

>[!NOTE]
>
>该 **[!UICONTROL Personalization deadline]** 选项允许中央实体选择一个截止日期，本地实体必须在此截止日期之前提交要用于配置营销活动的文档（电子表格、图像）。 这不是强制选项。 跨越此日期不会影响营销活动实施。

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### 受众 {#audience}

中心实体必须在创建协作营销活动后指定每个营销活动涉及的本地实体。

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** 除非有关地方实体已经指定，否则不得批准。

### 批准模式 {#approval-modes}

对于 **协作营销活动**，您可以指定订单批准模式。

![](assets/mkg_dist_edit_kit1.png)

在手动模式下，本地实体需要订阅营销活动才能参与。

在自动模式中，本地实体预订了营销活动。 它可以取消营销活动订阅或修改其参数，而无需获得中央实体的批准。

![](assets/mkg_dist_edit_kit2.png)

### 通知 {#notifications}

通知的配置与本地实体的通知相同。 Refer to [this section](../../campaign/using/creating-a-local-campaign.md#notifications).

## 订购营销活动 {#ordering-a-campaign}

当协作营销活动添加到营销活动包列表时，将通知属于由中心实体定义的受众的本地实体(协作营销活动（通过目标批准） **** ，没有预定义的受众)。 发送的消息包含一个链接，用于注册营销活动，如下所示：

![](assets/mkg_dist_mutual_op_notification.png)

此消息还使本地实体可以查看由创建包的中央操作员输入的说明以及链接到营销活动的文档。 这些内容不属于营销活动本身，尽管它们提供了有关该活动的其他信息。

本地运营商通过Web界面登录后，他们可以输入要订购的协作营销活动的个性化信息：

![](assets/mkg_dist_mutual_op_command.png)

当地单位完成注册后，会通过电子邮件通知中央单位批准其订单。

![](assets/mkg_dist_mutual_op_valid_command.png)

有关详细信息，请参阅“批准 [流程](../../campaign/using/creating-a-local-campaign.md#approval-process) ”部分。

## 批准订单 {#approving-an-order}

批准协作营销活动包订单的过程与批准本地营销活动时的过程相同。 Refer to [this section](../../campaign/using/creating-a-local-campaign.md#approving-an-order).
