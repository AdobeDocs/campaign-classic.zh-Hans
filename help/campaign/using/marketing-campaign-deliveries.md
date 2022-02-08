---
product: campaign
title: 营销活动投放
description: 了解有关营销活动投放的更多信息
audience: campaign
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: d3f5c56078ddac7597925191fd347bdcab61714d
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 2%

---

# 营销活动投放 {#marketing-campaign-deliveries}

![](../../assets/common.svg)

投放可通过营销活动仪表板、营销活动工作流创建，或直接通过投放概述创建。

从营销活动创建投放后，投放将链接到此营销活动，并在营销活动级别进行整合。

![](assets/do-not-localize/how-to-video.png)[ 在视频中发现此功能](#create-email-video)

## 创建投放 {#creating-deliveries}

要创建链接到营销策划的投放，请单击 **[!UICONTROL Add a delivery]** 链接。

![](assets/campaign_op_add_delivery.png)

建议的配置适用于不同类型的投放：直邮、电子邮件、移动渠道。 [了解详情](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 启动投放 {#starting-a-delivery}

在批准所有批准后，即可开始投放。 然后，投放过程取决于投放类型。 有关电子邮件或移动渠道投放，请参阅 [开始在线投放](#starting-an-online-delivery)，以及直邮投递的信息，请参阅 [启动离线投放](#starting-an-offline-delivery).

### 开始在线投放 {#starting-an-online-delivery}

在授予所有批准请求后，投放状态将更改为 **[!UICONTROL Pending confirmation]** 和可由运算符启动。 在适当情况下，指定为审阅人以开始投放的Adobe Campaign操作员（或一组操作员）会收到通知，表明投放已准备就绪，可以启动。

>[!NOTE]
>
>如果指定了特定的运算符或一组运算符以在投放的属性中启动投放，则您还可以允许负责投放的运算符确认发送。 为此，请激活 **NMS_ActivateOwnerConfirmation** 输入 **1** 作为值。 选项通过 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 节点。
>  
>要取消激活此选项，请输入 **0** 作为值。 然后，发送确认流程将起默认作用：只有在投放属性（或管理员）中为发送指定的操作员或操作员组才能确认和执行发送。

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

该信息也会显示在营销活动仪表板上。 的 **[!UICONTROL Confirm delivery]** 链接允许您开始投放。

![](assets/s_ncs_user_edit_del_to_start.png)

通过确认消息，您可以确保此操作的安全。

### 启动离线投放 {#starting-an-offline-delivery}

在授予所有批准后，投放状态将更改为 **[!UICONTROL Pending extraction]**. 提取文件通过特殊的工作流创建，在默认配置中，当直邮投放处于待提取状态时，该工作流会自动启动。 进程进行中时，该进程会显示在功能板中，并可通过其链接进行编辑。

>[!NOTE]
>
>与Campaign包相关的技术工作流，请参见 [技术工作流列表](../../workflow/using/about-technical-workflows.md).

**步骤1 — 文件批准**

成功执行提取工作流后，必须批准提取文件（前提是已在投放设置中选择提取文件的批准）。

有关更多信息，请参阅 [批准提取文件](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**步骤2 — 将消息批准给服务提供商**

* 提取文件获得批准后，即可生成路由器通知电子邮件的校样。 此电子邮件基于投放模板构建。 必须获得批准。

   >[!NOTE]
   >
   >只有在批准窗口中启用了校样的发送和批准时，此步骤才可用。

![](assets/s_ncs_user_file_valid_select_BAT.png)


* 单击 **[!UICONTROL Send a proof]** 按钮以创建校样。

   校样目标必须事先定义。

   您可以创建所需数量的校样。 可通过 **[!UICONTROL Direct mail...]** 投放详细信息的链接。

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* 投放状态将更改为 **[!UICONTROL To submit]**. 单击 **[!UICONTROL Submit proofs]** 按钮以启动批准流程。

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* 投放状态将更改为 **[!UICONTROL Proof to validate]** 而按钮则允许您接受或拒绝批准。

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   您可以接受或拒绝此批准，或返回提取步骤。

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* 提取文件将发送到路由器，并完成交付。

### 费用和库存计算 {#calculation-of-costs-and-stocks}

文件提取会启动两个操作：预算计算和库存计算。 预算条目会更新。

* 的 **[!UICONTROL Budget]** 选项卡，用于管理营销活动的预算。 成本分录的合计显示在 **[!UICONTROL Calculates cost]** 营销活动主选项卡及其所属项目的字段。 金额也反映在促销活动预算中。

   实际成本最终将根据路由器提供的信息计算。 只有实际发送的消息才会开票。

* 股票于 **[!UICONTROL Administration > Campaign management > Stocks]** 树节点，以及 **[!UICONTROL Administration > Campaign management > Service providers]** 节点。

   库存行在库存部分中可见。 要定义初始库存，请打开库存行。 每次交货时，库存都会减少。 您可以定义警报级别和通知。

>[!NOTE]
>
>有关成本计算和库存管理的详细信息，请参阅 [供应商、库存和预算](../../campaign/using/providers--stocks-and-budgets.md).

## 管理关联文档 {#managing-associated-documents}

您可以将各种文档与活动关联起来：报表、照片、网页、图表等。这些文档可以采用任何格式(Microsoft Word、PowerPoint、PNG、JPG、AcrobatPDF等)。 了解如何将文档与营销活动关联 [在此部分中](../../campaign/using/marketing-campaign-assets.md).

>[!IMPORTANT]
>
>此模式专为小文档保留。

在营销活动中，您还可以参考其他项目，例如促销优惠券、与特定分店或商店相关的特价优惠等。 当这些元素包含在大纲中时，它们可以与直邮投放相关联。 [了解详情](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用的是MRM，则还可以管理可供多个参与者协作工作的营销资源库。 请参阅 [管理营销资源](../../mrm/using/managing-marketing-resources.md).

### 添加文档 {#adding-documents}

文档可以在营销策划级别（上下文文档）或项目级别（常规文档）进行关联。

的 **[!UICONTROL Documents]** 选项卡包含：

* 内容所需的所有文档的列表（模板、图像等） 可由Adobe Campaign运营商在本地下载，
* 包含路由器信息的文档（如果有）。

文档通过 **[!UICONTROL Edit > Documents]** 选项卡。

![](assets/s_ncs_user_op_add_document.png)

您还可以通过营销策划仪表板中提供的链接，将文档添加到营销策划。

![](assets/add_a_document_in_op.png)

单击 **[!UICONTROL Details]** 图标以查看文件内容并添加信息：

![](assets/s_ncs_user_op_add_document_details.png)

在功能板中，与营销活动关联的文档分组在 **[!UICONTROL Document(s)]** 部分，如以下示例中所示：

![](assets/s_ncs_user_op_edit_document.png)

也可以从此视图编辑和修改它们。

### 通过投放大纲关联和构建链接的资源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>投放大纲专门用于直邮营销活动的上下文。

投放大纲表示一组结构化元素（文档、分支/商店、促销优惠券等） 在公司中创建，并用于特定营销活动。

这些元素按投放大纲分组，并将特定投放大纲与投放相关联；它将在发送到的提取文件中引用 **服务提供商** 以便附在投放上。 例如，您可以创建一个投放大纲，以引用分支及其使用的营销手册。

对于营销活动，投放大纲允许您根据特定条件构建要与投放关联的外部元素：相关分支、已授予的促销优惠、参加当地活动的邀请等。

#### 创建大纲 {#creating-an-outline}

要创建大纲，请单击 **[!UICONTROL Delivery outlines]** 子选项卡 **[!UICONTROL Edit > Documents]** 选项卡。

>[!NOTE]
>
>如果此选项卡不存在，则此功能不适用于此营销活动。 请参阅营销活动模板配置。
>   
>有关更多信息，请参阅 [营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

接下来，单击 **[!UICONTROL Add a delivery outline]** 和为营销活动创建大纲层次结构：

1. 右键单击树的根并选择 **[!UICONTROL New > Delivery outlines]**.
1. 右键单击刚刚创建的大纲并选择 **[!UICONTROL New > Item]** 或 **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

大纲可以包含项目和个性化字段、资源和选件：

* 项目可以是实物文档，例如，此处引用和描述的物体文档，将附加到投放。
* 个性化字段允许您创建与投放相关的个性化元素，而不是收件人。 因此，可以创建用于特定目标（欢迎选件、折扣等）投放的值 这些配置文件将在Adobe Campaign中创建，并通过 **[!UICONTROL Import personalization fields...]** 链接。

   ![](assets/s_ncs_user_op_add_composition_field.png)

   也可以通过单击 **[!UICONTROL Add]** 图标。

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 资源是指在营销资源仪表板中通过 **[!UICONTROL Resources]** 链接 **[!UICONTROL Campaigns]** 选项卡。

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >有关营销资源的更多信息，请参阅 [管理营销资源](../../mrm/using/managing-marketing-resources.md).

#### 选择大纲 {#selecting-an-outline}

对于每个投放，您可以从为提取大纲保留的部分中选择要关联的大纲，如以下示例中所示：

![](assets/s_ncs_user_op_select_composition.png)

选定的轮廓随后显示在窗口的下部。 可以使用字段右侧的图标进行编辑，也可以使用下拉列表进行更改：

![](assets/s_ncs_user_op_select_composition_b.png)

的 **[!UICONTROL Summary]** 的选项卡中，还会显示以下信息：

![](assets/s_ncs_user_op_select_composition_c.png)

#### 提取结果 {#extraction-result}

在提取并发送给服务提供商的文件中，大纲的名称，并在适当情况下，其特征（成本、描述等） 根据与服务提供商关联的导出模板中的信息，被添加到内容中。

在以下示例中，将与投放关联的大纲的标签、估计成本和描述将添加到提取文件中。

![](assets/s_ncs_user_op_composition_in_export_template.png)

导出模型必须与为相关投放选择的服务提供商关联。 请参阅 [创建服务提供商及其成本结构](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>有关导出的更多信息，请参阅 [快速入门](../../platform/using/get-started-data-import-export.md) 中。

#### 教程视频 {#create-email-video}

此视频介绍如何在Adobe Campaign中创建营销活动和电子邮件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

还提供其他Campaign操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
