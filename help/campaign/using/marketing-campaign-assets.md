---
product: campaign
title: 营销活动文档和投放概述
description: 进一步了解营销活动文档和投放概述
feature: Campaigns
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 1%

---

# 管理关联文档 {#managing-associated-documents}

![](../../assets/v7-only.svg)

您可以将各种文档与营销活动关联：报表、照片、网页、图表等。 这些文档可以采用任何格式(Microsoft Word、PowerPoint、PNG、JPG、AcrobatPDF等)。

>[!IMPORTANT]
>
>此功能专为小资产和文档保留。

在营销活动中，您还可以参考其他项目，例如促销优惠券、与特定品牌或商店相关的特惠等。 当这些元素包含在大纲中时，它们可以与直邮投放相关联。 请参阅 [关联和构建通过投放大纲链接的资源](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>如果您使用Campaign营销资源管理模块，则还可以管理可供多个用户协作工作的营销资源库。 [了解详情](../../mrm/using/managing-marketing-resources.md)。

## 添加文档 {#adding-documents}

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

## 关联和构建通过投放大纲链接的资源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>投放大纲专门用于直邮营销活动的上下文。

投放大纲表示一组结构化元素（文档、商店、促销优惠券等） 由公司创建，用于特定营销活动。

这些元素按投放大纲进行分组，每个投放大纲都将与投放相关联；它将在发送到的提取文件中引用 **服务提供商** 以便附在投放上。 例如，您可以创建一个投放大纲，以引用分支及其使用的营销手册。

对于营销活动，投放大纲允许您根据特定条件构建要与投放关联的外部元素：相关分支、已授予的促销优惠、参加当地活动的邀请等。

### 创建大纲 {#creating-an-outline}

要创建大纲，请单击 **[!UICONTROL Delivery outlines]** 子选项卡 **[!UICONTROL Edit > Documents]** 选项卡。

>[!NOTE]
>
>如果此选项卡不存在，则此功能不适用于此营销活动。 请参阅营销活动模板配置。
>   
>有关模板的更多信息，请参阅 [此部分](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

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
   >有关营销资源的更多信息，请参阅 [此部分](../../mrm/using/managing-marketing-resources.md).

### 选择大纲 {#selecting-an-outline}

对于每个投放，您可以从为提取大纲保留的部分中选择要关联的大纲，如以下示例中所示：

![](assets/s_ncs_user_op_select_composition.png)

选定的轮廓随后显示在窗口的下部。 可以使用字段右侧的图标进行编辑，也可以使用下拉列表进行更改：

![](assets/s_ncs_user_op_select_composition_b.png)

的 **[!UICONTROL Summary]** 的选项卡中，还会显示以下信息：

![](assets/s_ncs_user_op_select_composition_c.png)

### 提取结果 {#extraction-result}

在提取并发送给服务提供商的文件中，大纲的名称，并在适当情况下，其特征（成本、描述等） 根据与服务提供商关联的导出模板中的信息，被添加到内容中。

在以下示例中，将与投放关联的大纲的标签、估计成本和描述将添加到提取文件中。

![](assets/s_ncs_user_op_composition_in_export_template.png)

导出模型必须与为相关投放选择的服务提供商关联。 请参阅[此小节](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有关导出的更多信息，请参阅 [此部分](../../platform/using/get-started-data-import-export.md) 中。
