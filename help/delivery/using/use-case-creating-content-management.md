---
product: campaign
title: "用例：创建内容管理"
description: "用例：创建内容管理"
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Delivery Templates
exl-id: b0d1cf0e-656e-4d24-9a31-16fef4cd40d0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---

# 用例：创建内容管理{#use-case-creating-content-management}



要在Adobe Campaign中创建内容管理，必须执行以下步骤：

* [步骤1 — 分析要生成的内容](#step-1---analyzing-the-content-to-be-produced)，
* [步骤2 — 创建数据架构](#step-2---creating-the-data-schema)，
* [步骤3 — 创建输入表单](#step-3---creating-the-input-form)，
* [步骤4 — 创建构造模板](#step-4---creating-the-construction-template)，
* [步骤5 — 创建发布模板](#step-5---creating-the-publication-template)，
* [步骤6 — 创建内容](#step-6---creating-contents)。

## 步骤1 — 分析要生成的内容 {#step-1---analyzing-the-content-to-be-produced}

在开始之前，您需要对要生成的内容进行精确分析：标识要显示的元素，研究与其关联的约束，为每个元素定义类型等。 您还需要区分静态元素和变量元素。

例如，创建包含以下内容类型的新闻稿HTML：

![](assets/s_ncs_content_newsletter.png)

此新闻稿包含三种类型的元素：

1. 变量元素，其内容由用户在投放创建期间通过输入表单输入或选择。

   ![](assets/s_ncs_content_define_element_types.png)

1. 根据数据库中保存的信息（在此例中是收件人的名字和姓氏）动态输入的个性化字段。

   ![](assets/s_ncs_content_define_dynamics.png)

1. 静态元素，这些元素对于所有新闻稿都相同。

   ![](assets/s_ncs_content_define_statics.png)

本新闻稿的各种元素是根据在JavaScript模板中定义的规则组合在一起的，该模板引用了要插入的所有元素并概念化了其布局。

这些元素通过专用架构创建，专用架构为每个内容指定以下元素：名称、标签、类型、大小以及与在Adobe Campaign中处理内容相关的任何其他信息。

## 步骤2 — 创建数据架构 {#step-2---creating-the-data-schema}

数据架构是与内容关联的XML文档。 它描述了此内容中数据的XML结构。

>[!NOTE]
>
>有关在Adobe Campaign中创建和配置数据架构的更多信息，请参阅[此部分](../../configuration/using/about-schema-edition.md)。
>
>在[数据架构](data-schemas.md)中详细列出了特定于内容管理的配置元素。

要创建数据架构，请应用以下步骤：

1. 打开Adobe Campaign Explorer并选择&#x200B;**[!UICONTROL Administration > Configuration > Data schemas]**&#x200B;节点。

   单击位于数据架构列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

1. 为内容管理选择&#x200B;**[!UICONTROL Create a schema]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_ncs_content_create_schema.png)

1. 在相应的字段中输入架构的名称和标签。 您可以添加描述，并在必要时链接特定图像。

   ![](assets/s_ncs_content_param_schema.png)

   单击&#x200B;**[!UICONTROL Next]**&#x200B;进行验证。

1. 在&#x200B;**[!UICONTROL Edit schema]**&#x200B;窗口中输入架构的内容。

   使用&#x200B;**[!UICONTROL Insert]**&#x200B;按钮创建架构内容。

   ![](assets/s_ncs_content_param_schema_step2.png)

   有关详细信息，请参阅[编辑架构](data-schemas.md#editing-schemas)。

   对于内容中引用的每个元素，您需要选择匹配类型。

   在此示例中，标识的内容、格式和类型包括：

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
   <td> 标题<br /> </td> 
   <td> 属性<br /> </td> 
   <td> 字符串<br /> </td> 
   <td> 标题<br /> </td> 
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
   <td> 简介段落<br /> </td> 
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
   <td> 备忘录<br /> </td> 
   <td> 作者<br /> </td> 
  </tr> 
  <tr> 
   <td> 标题徽标(存储在Adobe Campaign公共资源中)<br /> </td> 
   <td> 属性<br /> </td> 
   <td> 链接<br /> </td> 
   <td> 图像<br /> </td> 
  </tr> 
 </tbody> 
</table>

架构将包含以下信息：

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

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建数据架构。

## 第3步 — 创建输入表单 {#step-3---creating-the-input-form}

输入表单允许您通过Adobe Campaign客户端控制台中的输入界面编辑内容实例。

表单的描述是一种结构化XML文档，遵循“xtk：form”表单架构的语法。

>[!NOTE]
>
>有关在Adobe Campaign中创建和配置表单的更多信息，请参阅[此章节](../../configuration/using/identifying-a-form.md)。
>
>在[输入表单](input-forms.md)中详细列出了特定于内容管理的配置元素。

要创建内容管理的输入表单，请应用以下步骤：

1. 打开Adobe Campaign Explorer并选择&#x200B;**[!UICONTROL Administration > Configuration > Input forms]**&#x200B;节点。

   单击表单列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

1. 输入表单的名称和链接到表单的标签，然后选择&#x200B;**[!UICONTROL Content management]**&#x200B;类型。

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >要使这两个元素自动匹配，我们建议使用与链接数据架构相同的名称。 使用输入区域上方的&#x200B;**[!UICONTROL Insert]**&#x200B;按钮从链接到表单的架构添加字段。

   ![](assets/s_ncs_content_param_form_edit_step2.png)

1. 在编辑器的中间部分，指定要显示在输入表单中的字段。

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

   **[!UICONTROL Preview]**&#x200B;选项卡允许您在编辑表单时检查表单的渲染：

   ![](assets/s_ncs_content_param_form_preview.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建输入表单。

## 第4步 — 创建构造模板 {#step-4---creating-the-construction-template}

使用XSLT语言可以将XML文档转换为另一个输出文档。 在称为样式表的文档中，此转换以XML形式描述。

在本例中，我们希望使用JavaScript模板来定义所生成文档中的数据结构和布局模式。

>[!NOTE]
>
>[格式](formatting.md)中详细介绍了链接到文档生成(JavaScript或XSL模板)的约束。

要在Adobe Campaign中使用JavaScript模板，请应用以下步骤：

1. 打开Adobe Campaign Explorer并选择&#x200B;**[!UICONTROL Administration > Configuration > JavaScript Templates]**&#x200B;节点。

   单击模板列表上方的&#x200B;**[!UICONTROL New]**&#x200B;图标。

1. 输入模板名称并选择为内容管理创建的方案。
1. 导入要在消息中显示的设置内容。

   添加变量元素，同时遵循[JavaScript模板](formatting.md#javascript-templates)中详述的语法。

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

   通过在模板的开头调用函数，您可以设置对从Adobe Campaign数据库中获取的个性化数据的调用（在本例中为：recipient.firstName和recipient.lastName），以便在投放中使用数据时进行解释。 有关详细信息，请参阅[包含JavaScript模板](formatting.md#including-a-javascript-template)。

   在此示例中，函数将包含以下代码：

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

   为了使JavaScript模板有效，必须预先从树结构中的&#x200B;**[!UICONTROL JavaScript codes]**&#x200B;节点创建此函数，如下所示：

   ![](assets/contentmgt_jscode_perso_sample.png)

## 步骤5 — 创建发布模板 {#step-5---creating-the-publication-template}

下一步涉及创建内容发布模板以链接架构、表单和内容构建模板。 此发布模板可以有多种输出格式。

>[!NOTE]
>
>有关内容发布模板的详细信息，请参阅[发布模板](publication-templates.md)。

在此示例中，步骤如下：

1. 通过&#x200B;**[!UICONTROL Administration > Configuration > Publication templates]**&#x200B;节点创建新的发布模板。
1. 输入名称和标签，然后选择要使用的架构和表单。
1. 然后输入模板的名称，并选择要应用的渲染模式。 在这里，我们根据上面创建的模板呈现了&#x200B;**[!UICONTROL JavaScript]**&#x200B;类型。

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >默认情况下，**[!UICONTROL DOM interface]**&#x200B;选项处于选中状态，这意味着如果您使用E4X语法，将无法访问此文档。 选中此选项后，必须使用DOM接口，这是推荐的语法。
   >
   >您仍然可以使用E4X语法。 如果是这样，请确保取消选中此选项。

   使用&#x200B;**[!UICONTROL Add]**&#x200B;按钮创建其他转换模板。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建发布模板。

## 步骤6 — 创建内容 {#step-6---creating-contents}

您现在可以基于此发布模板创建内容。

>[!NOTE]
>
>有关创建内容的详细信息，请参阅[使用内容模板](using-a-content-template.md)。

### 在投放向导中创建内容 {#creating-content-in-the-delivery-wizard}

要直接在投放中创建内容，请应用以下步骤：

1. 首先，通过投放属性的&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡引用发布模板。

   ![](assets/s_ncs_content_in_delivery.png)

   向投放向导中添加了一个附加选项卡，以便通过内容管理表单定义内容。

1. 输入新闻稿的变量信息。

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. 单击&#x200B;**[!UICONTROL HTML preview]**&#x200B;选项卡以查看渲染。 您需要选择一个收件人以测试个性化。

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
