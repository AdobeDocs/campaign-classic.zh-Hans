---
title: 构建调查
seo-title: 构建调查
description: 构建调查
seo-description: null
page-status-flag: never-activated
uuid: 50d501b9-2b4f-48d1-b394-f7f71c413990
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 6850851d-1dbe-44f0-bbff-18dbac2cad9a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 构建调查{#building-a-survey}

## 创建新调查 {#creating-a-new-survey}

本章详细介绍了使用Adobe **Campaign设计** Survey类型表单以及可用的选项和配置。 Adobe Campaign允许您向用户提供此调查，并在数据库中收集和存档答案。

通过树的节点访 **[!UICONTROL Resources > Online > Web applications]** 问Web表单。 要创建调查，请单击 **[!UICONTROL New]** 应用程序列表上方的按钮，或右键单击列表并选择 **[!UICONTROL New]**。

选择调查模板(**[!UICONTROL newSurvey]** 默认)。

![](assets/s_ncs_admin_survey_select_template.png)

表单的页面是使用特殊编辑器创建的，它允许您定义和配置（文本）输入字段、选择字段（列表、复选框等）和静态元素（图像、HTML内容等）。 可以在“容器”中收集它们，并根据要求进行布置(请参 [阅添加问题](#adding-questions))。

>[!NOTE]
>
>有关如何定义内容和创建Web表单的屏幕布局的详细信息，请参阅 [此部分](../../web/using/about-web-forms.md)。

## 添加字段 {#adding-fields}

表单中的字段使用户能够输入信息并选择选项。 对于表单中的每个页面，它们是使用菜单通过工具栏中的第一个按钮创建 **[!UICONTROL Add using the wizard]** 的。

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>您还可以使用右键单击并插入输入区域。 默认情况下，区域会插入到所选树的末尾。 使用工具栏中的箭头移动它。

### 字段类型 {#types-of-fields}

向调查添加字段时，您需要选择其类型。 可以使用以下选项：

1. **[!UICONTROL Answer a question]**:此选项允许您声明新字段（称为“存档字段”）以存储答案。 在这种情况下，即使参加者多次填写表单，也会保存收集的所有值。 此存储模式仅在调查中 **可用**。 请参阅存 [储收集的答案](../../web/using/managing-answers.md#storing-collected-answers)。
1. **[!UICONTROL Edit a recipient]**:此选项允许您选择数据库中的字段。 在这种情况下，用户答案将存储在此字段中。 对于每个参加者，只保留保存的最后一个值，并将其添加到配置文件数据。
1. **[!UICONTROL Add a variable]**:此选项允许您创建设置，以便信息不存储在数据库中。 局部变量可声明为上游。 您还可以在创建字段时直接添加这些字段。
1. **[!UICONTROL Import an existing question]**:此选项允许您导入在其他调查中创建的现有问题。

   >[!NOTE]
   >
   >存储收集的答案中详细介绍了存储模 [式和字段导入](../../web/using/managing-answers.md#storing-collected-answers)。

要添加的字段的性质（下拉列表、文本字段、复选框等）调整为选定的存储模式。 您可以使用选项卡的字 **[!UICONTROL Type]** 段来更改它， **[!UICONTROL General]** 但是请确保与数据类型保持一致。

![](assets/s_ncs_admin_survey_change_type.png)

本节详细介绍了各种类型的可 [用字段](../../web/using/about-web-forms.md)。

## 特定于调查的元素 {#survey-specific-elements}

在线调查使用Web应用程序功能。 与调查字段链接的特定功能在下面详细介绍。

### 多选 {#multiple-choice}

对于 **[!UICONTROL Multiple choice]** 类型控件，您可以定义最小和最大选择数。 例如，此选项允许您从可用选项强制选择至 **少2** 个值，最 **多4个值** :

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

如果选择的数量过大或过小，则显示相应的消息。

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>在这种情况下，选项会使用复选框进行选择。 如果只能使用一个选项，则使用单选按钮。

相应的配置如下：

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

此外，此输入字段的存储位置必须是类型存档 **[!UICONTROL Multiple values]** 的字 **段**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* 此功能仅对 **Survey类型表单可用** 。
>* 此选项与随机问题显示不兼容。 For more on this, refer to [Adding questions](#adding-questions).


### 添加问题 {#adding-questions}

容器有两种类型：标准和问题。 标准容器用于配置页面布局和页面中的条件显示。 本节详细介绍 [了这些内容](../../web/using/about-web-forms.md)。

使用“ **问题** ”容器向页面添加问题，并在层次结构中插入可能的答案。 可以在报告中分析用户对放入此类容器中的问题的答复。

>[!CAUTION]
>
>切勿在层次 **结构中** ，将Question容 **器插入其** 他Question容器下。

![](assets/s_ncs_admin_question_label.png)

问题的标签在标签字段中输入。 在这种情况下，将应用表单样式表中的样式。 选择选 **[!UICONTROL Enter the title in HTML format]** 项以对其进行个性化。 这将允许您访问HTML编辑器。

>[!NOTE]
>
>有关使 [用HTML编辑器](../../web/using/about-web-forms.md) ，请参阅本节。

例如：

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

在上面的示例中，渲染将如下所示：

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>每个问题都有一个 **问题类** 型容器。

您可以启用Adobe Campaign随机绘制问题。 然后，可以在配置窗口底部的字段中指定要在页面中显示的问题数。

![](assets/s_ncs_admin_survey_containers_qu_display.png)

渲染将如下：

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

刷新页面时，显示的问题不相同。

>[!CAUTION]
>
>当随机显示问题(在页&#x200B;**[!UICONTROL Display randomly]** 面上选中的选项)时，请注意不要使用多个选择问题，对于这些问题，必须选择一个或多个。

