---
product: campaign
title: 生成个性化 PDF 文档
description: 了解如何生成个性化的PDF文档
feature: Personalization
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 1%

---

# 生成个性化 PDF 文档{#generating-personalized-pdf-documents}

![](../../assets/common.svg)

## 关于变量PDF文档 {#about-variable-pdf-documents}

Adobe Campaign允许您为来自LibreOffice或Microsoft Word文档的电子邮件附件生成变量PDF文档。

支持以下扩展：&quot;。docx&quot;、&quot;。doc&quot;和&quot;。odt&quot;。

要个性化您的文档，可使用与电子邮件个性化相同的JavaScript功能。

您需要激活 **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** 选项。 将文件附加到投放电子邮件后，即可访问此选项。 有关附加计算文件的更多信息，请参阅 [附加文件](attaching-files.md) 中。

发票题头个性化示例：

![](assets/s_ncs_pdf_simple.png)

要通过URL生成动态表或包含图像，您需要遵循特定流程。

## 生成动态表 {#generating-dynamic-tables}

生成动态表的步骤如下：

* 创建一个包含三行且所需列数的表，然后配置其布局（边框等）。
* 将光标放在表格上，然后单击 **[!UICONTROL Table > Table properties]** 菜单。 转到 **[!UICONTROL Table]** 选项卡，输入以开头的名称 **NlJs表**.
* 在第一行的第一个单元格中，定义一个循环（例如，“for”），用于对要在表中显示的值进行迭代。
* 在表第二行的每个单元格中，插入返回要显示的值的脚本。
* 在表的第三行和最后一行中关闭循环。

   动态表定义的示例：

   ![](assets/s_ncs_pdf_table.png)

## 插入外部图像 {#inserting-external-images}

例如，如果您希望使用URL在收件人的字段中输入的图像来个性化文档，则插入外部图像会非常有用。

要实现此目的，您需要配置个性化块，然后在附件中包含对个性化块的调用。

**示例：根据收件人所在的国家/地区插入个性化徽标**

**步骤1:创建附件：**

* 插入对个性化块的调用： **&lt;%@ include view=&quot;blockname&quot; %>**.
* 将您的内容（无论是否个性化）插入文件正文。

![](assets/s_ncs_open_office_blocdeperso.png)

**步骤2:创建个性化块：**

* 转到 **[!UICONTROL Resources > Campaign management > Personalization blocks]** 菜单访问Adobe Campaign。
* 创建新的“My Logo”个性化块，并将“My_Logo”作为内部名称。
* 单击 **[!UICONTROL Advanced parameters...]** 链接，然后检查 **[!UICONTROL "The content of the block is included in an attachment"]** 选项。 这样，您就可以将个性化块的定义直接复制到OpenOffice文件的内容中。

   ![](assets/s_ncs_pdf_bloc_option.png)

   您需要区分个性化块中的两种类型的声明：

   * 个性化字段的Adobe Campaign代码，其中“open”和“closed”雪佛兰必须分别替换为转义字符( `&lt;` 和 `&gt;`)。
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

根据收件人所在的国家/地区，个性化会显示在链接到投放的文档中：

![](assets/s_ncs_pdf_result.png)
