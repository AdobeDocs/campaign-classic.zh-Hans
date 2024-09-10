---
product: campaign
title: 使用内容模板
description: 使用内容模板
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 3%

---

# 使用内容模板{#using-a-content-template}



## 关于内容模板 {#about-content-templates}

可以直接在投放中引用和使用内容模板。 请参阅[通过内容管理创建投放](#creating-a-delivery-via-content-management)

它们还可用于创建内容实例。 创建实例后，这些实例就可以交付了（请参阅[交付内容实例](#delivering-a-content-instance)）或导出（请参阅[创建内容实例](#creating-a-content-instance)）。

## 通过内容管理创建投放 {#creating-a-delivery-via-content-management}

考虑到使用输入字段输入内容，您可以在投放中引用内容模板。 向投放助手添加了其他选项卡，用于定义投放内容。

![](assets/s_ncs_content_deliver_a_content.png)

将根据所选设置自动应用布局。 要查看它，请单击&#x200B;**[!UICONTROL HTML preview]** （或&#x200B;**[!UICONTROL Text preview]** ）并选择收件人以测试个性化元素。

![](assets/s_ncs_content_deliver_a_content_html.png)

有关更多信息，请参阅完整的实施示例：[在投放助理中创建内容](use-case-creating-content-management.md#creating-content-in-the-delivery-assistant)。

## 创建内容实例 {#creating-a-content-instance}

您可以直接在Adobe Campaign树中创建内容，以在工作流中使用，或者直接导出或插入新投放中。

应用以下步骤：

1. 选择树的&#x200B;**[!UICONTROL Resources > Contents]**&#x200B;节点，右键单击并选择&#x200B;**[!UICONTROL Properties]**。

   ![](assets/s_ncs_content_folder_properties.png)

1. 选择将在此文件夹中处于活动状态的发布模板。

   ![](assets/s_ncs_content_folder_templates.png)

1. 您现在可以使用内容列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮创建新内容。

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. 在表单中输入字段。

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. 然后单击&#x200B;**[!UICONTROL HTML preview]**&#x200B;选项卡以查看渲染。 此处，不输入从数据库获取的个性化字段。

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. 创建后，该内容即添加到可用内容列表中。 单击&#x200B;**[!UICONTROL Properties]**&#x200B;链接以更改其标签、状态或查看其历史记录。

   ![](assets/s_ncs_content_folder_template_properties.png)

1. 如有必要，在内容获得批准后，可以使用工具栏上的相应按钮生成内容。

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >您可以授权生成未批准的内容。 为此，请更改发布模板中的相关选项。 有关详细信息，请参阅[创建和配置模板](publication-templates.md#creating-and-configuring-the-template)。

   默认情况下，HTML和文本内容在Adobe Campaign实例的&#x200B;**发布**&#x200B;文件夹中生成。 您可以通过&#x200B;**NcmPublishingDir**&#x200B;选项更改发布文件夹。

## 交付内容实例 {#delivering-a-content-instance}

要创建并投放内容实例，投放模板需要链接到用于生成此内容的发布模板。 有关详情，请参阅[投放](publication-templates.md#delivery)。

此外，内容存储文件夹必须专用于从此发布模板中获取的内容（当内容文件夹允许您生成多种类型的内容时，无法自动创建投放）。

要根据所选内容自动创建投放，请单击&#x200B;**[!UICONTROL Delivery]**&#x200B;图标并选择模板。

![](assets/s_ncs_content_folder_create_the_delivery.png)

文本和HTML内容会自动输入。
