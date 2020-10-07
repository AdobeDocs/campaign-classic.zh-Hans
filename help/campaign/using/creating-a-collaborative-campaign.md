---
title: 创建协作活动
seo-title: 创建协作活动
description: 创建协作活动
seo-description: null
page-status-flag: never-activated
uuid: 13d8ff65-1480-422a-85b6-40b553a3c151
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 01d8be92-7312-4386-b5f5-651af31308f7
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 4%

---


# 创建协作活动{#creating-a-collaborative-campaign-intro}

中央实体从分布式营销创建协作 **活动** 。 请参见[此页面](../../campaign/using/about-distributed-marketing.md#collaborative-campaign)。

## 创建协作活动 {#creating-a-collaborative-campaign}

要配置协作活动，请单击节 **[!UICONTROL Campaign management > Campaigns]** 点，然后单击图 **[!UICONTROL New]** 标。

>[!NOTE]
>
>此外， **[!UICONTROL collaborative campaigns (by campaign)]**&#x200B;这些活动可以通过Web界面进行配置和执行。

协作活动库的配置过程与本地活动模板的配置过程相似。 下面详细介绍了不同协作活动的规格。

### 按表单 {#by-form}

要创建协作活动（按表单），必须 **[!UICONTROL Collaborative campaign (by form)]** 选择模板。

![](assets/mkg_dist_mutual_op_form2.png)

在选项 **[!UICONTROL Edit]** 卡中，单 **[!UICONTROL Advanced campaign settings...]** 击链接以访问 **分布式营销** 选项卡。

选择“按 **表单** Web界面”。 此类型的界面允许您创建个性化字段,本地实体在订购活动时将使用这些。 请参阅 [创建本地活动（按表单）](../../campaign/using/examples.md#creating-a-local-campaign--by-form-)。

保存活动。 您现在可以通过单击按钮 **从活动** ，在 **活动世界** 中的 **[!UICONTROL Create]** 包视图使用它。

该 **[!UICONTROL Campaign Package]** 视图允许您使用本地活动模板（现成的或重复的）以及协作活动的引用活动，以便为不同组织实体创建活动。

![](assets/mkg_dist_mutual_op_form1b.png)

### 按活动 {#by-campaign}

要创建协作活动(按活动)，必 **[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]** 须选择模板。

![](assets/mkg_dist_mutual_op_by_op2.png)

对活动进行排序时，本地实体可以完成中央实体预定义的条件，并在对活动进行排序之前对其进行评估。

活动(按活动) **批准协作本地实体的订单** ，即为中央实体创建子活动。 本地实体一旦可用，便可以修改：

* 活动工作流，
* 类型规则,
* 和个性化字段。

本地实体执行子活动。 中央实体执行父活动。

中央实体可以（通过链接）从该仪表板中 **视图与协作活动链接的** 所有子活动(通过 **[!UICONTROL List of associated campaigns]** 活动)。

![](assets/mkg_dist_mutual_op_by_op.png)

### 通过目标批准 {#by-target-approval}

要创建协作活动(通过目标批准)，必 **[!UICONTROL Collaborative campaign (by target approval)]** 须选择模板。

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>在此模式下，中央实体无需指定本地实体。

活动工作流必须集 **成本地批准** 类型活动。 活动参数如下：

* **[!UICONTROL Action to perform]** :目标批准通知。
* **[!UICONTROL Distribution context]** :明确。
* **[!UICONTROL Data distribution]** :本地实体分发。

**本地实体分发** ，必须创建数据分发类型。 通过数据分发模板，您可以限制分组值列表中的记录数。 在 **[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;中，单 **[!UICONTROL New]** 击图标以创建新 **[!UICONTROL Data distribution]**。 有关数据分发的详细信息，请参阅 [工作流](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-) 指南。

![](assets/mkg_dist_data_distribution.png)

Select the **Targeting dimension** and the **[!UICONTROL Distribution field]**. 对于， **[!UICONTROL Assignment type]**&#x200B;选择 **本地实体**。

在选项卡 **[!UICONTROL Distribution]** 中，为每个本地实体添加一个字段并指定值。

![](assets/mkg_dist_data_distribution2.png)

您可以在目标类 **型投放** 之后添 **加第二** 个活动批准，以在其上配置报告。

在活动创建通知消息中，本地实体接收由中央实体参数预定义的联系列表。

![](assets/mkg_dist_mutual_op_by_valid1.png)

本地实体可以根据活动内容删除某些联系人。

![](assets/mkg_dist_mutual_op_by_valid2.png)

### 简单 {#simple}

要创建简单的协作活动，必 **[!UICONTROL Collaborative campaign (simple)]** 须选择模板。

## Creating a collaborative campaign package {#creating-a-collaborative-campaign-package}

要使活动可供本地实体使用，中央实体必须创建活动包。

应用以下步骤：

1. 在活动 **[!UICONTROL Navigation]** 页面的 **部分** ，单击该链 **[!UICONTROL Campaign packages]** 接。
1. 单击 **[!UICONTROL Create]** 按钮。
1. 窗口顶部的部分允许您选择模 **[!UICONTROL New collaborative package (mutualizedEmpty)]** 板。
1. 选择引用活动。
1. 指定活动包的标签、文件夹和执行计划。

### 日期{#dates}

开始和结束日期定义活动在活动包列表中的可见性期间。

对于 **协作活动**,中央实体必须指定注册和个性化的截止日期。

>[!NOTE]
>
>允许 **[!UICONTROL Personalization deadline]** 中央实体选择一个截止日期，本地实体必须在该截止日期之前提交要用于配置活动的文档（电子表格、图像）。 这不是强制选项。 侧步此日期不会影响活动实施。

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### 受众 {#audience}

中央实体必须在创建协作活动后立即指定每个活动涉及的本地实体。

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** 除非已指定相关本地实体，否则不能批准。

### 批准模式 {#approval-modes}

对于 **协作活动**，您可以指定订单审批模式。

![](assets/mkg_dist_edit_kit1.png)

在手动模式下，本地实体需要订阅活动才能参与。

在自动模式中，本地实体预订活动。 它可以取消活动订阅或修改其参数，而无需中央实体批准。

![](assets/mkg_dist_edit_kit2.png)

### 通知 {#notifications}

通知的配置与本地实体的通知相同。 请参阅[此章节](../../campaign/using/creating-a-local-campaign.md#notifications) 。

## 订购活动 {#ordering-a-campaign}

当协作活动添加到活动包的列表时，将通知属于由中央实体定义的受众的本地实体(协作 **活动(通过目标批准)** ，没有预定义的受众)。 发送的邮件包含一个链接，用于注册活动，如下所示：

![](assets/mkg_dist_mutual_op_notification.png)

此消息还使本地实体能够视图创建包的中央运算符输入的描述，以及链接到活动的文档。 这些信息不属于活动本身，但它们提供了更多相关信息。

本地运营商通过Web界面登录后，可以向他们希望订购的协作活动输入个性化信息：

![](assets/mkg_dist_mutual_op_command.png)

本地实体完成注册后，会通过电子邮件通知中央实体批准其订单。

![](assets/mkg_dist_mutual_op_valid_command.png)

For more on this, refer to the [Approval process](../../campaign/using/creating-a-local-campaign.md#approval-process) section.

## 批准订单 {#approving-an-order}

协作活动包订单的批准过程与本地活动的批准过程相同。 请参阅[此章节](../../campaign/using/creating-a-local-campaign.md#approving-an-order) 。
