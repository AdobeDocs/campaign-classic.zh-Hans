---
solution: Campaign Classic
product: campaign
title: 营销活动投放
description: 了解有关营销活动投放的更多信息
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 1%

---


# 营销活动投放{#marketing-campaign-deliveries}

投放可以通过活动仪表板、活动工作流或直接通过投放概述创建。

当从活动创建投放时，将链接到此活动并在活动级别进行整合。

![](assets/do-not-localize/how-to-video.png)[ 在视频中发现此功能](#create-email-video)

## 创建投放{#creating-deliveries}

要创建链接到活动的投放，请单击活动仪表板中的&#x200B;**[!UICONTROL Add a delivery]**&#x200B;链接。

![](assets/campaign_op_add_delivery.png)

建议的配置适用于不同类型的投放:直邮、电子邮件、移动渠道。 [了解详情](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 启动投放{#starting-a-delivery}

一旦所有批准都获得批准，投放即可开始。 然后，投放过程取决于投放的类型。 有关电子邮件或移动渠道投放，请参阅[启动联机投放](#starting-an-online-delivery)和有关直接邮件投放，请参阅[启动脱机投放](#starting-an-offline-delivery)。

### 启动联机投放{#starting-an-online-delivery}

在授予所有批准请求后，投放状态将更改为&#x200B;**[!UICONTROL Pending confirmation]**，可由操作员启动。 在适当时，指定为开始投放的审阅者的Adobe Campaign运算符(或操作员组)会通知投放已准备好启动。

>[!NOTE]
>
>如果指定了特定运算符或操作员组以在投放的属性中启动投放，则您还可以允许负责投放的运算符确认发送。 为此，请输入&#x200B;**1**&#x200B;作为值，激活&#x200B;**NMS_ActivateOwnerConfirmation**&#x200B;选项。 这些选项从Adobe Campaign资源管理器中的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;节点进行管理。
>  
>要取消激活此选项，请输入&#x200B;**0**&#x200B;作为值。 然后，发送确认过程将作为默认过程运行：只有在“投放”属性（或管理员）中为发送指定的运算符或操作员组才能确认并执行发送。

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

该信息也会显示在活动仪表板上。 通过&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;链接可开始投放。

![](assets/s_ncs_user_edit_del_to_start.png)

通过确认消息，您可以保护此操作。

### 启动脱机投放{#starting-an-offline-delivery}

授予所有批准后，投放状态将更改为&#x200B;**[!UICONTROL Pending extraction]**。 提取文件是通过特殊工作流创建的，在默认配置中，当直接邮件投放挂起提取时，将自动开始。 当进程进行中时，该进程将显示在仪表板中，并可通过其链接进行编辑。

>[!NOTE]
>
>与活动包相关的技术工作流以技术工作流](../../workflow/using/about-technical-workflows.md)的[列表显示。

**步骤1 — 文件批准**

成功执行提取工作流后，必须批准提取文件(前提是在投放设置中选择了提取文件批准)。

有关详细信息，请参阅[批准提取文件](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file)。

**第2步 — 批准发送给服务提供商的消息**

* 批准提取文件后，您可以生成路由器通知电子邮件的验证。 此电子邮件是基于投放模板构建的。 必须批准。

   >[!NOTE]
   >
   >仅当在批准窗口中启用了验证的发送和批准时，此步骤才可用。

![](assets/s_ncs_user_file_valid_select_BAT.png)


* 单击&#x200B;**[!UICONTROL Send a proof]**&#x200B;按钮以创建验证。

   验证目标必须事先定义。

   您可以创建任意所需数量的验证。 可通过投放详细信息的&#x200B;**[!UICONTROL Direct mail...]**&#x200B;链接访问这些链接。

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* 投放状态将更改为&#x200B;**[!UICONTROL To submit]**。 单击&#x200B;**[!UICONTROL Submit proofs]**&#x200B;按钮以开始批准过程。

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* 投放状态更改为&#x200B;**[!UICONTROL Proof to validate]**，并且通过按钮可以接受或拒绝批准。

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   您可以接受或拒绝此批准，或返回到提取步骤。

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* 提取文件将发送到路由器，投放完成。

### 费用和库存计算{#calculation-of-costs-and-stocks}

文件提取启动两个操作：预算计算和库存计算。 将更新预算条目。

* 使用&#x200B;**[!UICONTROL Budget]**&#x200B;选项卡可以管理活动的预算。 成本条目的合计显示在活动主选项卡的&#x200B;**[!UICONTROL Calculates cost]**&#x200B;字段中，并显示它所属的项目。 金额也反映在活动预算中。

   实际成本最终将由路由器提供的信息计算。 只有实际发送的消息才会开票。

* 库存在树的&#x200B;**[!UICONTROL Administration > Campaign management > Stocks]**&#x200B;节点中定义，成本结构在&#x200B;**[!UICONTROL Administration > Campaign management > Service providers]**&#x200B;节点中定义。

   库存线在库存部分中可见。 要定义初始库存，请打开一个库存行。 每次发生投放时，库存会减少。 您可以定义警报级别和通知。

>[!NOTE]
>
>有关成本计算和库存管理的更多信息，请参阅[提供商、库存和预算](../../campaign/using/providers--stocks-and-budgets.md)。

## 管理关联的文档{#managing-associated-documents}

您可以将各种文档与活动关联：报表、照片、网页、图表等。 这些文档可以采用任何格式(Microsoft Word、PowerPoint、PNG、JPG、Acrobat PDF等)。 了解如何将文档与本节](../../campaign/using/marketing-campaign-assets.md)中的活动[链接。

>[!IMPORTANT]
>
>此模式保留给小文档。

在活动中，您还可以参考其他项目，例如促销优惠券、与特定分店或商店相关的特殊优惠等。 当这些元素包含在大纲中时，它们可以与直邮投放关联。 [了解详情](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用MRM，则还可以管理可供多个参与者协作工作的营销资源库。 请参阅[管理营销资源](../../campaign/using/managing-marketing-resources.md)。

### 添加文档{#adding-documents}

文档可以在活动级别(上下文文档)或项目级别(一般文档)关联。

**[!UICONTROL Documents]**&#x200B;选项卡包含：

* 列表内容（模板、图像等）所需的所有文档 由具有适当权限的Adobe Campaign运营商本地下载，
* 文档包含路由器信息（如果有）。

文档通过&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;选项卡链接到项目或活动。

![](assets/s_ncs_user_op_add_document.png)

您还可以通过文档中提供的链接将仪表板添加到活动。

![](assets/add_a_document_in_op.png)

单击&#x200B;**[!UICONTROL Details]**&#x200B;图标以视图文件内容并添加信息：

![](assets/s_ncs_user_op_add_document_details.png)

在仪表板中，与活动关联的文档在&#x200B;**[!UICONTROL Document(s)]**&#x200B;部分进行分组，如下例所示：

![](assets/s_ncs_user_op_edit_document.png)

也可以通过此视图编辑和修改它们。

### 通过投放概要{#associating-and-structuring-resources-linked-via-a-delivery-outline}关联和构造链接的资源

>[!NOTE]
>
>投放概要仅用于直接邮件活动的上下文。

投放概要表示一组结构化元素(文档、分支/商店、优惠券等) 创建的公司。

这些元素按投放概要分组，特定投放概要将与投放关联；它将在发送到&#x200B;**服务提供商**&#x200B;的提取文件中引用，以便附加到投放。 例如，您可以创建引用分支及其使用的营销小册子的投放概要。

对于活动,投放概要允许您根据特定条件构造要与投放关联的外部元素：相关分支、授予的促销优惠、向当地事件发出的邀请等。

#### 创建大纲{#creating-an-outline}

要创建大纲，请单击相关活动&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子选项卡。

>[!NOTE]
>
>如果此选项卡不存在，则此功能对此活动不可用。 请参阅活动模板配置。
>   
>有关详细信息，请参阅[活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

![](assets/s_ncs_user_op_composition_link.png)

接下来，单击&#x200B;**[!UICONTROL Add a delivery outline]**&#x200B;并创建活动的轮廓层次：

1. 右键单击树的根，然后选择&#x200B;**[!UICONTROL New > Delivery outlines]**。
1. 右键单击刚刚创建的大纲，然后选择&#x200B;**[!UICONTROL New > Item]**&#x200B;或&#x200B;**[!UICONTROL New > Personalization fields]**。

![](assets/s_ncs_user_op_add_composition.png)

大纲可以包含项目和个性化字段、资源和优惠:

* 项目可以是物理文档，例如，此处引用和描述的项目将附加到投放。
* 个性化字段使您能够创建与投放相关的个性化元素，而不是收件人。 因此，可以创建要在特定目标(欢迎优惠、折扣等)的投放中使用的值。 它们以Adobe Campaign创建，并通过&#x200B;**[!UICONTROL Import personalization fields...]**&#x200B;链接导入到大纲中。

   ![](assets/s_ncs_user_op_add_composition_field.png)

   也可以通过单击列表区域右侧的&#x200B;**[!UICONTROL Add]**&#x200B;图标直接在大纲中创建它们。

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 资源是在通过&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Resources]**&#x200B;链接访问的营销资源仪表板中生成的营销资源。

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >有关营销资源的详细信息，请参阅[管理营销资源](../../campaign/using/managing-marketing-resources.md)。

#### 选择大纲{#selecting-an-outline}

对于每个投放，您可以从为提取大纲保留的部分中选择要关联的大纲，如下例所示：

![](assets/s_ncs_user_op_select_composition.png)

选定的轮廓随后将显示在窗口的下部。 可以使用字段右侧的图标进行编辑或使用下拉式列表更改：

![](assets/s_ncs_user_op_select_composition_b.png)

投放的&#x200B;**[!UICONTROL Summary]**&#x200B;选项卡还显示以下信息：

![](assets/s_ncs_user_op_select_composition_c.png)

#### 提取结果{#extraction-result}

在提取并发送到服务提供商的文件中，大纲的名称，并在适当时，其特征（费用、描述等） 将根据与服务提供商关联的导出模板中的信息添加到内容。

在以下示例中，将与投放关联的大纲的标签、估计成本和说明将添加到提取文件。

![](assets/s_ncs_user_op_composition_in_export_template.png)

导出模型必须与为相关服务提供商选择的投放关联。 请参阅[创建服务提供商及其成本结构](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有关导出的详细信息，请参阅[入门](../../platform/using/get-started-data-import-export.md)部分。

#### 教程视频{#create-email-video}

此视频介绍如何在Adobe Campaign中创建活动和电子邮件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

其他活动操作视频[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)可用。