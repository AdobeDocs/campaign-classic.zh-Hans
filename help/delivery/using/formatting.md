---
product: campaign
title: 格式化
description: 格式化
feature: Email Design
exl-id: d9688dc4-20c6-4a9a-990f-465f39b2faa2
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# 格式化{#formatting}

![](../../assets/common.svg)

## JavaScript模板 {#javascript-templates}

JavaScript模板是包含JavaScript代码的HTML或文本文档。 其构建方式与投放操作中的电子邮件内容相同。

### JavaScript模板的标识 {#identification-of-a-javascript-template}

JavaScript模板由其名称和命名空间进行标识，与架构和表单类似。 但是，建议将 **.js** 选项。

### JavaScript模板的结构 {#structure-of-a-javascript-template}

基于“cus:book”架构的JavaScriptHTML格式模板示例：

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

* 合并字段：通过 **`<%= <source> %>`** 语法位置 `<source>`是要显示的数据的源字段。
* 指令块：执行&lt;%和%>标记之间包含的一系列JavaScript指令。

的 **内容** 对象表示输入XML文档的主要元素。

在本例中，下面一行显示了名称簿名的内容：

```
<h1><%= content.@name %></h1>
```

以下代码迭代 `<chapter>` 收藏集元素：

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

内容的属性和元素表示为JavaScript对象，并遵循源文档的结构。

**示例**:

* **内容。@name**:检索主元素的“name”属性的值
* **内容。@`['name']`**:与相同 **内容。@name** 语法
* **content.chapter.length**:返回 `<chapter` 收集元素
* **content.chapter`[0]`.@name**:检索 `<chapter>` 元素
* **chapter.name()**:返回的名称 `<chapter>` 元素
* **chapter.parent()。name()**:返回的父元素的名称 `<chapter>`

>[!CAUTION]
>
>由于“ — ”字符在JavaScript语言中是保留的，因此必须通过 `['<field>']` 语法。
>
>例如： `content.@['offer-id']`.

编程语言（变量、循环、条件测试、函数等）的所有功能。 )可用于构建输出文档。 可访问SOAP API以扩充输出文档。

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

### 包含JavaScript模板 {#including-a-javascript-template}

您可以构成函数或变量库，供日后使用。 为此，请将JavaScript模板导入为 **eval** 函数。 这样，您就可以使用其他JavaScript模板中声明的其他函数来扩充上下文。

**示例**:导入 **common.jsp** 模板。

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### 编辑JavaScript模板 {#editing-a-javascript-template}

编辑区域允许您填充JavaScript模板的内容：

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>必须填充关联的数据模型架构，以初始化JavaScript对象。

要随时生成输出文档的预览，请选择内容和输出格式(HTML、文本、XML)，然后单击 **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>要预览输出文档，无需保存更改。

### 如何创建和使用JavaScript模板的示例 {#example-of-how-to-create-and-use-a-javascript-template}

在下面，您将找到使用JavaScript模板实施以下内容管理所需的配置：

![](assets/d_ncs_content_sample_1.png)

此示例涉及以下步骤：

1. 创建以下架构(在本例中为： **neo:news**):

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

1. 创建链接的 **[!UICONTROL Content management]** 类型表单(**neo:news**)

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

1. 创建JavaScript模板，其中包含HTML和文本格式的消息内容。

   * 在本例中，对于HTML:

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

1. 现在，创建用于两种格式的发布模板：

   * 对于HTML:

      ![](assets/d_ncs_content_sample_2.png)

   * 对于文本：

      ![](assets/d_ncs_content_sample_3.png)

1. 然后，您可以在投放中使用此内容模板。

   有关更多信息，请参阅 [使用内容模板](using-a-content-template.md).

## XSL样式表 {#xsl-stylesheets}

XSLT语言允许将XML文档更改为输出文档。 根据样式表的输出方法，生成的文档可以以HTML、纯文本或其他XML树形式生成。

此转换又以XML形式在称为样式表的文档中详细描述。

### 识别样式表 {#identifying-a-stylesheet}

样式表由其名称和命名空间来标识，就像架构和表单一样。 但是，建议您将 **.xsl** 扩展到样式表的名称。

样式表的标识键是由命名空间和名称以冒号分隔的字符串；例如： **cus:book.xsl**.

### 样式表的结构 {#structure-of-a-stylesheet}

基于示例架构“cus:book”的HTML格式样式表示例：

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

样式表是遵循以下规则的XML文档：

* 属性的值介于引号之间，
* 元素必须具有开始标记和结束标记，
* 将“&lt;”或“&amp;”字符替换为 **&#39;&lt;&#39;** 或 **&#39;&amp;&#39;** 实体，
* 每个XSL元素必须使用 **xsl** 命名空间。

样式表必须以XSL根元素标记开头 **`<xsl:stylesheet>`** 以 **`</xsl:stylesheet>`** 标记。 XSL命名空间必须在开始标记中定义，如下所示：

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

的 **`<xsl:output>`** 元素指定所生成文档的格式。 指定所需的字符集和输出格式。

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

下面的说明描述了用于输出文档格式化的样式表的配置。

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

默认情况下，XSLT处理器会搜索 **模板** 适用于输入XML文档的根或主节点。 输出文档的构建从此开始 **模板**.

在我们的示例中，HTML页面通过显示书籍名称和章节列表从“cus:book”模式生成。

>[!NOTE]
>
>有关XSLT语言的详细信息，请参阅XSLT参考文档。

### 显示HTML/XML {#displaying-html-xml}

显示 **html** 字段，请使用 **disable-output-egine=&quot;yes&quot;** 选项 **`<xsl:value-of>`** 指令。 这样，您就无需将字符替换为其XML实体（例如，将&lt;替换为&lt;）。

的 **`<xsl:text>`** 指令 **disable-output-egine=&quot;yes&quot;** 选项允许您为个性化字段或条件测试插入JavaScript标记。

示例:

* 显示“html”类型字段的内容：

   ```
   <xsl:value-of select="summary" disable-output-escaping="yes"/>
   ```

* 插入个性化字段 **&lt;%= recipient.email %>**:

   ```
   <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
   ```

* 添加条件测试 **&lt;% if(recipient.language == &#39;en&#39;) `{` %>**:

   ```
   <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
   ```

### 包含样式表 {#including-stylesheets}

可以构建要在多个样式表之间共享的模板或变量库。 “longMonth” **模板**&#x200B;上面介绍的是一个典型示例，它说明了将模板远程定位到样式表中以便以后可以重复使用的优点。

的 **`<xsl:include>`** 指令指示要包含在文档中的样式表的名称。

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
>不能在要包含的样式表的引用中输入命名空间的名称。 作为标准，此样式表是使用用户命名空间创建的。

### 编辑样式表 {#editing-a-stylesheet}

编辑区域允许您填充样式表的内容：

![](assets/d_ncs_content_form14.png)

要随时生成输出文档的预览，请选择内容实例和格式(HTML、文本、XML)，然后单击 **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>无需在样式表中保存更改即可查看输出文档预览。

## 映像管理 {#image-management}

### 图像引用 {#image-referencing}

在HTML输出文档中输入的图像可以使用绝对或相对引用进行引用。

相对引用允许您在 **NcmRessourcesDir** 和 **NcmResourcesDirPreview** 选项。 这些选项包含要在Adobe Campaign客户端控制台中发布和预览的图像的位置。

这两个选项可通过 **[!UICONTROL Administration > Platform > Options]** 文件夹。

**示例**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

在样式表处理期间， **_resPath** 根据上下文（预览或发布），输入XML文档主元素上的属性将自动填充一个或多个选项。

有关如何使用图像放置选项及其与图像一起使用的示例：

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>我们建议声明一个变量，其中包含存储图像的服务器引用（我们的示例中为“resPath”）。

### 使用公共资源 {#using-public-resources}

您还可以使用 **[!UICONTROL Public resources]** 声明图像，并根据在部署向导中输入的实例设置，将其上传到服务器。

然后，您可以在内容中调用这些图像。 要实现此目的，请在内容管理架构中使用以下语法：

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
>更多信息 **[!UICONTROL Public resources]** 以及如何配置和使用它们，请参阅 [此部分](../../installation/using/deploying-an-instance.md#managing-public-resources).

## 日期显示 {#date-display}

在XML输入文档中，日期以内部XML格式存储： **YYYY/MM/DD HH:MM:SS** (示例2018/10/01 12:23:30)。

Adobe Campaign为JavaScript模板和XSL样式表提供日期格式设置函数，详见下文。

### JavaScript日期格式 {#javascript-date-formatting}

要以所需的格式显示日期，Adobe Campaign会 **formatDate** 函数，该函数将作为日期内容的输入，并使用以下语法指定输出格式的字符串： **%4Y/%2M/%2D %2H%2N%2S**

示例:

* 在 **31/10/2018** 格式：

   ```
    <%= formatDate(content.@date, "%2D/%2M/%4Y") %>
   ```

* 在 **2018年7月** 格式：

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

XSLT语法中没有标准的日期管理功能。 要以所需格式显示日期，Adobe Campaign提供了外部功能 **date-format**. 此函数将输入日期的内容，并使用以下语法指定输出格式的字符串： **%4Y/%2M/%2D %2H%2N%2S**

示例:

* 在 **01/10/2018** 格式：

   ```
   <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
   ```

* 在 **2018年7月** 格式：

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
