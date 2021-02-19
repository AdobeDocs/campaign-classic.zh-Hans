---
solution: Campaign Classic
product: campaign
title: '"用例：创建内容管理"'
description: '"用例：创建内容管理"'
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 2%

---


# 用例：创建内容管理{#use-case-creating-content-management}

要在Adobe Campaign中创建内容管理，必须执行以下步骤：

* [第1步 — 分析要制作的内容](#step-1---analyzing-the-content-to-be-produced),
* [第2步 — 创建数据模式](#step-2---creating-the-data-schema),
* [第3步 — 创建输入表单](#step-3---creating-the-input-form),
* [第4步 — 创建构造模板](#step-4---creating-the-construction-template),
* [第5步 — 创建发布模板](#step-5---creating-the-publication-template),
* [第6步 — 创建内容](#step-6---creating-contents)。

## 第1步 — 分析要生成的内容{#step-1---analyzing-the-content-to-be-produced}

在开始之前，您需要对要制作的内容进行精确分析:确定要显示的元素，研究与这些元素链接的约束，为每个元素定义类型等。 您还需要区分静态元素和可变客户。

例如，要在HTML中创建包含以下类型内容的新闻稿：

![](assets/s_ncs_content_newsletter.png)

此新闻稿包含三种类型的元素：

1. 变量元素，其内容由用户在创建投放时通过输入表单输入或选择。

   ![](assets/s_ncs_content_define_element_types.png)

1. 个性化字段，根据保存在数据库中的信息(本例中为收件人的名和姓)动态输入。

   ![](assets/s_ncs_content_define_dynamics.png)

1. 静态元素，对于所有Newsletter都是相同的。

   ![](assets/s_ncs_content_define_statics.png)

此Newsletter的各种元素是根据JavaScript模板中定义的规则组合在一起的，该模板引用要插入的所有元素并概念化其布局。

这些元素是通过专用模式创建的，该专用程序为每个内容指定以下元素：名称、标签、类型、大小，以及与Adobe Campaign中处理相关的任何其他信息。

## 第2步 — 创建数据模式{#step-2---creating-the-data-schema}

数据模式是与内容关联的XML文档。 它描述此内容中数据的XML结构。

>[!NOTE]
>
>有关在Adobe Campaign中创建和配置模式的详细信息，请参阅[本节](../../configuration/using/about-schema-edition.md)。
>
>[数据模式](../../delivery/using/data-schemas.md)中详细介绍了特定于内容管理的配置元素。

要创建数据模式，请应用以下步骤：

1. 打开Adobe Campaign资源管理器并选择&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;节点。

   单击位于数据列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

1. 选择&#x200B;**[!UICONTROL Create a schema]**&#x200B;选项进行内容管理，然后单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_ncs_content_create_schema.png)

1. 在相应的字段中输入模式的名称和标签。 您可以根据需要添加描述和链接特定图像。

   ![](assets/s_ncs_content_param_schema.png)

   单击&#x200B;**[!UICONTROL Next]**&#x200B;以验证。

1. 在&#x200B;**[!UICONTROL Edit schema]**&#x200B;窗口中输入模式的内容。

   使用&#x200B;**[!UICONTROL Insert]**&#x200B;按钮创建模式内容。

   ![](assets/s_ncs_content_param_schema_step2.png)

   有关详细信息，请参阅[编辑模式](../../delivery/using/data-schemas.md#editing-schemas)。

   对于内容中引用的每个元素，您需要选择匹配类型。

   在此示例中，标识的内容、其格式和类型为：

<table> 
 <thead> 
  <tr> 
   <th> <strong>内容</strong> <br /> </th> 
   <th> <strong>格式</strong> <br /> </th> 
   <th> <strong>类型</strong> <br /> </th> 
   <th> <strong>标签</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Title<br /> </td> 
   <td> 属性<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> Title<br /> </td> 
  </tr> 
  <tr> 
   <td> 子标题<br /> </td> 
   <td> 属性<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 名称<br /> </td> 
  </tr> 
  <tr> 
   <td> 事件日期<br /> </td> 
   <td> 属性<br /> </td> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
  </tr> 
  <tr> 
   <td> 导言段落<br /> </td> 
   <td> 元素<br /> </td> 
   <td> HTML<br /> </td> 
   <td> 概述<br /> </td> 
  </tr> 
  <tr> 
   <td> 作者的照片<br /> </td> 
   <td> 属性<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> URL<br /> </td> 
  </tr> 
  <tr> 
   <td> 作者<br /> </td> 
   <td> 元素<br /> </td> 
   <td> Memo<br /> </td> 
   <td> 作者<br /> </td> 
  </tr> 
  <tr> 
   <td> 标题标志(存储在Adobe Campaign公共资源中)<br /> </td> 
   <td> 属性<br /> </td> 
   <td> 链接<br /> </td> 
   <td> 图像<br /> </td> 
  </tr> 
 </tbody> 
</table>

模式将包含以下信息：

```
<element label="Invitation" name="invitation" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    <attribute label="Title" length="40" name="title" type="string"/>
    <element label="Presentation" name="presentation" type="html"/>
    <attribute label="Date" name="date" type="date"/>
    <attribute label="Name" length="10" name="name" type="string"/>
    <attribute label="URL" name="url" type="string"/>
    <element label="Author" name="author" type="memo"/>
    <element label="Image" name="image" target="xtk:fileRes" type="link"/>
  </element>
```

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建数据模式。

## 步骤3 — 创建输入表单{#step-3---creating-the-input-form}

通过输入表单，您可以通过Adobe Campaign客户端控制台中的输入界面编辑内容实例。

表单的描述是一个结构化XML文档，它观察“xtk:form”表单模式的语法。

>[!NOTE]
>
>有关在Adobe Campaign中创建和配置表单的详细信息，请参阅[本节](../../configuration/using/identifying-a-form.md)。
>
>[输入表单](../../delivery/using/input-forms.md)中详细介绍了特定于内容管理的配置元素。

要创建用于内容管理的输入表单，请应用以下步骤：

1. 打开Adobe Campaign资源管理器并选择&#x200B;**[!UICONTROL Administration > Configuration > Input forms]**&#x200B;节点。

   单击表单列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

1. 输入表单的名称和链接到表单的标签，然后选择&#x200B;**[!UICONTROL Content management]**&#x200B;类型。

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >要使这两个元素能够自动匹配，我们建议使用与链接数据模式相同的名称。 使用输入区域上方的&#x200B;**[!UICONTROL Insert]**&#x200B;按钮添加链接到表单的模式中的字段。

   ![](assets/s_ncs_content_param_form_edit_step2.png)

1. 在编辑器的中间部分，指定要在输入表单中显示的字段。

   在本例中，我们将提供以下类型的信息：

   ```
    <input xpath="@title"/>
     <input xpath="@date"/>
     <input xpath="presentation"/>
     <input xpath="@name"/>
     <input xpath="@url"/>
     <input xpath="author"/>
     <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
       <sysFilter>
         <condition expr="@isImage = true"/>
       </sysFilter>
     </input>
   ```

   使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡可以在编辑表单时检查其呈现：

   ![](assets/s_ncs_content_param_form_preview.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;创建输入表单。

## 第4步 — 创建构造模板{#step-4---creating-the-construction-template}

使用XSLT语言，可将XML文档转换为另一个输出文档。 此转换在称为样式表的文档的XML中进行说明。

在此示例中，我们希望使用JavaScript模板在生成的文档中定义数据构建和布局模式。

>[!NOTE]
>
>[Formatting](../../delivery/using/formatting.md)中详细介绍了链接到文档构建（JavaScript或XSL模板）的约束。

要在Adobe Campaign中使用JavaScript模板，请应用以下步骤：

1. 打开Adobe Campaign资源管理器并选择&#x200B;**[!UICONTROL Administration > Configuration > JavaScript Templates]**&#x200B;节点。

   单击模板列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

1. 输入模板名称，然后选择您为模式创建的内容管理。
1. 导入要在消息中显示的集内容。

   根据[JavaScript模板](../../delivery/using/formatting.md#javascript-templates)中详细说明的语法添加变量元素。

   要显示示例中显示的内容，JavaScript模板必须包含以下元素：

   ```
   <html>
   <% eval(xtk.javascript.load("xac:perso").data); %>
   <head>
     <title>Invitation to an exceptional dedication session</title>
   </head>
   <body link="#0E59AE" vlink="#0E59AE" alink="#0E59AE" style="background-color:white;">
       <table width="546" border="0" align="center" cellpadding="0" cellspacing="0" style="border-left: solid 1px gray;border-top: solid 1px gray;border-right: solid 1px gray;">
         <tr>
           <td colspan="3">
             <%= generateImgTag(content.@["image-id"]) %>
           </td>
         </tr>
       </table>
       <table width="546" border="0" align="center" cellpadding="0" cellspacing="0" style="border-left: solid 1px gray;border-right: solid 1px gray;">
         <tr>
           <td>
             <table border="0" cellspacing="0" cellpadding="5">
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:2em; padding-bottom:2em;" width="730" align="middle">
                   <b>
                     <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:14px; color:#800080;">
                       <span style="FONT-VARIANT: small-caps"><%= content.@title %> - <%= content.@name %></span>
                     </font>
                   </b>
                 </td>
                 <td width="10"> </td>
               </tr>
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:1em; padding-bottom:1em;" width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                     Hello <%= perso('recipient.firstName') %> <%= perso('recipient.lastName') %>,
                     <p>
                       <%= content.presentation %>
                     </p>               
                     <center>
                       <b><%= formatDate(content.@date, "%2D %Bl %4Y") %></b> come to our Book Fair and meet our favorite authors and illustrators.<br>
                       <br>
                       <a href="https://www.site.web.com/registration" target="_blank"><b>REGISTER</b></a>
                     </center>
                   </font>
                 </td>
                 <td width="10"> </td>
               </tr>
               <tr>
                 <td width="10"> </td>
                 <td style="padding-top:1em; padding-bottom:1em;" width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                    <img style="float:left;margin-right:10px" border="0" src="<%= content.@url %>" width="70" height="70">
                     <b><%= content.author %></b>, will be signing their book between 2
   and 5:30PM.
                   </font>
                 </td>
                 <td width="10"> </td>
               </tr>            
                   <tr>
                 <td width="10"> </td>
                 <td width="730">
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">                  
                 </td>
                 <td width="10"> </td>
               </tr>           
               <tr>
                 <td width="10"> </td>
                 <td>
                   <font style="font-family:Verdana, Arial, Helvetica, sans-serif; font-size:11px; color:#666666;">
                     <center>
                       <p>
                         <a href="https://www.site.web.com/program" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Program</b></span></a>
                          | 
                         <a href="https://www.site.web.com/information" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Useful information</b></span></a>
                          | 
                       <a href="https://www.site.web.com/registration" target="_blank"><span style="FONT-VARIANT: small-caps"><b>Register</b></span></a></p>
                       </center>
                     </font>
                   </td>
                   <td width="10"> </td>
                 </tr>
               </table>
               <br>
             </td>
           </tr>
         </table>
   </body>
   </html>
   ```

   通过在模板开始调用函数，可以设置对从Adobe Campaign数据库获取的个性化数据的调用(在本例中：收件人.firstName和收件人.lastName)，以便在投放中使用时解释它。 有关详细信息，请参阅[包括JavaScript模板](../../delivery/using/formatting.md#including-a-javascript-template)。

   在此示例中，该函数将包含以下代码：

   ```
   function perso(strPerso)
   {
     var strStart = '<' + '%' + '=';
     var strEnd = '%' + '>';
     return strStart + strPerso + strEnd;
   }
     function bloc(strPerso)
   {
     var strStart = '<' + '%' + '@ include view="';
     var strEnd = '" %' + '>';
     return strStart + strPerso + strEnd;
   }
   ```

   要使JavaScript模板有效，必须事先从树结构中的&#x200B;**[!UICONTROL JavaScript codes]**&#x200B;节点创建此函数，如下所示：

   ![](assets/contentmgt_jscode_perso_sample.png)

## 第5步 — 创建发布模板{#step-5---creating-the-publication-template}

下一步包括创建内容发布模板，以链接模式、表单和内容构建模板。 此发布模板可以有多种输出格式。

>[!NOTE]
>
>有关内容发布模板的详细信息，请参阅[发布模板](../../delivery/using/publication-templates.md)。

在此示例中，步骤如下：

1. 通过&#x200B;**[!UICONTROL Administration > Configuration > Publication templates]**&#x200B;节点创建新发布模板。
1. 输入名称和标签，然后选择要使用的模式和表单。
1. 然后输入模板的名称并选择要应用的渲染模式。 此处，我们根据上面创建的模板提供了&#x200B;**[!UICONTROL JavaScript]**&#x200B;类型渲染。

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >默认情况下，**[!UICONTROL DOM interface]**&#x200B;选项处于选中状态，这意味着如果您使用E4X语法，将无法访问此文档。 选中此选项时必须使用DOM接口，并且是推荐的语法。
   >
   >您仍可以使用E4X语法。 如果是，请确保取消选中此选项。

   使用&#x200B;**[!UICONTROL Add]**&#x200B;按钮创建其他转换模板。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建发布模板。

## 第6步 — 创建内容{#step-6---creating-contents}

您现在可以基于此发布模板创建内容。

>[!NOTE]
>
>有关创建内容的详细信息，请参阅[使用内容模板](../../delivery/using/using-a-content-template.md)。

### 在投放向导{#creating-content-in-the-delivery-wizard}中创建内容

要直接在投放中创建内容，请应用以下步骤：

1. 开始，方法是通过投放属性的&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡引用发布模板。

   ![](assets/s_ncs_content_in_delivery.png)

   为了通过投放向导表单定义内容，将向内容管理中添加其他选项卡。

1. 输入新闻稿的变量信息。

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. 单击&#x200B;**[!UICONTROL HTML preview]**&#x200B;选项卡以视图渲染。 您需要选择收件人来测试个性化。

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
