---
title: 格式化
seo-title: 格式化
description: 格式化
seo-description: null
page-status-flag: never-activated
uuid: b6065289-c487-416b-8847-49aa0fb782bf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: d678db05-cc44-4086-98a5-e5296e8e5de8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3b752b283a14bc75954fe46da5a21970c1e17fa1
workflow-type: tm+mt
source-wordcount: '1449'
ht-degree: 0%

---


# 格式化{#formatting}

## JavaScript模板 {#javascript-templates}

JavaScript模板是包含JavaScript代码的HTML或文本文档。 它的构建方式与投放操作中的电子邮件内容相同。

### JavaScript模板的标识 {#identification-of-a-javascript-template}

JavaScript模板由其名称和命名空间进行标识，就像模式和表单一样。 但是，建议将。js选 **项添加** 到模板名称。

### JavaScript模板的结构 {#structure-of-a-javascript-template}

基于“cus:book”模式的JavaScript HTML格式模板示例：

```
<html>
  <body>
    <!-- Title of book -->
    <h1><%= content.@name %></h1>
    <ul>
      <% for each(var chapter in content.chapter) { %>
        <li><%= chapter.@name %></li>
      <% }%>
    </ul>
  </body>
</html>
```

各种JavaScript指令以以下形式显示：

* 合并字段：使用语法显示数据的内 **`<%= <source> %>`** 容， `<source>`其中是要显示的数据的源字段。
* 指令块：执行包含在&lt;%和%>标记之间的一系列JavaScript指令。

内容 **对象** 表示输入XML文档的主要元素。

在我们的示例中，以下行显示名称帐簿名称的内容：

```
<h1><%= content.@name %></h1>
```

以下代码迭代收集 `<chapter>` 元素：

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

内容的属性和元素表示为JavaScript对象，并且与源文档的结构相关。

**示例**:

* **内容。@name**:检索主元素的“name”属性的值
* **内容。@`['name']`**:与内容相 **同。@name** 语法
* **content.chapter.length**:返回集合元素上的元 `<chapter` 素数
* **content.chapter`[0]`。@name**:检索第一个元素的名 `<chapter>` 称
* **chapter.name()**:返回元素的名 `<chapter>` 称
* **chapter.parent()。name()**:返回的父元素的名称 `<chapter>`

>[!CAUTION]
>
>由于“-”字符在JavaScript语言中是保留的，因此必须通过语法恢复包含此字符的任何属性或元素的 `['<field>']` 值。
>
>For example: `content.@['offer-id']`.

编程语言（变量、循环、条件测试、函数等）的全部功能。 )可用于构建输出文档。 SOAP API可用于丰富输出文档。

示例:

* 条件测试：

   ```
   <% if (content.@number == 1 || content.@language == 'en') { %>
   <!-- Content to be displayed if test is true--> 
   <% } %>
   ```

* 函数调用：

   ```
   <!-- Displays a horizontal bar -->
   ;<% function DisplayHorizontalBar() { %>
     <hr/>
   <% } %> 
   
   <!-- The same function in a block  -->
   <% 
   function DisplayHorizontalBar2()
   {
     document.write('<hr/>');
   }
   %> 
   
   <!-- Returns the value in uppercase -->
   <% 
   function formatName(value)
   { 
     return value.toUpperCase(); 
   }
   %>
   
   <!-- Call functions -->
   <%= DisplayHorizontalBar1() %>
   <%= DisplayHorizontalBar2() %>
   <%= formatName(content.@name) %>
   ```

* 声明和变量调用：

   ```
   <%  var counter = 0; %>
   
   <%= counter += 10 %>
   ```

* 使用静态方法检索和显示收件人名称：

   ```
   <% var recipient = nms.recipient.get(1246); %>
   <%= recipient.lastName %>
   ```

* 使用非静态方法恢复和显示收件人名称：

   ```
   <% var query = xtk.queryDef.create(
     <queryDef schema="nms:recipient" operation="get">
       <select>
         <node expr="@lastName"/>
       </select>
       <where>
         <condition expr="@id=1246"/>
       </where>
     </queryDef>);
   
     var recipient = query.ExecuteQuery();
   %>
   
   <%= recipient.@lastName %>
   ```

### 包括JavaScript模板 {#including-a-javascript-template}

您可以构成函数或变量库供以后使用。 为此，请导入带eval函数的JavaScript **模板** 。 这样，您就可以使用其他JavaScript模板中声明的其他函数丰富上下文。

**示例**:导入 **common.jsp** 模板。

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### 编辑JavaScript模板 {#editing-a-javascript-template}

通过编辑区域，可以填充JavaScript模板的内容：

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>必须填充关联的数据模型模式，以初始化JavaScript对象。

要随时生成输出预览的文档，请选择内容和输出格式（HTML、文本、XML），然后单击 **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>不必保存更改即可预览输出文档。

### 如何创建和使用JavaScript模板的示例 {#example-of-how-to-create-and-use-a-javascript-template}

在下面，您将找到使用JavaScript模板实现以下内容管理所需的配置：

![](assets/d_ncs_content_sample_1.png)

此示例涉及以下步骤：

1. 创建以下模式(在本例中为： **neo:news**):

   ```
   <srcSchema _cs="Invitation (neo)"   entitySchema="xtk:srcSchema" img="xtk:schema.png" label="Invitation" mappingType="sql" name="news" namespace="neo" xtkschema="xtk:srcSchema">
   
     <enumeration basetype="string" default="en" name="language">
       <value label="Français" name="fr" value="fr"/>
       <value label="English" name="gb" value="gb"/>
     </enumeration>
   
     <enumeration basetype="string" name="css">
       <value label="Blue" name="bl" value="blue"/>
       <value label="Orange" name="or" value="orange"/>
     </enumeration>
   
     <element label="Intervenants" name="attendee">
       <key internal="true" name="id">
         <keyfield xpath="@id"/>
       </key>
       <attribute label="Name" name="name" type="string"/>
       <element label="Image" name="image" target="xtk:fileRes" type="link"/>
       <attribute label="Description" name="description" type="string"/>
       <attribute default="Gid()" label="Id" name="id" type="long"/>
     </element>
   
     <element label="Invitation" name="news" template="ncm:content" xmlChildren="true">
   
       <compute-string expr="@name"/>
       <attribute enum="language" label="Language" name="language" type="string"/>
       <attribute enum="css" label="Stylesheet" name="css" type="string"/>
       <attribute label="Title" name="title" type="string"/>
       <element label="Presentation" name="presentation" type="html"/>
       <attribute label="Date" name="date" type="date"/>
       <element label="Attendees list" name="attendeesList" ordered="true" ref="attendee" unbound="true"/>
   
     </element>
   </srcSchema>
   ```

1. 创建链接 **[!UICONTROL Content management]** 的类型表&#x200B;**单(neo:news**)

   ```
   <form _cs="News (neo)" entitySchema="xtk:form"  img="xtk:form.png" label="News"  name="news" namespace="neo" type="contentForm" xtkschema="xtk:form">
   
     <container type="iconbox">
       <container label="Invitation">
         <input xpath="@langue"/>
         <input xpath="@css"/>
         <input xpath="@title"/>
         <input xpath="@date"/>
         <input xpath="presentation"/>
       </container>
   
       <container label="Intervenants">
         <container toolbarCaption="Liste des intervenants" type="notebooklist" xpath="attendeesList" xpath-label="@nom">
           <container>
             <input xpath="@nom"/>
             <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
               <sysFilter>
                 <condition expr="@isImage = true"/>
               </sysFilter>
             </input>
             <input xpath="@description"/>
           </container>
         </container>
       </container>
     </container>
   
   </form>
   ```

1. 使用HTML和文本格式的消息内容创建JavaScript模板。

   * 在我们的示例中，对于HTML:

      ```
      <html>     
        <head>         
          <title>Newsletter</title>
           <style type="text/css">
            .body {font-family:Verdana, Arial, Helvetica, sans-serif; font-size:10px; color:#514c48; margin-left: auto; margin-right: auto;}
            .body table {width:748; border: solid 1px; cellpadding:0; cellspacing:0"}
           </style>
        </head>     
        <body>
          <p><center><%= mirrorPage %></center></p>
          <center>
            <table>      
             <tr>
              <td>                                                         
                <img src="[LOGO]"/>                                   
              </td>
              <td>
                <h1><%= content.@title %></h1>
              </td>
             </tr>
             <tr>
      
             <td>
              <div >                                    
                <h0><%= hello,</h0>                              
                <p><%= content.presentation %></p>                                          
      
                <h0>Useful information</h0>                              
                <p>                                  
                  <img src="[IMAGE 1]"/>When? <br/><%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.</p><br/>                                       
                <p>                                  
                  <img src="[IMAGE 2]"/>Who? <br>Meet our favorite authors and illustrators and get a signed copy of their book.</p><br/>                                                         
                <p>                                  
                  <img src="[IMAGE 3]"/>Attendance is free but there is a limited number of seats: sign up now!</p>
            </div>
            </td>
      
              <td>                                                    
               <div style="text-align:left; width:210; height:400px; background:url([IMAGE DE FOND])">
      
                  <h0><%= participant %></h0>
                  <%
                  var i
                  var iLength = content.attendeesList.length()
                  for (i=0; i<iLength; i++)
                  { %>
                  <p>
                    <%= generateImgTag(content.attendeesList[i].@["image-id"]) %>  <%= content.attendeesList[i].@description %>
                  </p>  
                  <% }  
                  %>                              
               </div2>
              </td>
          </tr>
        </table>
      </center>
      </body>    
      </html>
      ```

   * 对于文本：

      ```
      <%= content.@title %>
      <%= content.presentation %>
      
      *** When? On <%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.
      
      *** Who? Come and meet our favorite authors and illustrators and get a signed copy of their books. 
      
      *** Attendance is free but there is a limited number of seats: sign up now!
      
      Guests:
      ******************
      <%
      var i
      var iLength = content.attendeesList.length()
      //for (i=(iLength-1); i>-1; i--)
      for( i=0 ; i<iLength ; i++ )
        { %>
        Description <%= i %> : <%= content.attendeesList[i].@description %>
        <% }  
      %>
      ```

1. 现在创建用于两种格式的发布模板:

   * 对于HTML:

      ![](assets/d_ncs_content_sample_2.png)

   * 对于文本：

      ![](assets/d_ncs_content_sample_3.png)

1. 然后，您可以在投放中使用此内容模板。

   有关此内容的详细信息，请 [参阅使用内容模板](../../delivery/using/using-a-content-template.md)。

## XSL样式表 {#xsl-stylesheets}

XSLT语言允许您将XML文档更改为输出文档。 根据样式表的输出方法，可以在HTML、纯文本或其他XML树中生成结果文档。

此转换在XML中在称为样式表的文档中详细介绍。

### 标识样式表 {#identifying-a-stylesheet}

样式表由其名称和命名空间来标识，就像模式和表单一样。 但是，建议将。xsl扩 **展名** 添加到样式表的名称。

样式表的标识键是由命名空间和冒号分隔的名称组成的字符串；例如： **cus:book.xsl**。

### 样式表的结构 {#structure-of-a-stylesheet}

基于示例模式“cus:book”的HTML格式样式表示例：

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>
  <!-- Point of entry of the stylesheet -->
  <xsl:template match="/book">
    <html>
      <body>
        <!-- Book title -->
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <!-- List of chapters -->
          <xsl:for-each select="child::chapter">
            <li><xsl:value-of select="@name"/></li>
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

样式表是遵循以下规则的XML文档:

* 属性值在引号之间，
* 元素必须具有开始标记和结束标记，
* 将“&lt;”或“&amp;”字符替 **换为“** ” **或“&amp;** ”实体，
* 每个XSL元素都必须使用 **xsl** 命名空间。

样式表必须开始XSL根元素标 **`<xsl:stylesheet>`** 记，以标记结 **`</xsl:stylesheet>`** 尾。 XSL命名空间必须在开始标记中定义，如下所示：

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

元 **`<xsl:output>`** 素指定生成的文档的格式。 指定所需的字符集和输出格式。

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

以下说明描述了为输出文档的格式配置样式表。

```
<xsl:template match="/book">
  <html>
    <body>
      <!-- Book title -->
      <h1><xsl:value-of select="@name"/></h1>
      <lu>
        <!-- List of chapters -->
        <xsl:for-each select="child::chapter">
          <li><xsl:value-of select="@name"/></li>
        </xsl:for-each>
      </lu>
    </body>
  </html>
</xsl:template>
```

默认情况下，XSLT处理器会 **搜索** 应用于输入XML文档的根节点或主节点的模板。 输出文档的构建从此模板开 **始**。

在我们的示例中，通过显示书名和章节的列表，从“cus:book”模式生成HTML页面。

>[!NOTE]
>
>有关XSLT语言的详细信息，请参阅XSLT参考文档。

### 显示HTML/XML {#displaying-html-xml}

要显示 **html** 字段，请使 **用指令中的disable-output-esceing=** &quot;yes&quot; **`<xsl:value-of>`** 选项。 这样，您就避免用字符的XML实体替换字符（例如&lt;和&lt;）。

使用 **`<xsl:text>`** disable-output- **esceing=&quot;yes&quot;选项的指令** ，可以为个性化字段或条件测试插入JavaScript标签。

示例:

* 显示“html”类型字段的内容：

   ```
   <xsl:value-of select="summary" disable-output-escaping="yes"/>
   ```

* 插入个性化 **字段&lt;%=收件人.email %>**:

   ```
   <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
   ```

* 添加条件测 **试&lt;% if(收件人.language == &#39;en&#39;)`{`%>**:

   ```
   <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
   ```

### 包括样式表 {#including-stylesheets}

可以构建要在多个样式表之间共享的模板或变量库。 上面显示 **的**“longMonth”模板是一个典型的示例，其优点是在样式表中远程定位模板，以便以后可以重用它。

指 **`<xsl:include>`** 令指示要包含在文档中的样式表的名称。

**示例**:包括“common.xsl”样式表。

```
<? xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:include href="common.xsl"/> 
  <xsl:output encoding="ISO-8859-1" method="jsp" indent="yes"/>
  ...
</xsl:stylesheet>
```

>[!NOTE]
>
>不得在要包含的样式表引用中输入命名空间的名称。 作为标准，此样式表是使用用户命名空间创建的。

### 编辑样式表 {#editing-a-stylesheet}

通过编辑区域，您可以填充样式表的内容：

![](assets/d_ncs_content_form14.png)

要随时生成输出预览的文档，请选择内容实例和格式（HTML、文本、XML），然后单击 **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>无需在样式表中保存更改来视图输出文档预览。

## 图像管理 {#image-management}

### 图像引用 {#image-referencing}

在HTML输出文档中输入的图像可以使用绝对或相对引用进行引用。

相对引用允许您在NcmRessourcesDir和NcmRessourcesDirPreview选项中输 **入包含图像** 的服 **务器的URL** 。 这些选项包含要在Adobe Campaign客户端控制台中发布和预览的图像的位置。

这两个选项可通过文件夹中的选项管理屏幕 **[!UICONTROL Administration > Platform > Options]** 访问。

**示例**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

在样式表处理 **过程中** ，输入XML文档的主元素上的_resPath属性会根据上下文(预览或发布)自动填充一个或其他选项。

如何使用图像放置选项及其与图像一起使用的示例：

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>我们建议声明一个变量，其中包含存储图像的服务器的引用（本例中为“resPath”）。

### 使用公共资源 {#using-public-resources}

您还可以根据 **[!UICONTROL Public resources]** 在部署向导中输入的实例设置，使用声明图像并将其上传到服务器。

然后，可以在内容中调用这些图像。 为此，请在内容管理模式中使用以下语法：

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

在表单中，将通过以下语法添加用于选择图像的字段：

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>有关配置和 **[!UICONTROL Public resources]** 如何使用它们的详细信息，请参 [阅本节](../../installation/using/deploying-an-instance.md#managing-public-resources)。

## 日期显示 {#date-display}

在XML输入文档中，日期以内部XML格式存储： **YYYY/MM/DD HH:MM:SS** （示例2018/10/01 12:23:30）。

Adobe Campaign为JavaScript模板和XSL样式表提供日期格式化功能，详见下文。

### JavaScript日期格式 {#javascript-date-formatting}

要以所需格式显示日期，Adobe Campaign提 **供** formatDate函数，该函数将输入日期的内容，并提供一个字符串，该字符串使用以下语法指定输出格式： **%4Y/%2M/%2D %2H%2N%2S**

示例:

* 以31/10/2018 **格式显示日期** :

   ```
    <%= formatDate(content.@date, "%2D/%2M/%4Y") %>
   ```

* 以2018年7月格 **式显示日** 期：

   ```
   <%
    function displayDate(date)
     {
       var aMonth = 
       [ 'January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December' ];
   
       var month = formatDate(content.@date, "%2M")
       var year = formatDate(content.@date, "%4Y")
   
       return aMonth[month-1]+" "+year;
     }
   %>
   
   <%= displayDate(content.@date) %>
   ```

### XSL日期格式 {#xsl-date-formatting}

XSLT语法中没有标准的日期管理功能。 要以所需格式显示日期，Adobe Campaign提供外部函 **数date-format**。 此函数将日期的内容作为输入，并使用以下语法指定输出格式的字符串： **%4Y/%2M/%2D %2H%2N%2S**

示例:

* 要以01/10/2018 **格式显示日期** :

   ```
   <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
   ```

* 要以2018年7月格 **式显示日期** :

   ```
   <!-- Returns the month in the form of a string with the month number as input -->
   <xsl:template name="longMonth">
     <xsl:param name="monthNumber"/>
   
     <xsl:choose>
       <xsl:when test="$monthNumber = 1">January</xsl:when>
       <xsl:when test="$monthNumber = 2">February</xsl:when>
       <xsl:when test="$monthNumber = 3">March</xsl:when>
       <xsl:when test="$monthNumber = 4">April</xsl:when>
       <xsl:when test="$monthNumber = 5">May</xsl:when>
       <xsl:when test="$monthNumber = 6">June</xsl:when>
       <xsl:when test="$monthNumber = 7">July</xsl:when>
       <xsl:when test="$monthNumber = 8">August</xsl:when>
       <xsl:when test="$monthNumber = 9">September</xsl:when>
       <xsl:when test="$monthNumber = 10">October</xsl:when>
       <xsl:when test="$monthNumber = 11">November</xsl:when>
       <xsl:when test="$monthNumber = 12">December</xsl:when>
     </xsl:choose>
   </xsl:template> 
   
   <!-- Display date -->
   <xsl:call-template name="longMonth">
     <xsl:with-param name="monthNumber">
       <xsl:value-of select="external:date-format(@date, '%2M')"/>
     </xsl:with-param>
   </xsl:call-template>
    <xsl:value-of select="external:date-format(@date, '%4y')"/>
   ```
