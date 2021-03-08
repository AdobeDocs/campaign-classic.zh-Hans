---
solution: Campaign Classic
product: campaign
title: 创建协作活动
description: 创建协作活动
audience: campaign
content-type: reference
topic-tags: distributed-marketing
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 4%

---


# 创建协作活动{#creating-a-collaborative-campaign-intro}

中央实体从&#x200B;**分布式营销**&#x200B;活动模板创建协作活动。 请参见[此页面](../../campaign/using/about-distributed-marketing.md#collaborative-campaign)。

## 创建协作活动 {#creating-a-collaborative-campaign}

要配置协作活动，请单击&#x200B;**[!UICONTROL Campaign management > Campaigns]**&#x200B;节点，然后单击&#x200B;**[!UICONTROL New]**&#x200B;图标。

>[!NOTE]
>
>除&#x200B;**[!UICONTROL collaborative campaigns (by campaign)]**&#x200B;外，还可以通过Web接口配置和执行这些活动。

协作活动库的配置过程与本地活动模板的配置过程类似。 以下详述了不同协作活动的规格。

### 按表单{#by-form}

要创建协作活动（按表单），必须选择&#x200B;**[!UICONTROL Collaborative campaign (by form)]**&#x200B;模板。

![](assets/mkg_dist_mutual_op_form2.png)

在&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;链接以访问&#x200B;**分布式营销**&#x200B;选项卡。

选择&#x200B;**按表单** Web界面。 此类型的界面允许您创建个性化字段,本地实体在订购活动时将使用这些界面。 请参阅[创建本地活动（按表单）](../../campaign/using/examples.md#creating-a-local-campaign--by-form-)。

保存活动。 现在，您可以通过单击&#x200B;**[!UICONTROL Create]**&#x200B;按钮，从&#x200B;**活动**&#x200B;选项卡的&#x200B;**视图包**&#x200B;活动中使用它。

**[!UICONTROL Campaign Package]**&#x200B;视图允许您使用本地活动模板（现成或复制）以及协作活动的参考活动，以便为不同组织实体创建活动。

![](assets/mkg_dist_mutual_op_form1b.png)

### 按活动{#by-campaign}

要创建协作活动(按活动)，必须选择&#x200B;**[!UICONTROL Collaborative campaign (by campaign) (opCollaborativeByCampaign)]**&#x200B;模板。

![](assets/mkg_dist_mutual_op_by_op2.png)

对活动进行排序时，本地实体可以完成中央实体预定义的条件，并在对活动进行排序之前对其进行评估。

一旦中央实体批准&#x200B;**协作活动(按活动)**&#x200B;的订单，就为本地实体创建子活动。 本地实体在可用后即可修改：

* 活动工作流，
* 类型规则,
* 和个性化字段。

本地实体执行子活动。 中央实体执行父活动。

中央实体可以从此仪表板（通过&#x200B;**[!UICONTROL List of associated campaigns]**&#x200B;链接）视图与&#x200B;**协作活动(通过活动)**&#x200B;链接的所有子活动。

![](assets/mkg_dist_mutual_op_by_op.png)

### 按目标批准{#by-target-approval}

要创建协作活动(通过目标批准)，必须选择&#x200B;**[!UICONTROL Collaborative campaign (by target approval)]**&#x200B;模板。

![](assets/mkg_dist_mutual_op_by_valid.png)

>[!NOTE]
>
>在此模式下，中央实体无需指定本地实体。

活动工作流必须集成&#x200B;**本地批准**&#x200B;类型活动。 活动参数如下：

* **[!UICONTROL Action to perform]** :目标批准通知。
* **[!UICONTROL Distribution context]** :明确。
* **[!UICONTROL Data distribution]** :本地实体分发。

**本地实体** 分发类型数据分发必须创建。通过列表分布模板，可以限制分组值的记录数。 在&#x200B;**[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;中，单击&#x200B;**[!UICONTROL New]**&#x200B;图标以创建新&#x200B;**[!UICONTROL Data distribution]**。 有关工作流分发的详细信息，请参阅[数据](../../workflow/using/using-the-local-approval-activity.md#step-1--creating-the-data-distribution-template-)指南。

![](assets/mkg_dist_data_distribution.png)

选择&#x200B;**定位维度**&#x200B;和&#x200B;**[!UICONTROL Distribution field]**。 对于&#x200B;**[!UICONTROL Assignment type]**，选择&#x200B;**本地实体**。

在&#x200B;**[!UICONTROL Distribution]**&#x200B;选项卡中，为每个本地实体添加一个字段并指定值。

![](assets/mkg_dist_data_distribution2.png)

您可以在&#x200B;**目标**&#x200B;类型活动后添加第二个&#x200B;**投放批准**，以在其上配置报告。

在活动创建通知消息中，本地实体接收由中央实体参数预定义的联系列表。

![](assets/mkg_dist_mutual_op_by_valid1.png)

本地实体可以根据活动内容删除某些联系人。

![](assets/mkg_dist_mutual_op_by_valid2.png)

### 简单{#simple}

要创建简单的协作活动，必须选择&#x200B;**[!UICONTROL Collaborative campaign (simple)]**&#x200B;模板。

## 创建协作活动包{#creating-a-collaborative-campaign-package}

要使活动可供本地实体使用，中央实体必须创建活动包。

应用以下步骤：

1. 在&#x200B;**活动**&#x200B;页面的&#x200B;**[!UICONTROL Navigation]**&#x200B;部分，单击&#x200B;**[!UICONTROL Campaign packages]**&#x200B;链接。
1. 单击 **[!UICONTROL Create]** 按钮。
1. 窗口顶部的部分允许您选择&#x200B;**[!UICONTROL New collaborative package (mutualizedEmpty)]**&#x200B;模板。
1. 选择引用活动。
1. 指定活动包的标签、文件夹和执行计划。

### 日期{#dates}

开始和结束日期定义活动在活动包列表中的可见性期。

对于&#x200B;**协作活动**,中央实体必须指定注册和个性化的截止日期。

>[!NOTE]
>
>**[!UICONTROL Personalization deadline]**&#x200B;允许中央实体选择一个截止日期，本地实体必须在此截止日期前交付要用于配置活动的文档（电子表格、图像）。 这不是强制性选项。 越界此日期不会影响活动实施。

![](assets/s_advuser_mkg_dist_create_mutual_entry.png)

### 受众 {#audience}

中央实体必须在创建协作活动后立即指定每个活动涉及的本地实体。

![](assets/s_advuser_mkg_dist_create_mutual_entry2.png)

>[!CAUTION]
>
>**[!UICONTROL Simple, by form and by campaign collaborative campaign kits]** 除非已指定相关本地实体，否则无法批准。

### 批准模式{#approval-modes}

对于&#x200B;**协作活动**，可指定订单批准模式。

![](assets/mkg_dist_edit_kit1.png)

在手动模式下，本地实体需要订阅活动才能参与。

在自动模式中，本地实体预订活动。 它可以取消活动订阅或修改其参数，而无需中央实体批准。

![](assets/mkg_dist_edit_kit2.png)

### 通知{#notifications}

通知的配置与本地实体的通知相同。 请参阅[此章节](../../campaign/using/creating-a-local-campaign.md#notifications) 。

## 排序活动{#ordering-a-campaign}

当协作活动被添加到活动包的列表时，将通知属于中央实体所定义的受众的本地实体(**协作活动(通过目标批准)**&#x200B;没有预定义的受众)。 发送的邮件包含一个链接，用于注册活动，如下所示：

![](assets/mkg_dist_mutual_op_notification.png)

此消息还使本地实体能够视图由创建包的中央运算符输入的描述，以及链接到活动的文档。 这些信息不属于活动本身，尽管它们提供了关于它的其他信息。

本地运营商通过Web界面登录后，可以向希望订购的协作活动输入个性化信息：

![](assets/mkg_dist_mutual_op_command.png)

本地实体完成注册后，会通过电子邮件通知中央实体批准其订单。

![](assets/mkg_dist_mutual_op_valid_command.png)

有关详细信息，请参阅[批准流程](../../campaign/using/creating-a-local-campaign.md#approval-process)部分。

## 批准订单{#approving-an-order}

批准协作活动包订单的过程与在本地活动中批准时的过程相同。 请参阅[此章节](../../campaign/using/creating-a-local-campaign.md#approving-an-order) 。
