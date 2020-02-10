---
title: 生成个性化的PDF文档
seo-title: 生成个性化的PDF文档
description: 生成个性化的PDF文档
seo-description: null
page-status-flag: never-activated
uuid: d4c27523-bff3-457a-ba60-e2747a2b3166
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 8dfc5e7c-c762-46ba-bbda-a7251354cb47
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 生成个性化的PDF文档{#generating-personalized-pdf-documents}

## 关于可变PDF文档 {#about-variable-pdf-documents}

Adobe Campaign允许您从LibreOffice或Microsoft word文档生成可变PDF文档（用于电子邮件附件、直接邮件传送）。

支持以下扩展：&quot;。docx&quot;、&quot;。doc&quot;和&quot;。odt&quot;。

为了个性化您的文档，可以使用与电子邮件个性化相同的JavaScript功能。

您需要激活该 **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** 选项。 将文件附加到传送电子邮件时，此选项可供访问。 有关附加计算文件的详细信息，请参阅附加 [文件部分](../../delivery/using/attaching-files.md) 。

发票题头个性化示例：

![](assets/s_ncs_pdf_simple.png)

要通过URL生成动态表或包含图像，您需要遵循特定流程。

## 生成动态表 {#generating-dynamic-tables}

生成动态表的过程如下：

* 创建包含三行和所需列的表，然后配置其布局（边框等）。
* 将光标放在表上并单击菜 **[!UICONTROL Table > Table properties]** 单。 转到选项卡 **[!UICONTROL Table]** 并输入以NlJsTable开头的 **名称**。
* 在第一行的第一个单元格中，定义一个循环（例如，“for”），该循环允许对要在表中显示的值进行迭代。
* 在表的第二行的每个单元格中，插入返回要显示的值的脚本。
* 关闭表的第三行和最后一行中的循环。

   动态表定义示例：

   ![](assets/s_ncs_pdf_table.png)

## 插入外部图像 {#inserting-external-images}

例如，如果您希望使用在收件人字段中输入其URL的图像对文档进行个性化，则插入外部图像很有用。

为此，您需要配置个性化块，然后在附件中包含对个性化块的调用。

**示例：根据收件人所在的国家／地区插入个性化的徽标**

**第1步：创建附件：**

* 插入对个性化区块的调用： **&lt;%@ include view=&quot;blockname&quot; %>**。
* 将您的内容（无论是否个性化）插入文件正文。

![](assets/s_ncs_open_office_blocdeperso.png)

**第2步：创建个性化基块：**

* 转到Adobe **[!UICONTROL Resources > Campaign management > Personalization blocks]** Campaign控制台的菜单。
* 创建新的“My Logo”个性化块，其中“My_Logo”作为内部名称。
* 单击链接， **[!UICONTROL Advanced parameters...]** 然后选中该 **[!UICONTROL "The content of the block is included in an attachment"]** 选项。 这样，您就可以将个性化块的定义直接复制到OpenOffice文件的内容中。

   ![](assets/s_ncs_pdf_bloc_option.png)

   您需要在个性化区块中区分两种类型的声明：

   * 个性化字段的Adobe Campaign代码，其中“打开”和“关闭”雪佛兰必须替换为转义字符(分别 `&lt;` 和 `&gt;`)。
   * 整个OpenOffice XML代码将复制到OpenOffice文档中。

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

根据收件人所在的国家／地区，个性化显示在与分发链接的文档中：

![](assets/s_ncs_pdf_result.png)
