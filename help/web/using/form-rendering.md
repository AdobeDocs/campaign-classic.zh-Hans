---
solution: Campaign Classic
product: campaign
title: 窗体渲染
description: 窗体渲染
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 2%

---


# 窗体渲染{#form-rendering}

## 选择表单呈现模板{#selecting-the-form-rendering-template}

表单设置允许您选择用于生成页面的模板。 要访问它们，请单击表单详细信息工具栏中的&#x200B;**[!UICONTROL Settings]**&#x200B;按钮，然后选择&#x200B;**[!UICONTROL Rendering]**&#x200B;选项卡。 默认情况下，有许多模板（样式表）可用。

![](assets/s_ncs_admin_survey_rendering_select.png)

编辑器的底部部分允许您视图所选模板的呈现。

缩放功能允许您编辑选定的模板。

![](assets/s_ncs_admin_survey_render_edit.png)

您可以修改或覆盖这些模板。 为此，请单击&#x200B;**[!UICONTROL Page layout...]**&#x200B;链接并个性化信息。

![](assets/s_ncs_admin_survey_render_edit_param.png)

您可以：

* 更改用作徽标的图像并调整其大小，
* 此外，指定当用户选择此渲染模板时访问预览图像的路径。

通过&#x200B;**[!UICONTROL Headers/Footers]**&#x200B;选项卡，您可以使用此模板更改每个表单页面的页眉和页脚中显示的信息。

![](assets/s_ncs_admin_survey_render_edit_header.png)

**[!UICONTROL Page headers]**&#x200B;和&#x200B;**[!UICONTROL Page footers]**&#x200B;部分的每一行对应于HTML页中的一行。 单击&#x200B;**[!UICONTROL Add]**&#x200B;以创建新行。

选择现有行，然后单击&#x200B;**[!UICONTROL Detail]**&#x200B;按钮对其进行个性化设置。

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

您可以通过相关选项卡更改行的内容、添加边框和更改字体属性。 单击&#x200B;**[!UICONTROL OK]**&#x200B;以确认这些更改。

**[!UICONTROL Position]**&#x200B;字段允许您定义元素在页眉和页脚中的位置。

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>渲染模板存储在&#x200B;**[!UICONTROL Administration > Configuration > Form rendering]**&#x200B;节点中。\
>有关详细信息，请参阅[自定义表单渲染](#customizing-form-rendering)

## 自定义表单渲染{#customizing-form-rendering}

### 更改元素{#changing-the-layout-of-elements}的布局

您可以使表单的每个元素（输入字段、图像、单选按钮等）的样式表过载。

为此，请使用&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡。

![](assets/s_ncs_admin_survey_advanced_tab.png)

它允许您定义以下属性：

* **[!UICONTROL Label position]**:请参 [阅定义标签的位置](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Label format]**:换行或无换行，
* **[!UICONTROL Number of cells]** :请参 [阅定位页面上的字段](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** （左、右、居中） **[!UICONTROL Vertical alignment]** 和（高、低、中）,
* **[!UICONTROL Width]** 区域：这可以表示为百分比，也可以表示为em、点或像素（默认值）,
* 最大&#x200B;**[!UICONTROL Length]**:允许的最大字符数（对于“文本”、“编号”和“密码”类型控件）、
* **[!UICONTROL Lines]**:类型区域 **[!UICONTROL Multi-line text]** 的行数，
* **[!UICONTROL Style inline]**:使您能够使用其他设置使CSS样式表过载。这些字符使用&#x200B;**;**&#x200B;字符分隔，如下例所示：

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### 定义页眉和页脚{#defining-headers-and-footers}

在树结构中对字段进行排序，树结构的根名称与页面名称相同。 选择它以修改名称。

窗口的标题必须在表单属性窗口的&#x200B;**[!UICONTROL Page]**&#x200B;选项卡中输入。 您还可以向页眉和页脚添加设置的内容（此信息将显示在每页上）。 此内容在&#x200B;**[!UICONTROL Texts]**&#x200B;选项卡的匹配部分中输入，如下所示：

![](assets/s_ncs_admin_survey_titles_config.png)

### 将元素添加到HTML头{#adding-elements-to-html-header}

您可以输入要插入到表单页面HTML标题中的其他元素。 为此，请在相关页面的&#x200B;**[!UICONTROL Header]**&#x200B;选项卡中输入元素。

这允许您引用将在页面标题栏中显示的图标，例如。

![](assets/webform_header_page_tab.png)

## 定义控件设置{#defining-control-settings}

当用户填写表单时，会根据特定字段的格式或配置自动对其执行检查。 这样，您就可以将某些字段设为必填字段（请参阅[定义必填字段](#defining-mandatory-fields)）或检查所输入数据的格式（请参阅[检查数据格式](#checking-data-format)）。 检查在页面批准过程中执行(通过单击启用输出过渡的链接或按钮)。

### 定义必填字段{#defining-mandatory-fields}

要将某些字段设为必填字段，请在创建字段时选择此选项。

![](assets/s_ncs_admin_survey_required_field.png)

如果用户在未输入字段的情况下批准此页面，将显示以下消息：

![](assets/s_ncs_admin_survey_required_default_msg.png)

单击&#x200B;**[!UICONTROL Personalize this message]**&#x200B;链接可个性化此消息。

![](assets/s_ncs_admin_survey_required_custom_msg.png)

如果用户在未输入字段的情况下批准此页面，将显示以下消息：

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### 正在检查数据格式{#checking-data-format}

对于其值存储在存储库现有字段中的表单检查，将应用数据字段的规则。

对于其值存储在变量中的表单检查，批准规则取决于变量的格式。

例如，如果创建&#x200B;**[!UICONTROL Number]**&#x200B;检查以存储客户端号，如下所示：

![](assets/s_ncs_admin_survey_choose_format.png)

用户必须在表单字段中输入整数。

## 定义字段条件显示{#defining-fields-conditional-display}

您可以根据用户选择的值配置要显示的页面上的字段显示。 这可以应用于一个字段或一组字段(当它们在容器中分组时)。

对于页面的每个元素，**[!UICONTROL Visibility]**&#x200B;部分允许您定义显示条件。

![](assets/s_ncs_admin_survey_condition_edit.png)

条件可能与数据库字段或变量的值有关。

在字段选择窗口中，您可以从以下数据中进行选择：

![](assets/s_ncs_admin_survey_condition_select.png)

* 主树包含表单上下文的参数。 默认参数为标识符(与收件人的加密标识符匹配)、语言和来源。

   有关详细信息，请参见此 [ 页面](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

* **[!UICONTROL Recipients]**&#x200B;子树包含插入到表单中并存储在数据库中的输入字段。

   有关详细信息，请参阅[在数据库中存储数据](../../web/using/web-forms-answers.md#storing-data-in-the-database)。

* **[!UICONTROL Variables]**&#x200B;子树包含此表单的可用变量。 有关详细信息，请参阅[将数据存储在本地变量](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)。

有关此内容的详细信息，请参阅此处提供的用例：[根据所选值显示不同的选项](../../web/using/use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values)。

您还可以使用&#x200B;**[!UICONTROL Test]**&#x200B;对象对表单页面的显示进行条件设置。 有关详细信息，请参见此 [ 页面](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

## 从现有表单{#importing-elements-from-an-existing-form}导入元素

可以从其他容器导入字段或Web 窗体。 这允许您创建可重用块库，这些块将插入到表单中，如地址块、新闻稿订阅区域等。

要将元素导入表单，请应用以下步骤：

1. 编辑要将一个或多个元素插入的页面，然后单击工具栏中的&#x200B;**[!UICONTROL Import an existing block]**。

   ![](assets/s_ncs_admin_survey_import_block.png)

1. 选择包含要导入的字段的Web表单，并选择要导入的容器和字段。

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >通过源表单名称右侧的&#x200B;**[!UICONTROL Edit link]**&#x200B;图标，可以视图所选Web表单。

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;以确认插入。

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)

