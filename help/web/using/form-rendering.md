---
product: campaign
title: 窗体渲染
description: 窗体渲染
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Forms
exl-id: 723a6c47-5323-4914-a014-58be493852cc
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 2%

---

# 窗体渲染{#form-rendering}



## 选择表单渲染模板 {#selecting-the-form-rendering-template}

利用表单设置，可选择用于生成页面的模板。 要访问它们，请单击 **[!UICONTROL Properties]** 按钮，然后选择 **[!UICONTROL Rendering]** 选项卡。 默认情况下，有许多模板（样式表）可用。

![](assets/s_ncs_admin_survey_rendering_select.png)

利用该编辑器的底部部分，可以查看所选模板的渲染。

缩放功能允许您编辑选定的模板。

![](assets/s_ncs_admin_survey_render_edit.png)

您可以修改或覆盖这些模板。 要执行此操作，请单击 **[!UICONTROL Page layout...]** 链接信息并使其个性化。

![](assets/s_ncs_admin_survey_render_edit_param.png)

您可以：

* 更改用作徽标的图像，并调整其大小，
* 当用户选择此渲染模板时，还可以指定用于访问预览图像的路径。

此 **[!UICONTROL Headers/Footers]** 选项卡允许您使用此模板更改每个表单页面页眉和页脚中显示的信息。

![](assets/s_ncs_admin_survey_render_edit_header.png)

每行 **[!UICONTROL Page headers]** 和 **[!UICONTROL Page footers]** 部分对应于HTML页中的一行。 单击 **[!UICONTROL Add]** 以创建新行。

选择现有行，然后单击 **[!UICONTROL Detail]** 按钮对其进行个性化。

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

您可以通过相关选项卡更改线内容、添加边框和更改字体属性。 单击 **[!UICONTROL OK]** 以确认这些更改。

此 **[!UICONTROL Position]** 利用字段，可定义元素在页眉和页脚中的位置。

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>渲染模板存储在中 **[!UICONTROL Administration > Configuration > Form rendering]** 节点。\
>有关更多信息，请参阅 [自定义表单渲染](#customizing-form-rendering)

## 自定义表单渲染 {#customizing-form-rendering}

### 更改元素布局 {#changing-the-layout-of-elements}

您可以重载表单中每个元素（输入字段、图像、单选按钮等）的样式表。

要执行此操作，请使用 **[!UICONTROL Advanced]** 选项卡。

![](assets/s_ncs_admin_survey_advanced_tab.png)

它使您能够定义以下属性：

* **[!UICONTROL Label position]**：请参阅 [定义标签的位置](defining-web-forms-layout.md#defining-the-position-of-labels)，
* **[!UICONTROL Label format]**：自动换行或不自动换行，
* **[!UICONTROL Number of cells]** ：请参阅 [定位页面上的字段](defining-web-forms-layout.md#positioning-the-fields-on-the-page)，
* **[!UICONTROL Horizontal alignment]** （左、右、居中）和 **[!UICONTROL Vertical alignment]** （高、低、中）、
* **[!UICONTROL Width]** 区域的：这可以用百分比或以ems、点或像素（默认值）表示，
* 最大值 **[!UICONTROL Length]**：允许的最大字符数（对于文本、数字和密码类型控件），
* **[!UICONTROL Lines]**：行数 **[!UICONTROL Multi-line text]** 文字区域，
* **[!UICONTROL Style inline]**：允许您使用其他设置重载CSS样式表。 这些字符使用以下方式分隔： **；** 个字符，如以下示例所示：

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### 定义页眉和页脚 {#defining-headers-and-footers}

字段按树结构排序，其根与页面同名。 选择它以修改名称。

窗口的标题必须输入到 **[!UICONTROL Page]** 表单属性窗口的选项卡。 您还可以向页眉和页脚添加一组内容（此信息将显示在每个页面上）。 此内容输入到的匹配部分 **[!UICONTROL Texts]** 选项卡，如下所示：

![](assets/s_ncs_admin_survey_titles_config.png)

### 向HTML标题添加元素 {#adding-elements-to-html-header}

您可以输入要插入到表单页的HTML标题中的其他元素。 要执行此操作，请在 **[!UICONTROL Header]** 选项卡中。

例如，这允许您引用将显示在页面标题栏中的图标。

![](assets/webform_header_page_tab.png)

## 定义控制设置 {#defining-control-settings}

当用户填写表单时，将根据字段的格式或配置，自动对特定字段执行检查。 这使您可以将某些字段设为必填字段(请参阅 [定义必填字段](#defining-mandatory-fields))或检查输入数据的格式(请参阅 [检查数据格式](#checking-data-format))。 在页面审批期间执行检查（通过单击启用输出过渡的链接或按钮）。

### 定义必填字段 {#defining-mandatory-fields}

要将某些字段设为必填字段，请在创建字段时选择此选项。

![](assets/s_ncs_admin_survey_required_field.png)

如果用户未输入字段即批准此页面，则会显示以下消息：

![](assets/s_ncs_admin_survey_required_default_msg.png)

您可以通过单击 **[!UICONTROL Personalize this message]** 链接。

![](assets/s_ncs_admin_survey_required_custom_msg.png)

如果用户未输入字段即批准此页面，则会显示以下消息：

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### 检查数据格式 {#checking-data-format}

对于其值存储在数据库的现有字段中的表单检查，将应用存储字段的规则。

对于其值存储在变量中的表单检查，审批规则取决于变量的格式。

例如，如果您创建 **[!UICONTROL Number]** 选中以存储客户端编号，如下所示：

![](assets/s_ncs_admin_survey_choose_format.png)

用户必须在表单字段中输入整数。

## 定义字段条件显示 {#defining-fields-conditional-display}

您可以根据用户选择的值，配置要在页面上显示的字段的显示。 这可以应用于一个字段或一组字段（当它们分组在容器中时）。

对于页面的每个元素， **[!UICONTROL Visibility]** 部分用于定义显示条件。

![](assets/s_ncs_admin_survey_condition_edit.png)

条件可能与数据库字段或变量的值有关。

在字段选择窗口中，您可以从以下数据中进行选择：

![](assets/s_ncs_admin_survey_condition_select.png)

* 主树包含表单上下文的参数。 默认参数是Identifier（与收件人的加密标识符匹配）、Language和Origin。

   有关详细信息，请参见此 [ 页面](defining-web-forms-properties.md#form-url-parameters)。

* 此 **[!UICONTROL Recipients]** 子树包含插入到表单中并存储在数据库中的输入字段。

   有关更多信息，请参阅 [将数据存储在数据库中](web-forms-answers.md#storing-data-in-the-database).

* 此 **[!UICONTROL Variables]** 子树包含此表单可用的变量。 有关更多信息，请参阅 [将数据存储在局部变量中](web-forms-answers.md#storing-data-in-a-local-variable).

有关更多信息，请参阅此处提供的用例： [根据选定的值显示不同的选项](use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values).

您还可以使用设置表单页面显示的条件 **[!UICONTROL Test]** 对象。 有关详细信息，请参见此 [ 页面](defining-web-forms-page-sequencing.md#conditional-page-display)。

## 从现有表单导入元素 {#importing-elements-from-an-existing-form}

可以从其他Web窗体导入字段或容器。 这样，您就可以创建一个可重复使用的块库，这些块将插入到表单中，例如地址块、新闻稿订阅区域等。

要将元素导入表单，请应用以下步骤：

1. 编辑要向其中插入一个或多个元素的页面，然后单击 **[!UICONTROL Import an existing block]** 工具栏中。

   ![](assets/s_ncs_admin_survey_import_block.png)

1. 选择包含要导入的字段的Web窗体并选择要导入的容器和字段。

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >此 **[!UICONTROL Edit link]** 通过源表单名称右侧的图标，可以查看选定的Web表单。

1. 单击 **[!UICONTROL Ok]** 以确认插入。

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)
