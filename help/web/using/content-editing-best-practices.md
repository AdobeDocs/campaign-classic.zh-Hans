---
solution: Campaign Classic
product: campaign
title: 内容编辑最佳实践
description: 内容编辑最佳实践
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---


# 内容编辑最佳实践{#content-editing-best-practices}

为确保编辑的最佳操作，我们建议遵循以下准则：

* 在&#x200B;**导入Adobe Campaign中的HTML页面模板**&#x200B;之前，请确保在各种浏览器中正确打开和显示模板。
* 如果HTML页包含&#x200B;**JavaScript脚本**，则需要在编辑器外执行&#x200B;**且没有错误**。
* 在构建模板时，我们建议向标记添加 **&#39;type’** 属性。`<input>`此信息将由编辑器处理，并帮助用户在配置Web 应用程序时将数据库字段链接到表单的字段。

   模板中的 HTML 代码示例：

   ```
   <input id="email" type="email" name="email"/>
   ```

   **&#39;type&#39;**&#x200B;属性在接口中以以下形式可见：

   ![](assets/dce_sidebar_inputtypechanges.png)

   “type”属性的官方列表在此网站](https://www.w3schools.com/tags/att_input_type.asp)中提供。[

* 使用数字内容编辑器模拟结束页面的步骤：

   ![](assets/dce_enchainement.png)

* 确保页面中只有一个`<body> </body>`。
* 上传CSS或JS文件时，.zip文件中包含的图像将不会上传。 因此，不会更新对CSS中存在的这些图像的引用。

## 内容编辑器支持的格式{#content-editor-supported-formats}

该数字内容编辑器支持HTML格式：您可以随时切换到&#x200B;**source**&#x200B;模式。

数字内容编辑器的导入函数与以下支持的格式配合使用：

* CSS:.zip文件中存在的图像不会导入。 在CSS中对这些图像的引用不会更新。
* JS:.zip文件中存在的图像不会导入。 对JS中这些图像的引用不会更新。
* Iframe:链接的页面不会导入。
* 登陆页和Web应用程序：如果缺少&#x200B;**form**&#x200B;标记，将显示警告。 `<form> </form>`必须始终存在于邮件正文中。

该数字内容编辑器还适用于以下受支持的代码页：

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8（使用物料清单时建议）
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

## HTML内容状态{#html-content-statuses}

编辑器的上半部分显示与内容状态相关的消息。 消息的颜色代码如下所示：

* **灰色消息**:信息消息，无需在编辑器中执行任何操作。
* **蓝色消息**:与正在编辑的内容相关的信息消息。
* **黄色消息**:警告或错误消息，要求代表用户执行操作。

### 编辑Web 应用程序{#list-of-messages-when-editing-a-web-application}时的消息列表

* HTML内容可正常使用。
* Web 应用程序尚未发布，无法联机访问。
* Web 应用程序处于联机状态，请再次发布以应用任何更改。
* 页面内容无法正常工作。 它必须包含HTML表单(`<form>`)
* 没有要配置的输入区域或按钮。
* 要启用过渡至下一页，您需要将“下一页”操作链接到当前页面上的按钮或链接。

### 编辑投放{#list-of-messages-when-editing-a-delivery}时的消息列表

* 投放内容具有功能
* 没有要配置的字段或个性化块。
* 投放内容已准备就绪，请再次运行分析以应用任何更改。
* 投放已准备好发送。

