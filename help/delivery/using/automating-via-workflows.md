---
product: campaign
title: 通过工作流实现自动化
description: 了解如何通过工作流实现内容管理自动化
exl-id: bc6ebf5d-cc21-4750-9713-2bf259e7d6bf
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1190'
ht-degree: 0%

---

# 使用工作流实现自动化{#automating-via-workflows}

![](../../assets/common.svg)

## 内容管理活动 {#content-management-activity}

使用通过Adobe Campaign客户端界面配置的工作流程，可以自动创建、编辑和发布内容。

的 **内容管理** 通过 **[!UICONTROL Tools]** 工具栏。

活动属性分为四个步骤：

* **[!UICONTROL Content]** :允许您输入现有内容或创建内容，
* **[!UICONTROL Update content]** :允许您修改内容的主题或通过XML数据流更新内容，
* **[!UICONTROL Action to execute]** :允许您保存或生成内容，
* **[!UICONTROL Transition]** :用于选择是否生成输出过渡并为其指定名称。

![](assets/d_ncs_content_wf.png)

### 内容 {#content}

* **由过渡指定**

   要使用的内容是之前创建的。 进程将涉及由传入事件传播的内容实例。 内容标识符通过事件的“contentId”变量进行访问。

* **显式**

   允许您选择之前创建的内容。

* **由脚本计算**

   根据JavaScript模板选择内容实例。 要评估的代码允许您检索内容标识符。

* **新建，通过发布模板创建**

   通过发布模板创建新内容。 内容实例将保存在填充的“String”文件夹中。

### 更新内容 {#update-the-content}

* **主题**

   允许您在发布时修改投放操作的主题。

* **从XML馈送访问数据**

   内容从外部源的XML源进行更新。 必须输入URL才能进行数据下载。

   XSL样式表可用于转换传入的XML数据。

### 要执行的操作 {#action-to-execute}

* **保存**

   保存创建或修改的内容。 保存内容的标识符会传播到传出事件的“contentId”变量中。

* **生成**

   为具有“File”类型发布的每个转换模板生成输出文件。 将为每个生成的文件激活传出过渡，并使用以下参数：“contentId”变量中保存的内容的标识符以及“filename”变量中的文件名。

### 过渡 {#transition}

的 **生成输出过渡** 选项，可向 **[!UICONTROL Content management]** 活动，将新活动链接到工作流执行。 选中此选项后，输入过渡的标签。

## 示例 {#examples}

### 自动创建和交付内容 {#automating-content-creation-and-delivery}

以下示例可自动创建和交付内容块。

![](assets/d_ncs_content_workflow2.png)

内容通过“内容管理”活动进行配置：

![](assets/d_ncs_content_workflow3.png)

通过发布模型和内容字符串文件夹创建新的内容实例。

在我们的示例中，我们超载了投放主题。 系统将考虑该事件，而不是 **[!UICONTROL Delivery]** 模板。

内容由来自输入URL的XML馈送自动填充：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

数据格式与在发布模板(**cus:book** );the **`<section>`** 元素必须替换为 **`<chapter>`** 元素。 我们需要应用“cus:book-workflow.xsl”样式表以进行必要的更改。

使用的XSLT样式表的源代码：

```
<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
 <xsl:output indent="yes" method="xml"  encoding="ISO-8859-1"/>

 <xsl:template match="text()|@*"/>

  <xsl:template match="*">
    <xsl:variable name="element.name" select="name(.)"/>
    <xsl:element name="{$element.name}">
      <xsl:copy-of select="text()|@*"/>
      <xsl:apply-templates/>
    </xsl:element>
  </xsl:template>

  <xsl:template match="book">
  <book name="test">
     <xsl:apply-templates/>
    <book>
 </xsl:template>

  <xsl:template match="section">
    <chapter>
      <xsl:for-each select="@*">
        <xsl:copy-of select="."/>
      </xsl:for-each>
       <xsl:apply-templates/>
    </chapter>
  </xsl:template>
  
</xsl:stylesheet>
```

活动的最终操作是保存内容实例并继续执行下一项任务。

通过 **查询** 活动。

安 **AND — 连接** 添加了活动，以确保仅在完成target查询和内容更新后才开始投放。

投放操作通过 **投放** 活动：

![](assets/d_ncs_content_workflow4.png)

将基于模板创建新投放操作。

活动的投放模板用于选择发布模板的转换模板。 内容生成过程将考虑所有没有投放模板的HTML和文本模板，或者那些使用与活动相同的模板引用的内容和文本模板。

将通过传入事件输入要传送的目标。

投放内容通过传入事件填充。

完成活动的最后一步是准备并启动投放。

### 创建内容以供稍后发布 {#creating-content-and-publishing-it-later}

此示例会创建一个内容块，并在特定时间延迟后启动文件发布。

![](assets/d_ncs_content_workflow5.png)

第一个 **内容管理** 任务会创建内容实例。

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>的 **[!UICONTROL Publication]** 必须使用要生成的目标的位置填充转换模板窗口的选项卡。

将添加等待活动，以暂停下一个过渡一周。

![](assets/d_ncs_content_workflow7.png)

在此时间段内手动输入内容。

下一个任务将启动内容生成。

![](assets/d_ncs_content_workflow8.png)

将通过传入过渡输入要发布的内容。

最终操作是通过强制发布目录生成此内容。

的 **JavaScript代码** 活动会检索每个生成文件的完整名称。

![](assets/d_ncs_content_workflow9.png)

### 创建投放及其内容 {#creating-the-delivery-and-its-content}

此示例使用与第一个示例相同的概念，但只有它在第一步中创建投放操作。

![](assets/d_ncs_content_workflow10.png)

第一个 **创建投放** 任务会创建投放操作。

利用分支活动，可并行启动目标计算和内容实例的创建。

执行任务后，AND-join框将激活 **投放** 任务，以启动之前创建的有关内容和定位的投放。

![](assets/d_ncs_content_workflow11.png)

将通过过渡填充要启动的投放操作。

将通过传入事件输入要传送的目标。

投放内容通过传入事件填充。

活动的最终操作是准备并启动投放。

### 从FTP导入内容 {#importing-content-from-ftp}

如果您的交付内容位于FTP或SFTP服务器上的HTML文件中，则可以轻松地将此内容加载到Adobe Campaign交付中。 请参阅 [此示例](../../workflow/using/loading-delivery-content.md).

### 从Amazon Simple Storage Service(S3)连接器导入内容 {#importing-content-from-amazon-simple-storage-service--s3--connector}

如果您的投放内容位于Amazon简单存储服务(S3)存储段中，则可以轻松地将此内容加载到Adobe Campaign投放中。 请参阅 [此示例](../../workflow/using/loading-delivery-content.md).

## 半自动更新 {#semi-automatic-update}

可以在“半自动”模式下更新内容数据。 通过URL从XML馈送中恢复数据。

通过输入表单手动激活数据恢复。

目的是宣布 **editBtn** type **`<input>`** 字段。 此控件包括编辑区域和用于启动处理的按钮。

利用编辑区域，可填充用于构建要检索的XML数据馈送URL的变量数据。

按钮执行 **GetAndTransform** 在 **`<input>`** 标记。

格式的控制声明如下：

```
<input type="editbtn" xpath="<path>">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="<url>" type="string"/>
      <param exprIn="'xtk:xslt|<style sheet>'" type="string"/>
      <param type="DOMElement" xpathOut="<output path>"/>
    </soapCall>
  </enter>
</input>
```

的 **GetAndTransform** 方法必须在 **`<enter>`** 元素 **`<input>`** 标记。 此标记将从动态构建的表达式恢复XML数据的URL作为参数。 函数的第二个参数是可选的，当传入的XML数据与内容的格式不同时，会引用用于中间转换的样式表。

输出会根据在最后一个参数中输入的路径来更新内容。

**示例**:为了说明此示例，我们从“cus:book”模式开始。

添加了半自动更新编辑控制输入表单：

![](assets/d_ncs_content_exemple9.png)

```
<input label="File name" type="editbtn" xpath="/tmp/@name">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="'https://myserver.adobe.com/incoming/' + [/tmp/@name] + '.xml'" type="string"/>
      <param exprIn="'xtk:xslt|cus:book-workflow.xsl'" type="string"/>
      <param type="DOMElement" xpathOut="."/>
    </soapCall>
  </enter>
</input>
```

利用编辑区域，可输入要检索的文件的名称。 URL是基于此名称构建的，例如：https://myserver.adobe.com/incomin/data.xml

要检索的数据的格式与工作流自动化示例1中的格式相同。 我们将使用本示例中显示的“cus:book-workflow.xsl”样式表。

作业执行结果会从路径“。”更新内容实例。
