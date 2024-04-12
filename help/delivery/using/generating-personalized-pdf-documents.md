---
product: campaign
title: 生成个性化 PDF 文档
description: 了解如何生成个性化PDF文档
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Personalization
role: User
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 1%

---

# 生成个性化 PDF 文档{#generating-personalized-pdf-documents}

## 关于可变PDF文档 {#about-variable-pdf-documents}

Adobe Campaign允许您从LibreOffice或Microsoft Word文档为电子邮件附件生成可变PDF文档。

支持以下扩展：“.docx”、“.doc”和“.odt”。

要个性化您的文档，可以使用与电子邮件个性化相同的JavaScript功能。

您需要激活 **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** 选项。 将文件附加到投放电子邮件时，此选项可访问。 有关附加计算文件的详细信息，请参阅 [附加文件](attaching-files.md) 部分。

发票标头个性化示例：

![](assets/s_ncs_pdf_simple.png)

要通过URL生成动态表或包含图像，您需要遵循特定过程。

## 生成动态表 {#generating-dynamic-tables}

生成动态表的过程如下：

* 创建一个表，使之包含三行以及所需数量的列，然后配置其布局（边框等）。
* 将光标放在表格上并单击 **[!UICONTROL Table > Table properties]** 菜单。 转到 **[!UICONTROL Table]** 选项卡，并输入以开头的名称 **NlJsTable**.
* 在第一行的第一个单元格中，定义一个循环（例如“for”），该循环可对要在表中显示的值进行迭代。
* 在表第二行的每个单元格中，插入返回要显示的值的脚本。
* 关闭表的第三行和最后一行中的循环。

  动态表定义的示例：

  ![](assets/s_ncs_pdf_table.png)

## 插入外部图像 {#inserting-external-images}

例如，如果您希望使用在收件人字段中输入URL的图像对文档进行个性化，则插入外部图像会很有用。

要实现此目的，您需要配置个性化块，然后在附件中包含对个性化块的调用。

**示例：根据收件人的国家/地区插入个性化徽标**

**第1步：创建附件：**

* 将调用插入个性化块： **&lt;%@包含视图=&quot;blockname&quot; %>**.
* 将您的内容（无论是否个性化）插入文件正文。

![](assets/s_ncs_open_office_blocdeperso.png)

**第2步：创建个性化块：**

* 转到 **[!UICONTROL Resources > Campaign management > Personalization blocks]** Adobe Campaign控制台的菜单。
* 创建新的“我的徽标”个性化块，并将“My_Logo”作为内部名称。
* 单击 **[!UICONTROL Advanced parameters...]** 链接，然后查看 **[!UICONTROL "The content of the block is included in an attachment"]** 选项。 这使您可以将个性化块的定义直接复制到OpenOffice文件的内容中。

  ![](assets/s_ncs_pdf_bloc_option.png)

  您需要区分个性化块中的两种类型的声明：

   * 个性化字段的Adobe Campaign代码，其“打开”和“关闭”V形必须分别替换为转义字符 `&lt;` 和 `&gt;`)。
   * 整个OpenOffice XML代码将被复制到OpenOffice文档中。

在示例中，个性化块如下所示：

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

根据收件人的国家/地区，个性化内容会在链接到投放的文档中可见：

![](assets/s_ncs_pdf_result.png)
