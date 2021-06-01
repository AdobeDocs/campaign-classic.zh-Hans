---
product: campaign
title: Web 窗体入门
description: Campaign中的Web窗体入门
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 63602bed-ace6-4632-a735-5d268a7d72d0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 5%

---

# Web 窗体入门{#about-web-forms}

Adobe Campaign集成了一个图形模块，用于定义和发布Web窗体以创建包含输入和选择字段的页面，这些页面可能包含数据库中的数据。 这样，您就可以设计和发布网页，以供用户访问以查看或输入信息。

本章详细介绍Web窗体的创建和管理、如何管理字段和页面以及存储和保存模式。

>[!CAUTION]
>
>出于隐私原因，我们建议对所有外部资源使用HTTPS。

## 创建Web窗体{#steps-for-creating-a-web-form}的步骤

本章详细介绍在Adobe Campaign中设计&#x200B;**webForm**&#x200B;类型表单所需的步骤，以及可用的选项和配置。 Adobe Campaign允许您将此Web窗体提供给用户，以及在数据库中收集和存档答案。

>[!CAUTION]
>
>配置Web应用程序和Web窗体时，您需要最小900像素的垂直分辨率(例如：1600x900)。

可通过&#x200B;**Campaigns**&#x200B;选项卡的“Web应用程序”菜单访问Web窗体。 在Adobe Campaign树中，它们被分组到&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;节点下。

要创建Web窗体，请单击Web应用程序列表上方的&#x200B;**[!UICONTROL Create]**&#x200B;按钮。

![](assets/webapp_create_new.png)

选择Web窗体模板（默认为&#x200B;**[!UICONTROL newWebForm]**）。

![](assets/s_ncs_admin_survey_select_template.png)

这会将您转到表单的仪表板。

![](assets/webapp_empty_dashboard.png)

使用&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡可创建内容。

![](assets/webapp_edit_tab.png)

要定义Web窗体的配置和内容，请应用以下步骤：

* 首先，创建所需的页面和控件：输入字段、下拉列表、HTML内容等。

   下面详细介绍了此步骤。

* 定义页面排序和显示条件。

   [定义Web窗体页面排序](../../web/using/defining-web-forms-page-sequencing.md)中详细介绍了此步骤。

* 如有必要，翻译内容。

   [翻译Web窗体](../../web/using/translating-a-web-form.md)中详细介绍了此步骤。

## 关于Web窗体设计{#about-web-forms-designing}

表单的页面通过特定编辑器创建，通过该编辑器可定义和配置输入区域（文本）、选择字段（列表、复选框等） 和静态元素（图像、HTLM内容等）。 可以将它们分组到容器中，并根据您的需要更改其布局（有关更多信息，请参阅[创建容器](../../web/using/defining-web-forms-layout.md#creating-containers)）。

以下部分详细说明了如何为表单屏幕定义内容和布局：

* [向 Web 窗体添加字段](../../web/using/adding-fields-to-a-web-form.md),
* [插入HTML内容](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)、
* [Web 窗体中的静态元素](../../web/using/static-elements-in-a-web-form.md),
* [定义 Web 窗体布局](../../web/using/defining-web-forms-layout.md).

>[!NOTE]
>
>* 在页面设计过程中，您可以在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中查看最终渲染。 要查看更改，请先保存表单。 所有错误都显示在&#x200B;**[!UICONTROL Log]**&#x200B;选项卡中。
>* 要确保页面按适当的顺序显示和信息存储，请在Web窗体中启用调试模式。 为此，请转到&#x200B;**[!UICONTROL Preview]**&#x200B;子选项卡并选中&#x200B;**[!UICONTROL Enable debug mode]**&#x200B;框：所有收集的信息和可能的执行错误都将显示在每个页面的底部。

>



### 使用工具栏{#using-the-icons-in-the-toolbar}中的图标

您还可以使用工具栏中的图标或右键单击以插入输入区域。

![](assets/s_ncs_admin_webform_add_selection.png)

在这种情况下，首先选择要添加的字段类型和答案存储模式。

![](assets/s_ncs_admin_webform_select_storage.png)

单击&#x200B;**[!UICONTROL Ok]**&#x200B;以批准选择。

![](assets/s_ncs_admin_webform_confirm_storage.png)
