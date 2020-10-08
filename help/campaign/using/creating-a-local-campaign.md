---
title: 创建本地活动
seo-title: 创建本地活动
description: 创建本地活动
seo-description: null
page-status-flag: never-activated
uuid: 86e78d9e-26cb-4aea-b8ce-5e52ae352b48
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: bd057441-8524-49e6-b5d5-fbd0ec5bca85
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 1%

---


# 创建本地活动{#creating-a-local-campaign}

本地活动是使用特定执行计划在列表中引用的模 **[!UICONTROL campaign packages]** 板创 **建的实例**。 其目标是使用由活动模板设置和配置的中央实体满足本地通信需求。 实施本地操作的主要阶段如下：

**对于中央实体**

1. 创建本地活动模板。
1. 从模板创建活动包。
1. 发布活动包。
1. 批准订单。

**对于本地实体**

1. 订购活动。
1. 执行活动。

## Creating a local campaign template {#creating-a-local-campaign-template}

要创建活动包，必须首先通过节 **点** 创建 **[!UICONTROL Resources > Templates]** 活动模板。

要创建新的本地模板，请重复默认 **[!UICONTROL Local campaign (opLocal)]** 模板。

![](assets/mkg_dist_local_op_creation.png)

命名活动模板并填写可用字段。

![](assets/mkg_dist_local_op_creation1.png)

在活动窗口中，单击选 **[!UICONTROL Edit]** 项卡，然后单击 **[!UICONTROL Advanced campaign settings...]** 链接。

![](assets/mkt_distr_4.png)

### Web界面 {#web-interface}

在“分 **布式营销** ”选项卡中，您可以选择Web界面的类型，并指定在本地实体下订单时要输入的默认值和参数。

Web界面与本地实体在订购活动时要填写的表单相对应。

选择要应用于从模板创建的活动的Web界面类型：

![](assets/mkt_distr_1.png)

可用的Web界面有四种类型：

* **[!UICONTROL By brief]** :本地实体必须提供描述活动配置的说明。 一旦订单被批准，中央实体将配置并执行整个活动。

   ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** :本地实体有权访问Web表单，根据所使用的模板，他们可以编辑内容、目标、最大大小以及使用个性化字段创建和提取日期。 本地实体可以评估来自此Web表单的目标和预览内容。

   ![](assets/mkt_distr_8.png)

   提供的表单在Web 应用程序中指定，该列表必须在模板链接的字段的下 **[!UICONTROL Web Interface]** 拉中选择 **[!UICONTROL Advanced campaign settings...]** 。 请参阅 [创建本地活动（按表单）](../../campaign/using/examples.md#creating-a-local-campaign--by-form-)。

   >[!NOTE]
   >
   >此示例中使用的Web 应用程序就是一个示例。 您必须创建特定Web应用程序才能使用表单。 请参阅 [API](../../configuration/using/about-web-services.md)。

   ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** :本地实体有权访问其外部网中的活动参数(非Adobe Campaign)。 这些参数与局部活动(按 **表单)的参数相同**。
* **[!UICONTROL Pre-set]** :本地实体使用默认表单对活动进行排序，而不对其进行本地化。

   ![](assets/mkt_distr_5.png)

### 默认值 {#default-values}

选择 **[!UICONTROL Default values]** 要由本地实体完成的。 例如：

* 联系和提取日期，
* 目标特征（年龄段等）。

![](assets/mkg_dist_local_op_creation2.png)

填写 **[!UICONTROL Parent marketing program]** 和字 **[!UICONTROL Charge]** 段。

![](assets/mkg_dist_local_op_creation3.png)

### 批准 {#approvals}

在链接 **[!UICONTROL Advanced parameters for campaign entry]** 中，可指定最大审阅人数。

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

本地实体在订购活动时将输入审阅者。

![](assets/mkt_distr_5.png)

如果不想为活动命名审阅者，请输入0。

### 文档 {#documents}

您可以允许本地实体运算符链接文档(文本文件、电子表格、图像、活动描述等) 到本地活动。 通过 **[!UICONTROL Advanced parameters for campaign entry...]** 链接可以限制文档数。 为此，只需在字段中输入允许的最大 **[!UICONTROL Number of documents]** 数字。

![](assets/s_advuser_mkg_dist_local_docs.png)

对活动包进行排序时，表单建议链接模板中相应字段中指示的任意数量文档。

![](assets/s_advuser_mkg_dist_add_docs.png)

如果不希望显示文档上传字段，请在 **[!UICONTROL 0]** 字段中输入 **[!UICONTROL Number of documents]** 该字段。

>[!NOTE]
>
>可通过 **[!UICONTROL Advanced parameters for campaign entry]** 检查来取消激活该 **[!UICONTROL Do not display the page used to enter the campaign parameters]**&#x200B;项。

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### Workflow {#workflow}

在选 **[!UICONTROL Targeting and workflows]** 项卡中，创建活动工作流，该工作流会收集 **[!UICONTROL Default values]** 在中指定的 **[!UICONTROL Advanced campaign settings...]** 投放并创建。

![](assets/mkg_dist_local_op_creation4b.png)

多次单 **[!UICONTROL Query]** 击活动以根据指定的配置 **[!UICONTROL Default values]**。

![](assets/mkt_dist_local_campaign_localize_query.png)

### 投放 {#delivery}

在选 **[!UICONTROL Audit]** 项卡中，单 **[!UICONTROL Detail...]** 击图标以视图 **[!UICONTROL Scheduling]** 选定投放。

![](assets/mkg_dist_local_op_creation4c.png)

通过 **[!UICONTROL Scheduling]** 该图标可配置投放的联系和执行日期。

![](assets/mkg_dist_local_op_creation4d.png)

如有必要，请配置投放的最大大小：

![](assets/mkg_dist_local_op_creation4e.png)

找到投放的HTML。 例如，在 **[!UICONTROL Delivery > Current order > Additional fields]**&#x200B;中，使 **[!UICONTROL Age segment]** 用字段根据投放的年龄定位目标。

![](assets/mkt_dist_local_campaign_localize_html.png)

保存活动模板。 您现在可以通过单击按钮 **从活动** ，在 **活动世界** 中的 **[!UICONTROL Create]** 包视图使用它。

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>活动模板及其一般配置详见 [活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

## 创建活动包 {#creating-the-campaign-package}

要使活动模板可供本地实体使用，需要将其添加到列表。 为此，中央机构需要创建新的包。

应用以下步骤：

1. 在活动 **[!UICONTROL Navigation]** 页面的 **部分** ，单击该链 **[!UICONTROL Campaign packages]** 接。
1. 单击 **[!UICONTROL Create]** 按钮。

   ![](assets/mkg_dist_add_an_entry.png)

1. 窗口上方的部分允许您选择以 [前指](#creating-a-local-campaign-template) 定的活动包模板。

   默认情况下，模 **[!UICONTROL New local campaign package (localEmpty)]** 板用于本地活动。

1. 指定活动包的标签、文件夹和执行计划。

### 日期{#dates}

开始和结束日期定义活动在活动包列表中的可见性期间。

发布日期是活动可供本地实体（订购）的日期。

>[!CAUTION]
>
>如果本地实体在截止日期之前未保留活动，则无法使用它。

此信息在发送给本地机构的通知消息中找到，如下所示：

![](assets/s_advuser_mkg_dist_local_notif.png)

### 受众 {#audience}

对于本地活动,中央实体可以通过检查来指定涉及的本地实体 **[!UICONTROL Limit the package to a set of local entities]**。

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### 其他设置 {#additional-settings}

保存包后，中央实体可以从选项卡中编辑 **[!UICONTROL Edit]** 它。

![](assets/mkg_dist_edit_kit.png)

在选项卡 **[!UICONTROL General]** 中，中央实体可以：

* 从链接配置活动包审 **[!UICONTROL Approval parameters...]** 阅者，
* 审查执行计划,
* 添加或删除本地实体。

>[!NOTE]
>
>默认情况下，每个实体只能对本 **地活动** 排序一次。
>   
>选中该 **[!UICONTROL Enable multiple creation]** 选项可允许从活动包创建多个本地活动。

![](assets/mkg_dist_local_op_multi_crea.png)

### 通知 {#notifications}

当活动可用或达到注册截止日期时，将向本地通知组的操作员发送消息。 For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## 订购活动 {#ordering-a-campaign}

活动包一旦获得批准并开始实施，本地实体便可访问。 本地实体会收到一封电子邮件，告知他们有新的活动包可用（一旦到达其发布日期）。

>[!NOTE]
>
>如果在创建本地实体包时指定了某些活动，则只有这些才能收到通知。 如果未指定本地实体，则所有本地实体都将收到通知。

![](assets/mkg_dist_local_op_notification.png)

要使用中央实体提供的活动,本地实体必须订购。

要订购活动，请执行以下操作：

1. 单击 **[!UICONTROL Order campaign]** 通知消息或Adobe Campaign中的相应按钮。

   输入您的ID和密码以对活动进行排序。 该界面由在Web应用程序中定义的一组页面组成。

   >[!NOTE]
   >
   >Web 应用程序详见 [Web功能指南](../../web/using/about-web-applications.md) 。

1. 在第一页（订单标签和注释）中输入必要的信息，然后单击 **[!UICONTROL Next]**。

   ![](assets/mkg_dist_subscribe_step1.png)

1. 完成可用参数并批准订单。

1. 通知将发送给组织实体所属本地实体的经理以批准此订单。

   ![](assets/mkg_dist_subscribe_step3.png)

1. 信息将返回给本地和中央实体。 虽然本地实体只能视图自己的订单，但中央实体可以按任何本地实体视图所有订单，如下所示：

   ![](assets/mkg_dist_subscribe_central_view.png)

   操作员可以显示订单详细信息：

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   该选 **[!UICONTROL Edit]** 项卡包含本地实体在订购活动时输入的信息。

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. 订单必须经中央实体批准才能定稿。

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   For more on this, refer to the [Approval process](#approval-process) section.

1. 然后，将通知本地运算符该活动可用：活动可用性可以在活动范围内的活动包的 **列表中** 。 然后可以使用活动。 For more on this, refer to [Accessing campaigns](../../campaign/using/accessing-campaigns.md).

   该 **[!UICONTROL Start targeting with order approval]** 选项允许本地实体在订单获得批准后立即运行活动。

   ![](assets/mkg_dist_local_op_catalog_use.png)

## 批准订单 {#approving-an-order}

要确认活动订单，中央实体必须批准该订单。

通过 **[!UICONTROL Campaign orders]** 活动范围访问 **的概述** ，您可以视图活动订单的状态并进行批准。

>[!NOTE]
>
>本地实体可以更改订单，直到订单获得批准。

### 批准流程 {#approval-process}

#### 电子邮件通知 {#email-notification}

当活动由本地实体订购时，其审阅者会通过电子邮件通知，如下所示：

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>在“审阅者”部分中会显示选 [择审阅](#reviewers) 者的信息。 他们可以接受或拒绝订单。

![](assets/mkg_dist_command_valid_web.png)

#### 通过Adobe Campaign控制台进行批准 {#approving-via-the-adobe-campaign-console}

订单也可以通过控制台在活动订单概述中进行批准。 要批准订单，请选择该订单并单击 **[!UICONTROL Approve the order]**。

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>在活动发布日期之前，仍可以编辑和重新配置活动。 本地实体还可以通过单击按钮拒绝该 **[!UICONTROL Cancel]** 活动。

#### 创建营销策划{#creating-a-campaign}

活动订单一经批准，即可由本地实体配置并执行。

![](assets/mkg_dist_mutual_op_created.png)

For more on this, refer to [Accessing campaigns](../../campaign/using/accessing-campaigns.md).

### 拒绝批准 {#rejecting-an-approval}

负责审批的经营者可以拒绝订单或活动包。

![](assets/mkg_dist_do_not_valid.png)

如果审阅人拒绝订单，则相关通知会自动发送给相关本地实体:它显示由拒绝批准的操作员输入的注释。

信息显示在活动包的列表页或活动顺序页。 如果本地实体有权访问Adobe Campaign控制台，则会告知其拒绝。

![](assets/mkg_dist_do_not_valid_view.png)

他们可以视图活动包选项卡中的相关注 **[!UICONTROL Edit]** 释。

![](assets/mkg_dist_do_not_valid_tab.png)

### 审阅者 {#reviewers}

每次需要批准时，审阅者都会通过电子邮件收到通知。

对于每个本地实体，将选择审阅者进行活动订单批准和活动批准。 有关选择本地审阅者的详细信息，请参阅 [组织实体](../../campaign/using/about-distributed-marketing.md#organizational-entities)。

>[!NOTE]
>
>为了能够进行此选择，订单批准必须尚未生效。

### 取消订单 {#canceling-an-order}

中央机构可以使用订单仪表板 **[!UICONTROL Delete]** 上的按钮取消订单。

![](assets/mkg_dist_local_op_cancel.png)

这会取消活动 **[!UICONTROL Campaign orders]** 。
