---
title: 内容编辑器界面
seo-title: 内容编辑器界面
description: 内容编辑器界面
seo-description: null
page-status-flag: never-activated
uuid: b108ea74-ae2c-4e47-bee8-12070927ba89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
dc-title: </strong> and
discoiquuid: 20c64d31-c2ed-4bc9-9f0e-46f2e0c08c88
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 内容编辑器界面{#content-editor-interface}

## 编辑窗口 {#editing-window}

DCE编辑窗口分为三个不同的部分。 它们允许您查看、修改和检查内容的状态。

![](assets/dce_decoupe_window_nb.png)

1. 顶 **部** (Top)部分是向用户发送消息的显示区域。 这些消息指示Web应用程序状态或正在创建的分发的状态，以及与内容相关的警告和错误消息。 有关详细信息，请参阅 [HTML内容状态](#html-content-statuses)。
1. 窗口左侧 **的部** 分是用于编辑内容的区域。 在此区域中，用户可以使用弹出工具栏直接与内容交互：在图像中插入链接、更改字体、删除字段等。 For more on this refer to [Editing forms](../../web/using/editing-content.md#editing-forms).
1. 窗口右侧 **的部** 分是控制面板区域。 此区域将编辑器的不同选项分组，特别是与配置页面标题和块常规选项相关的选项：添加边框、将数据库字段与输入区域链接、访问网页属性等。 有关详细信息，请参阅全局选 [项和编辑](#global-options)[内容部分](../../web/using/editing-content.md) 。

## 全局选项 {#global-options}

编辑器的右上部分允许您访问全局选项，以便控制当前创建的内容。

![](assets/dce_global_options.png)

它有四个图标：

![](assets/dce_icons_sidebar.png)

* 通过 **显示／隐藏块** ，您可以在内容块周围显示蓝色框架(与 `<div>` HTML标签相对应)。

* 通过 **选择其他内容** ，用户可以从模板（现有模板或现成模板）加载新内容。

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >所选内容将替换当前内容。

* 通过 **另存为模板** ，您可以将当前内容另存为模板。 必须输入模板的标签和内部名称。 模板存储在节 **[!UICONTROL Resources > Templates > Content templates]** 点中。

   ![](assets/dce_popup_savetemplate.png)

   保存后，模板即可用，并可在创建新内容时进行选择。

   ![](assets/dce_create_fromtemplate.png)

* 通过 **页面属性** 图标，可以选择HTML页面顶部的内容信息。

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >此信息与页面上 **`<title>`** 的 **`<meta>`** HTML和HTML标记相对应。
   >
   >关键字必须用逗号分隔。

## 块选项 {#block-options}

编辑器右侧的部分将主要选项分组，这些选项允许您对内容执行操作。 要显示这些选项，您必须选择一个块：这些选项的性质取决于所选的块。

![](assets/dce_right_section.png)

您可以：

* 确定一个或多个块的显示，请参阅定 [义可见性条件](../../web/using/editing-content.md#defining-a-visibility-condition),
* 定义边框和框架，请参阅 [添加边框和背景](../../web/using/editing-content.md#adding-a-border-and-background),
* 定义图像属性（大小、题注），请参阅编辑 [图像属性](../../web/using/editing-content.md#editing-image-properties),
* 将数据库链接到表单元素（输入区域、复选框），请参 [阅更改表单的数据属性](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* 将表单的一部分设为必填项，请参阅 [更改表单的数据属性](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* 为按钮定义操作，请参阅将 [操作添加到按钮](../../web/using/editing-content.md#adding-an-action-to-a-button)。

## 内容工具栏 {#content-toolbar}

工具栏是 **DCE界面的弹出元素** ，它根据所选块显示不同的功能。

>[!CAUTION]
>
>某些工具栏功能允许您设置HTML内容的格式。 但是，如果页面包含CSS样式表，则样式表中的 **说明** ，可能会被证明优先于使用工具栏 **指定的说明** 。

