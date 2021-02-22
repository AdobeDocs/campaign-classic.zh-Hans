---
solution: Campaign Classic
product: campaign
title: Web 窗体入门
description: 开始使用活动中的Web表单
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 5%

---


# Web 窗体入门{#about-web-forms}

Adobe Campaign集成了用于定义和发布Web 窗体的图形模块，以创建包含输入和选择字段的页面，并且该页面可能包括数据库中的数据。 这样，您就可以设计和发布网页，供用户访问视图或输入信息。

本章详细介绍了Web 窗体的创建和管理、如何管理字段和页面以及存储和保存模式。

>[!CAUTION]
>
>出于隐私考虑，我们建议对所有外部资源使用HTTPS。

## 创建Web表单的步骤{#steps-for-creating-a-web-form}

本章详细介绍了在Adobe Campaign中设计&#x200B;**webForm**&#x200B;类型表单所需的步骤，以及可用的选项和配置。 Adobe Campaign允许您使此Web表单可供用户使用，并在数据库中收集和存档答案。

>[!CAUTION]
>
>配置Web应用程序和Web表单时，您需要最低900像素的垂直分辨率(例如：1600x900)。

Web 窗体可通过&#x200B;**“活动”**&#x200B;选项卡的“Web 应用程序”菜单访问。 在Adobe Campaign树中，它们被分组在&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;节点下。

要创建Web表单，请单击Web 应用程序列表上方的&#x200B;**[!UICONTROL Create]**&#x200B;按钮。

![](assets/webapp_create_new.png)

选择Web表单模板（默认为&#x200B;**[!UICONTROL newWebForm]**）。

![](assets/s_ncs_admin_survey_select_template.png)

这将带您进入表单的仪表板。

![](assets/webapp_empty_dashboard.png)

使用&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡可以创建内容。

![](assets/webapp_edit_tab.png)

要定义Web表单的配置和内容，请应用以下步骤：

* 开始:输入字段、下拉列表、HTML内容等。

   此步骤详述如下。

* 定义页面顺序和显示条件。

   此步骤详见[定义Web表单页面排序](../../web/using/defining-web-forms-page-sequencing.md)。

* 如有必要，翻译内容。

   此步骤详见[翻译Web表单](../../web/using/translating-a-web-form.md)。

## 关于设计的Web表单{#about-web-forms-designing}

表单的页面是通过特定编辑器创建的，通过该编辑器可以定义和配置输入区域（文本）、选择字段(列表、复选框等) 和静态元素（图像、HTML内容等）。 它们可以分组为容器，并且布局会根据您的需要而进行更改(有关详细信息，请参阅[创建容器](../../web/using/defining-web-forms-layout.md#creating-containers))。

以下部分详细介绍了如何定义表单屏幕的内容和布局：

* [向 Web 窗体添加字段](../../web/using/adding-fields-to-a-web-form.md),
* [插入HTML内容](../../web/using/static-elements-in-a-web-form.md#inserting-html-content),
* [Web 窗体中的静态元素](../../web/using/static-elements-in-a-web-form.md),
* [定义 Web 窗体布局](../../web/using/defining-web-forms-layout.md).

>[!NOTE]
>
>* 在页面设计过程中，您可以在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中视图最终呈现。 要视图更改，请先保存表单。 所有错误都显示在&#x200B;**[!UICONTROL Log]**&#x200B;选项卡中。
>* 要确保页面显示和信息存储以适当的顺序发生，请在Web表单中启用调试模式。 要执行此操作，请转到&#x200B;**[!UICONTROL Preview]**&#x200B;子选项卡并选中&#x200B;**[!UICONTROL Enable debug mode]**&#x200B;框：所有收集的信息和可能的执行错误将显示在每个页面的底部。
>



### 使用工具栏中的图标{#using-the-icons-in-the-toolbar}

您还可以使用工具栏中的图标或右键单击以插入输入区域。

![](assets/s_ncs_admin_webform_add_selection.png)

在这种情况下，通过选择要添加的字段类型和答案开始模式进行存储。

![](assets/s_ncs_admin_webform_select_storage.png)

单击&#x200B;**[!UICONTROL Ok]**&#x200B;批准选择。

![](assets/s_ncs_admin_webform_confirm_storage.png)

