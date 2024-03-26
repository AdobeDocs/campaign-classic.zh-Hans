---
product: campaign
title: 创建本地活动
description: 创建本地活动
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Distributed Marketing
exl-id: 17b5865a-5e04-4b3b-8b6a-12d5c1a9c1da
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1572'
ht-degree: 2%

---

# 创建本地活动{#creating-a-local-campaign}



本地营销活动是从列表中引用的模板创建的实例 **[!UICONTROL campaign packages]** 带有 **特定执行计划**. 其目标是使用由中央实体设置和配置的活动模板满足本地通信需求。 实施本地操作的主要阶段如下：

**对于中央实体**

1. 创建本地活动模板。
1. 从模板创建活动包。
1. 发布活动包。
1. 正在审批订单。

**对于本地实体**

1. 订购营销活动。
1. 执行活动。

## 创建本地活动模板 {#creating-a-local-campaign-template}

要创建营销活动包，您必须先创建 **活动模板** 通过 **[!UICONTROL Resources > Templates]** 节点。

要创建新的本地模板，请复制默认模板 **[!UICONTROL Local campaign (opLocal)]** 模板。

![](assets/mkg_dist_local_op_creation.png)

命名您的营销活动模板并填写可用字段。

![](assets/mkg_dist_local_op_creation1.png)

在营销策划窗口中，单击 **[!UICONTROL Edit]** 选项卡，然后单击 **[!UICONTROL Advanced campaign settings...]** 链接。

![](assets/mkt_distr_4.png)

### Web 界面 {#web-interface}

在 **分布式营销** 选项卡，可以选择Web界面的类型，并指定本地实体下订单时要输入的默认值和参数。

Web界面对应于本地实体在订购营销活动时要填充的表单。

选择要应用于从模板创建的营销活动的Web界面类型：

![](assets/mkt_distr_1.png)

有四种类型的Web界面可用：

* **[!UICONTROL By brief]** ：本地实体必须提供描述，用于描述campaign配置。 订单获得批准后，中央实体会配置并执行整个营销活动。

  ![](assets/mkt_distr_6.png)

* **[!UICONTROL By form]** ：本地实体有权访问Web表单，在该Web表单中，他们可以使用个性化字段编辑内容、目标、其最大大小以及创建和提取日期，具体取决于使用的模板。 本地实体可以评估目标并预览此Web窗体中的内容。

  ![](assets/mkt_distr_8.png)

  提供的表单在Web应用程序中指定，必须从以下位置下拉列表中选择该表单： **[!UICONTROL web Interface]** 模板中的字段 **[!UICONTROL Advanced campaign settings...]** 链接。 请参阅 [创建本地活动（按表单）](examples.md#creating-a-local-campaign--by-form-).

  >[!NOTE]
  >
  >本示例中使用的Web应用程序就是一个示例。 您必须创建特定的Web应用程序才能使用表单。 请参阅 [API](../../configuration/using/about-web-services.md).

  ![](assets/mkt_distr_7.png)

* **[!UICONTROL By external form]** ：本地实体有权访问其外网(非Adobe Campaign)中的营销活动参数。 这些参数与 **本地营销活动（按表单）**.
* **[!UICONTROL Pre-set]** ：本地实体使用默认表单订购营销活动，而不进行本地化。

  ![](assets/mkt_distr_5.png)

### 默认值 {#default-values}

选择 **[!UICONTROL Default values]** 将由本地实体完成。 例如：

* 联系和提取日期，
* 目标特征（年龄段等）。

![](assets/mkg_dist_local_op_creation2.png)

完成 **[!UICONTROL Parent marketing program]** 和 **[!UICONTROL Charge]** 字段。

![](assets/mkg_dist_local_op_creation3.png)

### 审批 {#approvals}

从 **[!UICONTROL Advanced parameters for campaign entry]** 链接，您可以指定审阅人的最大数量。

![](assets/s_advuser_mkg_dist_add_valid_op1.png)

订购营销活动时，审阅人将由本地实体输入。

![](assets/mkt_distr_5.png)

如果不希望为促销活动命名审阅者，请输入0。

### 文档 {#documents}

您可以允许本地实体运算符链接文档（文本文件、电子表格、图像、营销活动描述等） 到本地营销活动。 此 **[!UICONTROL Advanced parameters for campaign entry...]** 链接允许您限制文档数量。 要实现此目的，只需输入 **[!UICONTROL Number of documents]** 字段。

![](assets/s_advuser_mkg_dist_local_docs.png)

在订购营销活动包时，表单会建议关联模板中相应字段中所指示的任意数量的文档。

![](assets/s_advuser_mkg_dist_add_docs.png)

如果不希望显示文档上传字段，请输入 **[!UICONTROL 0]** 在 **[!UICONTROL Number of documents]** 字段。

>[!NOTE]
>
>此 **[!UICONTROL Advanced parameters for campaign entry]** 可以通过检查取消激活 **[!UICONTROL Do not display the page used to enter the campaign parameters]**.

![](assets/s_advuser_mkg_dist_disable_op_parameters.png)

### 工作流 {#workflow}

在 **[!UICONTROL Targeting and workflows]** 选项卡，创建用于收集 **[!UICONTROL Default values]** 指定于 **[!UICONTROL Advanced campaign settings...]** 并创建投放。

![](assets/mkg_dist_local_op_creation4b.png)

双击 **[!UICONTROL Query]** 活动，以根据指定的进行配置 **[!UICONTROL Default values]**.

![](assets/mkt_dist_local_campaign_localize_query.png)

### 投放 {#delivery}

在 **[!UICONTROL Audit]** 选项卡，单击 **[!UICONTROL Detail...]** 图标以查看 **[!UICONTROL Scheduling]** 所选投放的。

![](assets/mkg_dist_local_op_creation4c.png)

此 **[!UICONTROL Scheduling]** 图标可让您配置投放的联系和执行日期。

![](assets/mkg_dist_local_op_creation4d.png)

如有必要，请配置投放的最大大小：

![](assets/mkg_dist_local_op_creation4e.png)

找到投放的HTML。 例如，在 **[!UICONTROL Delivery > Current order > Additional fields]**，使用 **[!UICONTROL Age segment]** 字段，用于根据目标的年龄定位投放。

![](assets/mkt_dist_local_campaign_localize_html.png)

保存您的活动模板。 您现在可以从以下位置使用它： **[!UICONTROL Campaign packages]** 在中查看 **[!UICONTROL Campaigns]** 选项卡，通过单击 **[!UICONTROL Create]** 按钮。

![](assets/mkt_distr_9.png)

>[!NOTE]
>
>有关营销活动模板及其常规配置的详情，请参见 [营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

## 创建活动包 {#creating-the-campaign-package}

要使营销活动模板可供本地实体使用，需要将其添加到列表中。 为此，中央机构需要制定新的方案。

应用以下步骤：

1. 在 **[!UICONTROL Navigation]** 部分，位于 **营销活动** 页面上，单击 **[!UICONTROL Campaign packages]** 链接。
1. 单击 **[!UICONTROL Create]** 按钮。

   ![](assets/mkg_dist_add_an_entry.png)

1. 窗口上方的部分允许您选择 [以前](#creating-a-local-campaign-template) 指定的活动包模板。

   默认情况下， **[!UICONTROL New local campaign package (localEmpty)]** 模板用于本地营销活动。

1. 指定活动包的标签、文件夹和执行计划。

### 日期 {#dates}

开始日期和结束日期定义营销活动包列表中的营销活动可见性时段。

可用日期是促销活动对本地实体（要订购）可用的日期。

>[!CAUTION]
>
>如果本地实体未在截止日期前预留营销活动，则将无法使用该营销活动。

此信息可在发送给本地机构的通知消息中找到，如下所示：

![](assets/s_advuser_mkg_dist_local_notif.png)

### 受众 {#audience}

对于本地活动，中央实体可以通过检查 **[!UICONTROL Limit the package to a set of local entities]**.

![](assets/s_advuser_mkg_dist_create_mutual_entry3.png)

### 其他设置 {#additional-settings}

保存包后，中央实体可以从以下位置编辑包 **[!UICONTROL Edit]** 选项卡。

![](assets/mkg_dist_edit_kit.png)

从 **[!UICONTROL General]** 选项卡，中央实体可以：

* 从配置campaign包审阅者 **[!UICONTROL Approval parameters...]** 链接，
* 查看执行计划，
* 添加或删除本地实体。

>[!NOTE]
>
>默认情况下，每个实体都可以对 **本地营销活动** 仅一次。
>   
>查看 **[!UICONTROL Enable multiple creation]** 选项，以允许从营销活动包创建多个本地营销活动。

![](assets/mkg_dist_local_op_multi_crea.png)

### 通知 {#notifications}

当营销活动可用或达到注册截止日期时，将向本地通知组的操作员发送消息。 有关详细信息，请参见 [组织实体](about-distributed-marketing.md#organizational-entities).

## 订购营销活动 {#ordering-a-campaign}

活动包获得批准且实施期开始后，本地实体即可访问这些活动包。 本地实体会收到一封电子邮件，通知他们新的Campaign包可用（一旦达到可用日期）。

>[!NOTE]
>
>如果在创建活动包时指定了某些本地实体，则它们将是唯一接收通知的本地实体。 如果未指定本地实体，则所有本地实体都将收到通知。

![](assets/mkg_dist_local_op_notification.png)

要使用中央实体提供的营销策划，本地实体必须对其进行排序。

要订购活动，请执行以下操作：

1. 单击 **[!UICONTROL Order campaign]** 或Adobe Campaign中的相应按钮进行修改。

   输入您的ID和密码以订购营销活动。 该界面由Web应用程序中定义的一组页面组成。

   >[!NOTE]
   >
   >有关Web应用程序的详情，请参见 [本节](../../web/using/about-web-applications.md).

1. 在首页中输入必需的信息（订单标签和备注），然后单击 **[!UICONTROL Next]**.

   ![](assets/mkg_dist_subscribe_step1.png)

1. 完成可用参数并批准订单。

1. 系统会向本地实体所属组织实体的经理发送通知，以批准此订单。

   ![](assets/mkg_dist_subscribe_step3.png)

1. 信息被返回到本地和中央实体。 虽然本地实体只能查看自己的订单，但中央实体可以查看任何本地实体的所有订单，如下所示：

   ![](assets/mkg_dist_subscribe_central_view.png)

   操作员可以显示订单详细信息：

   ![](assets/mkg_dist_local_op_catalog_detail_1.png)

   此 **[!UICONTROL Edit]** 选项卡包含本地实体在订购营销活动时输入的信息。

   ![](assets/mkg_dist_local_op_catalog_detail_1b.png)

1. 该命令必须得到中央实体的批准才能最后确定。

   ![](assets/mkg_dist_local_op_catalog_detail_3.png)

   有关详细信息，请参见 [审批流程](#approval-process) 部分。

1. 然后，会通知本地操作员该活动可用：可在以下位置的campaign包列表中找到campaign可用性： **营销活动** 选项卡。 然后，可以使用营销策划。 有关详细信息，请参见 [访问活动](accessing-campaigns.md).

   此 **[!UICONTROL Start targeting with order approval]** 选项允许本地实体在订单获得批准后立即运行活动。

   ![](assets/mkg_dist_local_op_catalog_use.png)

## 批准订单 {#approving-an-order}

要确认促销活动订单，必须获得中心实体的批准。

此 **[!UICONTROL Campaign orders]** 概述，可通过 **营销活动** 选项卡允许您查看并批准营销活动订单的状态。

>[!NOTE]
>
>本地实体可以对订单进行更改，直到获得批准为止。

### 审批流程 {#approval-process}

#### 电子邮件通知 {#email-notification}

当营销活动由本地实体订购时，其查看者会收到电子邮件通知，如下所示：

![](assets/mkg_dist_valid_notif_email.png)

>[!NOTE]
>
>选择审阅人将显示在 [审阅者](#reviewers) 部分。 他们可以接受或拒绝该订单。

![](assets/mkg_dist_command_valid_web.png)

#### 通过Adobe Campaign控制台进行审批 {#approving-via-the-adobe-campaign-console}

也可以在营销活动订单概述中，通过控制台批准订单。 要批准订单，请选择该订单并单击 **[!UICONTROL Approve the order]**.

![](assets/mkg_dist_local_order_valid.png)

>[!NOTE]
>
>在营销活动可用日期之前，仍可以编辑和重新配置营销活动。 本地实体也可以通过单击 **[!UICONTROL Cancel]** 按钮。

#### 创建活动 {#creating-a-campaign}

营销活动订单获得批准后，可以由本地实体配置并执行。

![](assets/mkg_dist_mutual_op_created.png)

有关详细信息，请参见 [访问活动](accessing-campaigns.md).

### 拒绝审批 {#rejecting-an-approval}

负责审批的操作员可以拒绝订单或活动程序包。

![](assets/mkg_dist_do_not_valid.png)

如果复查人拒绝订单，则系统会自动将相关通知发送给相关的本地实体：显示拒绝审批的操作员输入的备注。

信息显示在活动包列表页面或活动订单页面上。 如果他们有权访问Adobe Campaign控制台，则会将此拒绝通知本地实体。

![](assets/mkg_dist_do_not_valid_view.png)

他们可以在营销活动包的内容中查看相关评论 **[!UICONTROL Edit]** 选项卡。

![](assets/mkg_dist_do_not_valid_tab.png)

### 审阅者 {#reviewers}

每次需要审批时，审阅人都会收到电子邮件通知。

对于每个本地实体，将选择审阅人进行营销活动订单批准和营销活动批准。 有关选择本地审阅者的详细信息，请参阅 [组织实体](about-distributed-marketing.md#organizational-entities).

>[!NOTE]
>
>要使此选择成为可能，订单审批必须尚未生效。

### 取消订单 {#canceling-an-order}

中央机构可使用以下方式取消订单 **[!UICONTROL Delete]** 按钮，位于订单控制面板上。

![](assets/mkg_dist_local_op_cancel.png)

这将取消以下位置中的营销活动： **[!UICONTROL Campaign orders]** 视图。
