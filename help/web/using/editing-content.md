---
product: campaign
title: 编辑内容
description: 编辑内容
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps, Web Forms, Landing Pages
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 1%

---

# 编辑内容{#editing-content}



## 定义可见性条件 {#defining-a-visibility-condition}

您可以在网页元素上指定一个可见性条件：仅当遵守条件时，此元素才可见。

要添加可见性条件，请选择一个块，然后在 **[!UICONTROL Visibility condition]** 字段。

![](assets/dce_add_condition.png)

>[!NOTE]
>
>高级表达式编辑在 [本页](../../platform/using/defining-filter-conditions.md#list-of-functions).

![](assets/dce_popup_visibilitycondition.png)

这些条件采用XTK表达式语法(例如 **ctx.recipient@电子邮件 != &quot;&quot;** 或 **ctx.recipient@status==&quot;0&quot;**)。 默认情况下，所有字段都可见。

>[!NOTE]
>
>无法编辑不可见的动态块（如下拉菜单）。

## 添加边框和背景 {#adding-a-border-and-background}

您可以添加 **边框** 到选定块。 使用以下三个选项来定义边框：样式、大小和颜色。

![](assets/dce_popup_border.png)

您还可以定义 **背景颜色** 从颜色图表中选择颜色。

![](assets/dce_popup_background.png)

## 编辑窗体 {#editing-forms}

### 更改表单的数据属性 {#changing-the-data-properties-for-a-form}

您可以将数据库字段与输入区域、单选按钮或复选框类型块链接在一起。

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>默认字段是Web应用程序存储模式中的字段。

的 **字段** 输入区域允许您选择要与表单字段链接的数据库字段。

默认情况下，提供的字段是 **nms:recipient** 表。

![](assets/dce_field_selection.png)

的 **必填字段** 选项，则仅当用户填写了字段后，才可授权页面批准。 如果未填写必填字段，则会显示错误消息。

对于单选按钮和复选框， **需要其他配置**.

事实上，如果使用的模板默认不包含值，则必须在编辑器中完成该模板。

操作步骤：

* 单击 **[!UICONTROL Edit]** 图标。

   ![](assets/dce_sidebar_options.png)

* 在 **[!UICONTROL Value]** 字段。

   ![](assets/dce_sidebar_completeoptionradio.png)

### 修改表单字段 {#modifying-form-fields}

表单字段，如单选按钮、输入区域、下拉列表等。 可在其工具栏中修改。

这意味着您可以：

* 使用删除包含表单字段的块 **[!UICONTROL Delete]** 图标。
* 通过使用 **[!UICONTROL Duplicate]** 图标。
* 编辑 **[!UICONTROL Form data]** 将数据库字段链接到表单区域的窗口，使用 **[!UICONTROL Edit]** 图标。

   ![](assets/dce_toolbar_formblock_edition.png)

## 向按钮添加操作 {#adding-an-action-to-a-button}

当用户单击按钮时，您可以定义一个关联的操作。 为此，请从下拉列表中选择要执行的操作。

![](assets/dce_sidebar_button.png)

可用的操作如下：

* **[!UICONTROL Refresh]** :刷新当前页面。
* **[!UICONTROL Next page]** :创建指向Web应用程序中下一页的链接。
* **[!UICONTROL Previous page]** :创建指向Web应用程序中上一页的链接。

>[!NOTE]
>
>的 **[!UICONTROL None]** 值允许您不激活按钮。

您可以在相应字段中修改链接到按钮的标签。

## 添加链接 {#adding-a-link}

您可以将链接插入到任何页面元素中：图像、单词、词组、文本块等。

要实现此目的，请选择元素，然后使用弹出菜单中的第一个图标。

![](assets/dce_insertlink_icon.png)

此图标允许您访问所有可用类型的链接。

![](assets/dce_insertlink_menu.png)

个性化块和字段只能插入到文本类型块中。

>[!NOTE]
>
>对于每种类型的链接，可以配置打开模式：在 **Target** 下拉列表。 此值对应于 **`<target>`** HTML标记。
>
>可用列表 **目标** 如下所示：
>
>* 其他(IFrame)
>* 顶部窗口(_top)
>* 父窗口(_parent)
>* 新窗口(_blank)
>* 当前窗口(_self)
>* 默认浏览器行为
>


### 链接到URL {#link-to-a-url}

的 **链接到外部URL** 选项可打开源内容中的任何URL。

![](assets/dce_toolbar_imgblock_externallink.png)

在 **URL** 字段。 URL字段应输入为： **https://www.myURL.com**.

### 链接到Web应用程序 {#link-to-a-web-application}

的 **链接到Web应用程序** 选项，可访问Adobe Campaign Web应用程序。

![](assets/dce_toolbar_imgblock_appweb.png)

从相应的字段中选择Web应用程序。

建议的Web应用程序列表对应于 **[!UICONTROL Resources > Online > Web Applications]** 节点。

### 操作链接 {#link-to-an-action}

的 **用于定义操作的链接** 选项，可在单击源元素时配置操作。

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>有关可用操作的详情，请参阅 [向按钮添加操作](#adding-an-action-to-a-button) 中。

### 删除链接 {#delete-a-link}

插入链接后，工具栏会提供两个新图标： **编辑链接** 和 **断开链接** 以便您与创建的链接进行交互。

* **[!UICONTROL Edit link]** 可显示一个窗口，其中包含链接的所有参数。
* **[!UICONTROL Break the link]** 允许您在确认后删除链接和所有相关参数。

>[!NOTE]
>
>如果删除链接，则内容仍会保留。

## 更改字体属性 {#changing-font-attributes}

选择文本元素时，可以修改字体属性（样式、格式）。

![](assets/dce_toolbar_txt.png)

可用选项如下：

* **放大字体** 图标：增加所选文本的大小(添加 `<span style="font size:">`)
* **减少字体** 图标：减小所选文本的大小(添加 `<span style="font size:">`)
* **粗体** 图标：将选定文本变为粗体(将文本换行为 `<strong> </strong>` 标记)
* **斜体** 图标：将所选文本设置为斜体(将文本换行为  `<em> </em>` 标记)
* **下划线** 图标：为选定文本加下划线(将文本换行为 `<span style="text-decoration: underline;">` 标记)
* **左对齐** 图标：将文本与选定块的左侧对齐(添加style=&quot;text-align:left；”)
* **中心** 图标：将选定块的文本居中(添加style=&quot;text-align:中心；”
* **右对齐** 图标：将文本与选定块的右侧对齐(添加style=&quot;text-align:右；”
* **更改背景颜色** 图标：允许您更改选定块的背景颜色(添加style=&quot;background-color:rgba(170, 86, 255, 0.87)
* **更改文本颜色** 图标：允许您更改选定块的文本颜色或仅更改选定文本(`<span style="color: #CODE">`)

>[!NOTE]
>
>* **删除** 图标：删除块及其所有内容。
>
>* **复制** 图标：复制块以及与块相关的所有样式。


## 管理图像和动画 {#managing-images-and-animations}

通过数字内容编辑器，您可以 **任何类型的图像** 与浏览器兼容。

>[!CAUTION]
>
>不得在 **script** 标记。 这些文件将不会导入到Adobe Campaign服务器中。

### 添加/删除/复制图像 {#adding---deleting---duplicating-an-image}

要插入图像，请选择图像类型块，然后单击 **图像** 图标。

![](assets/dce_insert_image.png)

选择本地保存的图像文件。

![](assets/dce_popup_imgupload.png)

的 **删除** 图标会删除包含图像的标记。

的 **复制** 图标会复制标记及其内容。

>[!CAUTION]
>
>复制图像时，与新图像相关的标识符会被删除。

### 编辑图像属性 {#editing-image-properties}

选择包含图像的块时，您可以访问以下属性：

* **题注** 用于定义链接到图像的标题(对应于 **alt** HTML属性)。
* **Dimension** 用于指定图像大小（以像素为单位）。

   ![](assets/dce_popup_imgsize.png)

## 添加个性化内容 {#adding-personalization-content}

### 插入个性化字段 {#inserting-a-personalization-field}

的 **个性化字段** 利用插入图标的选项，可向内容中添加数据库字段，如收件人的姓名。 此选项仅适用于文本类型块。

![](assets/dce_toolbar_textblock_persofield.png)

默认情况下，提供的字段来自 **[!UICONTROL Recipient]** 表。 根据需要，编辑Web应用程序属性以选择另一个表。

该字段名称将在编辑器中显示，并以黄色突出显示。 在生成个性化时（例如，预览登陆页面时），该用户档案将被目标收件人的用户档案替换。

有关示例，请参见 [插入个性化字段](creating-a-landing-page.md#inserting-a-personalization-field) 中。

### 插入个性化块 {#inserting-a-personalization-block}

的 **个性化块** 选项允许您在内容中插入动态和个性化的块。 例如，您可以添加徽标或问候语消息。 它不适用于文本类型块。

![](assets/dce_toolbar_textblock_persoblock.png)

插入后，个性化块名称会显示在编辑器中，并以黄色突出显示。 在生成个性化时，会自动将其调整为收件人用户档案。

有关内置个性化块以及如何定义自定义个性化块的更多信息，请参阅 [本页](../../delivery/using/personalization-blocks.md).
