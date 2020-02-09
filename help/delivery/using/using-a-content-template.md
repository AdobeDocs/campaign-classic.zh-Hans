---
title: 使用内容模板
seo-title: 使用内容模板
description: 使用内容模板
seo-description: null
page-status-flag: never-activated
uuid: 893b9711-593f-4865-b61a-ef0fede9a2b0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 48f491b7-bf7b-457f-9cf2-db2bbf4eceea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 使用内容模板{#using-a-content-template}

## 关于内容模板 {#about-content-templates}

内容模板可以直接在分发中引用和使用。 请参阅通 [过内容管理创建分发](#creating-a-delivery-via-content-management)

它们还可用于创建内容实例。 创建这些实例后，即可交付(请参阅 [Delivering a content instance](#delivering-a-content-instance))或导出(请参阅 [Creating a content instance](#creating-a-content-instance))。

## 通过内容管理创建交付 {#creating-a-delivery-via-content-management}

在使用输入字段输入内容的视图中，您可以引用分发中的内容模板。 此时会向传送向导添加一个额外的选项卡，用于定义传送内容。

![](assets/s_ncs_content_deliver_a_content.png)

布局将根据所选设置自动应用。 要查看个性化元素，请单 **[!UICONTROL HTML preview]** 击(或 **[!UICONTROL Text preview]** )并选择收件人以测试个性化元素。

![](assets/s_ncs_content_deliver_a_content_html.png)

有关此功能的详细信息，请参阅完整的实施示例：在 [分发向导中创建内容](../../delivery/using/use-case--creating-content-management.md#creating-content-in-the-delivery-wizard)。

## 创建内容实例 {#creating-a-content-instance}

您可以直接在Adobe Campaign树中创建内容，以便用于工作流、导出或直接插入新分发。

应用以下步骤：

1. 选择 **[!UICONTROL Resources > Contents]** 树的节点，右键单击并选择 **[!UICONTROL Properties]**。

   ![](assets/s_ncs_content_folder_properties.png)

1. 选择将对此文件夹处于活动状态的发布模板。

   ![](assets/s_ncs_content_folder_templates.png)

1. 您现在可以使用内容列表上 **[!UICONTROL New]** 方的按钮创建新内容。

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. 在表单中输入字段。

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. 然后，单击 **[!UICONTROL HTML preview]** 选项卡以查看渲染。 此处，不输入从数据库获取的个性化字段。

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. 创建内容后，内容即添加到可用内容列表。 单击链 **[!UICONTROL Properties]** 接以更改其标签、状态或查看其历史记录。

   ![](assets/s_ncs_content_folder_template_properties.png)

1. 如有必要，内容获得批准后，可以使用工具栏中的相应按钮生成。

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >您可以授权生成未批准的内容。 为此，请更改发布模板中的相关选项。 有关详细信息，请参阅 [创建和配置模板](../../delivery/using/publication-templates.md#creating-and-configuring-the-template)。

   默认情况下，HTML和文本内容会在Adobe Campaign实例的 **publishing** 文件夹中生成。 借助NcmPublishingDir选项，您可以更改发 **布文件夹** 。

## 交付内容实例 {#delivering-a-content-instance}

要创建内容实例并交付它，需要将分发模板链接到用于生成此内容的发布模板。 For more on this, refer to [Delivery](../../delivery/using/publication-templates.md#delivery).

此外，内容存储文件夹必须专门用于从此发布模板获取的内容（当内容文件夹允许您生成多种类型的内容时，无法自动创建分发）。

要根据所选内容自动创建分发，请单击图 **[!UICONTROL Delivery]** 标并选择模板。

![](assets/s_ncs_content_folder_create_the_delivery.png)

文本和HTML内容将自动输入。
