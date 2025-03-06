---
product: campaign
title: 营销活动投放
description: 了解有关营销活动投放的更多信息
role: User
feature: Campaigns, Resource Management, Cross Channel Orchestration
hide: true
hidefromtoc: true
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 1%

---

# 营销活动投放 {#marketing-campaign-deliveries}

可通过活动功能板、活动工作流或直接通过投放概述创建投放。

从营销活动创建投放后，这些投放将链接到此营销活动，并在营销活动级别合并。

![](assets/do-not-localize/how-to-video.png)[在视频中发现此功能](#create-email-video)

## 创建投放 {#creating-deliveries}

要创建链接到营销活动的投放，请单击营销活动仪表板中的&#x200B;**[!UICONTROL Add a delivery]**&#x200B;链接。

![](assets/campaign_op_add_delivery.png)

建议的配置适用于不同类型的投放：直邮、电子邮件、移动渠道。 [了解详情](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 开始投放 {#starting-a-delivery}

获得所有批准后，即可开始投放。 然后，投放过程取决于投放类型。 对于电子邮件或移动渠道投放，请参阅[开始在线投放](#starting-an-online-delivery)；对于直邮投放，请参阅[开始离线投放](#starting-an-offline-delivery)。

### 开始在线投放 {#starting-an-online-delivery}

在批准所有审批请求后，投放状态将更改为&#x200B;**[!UICONTROL Pending confirmation]**，并可由操作员启动。 在适当的情况下，被指定作为开始传送的审阅者的Adobe Campaign操作员（或操作员组）将收到传送已准备好开始的通知。

>[!NOTE]
>
>如果指定了特定操作员或操作员组来在投放的属性中开始投放，您还可以允许负责投放的操作员确认发送。 为此，请通过输入&#x200B;**1**&#x200B;作为值来激活&#x200B;**NMS_ActivateOwnerConfirmation**&#x200B;选项。 这些选项是从Adobe Campaign资源管理器中的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;节点管理的。
>  
>要停用此选项，请输入&#x200B;**0**&#x200B;作为值。 然后，发送确认流程将默认运行：只有投放属性中为发送指定的操作员或操作员组（或管理员）才能确认并执行发送。

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

该信息也会显示在促销活动信息板上。 **[!UICONTROL Confirm delivery]**&#x200B;链接允许您开始投放。

![](assets/s_ncs_user_edit_del_to_start.png)

使用确认消息，您可以保护此操作的安全。

### 开始离线投放 {#starting-an-offline-delivery}

获得所有审批后，投放状态将更改为&#x200B;**[!UICONTROL Pending extraction]**。 提取文件通过特殊工作流创建，在默认配置中，当直邮投放挂起提取时，将自动启动该工作流。 当流程正在进行时，它将显示在仪表板中，并可通过其链接进行编辑。

>[!NOTE]
>
>与营销活动包相关的技术工作流显示在[技术工作流列表](../../workflow/using/about-technical-workflows.md)中。

**步骤1 — 文件审批**

成功执行提取工作流后，必须批准提取文件（前提是在投放设置中选择了提取文件批准）。

有关详细信息，请参阅[批准提取文件](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file)。

**步骤2 — 批准发送给服务提供者的消息**

* 提取文件获得批准后，即可生成路由器通知电子邮件的证明。 此电子邮件基于投放模板构建。 它必须被批准。

  >[!NOTE]
  >
  >仅当在审批窗口中启用了验证的发送和审批时，此步骤才可用。

![](assets/s_ncs_user_file_valid_select_BAT.png)


* 单击&#x200B;**[!UICONTROL Send a proof]**&#x200B;按钮以创建校样。

  必须预先定义验证目标。

  您可以创建所需数量的验证。 可通过投放详细信息的&#x200B;**[!UICONTROL Direct mail...]**&#x200B;链接访问这些内容。

  ![](assets/s_ncs_user_file_notif_submit_proof.png)

* 投放状态更改为&#x200B;**[!UICONTROL To submit]**。 单击&#x200B;**[!UICONTROL Submit proofs]**&#x200B;按钮开始审批流程。

  ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* 投放状态更改为&#x200B;**[!UICONTROL Proof to validate]**，并且有一个按钮允许您接受或拒绝审批。

  ![](assets/s_ncs_user_file_notif_supplier_link.png)

  您可以接受或拒绝此批准，或返回提取步骤。

  ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* 提取文件将发送到路由器，并完成投放。

### 成本和库存的计算 {#calculation-of-costs-and-stocks}

文件提取将启动两项操作：预算计算和库存计算。 更新预算条目。

* 通过&#x200B;**[!UICONTROL Budget]**&#x200B;选项卡，您可以管理营销活动的预算。 成本条目的总数显示在营销活动主选项卡及其所属项目的&#x200B;**[!UICONTROL Calculates cost]**&#x200B;字段中。 这些金额还反映在营销活动预算中。

  最终将根据路由器提供的信息计算实际成本。 只有实际发送的消息才会被计费。

* 库存在树的&#x200B;**[!UICONTROL Administration > Campaign management > Stocks]**&#x200B;节点中定义，成本结构在&#x200B;**[!UICONTROL Administration > Campaign management > Service providers]**&#x200B;节点中定义。

  库存行在库存区中可见。 要定义初始坯件，请打开坯件线。 每次进行交货时，库存都会减少。 您可以定义警报级别和通知。

>[!NOTE]
>
>有关成本计算和库存管理的详细信息，请参阅[供应商、库存和预算](../../campaign/using/providers-stocks-and-budgets.md)。

## 管理关联文档 {#managing-associated-documents}

您可以将如报告、照片、网页、图表等各种文档与营销活动关联起来。这些文档可以是任何格式(Microsoft Word、PowerPoint、PNG、JPG、Acrobat PDF等)。 在本节](../../campaign/using/marketing-campaign-assets.md)中了解如何将文档与促销活动[关联。

>[!IMPORTANT]
>
>此模式为小文档保留。

在营销策划中，您还可以参考其他项目，如促销优惠券、与特定分支或商店相关的特殊优惠等。 当这些元素包含在大纲中时，它们可以与直邮投放相关联。 [了解详情](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用的是MRM，您还可以管理营销资源库，该库可供多个参与者用于协作工作。 请参阅[管理营销资源](../../mrm/using/managing-marketing-resources.md)。

### 添加文档 {#adding-documents}

文档可以在营销活动级别（上下文文档）或项目群级别（常规文档）关联。

**[!UICONTROL Documents]**&#x200B;选项卡包含：

* 具有适当权限的Adobe Campaign操作员可本地下载的内容（模板、图像等）所需的所有文档列表，
* 包含路由器信息的文档（如果有）。

这些文档通过&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;选项卡链接到项目或营销策划。

![](assets/s_ncs_user_op_add_document.png)

您还可以通过信息板中提供的链接将文档添加到营销活动。

![](assets/add_a_document_in_op.png)

单击&#x200B;**[!UICONTROL Details]**&#x200B;图标可查看文件内容并添加信息：

![](assets/s_ncs_user_op_add_document_details.png)

在仪表板中，与营销活动关联的文档分组到&#x200B;**[!UICONTROL Document(s)]**&#x200B;部分，如以下示例所示：

![](assets/s_ncs_user_op_edit_document.png)

也可以从此视图编辑和修改它们。

### 关联并构建通过投放概要链接的资源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>投放大纲仅用于直邮营销活动的上下文。

投放概要表示在公司中为特定营销活动创建的结构化元素集（文档、分支/商店、促销优惠券等）。

这些元素在投放概要中分组，并且特定的投放概要将与投放关联；在发送到&#x200B;**服务提供商**&#x200B;的提取文件中将引用该投放概要，以便将其附加到投放。 例如，您可以创建一个投放概要，其中引用分支及其使用的营销小册子。

对于营销活动，利用投放概要，可根据特定条件构建要与投放关联的外部元素：相关分支、授予的促销优惠、本地活动邀请等。

#### 创建大纲 {#creating-an-outline}

要创建大纲，请在相关营销活动的&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;选项卡中单击&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子选项卡。

>[!NOTE]
>
>如果此选项卡不存在，则此功能不适用于此营销活动。 请参阅活动模板配置。
>   
>有关详细信息，请参阅[营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

![](assets/s_ncs_user_op_composition_link.png)

接下来，单击&#x200B;**[!UICONTROL Add a delivery outline]**&#x200B;并为该营销活动创建大纲的层次结构：

1. 右键单击树的根并选择&#x200B;**[!UICONTROL New > Delivery outlines]**。
1. 右键单击刚刚创建的大纲，然后选择&#x200B;**[!UICONTROL New > Item]**&#x200B;或&#x200B;**[!UICONTROL New > Personalization fields]**。

![](assets/s_ncs_user_op_add_composition.png)

大纲可包含项目和个性化字段、资源和选件：

* 项目可以是物理文档，例如，此处引用和描述的文档，将附加到投放。
* 通过个性化字段，您可以创建与投放而不是收件人相关的个性化元素。 因此，可以创建值以用于特定目标的投放（欢迎优惠、折扣等） 它们在Adobe Campaign中创建，并通过&#x200B;**[!UICONTROL Import personalization fields...]**&#x200B;链接导入大纲。

  ![](assets/s_ncs_user_op_add_composition_field.png)

  也可以通过单击列表区域右侧的&#x200B;**[!UICONTROL Add]**&#x200B;图标，直接在大纲中创建它们。

  ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 资源是在营销资源仪表板中生成的营销资源，可通过&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Resources]**&#x200B;链接访问。

  ![](assets/s_ncs_user_mkg_resource_ovv.png)

  >[!NOTE]
  >
  >有关营销资源的详细信息，请参阅[管理营销资源](../../mrm/using/managing-marketing-resources.md)。

#### 选择大纲 {#selecting-an-outline}

对于每次投放，您可以从为提取大纲保留的节中选择要关联的大纲，如以下示例所示：

![](assets/s_ncs_user_op_select_composition.png)

然后，所选轮廓将显示在窗口的下部。 可使用字段右侧的图标编辑或使用下拉列表更改它：

![](assets/s_ncs_user_op_select_composition_b.png)

投放的&#x200B;**[!UICONTROL Summary]**&#x200B;选项卡也显示以下信息：

![](assets/s_ncs_user_op_select_composition_c.png)

#### 提取结果 {#extraction-result}

在提取并发送到服务提供商的文件中，根据与服务提供商相关的导出模板中的信息将大纲的名称以及适当时其特征（成本、描述等）添加到内容中。

在以下示例中，与投放关联的大纲的标签、预计成本和描述将添加到提取文件中。

![](assets/s_ncs_user_op_composition_in_export_template.png)

导出模型必须与为相关投放选择的服务提供商关联。 请参阅[创建服务提供商及其成本结构](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有关导出的详细信息，请参阅[快速入门](../../platform/using/get-started-data-import-export.md)一节。

#### 教程视频 {#create-email-video}

此视频介绍如何在Adobe Campaign中创建活动和电子邮件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign操作方法视频。
