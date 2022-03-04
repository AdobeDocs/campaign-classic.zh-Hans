---
product: campaign
title: 使用内容模板
description: 使用内容模板
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# 使用内容模板{#using-a-content-template}

![](../../assets/common.svg)

## 关于内容模板 {#about-content-templates}

内容模板可直接在投放中引用和使用。 请参阅 [通过内容管理创建投放](#creating-a-delivery-via-content-management)

它们还可用于创建内容实例。 创建实例后，这些实例即可交付(请参阅 [交付内容实例](#delivering-a-content-instance))或导出(请参阅 [创建内容实例](#creating-a-content-instance))。

## 通过内容管理创建投放 {#creating-a-delivery-via-content-management}

在使用输入字段输入内容的视图中，可以引用投放中的内容模板。 投放向导中添加了用于定义投放内容的其他选项卡。

![](assets/s_ncs_content_deliver_a_content.png)

将根据选定的设置自动应用布局。 要查看该动态消息，请单击 **[!UICONTROL HTML preview]** (或 **[!UICONTROL Text preview]** )并选择一个收件人以测试个性化元素。

![](assets/s_ncs_content_deliver_a_content_html.png)

有关更多信息，请参阅完整的实施示例： [在投放向导中创建内容](use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## 创建内容实例 {#creating-a-content-instance}

您可以直接在Adobe Campaign树中创建内容，以用于工作流、导出内容或直接插入到新投放中。

应用以下步骤：

1. 选择 **[!UICONTROL Resources > Contents]** 树的节点，右键单击并选择 **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. 选择将对此文件夹处于活动状态的发布模板。

   ![](assets/s_ncs_content_folder_templates.png)

1. 您现在可以使用 **[!UICONTROL New]** 按钮。

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. 在表单中输入字段。

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. 然后，单击 **[!UICONTROL HTML preview]** 选项卡查看渲染。 在此，未输入从数据库获取的个性化字段。

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. 创建内容后，该内容会添加到可用内容列表中。 单击 **[!UICONTROL Properties]** 链接可更改其标签、状态或查看其历史记录。

   ![](assets/s_ncs_content_folder_template_properties.png)

1. 如有必要，内容获得批准后，即可使用工具栏上的相应按钮生成。

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >您可以授权生成未批准的内容。 为此，请更改发布模板中的相关选项。 有关更多信息，请参阅 [创建和配置模板](publication-templates.md#creating-and-configuring-the-template).

   默认情况下，HTML和文本内容会在 **发布** Adobe Campaign实例的文件夹。 由于 **NcmPublishingDir** 选项。

## 交付内容实例 {#delivering-a-content-instance}

要创建并交付内容实例，投放模板需要链接到用于生成此内容的发布模板。 有关更多信息，请参阅 [投放](publication-templates.md#delivery).

此外，内容存储文件夹必须专门用于从此发布模板获取的内容（当内容文件夹允许您生成多种类型的内容时，无法自动创建投放）。

要根据所选内容自动创建投放，请单击 **[!UICONTROL Delivery]** 图标，然后选择模板。

![](assets/s_ncs_content_folder_create_the_delivery.png)

文本和HTML内容会自动输入。
