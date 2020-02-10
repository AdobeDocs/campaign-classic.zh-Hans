---
title: 创建本地营销活动
seo-title: 创建本地营销活动
description: 创建本地营销活动
seo-description: null
page-status-flag: never-activated
uuid: 86e78d9e-26cb-4aea-b8ce-5e52ae352b48
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: bd057441-8524-49e6-b5d5-fbd0ec5bca85
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 创建本地营销活动{#creating-a-local-campaign}

本地营销活动是从具有特定执行计划的列表中引用的模板 **[!UICONTROL campaign packages]** 创建的 **实例**。 其目标是使用由中央实体设置和配置的营销活动模板满足本地通信需求。 实施本地操作的主要步骤如下：

**对于中央实体**

1. 创建本地营销活动模板。
1. 从模板创建营销活动包。
1. 发布营销活动包。
1. 批准订单。

**对于本地实体**

1. 订购营销活动。
1. 执行营销活动。

## 创建本地营销活动模板 {#creating-a-local-campaign-template}

要创建营销活动包，您必须首先通过节 **点创建** 系列活动 **[!UICONTROL Resources > Templates]** 模板。

要创建新的本地模板，请复制默认模 **[!UICONTROL Local campaign (opLocal)]** 板。

![](assets/mkg_dist_local_op_creation.png)

命名营销活动模板并填写可用字段。

![](assets/mkg_dist_local_op_creation1.png)

在营销活动窗口中，单击选 **[!UICONTROL Edit]** 项卡，然后单击链 **[!UICONTROL Advanced campaign settings...]** 接。

![](assets/mkt_distr_4.png)

### Web界面 {#web-interface}

在“分 **布式营销** ”选项卡中，您可以选择Web界面的类型，并指定在本地实体下订单时要输入的默认值和参数。

Web界面与在订购营销活动时由本地实体填写的表单相对应。

选择要应用于从模板创建的营销活动的Web界面类型：

![](assets/mkt_distr_1.png)

可用的Web界面有四种类型：

* **[!UICONTROL By brief]** :本地实体必须提供描述营销活动配置的说明。 一旦订单获得批准，中央实体就会配置并执行整个营销活动。

   ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** :本地实体可以访问Web表单，根据使用的模板，他们可以使用个性化字段编辑内容、目标、最大大小以及创建和提取日期。 本地实体可以评估目标并预览来自此Web表单的内容。

   ![](assets/mkt_distr_8.png)

   提供的表单在Web应用程序中指定，该表单必须从模板链接的字段的下拉列 **[!UICONTROL Web Interface]** 表中进行选 **[!UICONTROL Advanced campaign settings...]** 择。 请参阅 [创建本地营销活动（按表单）](../../campaign/using/examples.md#creating-a-local-campaign--by-form-)。

   >[!NOTE]
   >
   >此示例中使用的Web应用程序就是一个示例。 您必须创建特定Web应用程序才能使用表单。 请参阅 [API](../../configuration/using/about-web-services.md)。

   ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** :本地实体有权访问其外部网（而非Adobe Campaign）中的系列活动参数。 这些参数与本地营销活动(按 **表单)的参数相同**。
* **[!UICONTROL Pre-set]** :本地实体使用默认表单对营销活动进行排序，而不将其本地化。

   ![](assets/mkt_distr_5.png)

### 默认值 {#default-values}

选择 **[!UICONTROL Default values]** 要由本地实体完成的。 例如：

* 联系和提取日期，
* 目标特征（年龄段等）。

![](assets/mkg_dist_local_op_creation2.png)

填写 **[!UICONTROL Parent marketing program]** 和字 **[!UICONTROL Charge]** 段。

![](assets/mkg_dist_local_op_creation3.png)

### 批准 {#approvals}

在链接 **[!UICONTROL Advanced parameters for campaign entry]** 中，您可以指定最大审阅人数。

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

在订购营销活动时，本地实体将输入审阅者。

![](assets/mkt_distr_5.png)

如果不想为营销活动命名审阅者，请输入0。

### 文档 {#documents}

您可以允许本地实体操作员链接文档（文本文件、电子表格、图像、营销活动描述等）创建订单时转到本地营销活动。 通过 **[!UICONTROL Advanced parameters for campaign entry...]** 该链接可以限制文档数。 为此，只需在字段中输入允许的最大数 **[!UICONTROL Number of documents]** 字。

![](assets/s_advuser_mkg_dist_local_docs.png)

在订购营销活动包时，表单建议链接模板中相应字段中指示的任意数量的文档。

![](assets/s_advuser_mkg_dist_add_docs.png)

如果不希望显示文档上传字段，请在字 **[!UICONTROL 0]** 段中输 **[!UICONTROL Number of documents]** 入。

>[!NOTE]
>
>可以 **[!UICONTROL Advanced parameters for campaign entry]** 通过检查来取消激活 **[!UICONTROL Do not display the page used to enter the campaign parameters]**。

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### 工作流 {#workflow}

在选项卡 **[!UICONTROL Targeting and workflows]** 中，创建用于收集在中指定内容并创建 **[!UICONTROL Default values]** 分发的系列活 **[!UICONTROL Advanced campaign settings...]** 动工作流。

![](assets/mkg_dist_local_op_creation4b.png)

双击活 **[!UICONTROL Query]** 动，以根据指定的配置活动 **[!UICONTROL Default values]**。

![](assets/mkt_dist_local_campaign_localize_query.png)

### 投放 {#delivery}

在选项 **[!UICONTROL Audit]** 卡中，单击 **[!UICONTROL Detail...]** 图标以查看选 **[!UICONTROL Scheduling]** 定交付的内容。

![](assets/mkg_dist_local_op_creation4c.png)

通过 **[!UICONTROL Scheduling]** 该图标，您可以配置交付的联系和执行日期。

![](assets/mkg_dist_local_op_creation4d.png)

如有必要，请配置传送的最大大小：

![](assets/mkg_dist_local_op_creation4e.png)

找到交付的HTML。 例如，在中， **[!UICONTROL Delivery > Current order > Additional fields]**&#x200B;使用字 **[!UICONTROL Age segment]** 段根据目标的年龄定位交付。

![](assets/mkt_dist_local_campaign_localize_html.png)

保存您的营销活动模板。 现在，您可以通过单击按钮， **从** “营销活动” **范围的“营销活动包”视图中使****[!UICONTROL Create]** 用它。

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>系列活动模板及其常规配置在系列活动模板 [中有详细介绍](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

## 创建营销活动包 {#creating-the-campaign-package}

要使营销活动模板对本地实体可用，需要将其添加到列表中。 为此，中央机构需要创建新的一揽子计划。

应用以下步骤：

1. 在“营 **[!UICONTROL Navigation]** 销活动”页面的 **部分** ，单击链 **[!UICONTROL Campaign packages]** 接。
1. Click the **[!UICONTROL Create]** button.

   ![](assets/mkg_dist_add_an_entry.png)

1. 通过窗口上方的部分，您可以选择以前 [指定的](#creating-a-local-campaign-template) 系列活动包模板。

   默认情况下，模 **[!UICONTROL New local campaign package (localEmpty)]** 板用于本地营销活动。

1. 指定系列活动包的标签、文件夹和执行计划。

### 日期 {#dates}

开始日期和结束日期定义营销活动包列表中营销活动的可见性时间段。

发布日期是营销活动对本地实体（要订购）可用的日期。

>[!CAUTION]
>
>如果本地实体在截止日期之前未保留营销活动，则将无法使用它。

此信息在发送给本地代理的通知消息中找到，如下所示：

![](assets/s_advuser_mkg_dist_local_notif.png)

### 受众 {#audience}

对于本地营销活动，中央实体可以通过检查来指定涉及的本地实体 **[!UICONTROL Limit the package to a set of local entities]**。

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### 其他设置 {#additional-settings}

保存包后，中央实体即可从选项卡中编辑 **[!UICONTROL Edit]** 它。

![](assets/mkg_dist_edit_kit.png)

在选项卡 **[!UICONTROL General]** 中，中心实体可以：

* 通过链接配置营销活动包审 **[!UICONTROL Approval parameters...]** 阅者，
* 审查执行计划，
* 添加或删除本地实体。

>[!NOTE]
>
>默认情况下，每个实体只能对本地营销 **活动进行** 一次订购。
>   
>选中该 **[!UICONTROL Enable multiple creation]** 选项可允许从营销活动包创建多个本地营销活动。

![](assets/mkg_dist_local_op_multi_crea.png)

### 通知 {#notifications}

当营销活动可用或达到注册截止日期时，会向本地通知组的操作员发送一条消息。 For more on this, refer to [Organizational entities](../../campaign/using/about-distributed-marketing.md#organizational-entities).

## 订购营销活动 {#ordering-a-campaign}

一旦本地实体获得批准并且其实施期已开始，即可访问营销活动包。 本地实体会收到一封电子邮件，告知他们有新的营销活动包可用（一旦到达其发布日期）。

>[!NOTE]
>
>如果在创建营销活动包时指定了某些本地实体，则只有这些实体会收到通知。 如果未指定本地实体，则所有本地实体都将收到通知。

![](assets/mkg_dist_local_op_notification.png)

要使用中央实体提供的营销活动，本地实体必须对其进行订购。

要对营销活动进行排序，请执行以下操作：

1. 在通 **[!UICONTROL Order campaign]** 知消息中单击，或在Adobe Campaign中单击相应的按钮。

   输入您的ID和密码以对营销活动进行排序。 该界面由在Web应用程序中定义的一组页面组成。

   >[!NOTE]
   >
   >Web应用程序在 [Web功能指南中有详细介绍](../../web/using/about-web-applications.md) 。

1. 在第一页（订单标签和评论）中输入必要的信息，然后单击 **[!UICONTROL Next]**。

   ![](assets/mkg_dist_subscribe_step1.png)

   完成可用参数并批准订单。

   将向本地实体所属组织实体的经理发送通知以批准此订单。

   ![](assets/mkg_dist_subscribe_step3.png)

1. 信息将返回给本地和中央实体。 虽然本地实体只能查看自己的订单，但中央实体可以按任何本地实体查看所有订单，如下所示：

   ![](assets/mkg_dist_subscribe_central_view.png)

   运营商可以显示订单详细信息：

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   该选 **[!UICONTROL Edit]** 项卡包含本地实体在订购营销活动时输入的信息。

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. 该命令必须经中央实体批准才能最终完成。

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   有关详细信息，请参阅“批准 [流程](#approval-process) ”部分。

1. 然后，将通知本地运营商该营销活动可用：营销活动可用性位于营销活动范围内的营销活动包 **列表中** 。 然后可以使用营销活动。 For more on this, refer to [Accessing campaigns](../../campaign/using/accessing-campaigns.md).

   通过 **[!UICONTROL Start targeting with order approval]** 此选项，本地实体可在订单获得批准后立即运行营销活动。

   ![](assets/mkg_dist_local_op_catalog_use.png)

## 批准订单 {#approving-an-order}

要确认营销活动订单，中央实体必须批准该订单。

通过 **[!UICONTROL Campaign orders]** “营销活动”范围访 **问的概述** ，您可以查看营销活动订单的状态并批准它们。

>[!NOTE]
>
>本地实体可以更改订单，直到订单获得批准。

### 批准流程 {#approval-process}

#### 电子邮件通知 {#email-notification}

当营销活动由本地实体订购时，其审阅者会通过电子邮件收到通知，如下所示：

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>选择审阅者显示在“审阅 [者](#reviewers) ”部分。 他们可以接受或拒绝该订单。

![](assets/mkg_dist_command_valid_web.png)

#### 通过Adobe Campaign控制台进行批准 {#approving-via-the-adobe-campaign-console}

该订单也可以通过控制台在营销活动订单概述中进行批准。 要批准订单，请选择该订单，然后单击 **[!UICONTROL Approve the order]**。

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>在营销活动发布日期之前，仍可以编辑和重新配置营销活动。 本地实体也可以通过单击按钮拒绝营销 **[!UICONTROL Cancel]** 活动。

#### 创建营销活动 {#creating-a-campaign}

营销活动订单一经批准，便可由本地实体配置和执行。

![](assets/mkg_dist_mutual_op_created.png)

For more on this, refer to [Accessing campaigns](../../campaign/using/accessing-campaigns.md).

### 拒绝批准 {#rejecting-an-approval}

负责审批的操作员可以拒绝订单或营销活动包。

![](assets/mkg_dist_do_not_valid.png)

如果审阅人拒绝了订单，则相关通知会自动发送给相关的本地实体：它显示由拒绝批准的操作员输入的注释。

信息显示在系列活动包页面列表或系列活动订单页面上。 如果他们有权访问Adobe Campaign控制台，则本地实体会收到此拒绝通知。

![](assets/mkg_dist_do_not_valid_view.png)

他们可以在营销活动包的选项卡中查看相关 **[!UICONTROL Edit]** 评论。

![](assets/mkg_dist_do_not_valid_tab.png)

### 审阅者 {#reviewers}

每次需要批准时，审阅者都会通过电子邮件通知。

对于每个本地实体，将选择审阅者进行系列活动订单批准和系列活动批准。 有关选择本地审阅者的详细信息，请参阅 [组织实体](../../campaign/using/about-distributed-marketing.md#organizational-entities)。

>[!NOTE]
>
>要使此选择成为可能，订单批准必须尚未生效。

### 取消订单 {#canceling-an-order}

中央机构可以使用订单仪表板上 **[!UICONTROL Delete]** 的按钮取消订单。

![](assets/mkg_dist_local_op_cancel.png)

这会取消视图中的营销 **[!UICONTROL Campaign orders]** 活动。
