---
product: campaign
title: 内容编辑器界面
description: 内容编辑器界面
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: cb76f3dc-7f3a-49de-89cb-c106865ecb17
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 3%

---

# 内容编辑器界面{#content-editor-interface}



## 编辑窗口 {#editing-window}

DCE编辑窗口分为三个不同的部分。 它们允许您查看、修改和检查内容的状态。

![](assets/dce_decoupe_window_nb.png)

1. 此 **top** 部分是显示发送给用户的消息的区域。 这些消息指示Web应用程序状态或正在创建的投放的状态，以及与内容相关的警告和错误消息。 有关详细信息，请参见 [HTML内容状态](content-editing-best-practices.md#html-content-statuses).
1. 中的部分 **左侧** 是编辑内容的区域。 在此区域中，用户可以使用弹出式工具栏直接与内容交互：在图像中插入链接、更改字体、删除字段等。 有关详细信息，请参阅 [编辑表单](editing-content.md#editing-forms).
1. 中的部分 **右** 控制面板区域。 此区域对编辑器的不同选项进行分组，尤其是与配置块的页面标题和常规选项相关的选项：添加边框、将数据库字段与输入区域链接、访问Web页属性等。 有关详细信息，请参见 [全局选项](#global-options) 和 [编辑内容](editing-content.md) 部分。

## 全局选项 {#global-options}

该编辑器的右上部分允许您访问全局选项，以便控制当前创建的内容。

![](assets/dce_global_options.png)

它有四个图标：

![](assets/dce_icons_sidebar.png)

* 此 **显示/隐藏块** 图标可让您在内容块周围显示蓝色框架(对应于 `<div>` HTML)。

* 此 **选择其他内容** 图标允许用户从模板（现有模板或现成模板）加载新内容。

  ![](assets/dce_popup_templatechoice.png)

  >[!CAUTION]
  >
  >所选内容替换当前内容。

* 此 **另存为模板** 图标用于将当前内容另存为模板。 必须输入模板的标签和内部名称。 模板存储在中 **[!UICONTROL Resources > Templates > Content templates]** 节点。

  ![](assets/dce_popup_savetemplate.png)

  保存后，模板可用，并可在创建新内容时进行选择。

  ![](assets/dce_create_fromtemplate.png)

* 此 **页面属性** 图标允许您选择HTML页面顶部的内容信息。

  ![](assets/dce_popup_headerhtml.png)

  >[!NOTE]
  >
  >此信息对应于 **`<title>`** 和 **`<meta>`** 页面上的标签HTML。
  >
  >关键词必须以逗号分隔。

## 块选项 {#block-options}

编辑器右侧的部分对主要选项进行了分组，使您能够根据内容进行操作。 要显示这些选项，必须选择一个块：这些选项的性质取决于所选的块。

![](assets/dce_right_section.png)

您可以：

* 确定一个或多个块的显示，请参阅 [定义可见性条件](editing-content.md#defining-a-visibility-condition)，
* 定义边框和框架，请参阅 [添加边框和背景](editing-content.md#adding-a-border-and-background)，
* 定义图像属性（大小、标题），请参阅 [编辑图像属性](editing-content.md#editing-image-properties)，
* 将数据库链接到表单元素（输入区域、复选框），请参阅 [更改表单的数据属性](editing-content.md#changing-the-data-properties-for-a-form)，
* 将表单的一部分设为必填，请参阅 [更改表单的数据属性](editing-content.md#changing-the-data-properties-for-a-form)，
* 为按钮定义操作，请参阅 [向按钮添加操作](editing-content.md#adding-an-action-to-a-button).

## 内容工具栏 {#content-toolbar}

工具栏是 **弹出元素** DCE接口，根据选择的块显示不同的功能。

>[!CAUTION]
>
>利用某些工具栏功能，可将 HTML 格式的格式化。但是，如果页面包含CSS样式表，则 **说明** 从样式表中可以看到 **优先级** 按照工具栏中指定的说明执行操作。
