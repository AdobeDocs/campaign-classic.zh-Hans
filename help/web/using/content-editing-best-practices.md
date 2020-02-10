---
title: 内容编辑最佳实践
seo-title: 内容编辑最佳实践
description: 内容编辑最佳实践
seo-description: null
page-status-flag: never-activated
uuid: badc6806-b474-4cad-94a3-003a50271281
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 3ad38469-8e22-4bfc-8029-5d360f76d6bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 内容编辑最佳实践{#content-editing-best-practices}

为确保编辑的最佳操作，我们建议遵循以下准则：

* 在Adobe **Campaign中导入HTML页面模板之前** ，请确保在各种浏览器中正确打开和显示该模板。
* 如果HTML页包含 **JavaScript脚本**，则需要在编辑器外执行 **时不出错** 。
* 在构建模板时，我们建议向标 **记添加“type** ”属 `<input>` 性。 此信息将由编辑者处理，并帮助用户在配置Web应用程序时将数据库的字段链接到表单的字段。

   模板中的HTML代码示例：

   ```
   <input id="email" type="email" name="email"/>
   ```

   “ **type”属性** 在界面中以以下形式显示：

   ![](assets/dce_sidebar_inputtypechanges.png)

   此网站提供“类型”属性的正 [式列表](https://www.w3schools.com/tags/att_input_type.asp)。

* 使用DCE模拟结束页面的步骤：

   ![](assets/dce_enchainement.png)

* 确保页面中只 `<body> </body>` 有一个。
* 上传CSS或JS文件时，.zip文件中包含的图像不会上传。 因此，不会更新对CSS中存在的这些图像的引用。

## 内容编辑器支持的格式 {#content-editor-supported-formats}

数字内容编辑器支持HTML格式：您可以随时切换 **到源** 模式。

数字内容编辑器的导入功能可使用以下支持的格式：

* CSS:.zip文件中的图像不会导入。 不更新对CSS中这些图像的引用。
* JS:.zip文件中的图像不会导入。 JS中对这些图像的引用不会更新。
* Iframe:链接的页面不会导入。
* 登录页面和Web应用程序：如果缺 **少表单** 标记，将显示一条警告消息。 消息 `<form> </form>` 正文中必须始终存在一个。

数字内容编辑器还适用于以下支持的代码页：

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8（在使用BOM时建议）
* iso-8859-15
* us-ascii
* shift jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>HTML代码页必须在meta标签（HTML 4或HTML 5）或BOM中定义。 如果没有可用的代码页，请打开latin1中的文件。

## HTML内容状态 {#html-content-statuses}

编辑器的上半部分显示与内容状态相关的消息。 消息的颜色代码如下：

* **灰色消息**:信息消息，无需在编辑器中执行任何操作。
* **蓝色消息**:与正在编辑的内容相关的信息消息。
* **黄色消息**:需要代表用户执行操作的警告或错误消息。

### 编辑Web应用程序时的消息列表 {#list-of-messages-when-editing-a-web-application}

* HTML内容可正常使用。
* Web应用程序尚未发布，无法联机访问。
* Web应用程序处于联机状态，请再次发布以应用任何更改。
* 页面内容不起作用。 它必须包含HTML表单(`<form>`)
* 没有要配置的输入区域或按钮。
* 要启用到下一页的过渡，您需要将“下一页”动作链接到当前页面上的按钮或链接。

### 编辑传送时的消息列表 {#list-of-messages-when-editing-a-delivery}

* 交付内容具有功能
* 没有要配置的字段或个性化基块。
* 交付内容已准备好，请再次运行分析以应用任何更改。
* 交付已准备好发送。

