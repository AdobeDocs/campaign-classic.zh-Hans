---
title: 通过工作流实现自动化
seo-title: 通过工作流实现自动化
description: 通过工作流实现自动化
seo-description: null
page-status-flag: never-activated
uuid: c77e8b2b-2a2c-4c6e-8497-662e7269e226
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 4abce633-647f-4ae4-9419-859f6e2e8628
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 通过工作流实现自动化{#automating-via-workflows}

## 内容管理活动 {#content-management-activity}

使用通过Adobe Campaign客户端界面配置的工作流程，可以自动创建、编辑和发布内容。

内容 **管理活动** ，可通过工作流图 **[!UICONTROL Tools]** 的工具栏访问。

活动属性分为四个步骤：

* **[!UICONTROL Content]** :允许您输入现有内容或创建内容，
* **[!UICONTROL Update content]** :允许您修改内容主题或通过XML数据流更新内容，
* **[!UICONTROL Action to execute]** :允许您保存或生成内容，
* **[!UICONTROL Transition]** :允许您选择是否生成输出过渡并为其指定名称。

![](assets/d_ncs_content_wf.png)

### 内容 {#content}

* **由过渡指定**

   要使用的内容是以前创建的。 进程将与传入事件传播的内容实例相关。 内容标识符通过事件的“contentId”变量访问。

* **显式**

   允许您选择之前创建的内容。

* **由脚本计算**

   基于JavaScript模板选择内容实例。 要评估的代码允许您检索内容标识符。

* **新增功能，通过发布模板创建**

   通过发布模板创建新内容。 内容实例将保存在填充的“String”文件夹中。

### 更新内容 {#update-the-content}

* **主题**

   允许您在发布时修改提交操作的主题。

* **从XML源访问数据**

   从外部源的XML源更新内容。 必须输入URL才能下载数据。

   XSL样式表可用于转换传入的XML数据。

### 要执行的操作 {#action-to-execute}

* **保存**

   保存创建或修改的内容。 保存内容的标识符在传出事件的“contentId”变量中传播。

* **生成**

   为每个转换模板生成输出文件，并发布“File”类型。 将为每个生成的文件激活输出过渡，并使用以下参数：保存在“contentId”变量中的内容的标识符和“filename”变量中的文件名。

### 过渡 {#transition}

通过 **“生成输出过渡** ”选项，可向活动添加输出过渡，以将 **[!UICONTROL Content management]** 新活动链接到工作流执行。 选中此选项后，输入过渡的标签。

## 示例 {#examples}

### 自动化内容创建和交付 {#automating-content-creation-and-delivery}

以下示例自动创建和交付内容块。

![](assets/d_ncs_content_workflow2.png)

内容通过“内容管理”活动进行配置：

![](assets/d_ncs_content_workflow3.png)

通过发布模型和内容字符串文件夹创建新内容实例。

在我们的例子中，交货主体超载了。 将考虑该参数，而不是在模板中输入的参 **[!UICONTROL Delivery]** 数。

内容由来自输入的URL的XML源自动填充：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

数据格式与出版物模板中输入的数据模式不匹配(**示例中的cus:book** );元 **`<section>`** 素必须替换为元 **`<chapter>`** 素。 我们需要应用“cus:book-workflow.xsl”样式表来进行必要的更改。

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

活动的最终操作是保存内容实例并继续执行下一个任务。

定位通过查询活动 **执行** 。

添加 **了AND-join** （与加入）活动，以确保仅在目标查询和内容更新完成后才启动交付。

交付操作是通过“交付”活 **动配置的** :

![](assets/d_ncs_content_workflow4.png)

将基于模板创建新的交付操作。

活动的交付模板用于选择发布模板的转换模板。 内容生成将考虑所有没有分发模板的HTML和文本模板，或那些使用与活动相同的模板引用的模板。

要传送的目标通过传入事件输入。

传送内容通过传入事件填充。

完成活动的最后一步是准备并启动交付。

### 创建内容并稍后发布 {#creating-content-and-publishing-it-later}

此示例创建一个内容块，并在特定时间延迟后启动文件发布。

![](assets/d_ncs_content_workflow5.png)

第一个内 **容管理任务** ，创建内容实例。

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>必须 **[!UICONTROL Publication]** 在转换模板窗口的选项卡中填充要生成的目标位置。

将添加一个等待活动，以暂停下一个过渡一周。

![](assets/d_ncs_content_workflow7.png)

在此时间段内手动输入内容。

下一个任务将启动内容生成。

![](assets/d_ncs_content_workflow8.png)

要发布的内容是通过传入的过渡输入的。

最后，通过强制发布目录生成此内容。

“ **JavaScript代码** ”活动检索每个生成的文件的完整名称。

![](assets/d_ncs_content_workflow9.png)

### 创建分发及其内容 {#creating-the-delivery-and-its-content}

此示例使用与第一个示例相同的概念，只有它在第一个步骤中创建交付操作。

![](assets/d_ncs_content_workflow10.png)

第一个创 **建分发任务** ，创建分发操作。

fork活动允许您同时启动目标计算和内容实例的创建。

执行任务后，“与加入”框将激活“交付 **** ”任务，以启动先前创建的内容和定位交付。

![](assets/d_ncs_content_workflow11.png)

通过过渡来填充要启动的交付操作。

要传送的目标通过传入事件输入。

传送内容通过传入事件填充。

活动的最终操作是准备和启动交付。

### 从FTP导入内容 {#importing-content-from-ftp}

如果您的分发内容位于FTP或SFTP服务器上的HTML文件中，则可以轻松将此内容加载到Adobe Campaign分发中。 Refer to [this example](../../workflow/using/loading-delivery-content.md).

### 从Amazon Simple Storage Service(S3)连接器导入内容 {#importing-content-from-amazon-simple-storage-service--s3--connector}

如果您的交付内容位于Amazon Simple Storage Service(S3)存储段上，则可以轻松将此内容加载到Adobe Campaign交付中。 Refer to [this example](../../workflow/using/loading-delivery-content.md).

## 半自动更新 {#semi-automatic-update}

可以在“半自动”模式中更新内容数据。 通过URL从XML源中恢复数据。

通过输入表单手动执行数据恢复的激活。

其目的是在表单中 **声明editBtn** **`<input>`** type字段。 该控件包括编辑区域和启动处理的按钮。

编辑区域允许您填充变量数据，这些数据用于构建要检索的数据XML供给的URL。

该按钮执行 **在标签下填充的GetAndTransform** SOAP方 **`<input>`** 法。

表单中的控件声明如下：

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

必 **须在标记的元素下声明** GetAndTransform方 **`<enter>`****`<input>`** 法。 此标签将XML数据从动态构建的表达式中恢复的URL作为参数。 函数的第二个参数是可选的，当传入的XML数据与内容的格式不同时，该参数引用用于中间转换的样式表。

输出将根据在最后一个参数中输入的路径更新内容。

**示例**:为了说明此示例，我们从“cus:book”架构开始。

添加了一个半自动更新编辑控制输入表单：

![](assets/d_ncs_content_exemple9.png)

```
<input label="File name" type="editbtn" xpath="/tmp/@name">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="'https://server/incoming/' + [/tmp/@name] + '.xml'" type="string"/>
      <param exprIn="'xtk:xslt|cus:book-workflow.xsl'" type="string"/>
      <param type="DOMElement" xpathOut="."/>
    </soapCall>
  </enter>
</input>
```

编辑区域允许您输入要检索的文件的名称。 URL是根据此名称构建的，例如：https://server/incomin/data.xml

要检索的数据的格式与工作流自动化示例1中的格式相同。 我们将使用本示例中显示的“cus:book-workflow.xsl”样式表。

作业执行的结果从路径“.”更新内容实例。
