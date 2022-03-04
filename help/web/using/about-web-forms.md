---
product: campaign
title: Web 窗体入门
description: Campaign中的Web窗体入门
feature: Landing Pages, Web Forms
exl-id: 63602bed-ace6-4632-a735-5d268a7d72d0
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 5%

---

# Web 窗体入门{#about-web-forms}

![](../../assets/common.svg)

Adobe Campaign集成了一个图形模块，用于定义和发布Web窗体以创建包含输入和选择字段的页面，这些页面可能包含数据库中的数据。 这样，您就可以设计和发布网页，以供用户访问以查看或输入信息。

本章详细介绍Web窗体的创建和管理、如何管理字段和页面以及存储和保存模式。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## 创建Web窗体的步骤 {#steps-for-creating-a-web-form}

本章详细介绍设计 **webForm** 在Adobe Campaign中键入表单，以及可用的选项和配置。 Adobe Campaign允许您将此Web窗体提供给用户，以及在数据库中收集和存档答案。

>[!CAUTION]
>
>配置Web应用程序和Web窗体时，您需要最小900像素的垂直分辨率(例如：1600x900)。

Web窗体可通过 **促销活动** 选项卡。 在Adobe Campaign树中，它们被分组到 **[!UICONTROL Resources > Online > Web Applications]** 节点。

要创建Web窗体，请单击 **[!UICONTROL Create]** 按钮。

![](assets/webapp_create_new.png)

选择Web窗体模板( **[!UICONTROL newWebForm]** )。

![](assets/s_ncs_admin_survey_select_template.png)

这会将您转到表单的仪表板。

![](assets/webapp_empty_dashboard.png)

的 **[!UICONTROL Edit]** 选项卡，您可以创建内容。

![](assets/webapp_edit_tab.png)

要定义Web窗体的配置和内容，请应用以下步骤：

* 首先，创建所需的页面和控件：输入字段、下拉列表、HTML内容等。

   下面详细介绍了此步骤。

* 定义页面排序和显示条件。

   有关此步骤的详细信息，请参阅 [定义Web窗体页面排序](defining-web-forms-page-sequencing.md).

* 如有必要，翻译内容。

   有关此步骤的详细信息，请参阅 [翻译Web窗体](translating-a-web-form.md).

## 关于Web窗体设计 {#about-web-forms-designing}

表单的页面通过特定编辑器创建，通过该编辑器可定义和配置输入区域（文本）、选择字段（列表、复选框等） 和静态元素（图像、HTLM内容等）。 可以将它们分组到容器中，并根据您的需要更改其布局(有关更多信息，请参阅 [创建容器](defining-web-forms-layout.md#creating-containers))。

以下部分详细说明了如何为表单屏幕定义内容和布局：

* [向 Web 窗体添加字段](adding-fields-to-a-web-form.md),
* [插入HTML内容](static-elements-in-a-web-form.md#inserting-html-content),
* [Web 窗体中的静态元素](static-elements-in-a-web-form.md),
* [定义 Web 窗体布局](defining-web-forms-layout.md).

>[!NOTE]
>
>* 在页面设计期间，您可以在 **[!UICONTROL Preview]** 选项卡。 要查看更改，请先保存表单。 任何错误都显示在 **[!UICONTROL Log]** 选项卡。
>* 要确保页面按适当的顺序显示和信息存储，请在Web窗体中启用调试模式。 要执行此操作，请转到 **[!UICONTROL Preview]** 子选项卡，并检查 **[!UICONTROL Enable debug mode]** 框：所有收集的信息和可能的执行错误都将显示在每个页面的底部。
>


### 使用工具栏中的图标 {#using-the-icons-in-the-toolbar}

您还可以使用工具栏中的图标或右键单击以插入输入区域。

![](assets/s_ncs_admin_webform_add_selection.png)

在这种情况下，首先选择要添加的字段类型和答案存储模式。

![](assets/s_ncs_admin_webform_select_storage.png)

单击 **[!UICONTROL Ok]** 以批准选择。

![](assets/s_ncs_admin_webform_confirm_storage.png)
