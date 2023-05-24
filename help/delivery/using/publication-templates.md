---
product: campaign
title: 发布模板
description: 发布模板
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Templates
exl-id: 3b6e4974-4551-4da2-8eca-577c4f9cbd91
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 1%

---

# 发布模板{#publication-templates}



## 关于发布模板 {#about-publication-templates}

发布模板是要发布内容的身份证。 它引用发布过程中使用的资源，即：

* 数据架构，
* 输入表单，
* 每个输出文档的转换模板。

## 发布模板的标识 {#identification-of-a-publication-template}

发布模板由其名称和命名空间标识。

样式表的标识键是由命名空间和用冒号分隔的名称组成的字符串；例如： **cus：newsletter**.

>[!NOTE]
>
>在实践中，建议对架构、表单和发布模板使用相同的键。

## 创建和配置模板 {#creating-and-configuring-the-template}

默认情况下，发布模板存储在 **[!UICONTROL Administration > Configuration > Publication templates]** 节点。 要创建新模板，请单击 **[!UICONTROL New]** 按钮时，单击模板列表上方的“ ”按钮。

要配置发布模板，请填充模板的名称（即由名称和命名空间组成的标识键）、其标签、数据架构以及它所链接的输入表单。

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>每次基于此发布模板创建内容时，都会显示标签。

此 **检查状态以验证内容生成** 选项强制检查内容实例的“已验证”状态以授权文件生成。 有关更多信息，请参阅 [出版物](#publication).

必须为每个输出文档添加一个转换模板。 您可以根据需要创建任意数量的转换模板。

此 **[!UICONTROL Name of template]** 字段是一个自由标签，用于描述输出时的渲染类型。 对于每个转换模板，可在选项卡中找到发布设置。

### 渲染 {#rendering}

此 **[!UICONTROL Rendering]** 选项卡，选择：

* 用于投影输出文档的渲染类型：XSL样式表或JavaScript模板，
* 输出文档的格式：HTML、文本、XML或RTF，
* 包含构造数据的模板，即要使用的样式表或JavaScript模板。

### 发布 {#publication}

发布涉及以文件的形式生成输出文档(如果选择的类型为 **[!UICONTROL File]**.

![](assets/d_ncs_content_model2.png)

可以使用以下发布选项：

* 输出文件编码字符集可以通过 **[!UICONTROL Encoding]** 字段。 默认情况下使用拉丁语1 (1252)字符集。
* 此 **[!UICONTROL Multi-file generation]** 选项激活特殊文档发布模式。 此选项包括在输出文档的每个页面的开头填充分区标记。 生成内容将为每个填充的分区标记生成一个文件。 此模式用于从内容块生成微型站点。 有关更多信息，请参阅 [多文件生成](#multi-file-generation).
* 此 **[!UICONTROL Location]** 字段包含输出文件的名称。 该名称可由变量组成，以生成自动文件名。

   变量按以下格式填充： **`$(<xpath>)`**，其中 **`<xpath>`** 是发布模板数据架构的字段的路径。

   文件的名称可以包含日期类型字段。 要正确设置此字段的格式，请使用 **$date-format** 函数中，使用字段的路径和输出格式作为参数。

   默认情况下，文件名的构造格式使用“@name”和“@date”字段中的变量：

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   生成的文件名将如下所示： ct_news12_20110901.htm。

   >[!NOTE]
   >
   >有关内容生成的更多信息，请参阅 [创建内容实例](using-a-content-template.md#creating-a-content-instance).

### 投放 {#delivery}

利用此选项卡，可选择场景，以直接对内容启动投放。 将根据输出格式(HTML或文本)自动填充电子邮件的内容。

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>有关基于内容的投放创建的示例，请参阅 [交付内容实例](using-a-content-template.md#delivering-a-content-instance).

### 汇总 {#aggregator}

通过聚合脚本或查询列表中的数据，您可以使用内容数据扩充XML文档。 其目的是补充链接引用的某些信息，或从数据库中添加元素。

### 多文件生成 {#multi-file-generation}

要激活多个文件生成，请选择 **[!UICONTROL Multi-file generation]** 发布模型中的选项。 此选项允许您在样式表中为输出文档每一页的开头指定分区标记。 生成内容将为遇到的每个分区标记生成一个文件。

要集成在样式表中的分区标记如下：

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** 位置 **`<name_of_file>`** 是要生成的页面的文件名。

**示例：** 使用“cus：book”架构生成多个文件。

其原理是生成一个列出章节的主页，并可能在外部页面中显示章节的详细信息。

![](assets/d_ncs_content_chunk.png)

相应的样式表(“cus：book.xsl”)如下所示：

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

需要第二个样式表(“cus：chapter.xsl”)来生成章节的详细信息：

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

分区标记填充在页面的开头处，以包含在要生成的文件中。

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

文件名是使用 **$(path)** 变量包含发布路径和 **`<xsl:value-of select="@id" />`**，用于匹配输入文档中章节的标识符。

必须使用两个样式表“cus：book.xsl”和“cus：chapter.xsl”填充发布模型。

此 **[!UICONTROL Multi-file generation]** 选项必须在章节转换模型上处于活动状态：

![](assets/d_ncs_content_chunk2.png)

此 **[!UICONTROL Location]** 字段未用于生成多个文件，但您仍然必须填充此字段以避免发布时出错。
