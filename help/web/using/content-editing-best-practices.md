---
product: campaign
title: 内容编辑最佳实践
description: 内容编辑最佳实践
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 3%

---

# 内容编辑最佳实践{#content-editing-best-practices}



为确保编辑器获得最佳操作，我们建议遵循以下准则：

* 早于 **导入HTML页模板** 在Adobe Campaign中，请确保模板打开并在各种浏览器中正确显示。
* 如果HTML页包含 **javascript脚本**，则需要执行 **无错误** 在编辑器外。
* 在构建模板时，我们建议添加 **&#39;类型&#39;** 属性至 `<input>` 标记之间。 配置Web应用程序时，编辑器将处理此信息，并帮助用户将数据库的字段链接到表单的字段。

  模板中的 HTML 代码示例：

  ```
  <input id="email" type="email" name="email"/>
  ```

  此 **&#39;类型&#39;** 属性在界面中以下列形式显示：

  ![](assets/dce_sidebar_inputtypechanges.png)

  “类型”属性的官方列表可用 [在此网站中](https://www.w3schools.com/tags/att_input_type.asp).

* 使用DCE模拟结束页面的步骤：

  ![](assets/dce_enchainement.png)

* 确保只有一个 `<body> </body>` 在页面中。
* 上传CSS或JS文件时，不会上传.zip文件中包含的图像。 因此，不会更新CSS对这些图像的引用。

## 内容编辑器支持的格式 {#content-editor-supported-formats}

数字内容编辑器支持HTML格式：您可以切换到 **源** 模式。

数字内容编辑器的导入功能具有以下受支持的格式，如下所示：

* CSS： .zip文件中存在的图像未导入。 CSS对这些图像的引用不会更新。
* JS： .zip文件中存在的图像未导入。 JS中对这些图像的引用不会更新。
* Iframe：不导入链接的页面。
* 登陆页面和Web应用程序：如果 **表单** 标记缺失，将显示警告。 A `<form> </form>` 必须始终存在于消息正文中。

数字内容编辑器还可用于以下受支持的代码页面：

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8（使用BOM时推荐）
* iso-8859-15
* us-ascii
* shift jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>HTML代码页必须在meta标签(HTML4或HTML5)或BOM中定义。 如果没有可用的代码页，请使用latin1打开文件。

## HTML内容状态 {#html-content-statuses}

编辑器的上半部分显示与内容状态相关的消息。 消息的颜色代码如下：

* **灰色消息**：信息消息，无需在编辑器中执行任何操作。
* **蓝色消息**：与正在编辑的内容相关的信息消息。
* **黄色消息**：警告或错误消息，需要代表用户执行操作。

### 编辑Web应用程序时的消息列表 {#list-of-messages-when-editing-a-web-application}

* HTML内容可正常使用。
* Web应用程序尚未发布，无法联机访问。
* Web应用程序处于联机状态，请重新发布以应用任何更改。
* 页面内容无法正常运行。 必须包含HTML表单(`<form>`)
* 没有要配置的输入区域或按钮。
* 要启用到下一页的过渡，您需要将“下一页”操作链接到当前页面上的按钮或链接。

### 编辑投放时的消息列表 {#list-of-messages-when-editing-a-delivery}

* 投放内容可正常使用
* 没有要配置的字段或个性化块。
* 投放内容已准备就绪，请重新运行分析以应用任何更改。
* 投放已准备就绪，可供发送。
