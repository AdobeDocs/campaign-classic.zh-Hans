---
product: campaign
title: 设计调查
description: 了解设计调查的关键步骤
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 8d83dfd5-70ec-4656-965b-f6b5e6f9eec1
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 2%

---

# 设计调查{#building-a-survey}

![](../../assets/v7-only.svg)

## 创建新调查 {#creating-a-new-survey}

本章详细介绍使用Adobe Campaign设计&#x200B;**Survey**&#x200B;类型表单，以及可用选项和配置。 Adobe Campaign允许您将此调查提供给用户，并在数据库中收集和存档答案。

可通过树的&#x200B;**[!UICONTROL Resources > Online > Web applications]**&#x200B;节点访问Web窗体。 要创建调查，请单击应用程序列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮，或右键单击列表并选择&#x200B;**[!UICONTROL New]**。

选择调查模板（默认情况下为&#x200B;**[!UICONTROL newSurvey]**）。

![](assets/s_ncs_admin_survey_select_template.png)

表单的页面使用特殊编辑器创建，通过该编辑器可定义和配置（文本）输入字段、选择字段（列表、复选框等） 和静态元素（图像、HTML内容等）。 可以在“容器”中收集并根据要求进行布局。 [了解详情](#adding-questions)).

>[!NOTE]
>
>有关如何定义Web窗体内容和创建屏幕布局的更多信息，请参阅[本文档](../../web/using/about-web-forms.md)。

## 添加字段 {#adding-fields}

表单中的字段允许用户输入信息并选择选项。 对于表单中的每个页面，它们是通过工具栏中的第一个按钮使用&#x200B;**[!UICONTROL Add using the wizard]**&#x200B;菜单创建的。

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>您还可以使用右键单击并插入输入区域。 默认情况下，区域会插入到所选树的末尾。 使用工具栏中的箭头移动它。

### 字段类型 {#types-of-fields}

向调查添加字段时，您需要选择其类型。 可以使用以下选项：

1. **[!UICONTROL Answer a question]**:此选项允许您声明一个新字段（称为“已存档字段”）以存储答案。在这种情况下，会保存收集的所有值，即使参与者多次填写表单也是如此。 此存储模式仅在&#x200B;**调查**&#x200B;中可用。 [了解详情](../../surveys/using/managing-answers.md#storing-collected-answers)。
1. **[!UICONTROL Edit a recipient]**:此选项允许您选择数据库中的字段。在这种情况下，用户答案将存储在此字段中。 对于每个参与者，仅保留保存的最后一个值，并将其添加到用户档案数据中。
1. **[!UICONTROL Add a variable]**:此选项允许您创建设置，以便信息不会存储在数据库中。可以在上游声明局部变量。 您还可以在创建字段时直接添加它们。
1. **[!UICONTROL Import an existing question]**:利用此选项，可导入在其他调查中创建的现有问题。

   >[!NOTE]
   >
   >[此部分](../../surveys/using/managing-answers.md#storing-collected-answers)中详细介绍了存储模式和字段导入。

要添加的字段的性质（下拉列表、文本字段、复选框等） 将调整为所选的存储模式。 您可以使用&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**[!UICONTROL Type]**&#x200B;字段进行更改，但请确保与数据类型保持一致。

![](assets/s_ncs_admin_survey_change_type.png)

[此部分](../../web/using/about-web-forms.md)中详细描述了各种类型的可用字段。

## 特定于调查的元素 {#survey-specific-elements}

在线调查基于Web应用程序功能。 下面详细介绍了特定于调查的功能。

### 多选 {#multiple-choice}

对于&#x200B;**[!UICONTROL Multiple choice]**&#x200B;类型控件，可定义最小和最大选择数。 例如，通过此选项，可以从可用选项强制选择至少&#x200B;**2**&#x200B;值和最多&#x200B;**4**&#x200B;值：

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

如果选择的数量过大或过小，则会显示相应的消息。

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>在这种情况下，使用复选框来选择选项。 如果只能使用一个选项，则使用单选按钮。

相应的配置如下：

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

此外，此输入字段的存储位置必须是&#x200B;**[!UICONTROL Multiple values]**&#x200B;类型&#x200B;**存档字段**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* 此功能仅适用于&#x200B;**Survey**&#x200B;类型表单。
>* 此选项与随机问题显示不兼容。 [了解详情](#adding-questions)。


### 添加问题 {#adding-questions}

容器有两种类型：标准和问题。 标准容器用于配置页面布局和页面中的条件显示。 [了解详情](../../web/using/about-web-forms.md)。

使用&#x200B;**Question**&#x200B;容器向页面添加问题，并在层次结构中插入下面可能的答案。 可以在报表中分析用户对置于此类容器中的问题的响应。

>[!CAUTION]
>
>切勿在层次结构中另一个&#x200B;**问题**&#x200B;容器下插入&#x200B;**问题**&#x200B;容器。

![](assets/s_ncs_admin_question_label.png)

问题的标签在标签字段中输入。 在这种情况下，将应用表单样式表中的样式。 选择&#x200B;**[!UICONTROL Enter the title in HTML format]**&#x200B;选项以对其进行个性化。 这将允许您访问HTML编辑器。

>[!NOTE]
>
>有关使用HTML编辑器的更多信息，请参阅[本文档](../../web/using/about-web-forms.md)。

例如：

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

在以上示例中，呈现将如下所示：

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>每个问题都有一个&#x200B;**Question**&#x200B;类型容器。

您可以启用由Adobe Campaign随机绘制的问题。 然后，可以在配置窗口底部的字段中指定要在页面中显示的问题数。

![](assets/s_ncs_admin_survey_containers_qu_display.png)

呈现将如下所示：

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

刷新页面时，显示的问题不同。

>[!CAUTION]
>
>当随机显示问题（在页面上选中&#x200B;**[!UICONTROL Display randomly]**&#x200B;选项）时，请注意不要使用多个选择问题，对于这些问题，必须选择一个或多个选项。
