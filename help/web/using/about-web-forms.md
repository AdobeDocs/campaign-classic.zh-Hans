---
title: 关于Web表单
seo-title: 关于Web表单
description: 关于Web表单
seo-description: null
page-status-flag: never-activated
uuid: 1d129af4-008b-4f6a-9094-b2edd6c1eee1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 3b8e4691-fcbc-48ef-b529-11c9a9a9d788
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 关于Web表单{#about-web-forms}

Adobe Campaign集成了一个图形模块，用于定义和发布Web表单以创建包含输入和选择字段的页面，这些页面可能包括数据库中的数据。 这样，您就可以设计和发布用户可以访问的网页，以查看或输入信息。

本章详细介绍了Web表单的创建和管理、如何管理字段和页面以及存储和保存模式。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## 创建Web表单的步骤 {#steps-for-creating-a-web-form}

本章详细介绍了在Adobe Campaign中设计 **webForm** type form所需的步骤以及可用的选项和配置。 Adobe Campaign允许您向用户提供此Web表单，并在数据库中收集和存档答案。

>[!CAUTION]
>
>配置Web应用程序和Web表单时，您需要900像素的垂直分辨率最低(例如：1600x900)。

通过“营销活动”选项卡的“Web应用程序”菜单访问Web **表单** 。 在Adobe Campaign树中，它们被分组在节点 **[!UICONTROL Resources > Online > Web Applications]** 下。

要创建Web表单，请单击Web应 **[!UICONTROL Create]** 用程序列表上方的按钮。

![](assets/webapp_create_new.png)

选择Web表单模板(默 **[!UICONTROL newWebForm]** 认情况下)。

![](assets/s_ncs_admin_survey_select_template.png)

此操作将带您进入表单的功能板。

![](assets/webapp_empty_dashboard.png)

通过 **[!UICONTROL Edit]** 选项卡可创建内容。

![](assets/webapp_edit_tab.png)

要定义Web表单的配置和内容，请应用以下步骤：

* 首先，创建所需的页面和检查：输入字段、下拉列表、HTML内容等。

   此步骤详见下文。

* 定义页面排序并为显示条件。

   此步骤在定义Web表 [单页面排序中详细介绍](../../web/using/defining-web-forms-page-sequencing.md)。

* 如有必要，翻译内容。

   翻译Web表单中详 [细介绍了此步骤](../../web/using/translating-a-web-form.md)。

## 关于Web表单设计 {#about-web-forms-designing}

表单的页面是通过特定编辑器创建的，通过该编辑器可以定义和配置输入区域（文本）、选择字段（列表、复选框等）和静态元素（图像、HTML内容等）。 可以将它们分组到容器中，并根据您的需要更改其布局(有关详细信息，请参阅创 [建容器](../../web/using/defining-web-forms-layout.md#creating-containers))。

以下各节详细介绍了如何为表单屏幕定义内容和布局：

* [将字段添加到Web表单](../../web/using/adding-fields-to-a-web-form.md),
* [插入HTML内容](../../web/using/static-elements-in-a-web-form.md#inserting-html-content),
* [Web表单中的静态元素](../../web/using/static-elements-in-a-web-form.md),
* [定义Web表单布局](../../web/using/defining-web-forms-layout.md)。

>[!NOTE]
>
>* 在页面设计过程中，您可以在选项卡中查看最终的渲 **[!UICONTROL Preview]** 染效果。 要查看更改，请先保存表单。 所有错误都显示在选 **[!UICONTROL Log]** 项卡中。
>* 要确保页面显示和信息存储按适当的顺序进行，请在Web表单中启用调试模式。 为此，请转到子选 **[!UICONTROL Preview]** 项卡并选中该 **[!UICONTROL Enable debug mode]** 框：所有收集的信息和可能的执行错误将显示在每个页面的底部。
>



### 使用工具栏中的图标 {#using-the-icons-in-the-toolbar}

您还可以使用工具栏中的图标或右键单击以插入输入区域。

![](assets/s_ncs_admin_webform_add_selection.png)

在这种情况下，首先选择要添加的字段类型和答案存储模式。

![](assets/s_ncs_admin_webform_select_storage.png)

单击 **[!UICONTROL Ok]** 以批准选择。

![](assets/s_ncs_admin_webform_confirm_storage.png)

