---
product: campaign
title: 营销活动文档和投放概要
description: 了解有关营销活动文档和投放概要的更多信息
role: User
feature: Campaigns
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# 管理关联文档 {#managing-associated-documents}

您可以将各种文档与营销活动关联：报表、照片、网页、图表等。 这些文档可以是任何格式(Microsoft Word、PowerPoint、PNG、JPG、AcrobatPDF等)。

>[!IMPORTANT]
>
>此功能专为小型资产和文档保留。

在营销策划中，您还可以参考其他项目，如促销优惠券、与特定品牌或商店相关的特殊优惠等。 当这些元素包含在大纲中时，它们可以与直邮投放相关联。 请参阅 [关联并构建通过投放概要链接的资源](#associating-and-structuring-resources-linked-via-a-delivery-outline).

>[!NOTE]
>
>如果您使用Campaign营销资源管理模块，则还可以管理营销资源库，该库可供多个用户协作使用。 [了解详情](../../mrm/using/managing-marketing-resources.md)。

## 添加文档 {#adding-documents}

文档可以在营销活动级别（上下文文档）或项目群级别（常规文档）关联。

此 **[!UICONTROL Documents]** 选项卡包含：

* 内容所需的所有文档（模板、图像等）的列表 Adobe Campaign操作员通过适当权限可本地下载的广告文件、
* 包含路由器信息的文档（如果有）。

这些文档通过以下方式链接到项目或营销策划 **[!UICONTROL Edit > Documents]** 选项卡。

![](assets/s_ncs_user_op_add_document.png)

您还可以通过信息板中提供的链接将文档添加到营销活动。

![](assets/add_a_document_in_op.png)

单击 **[!UICONTROL Details]** 图标以查看文件内容和添加信息：

![](assets/s_ncs_user_op_add_document_details.png)

在功能板中，与活动关联的文档将分组到 **[!UICONTROL Document(s)]** 部分，如以下示例所示：

![](assets/s_ncs_user_op_edit_document.png)

也可以从此视图编辑和修改它们。

## 关联并构建通过投放概要链接的资源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>投放大纲仅用于直邮营销活动的上下文。

投放概要表示一组结构化元素（文档、商店、促销优惠券等） 由公司创建，并用于特定营销活动。

这些元素在投放概要中进行分组，每个投放概要都将与一个投放关联；将在发送到的提取文件中引用该投放概要。 **服务提供商** 以附加到投放。 例如，您可以创建一个投放概要，其中引用分支及其使用的营销小册子。

对于营销活动，利用投放概要，可根据特定条件构建要与投放关联的外部元素：相关分支、授予的促销优惠、本地活动邀请等。

### 创建大纲 {#creating-an-outline}

要创建大纲，请单击 **[!UICONTROL Delivery outlines]** 中的子选项卡 **[!UICONTROL Edit > Documents]** 相关营销活动的选项卡。

>[!NOTE]
>
>如果此选项卡不存在，则此功能不适用于此营销活动。 请参阅活动模板配置。
>   
>有关模板的更多信息，请参阅 [本节](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

接下来，单击 **[!UICONTROL Add a delivery outline]** 并为营销活动创建大纲的层次结构：

1. 右键单击树的根并选择 **[!UICONTROL New > Delivery outlines]**.
1. 右键单击刚刚创建的大纲，然后选择 **[!UICONTROL New > Item]** 或 **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

大纲可包含项目和个性化字段、资源和选件：

* 项目可以是物理文档，例如，此处引用和描述的文档，将附加到投放。
* 通过个性化字段，您可以创建与投放而不是收件人相关的个性化元素。 因此，可以创建值以用于特定目标的投放（欢迎优惠、折扣等） 它们在Adobe Campaign中创建，并通过导入大纲 **[!UICONTROL Import personalization fields...]** 链接。

  ![](assets/s_ncs_user_op_add_composition_field.png)

  也可以通过单击 **[!UICONTROL Add]** 图标（位于列表区域的右侧）。

  ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 资源是在营销资源仪表板中生成的营销资源，可通过访问 **[!UICONTROL Resources]** 链接 **[!UICONTROL Campaigns]** 选项卡。

  ![](assets/s_ncs_user_mkg_resource_ovv.png)

  >[!NOTE]
  >
  >有关营销资源的更多信息，请参阅 [本节](../../mrm/using/managing-marketing-resources.md).

### 选择大纲 {#selecting-an-outline}

对于每次投放，您可以从为提取大纲保留的节中选择要关联的大纲，如以下示例所示：

![](assets/s_ncs_user_op_select_composition.png)

然后，所选轮廓将显示在窗口的下部。 可使用字段右侧的图标编辑或使用下拉列表更改它：

![](assets/s_ncs_user_op_select_composition_b.png)

此 **[!UICONTROL Summary]** 投放的选项卡还会显示以下信息：

![](assets/s_ncs_user_op_select_composition_c.png)

### 提取结果 {#extraction-result}

在提取并发送到服务提供商的文件中，大纲的名称以及适当时其特征（成本、描述等） 根据与服务提供商关联的导出模板中的信息添加到内容。

在以下示例中，与投放关联的大纲的标签、预计成本和描述将添加到提取文件中。

![](assets/s_ncs_user_op_composition_in_export_template.png)

导出模型必须与为相关投放选择的服务提供商关联。 请参阅 [本节](../../campaign/using/providers-stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>有关导出的详细信息，请参阅 [本节](../../platform/using/get-started-data-import-export.md) 部分。
