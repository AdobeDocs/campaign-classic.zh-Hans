---
product: campaign
title: “用例：创建内容管理”
description: “用例：创建内容管理”
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: b0d1cf0e-656e-4d24-9a31-16fef4cd40d0
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 2%

---

# 用例：创建内容管理{#use-case-creating-content-management}



要在Adobe Campaign中创建内容管理，需要执行以下步骤：

* [步骤1 — 分析要生成的内容](#step-1---analyzing-the-content-to-be-produced),
* [第2步 — 创建数据架构](#step-2---creating-the-data-schema),
* [第3步 — 创建输入表单](#step-3---creating-the-input-form),
* [第4步 — 创建构建模板](#step-4---creating-the-construction-template),
* [第5步 — 创建发布模板](#step-5---creating-the-publication-template),
* [步骤6 — 创建内容](#step-6---creating-contents).

## 步骤1 — 分析要生成的内容 {#step-1---analyzing-the-content-to-be-produced}

在开始之前，您需要对要生成的内容进行精确分析：识别要显示的元素、研究与这些元素链接的约束、为每个元素定义类型等。 您还需要区分静态元素和变量元素。

例如，要在HTML中创建包含以下内容类型的新闻稿：

![](assets/s_ncs_content_newsletter.png)

此新闻稿包含三种类型的元素：

1. 变量元素，用户在投放创建期间通过输入表单输入或选择其内容。

   ![](assets/s_ncs_content_define_element_types.png)

1. 个性化字段，这些字段是根据数据库中保存的信息（在本例中为收件人的名字和姓氏）动态输入的。

   ![](assets/s_ncs_content_define_dynamics.png)

1. 静态元素，所有新闻稿的这些元素都是相同的。

   ![](assets/s_ncs_content_define_statics.png)

此新闻稿的各个元素都是根据JavaScript模板中定义的规则组合在一起的，该模板引用了要插入的所有元素并概念化了其布局。

这些元素是通过专用架构创建的，该架构为每个内容指定以下元素：名称、标签、类型、大小，以及与其在Adobe Campaign中的处理相关的任何其他信息。

## 第2步 — 创建数据架构 {#step-2---creating-the-data-schema}

数据模式是与内容关联的XML文档。 它描述此内容中数据的XML结构。

>[!NOTE]
>
>有关在Adobe Campaign中创建和配置数据模式的更多信息，请参阅 [此部分](../../configuration/using/about-schema-edition.md).
>
>有关特定于内容管理的配置元素的详细信息，请参阅 [数据模式](data-schemas.md).

要创建数据架构，请应用以下步骤：

1. 打开Adobe Campaign Explorer，然后选择 **[!UICONTROL Administration > Configuration > Data schemas]** 节点。

   单击 **[!UICONTROL New]** 图标。

1. 选择 **[!UICONTROL Create a schema]** 用于内容管理的选项，然后单击 **[!UICONTROL Next]**.

   ![](assets/s_ncs_content_create_schema.png)

1. 在相应的字段中输入架构的名称和标签。 您可以添加描述并链接特定图像（如有必要）。

   ![](assets/s_ncs_content_param_schema.png)

   单击 **[!UICONTROL Next]** 验证。

1. 在 **[!UICONTROL Edit schema]** 窗口。

   使用 **[!UICONTROL Insert]** 按钮以创建架构内容。

   ![](assets/s_ncs_content_param_schema_step2.png)

   有关更多信息，请参阅 [编辑模式](data-schemas.md#editing-schemas).

   对于内容中引用的每个元素，您需要选择一个匹配的类型。

   在本例中，标识的内容、其格式和类型为：

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

1. 单击 **[!UICONTROL Save]** 创建数据模式。

## 第3步 — 创建输入表单 {#step-3---creating-the-input-form}

利用输入表单，可通过Adobe Campaign客户端控制台中的输入界面编辑内容实例。

表单的描述是一个结构化XML文档，它遵循“xtk:form”表单模式的语法。

>[!NOTE]
>
>有关在Adobe Campaign中创建和配置表单的更多信息，请参阅 [此部分](../../configuration/using/identifying-a-form.md).
>
>有关特定于内容管理的配置元素的详细信息，请参阅 [输入表单](input-forms.md).

要创建用于内容管理的输入表单，请应用以下步骤：

1. 打开Adobe Campaign Explorer，然后选择 **[!UICONTROL Administration > Configuration > Input forms]** 节点。

   单击 **[!UICONTROL New]** 图标。

1. 输入表单的名称和链接到表单的标签，然后选择 **[!UICONTROL Content management]** 类型。

   ![](assets/s_ncs_content_param_form_edit.png)

   >[!NOTE]
   >
   >要启用这两个元素自动匹配，我们建议使用与链接数据架构相同的名称。 使用 **[!UICONTROL Insert]** 按钮以添加来自链接到表单的架构的字段。

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

   的 **[!UICONTROL Preview]** 选项卡，用于在编辑表单时检查表单的呈现：

   ![](assets/s_ncs_content_param_form_preview.png)

1. 单击 **[!UICONTROL Save]** 创建输入表单。

## 第4步 — 创建构建模板 {#step-4---creating-the-construction-template}

使用XSLT语言可将XML文档转换为另一输出文档。 此转换在称为样式表的文档中以XML形式描述。

在本例中，我们希望使用JavaScript模板来定义生成文档中的数据构建和布局模式。

>[!NOTE]
>
>链接到文档构建（JavaScript或XSL模板）的约束在 [格式](formatting.md).

要在Adobe Campaign中使用JavaScript模板，请应用以下步骤：

1. 打开Adobe Campaign Explorer，然后选择 **[!UICONTROL Administration > Configuration > JavaScript Templates]** 节点。

   单击 **[!UICONTROL New]** 图标。

1. 输入模板名称，然后选择您为内容管理创建的架构。
1. 导入要在消息中显示的设置内容。

   在遵守 [JavaScript模板](formatting.md#javascript-templates).

   要显示我们的示例中显示的内容，JavaScript模板必须包含以下元素：

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

   通过在模板开始时调用函数，您可以设置对从Adobe Campaign数据库获取的个性化数据的调用(在本例中为：recipient.firstName和recipient.lastName)，以便在投放中使用时可以对其进行解释。 有关更多信息，请参阅 [包含JavaScript模板](formatting.md#including-a-javascript-template).

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

   为了使JavaScript模板有效，必须事先从 **[!UICONTROL JavaScript codes]** 树结构中的节点，如下所示：

   ![](assets/contentmgt_jscode_perso_sample.png)

## 第5步 — 创建发布模板 {#step-5---creating-the-publication-template}

下一步包括创建内容发布模板，以链接架构、表单和内容构建模板。 此发布模板可以具有多种输出格式。

>[!NOTE]
>
>有关内容发布模板的更多信息，请参阅 [发布模板](publication-templates.md).

在本例中，步骤如下：

1. 通过 **[!UICONTROL Administration > Configuration > Publication templates]** 节点。
1. 输入名称和标签，然后选择要使用的架构和表单。
1. 然后输入模板的名称并选择要应用的渲染模式。 这里，我们有 **[!UICONTROL JavaScript]** 根据上面创建的模板类型渲染。

   ![](assets/s_ncs_content_param_form_publish.png)

   >[!NOTE]
   >
   >的 **[!UICONTROL DOM interface]** 默认勾选选项，这意味着如果您使用E4X语法，则无法访问此文档。 选中此选项后，必须使用DOM界面，推荐使用此语法。
   >
   >您仍可以使用E4X语法。 如果是，请确保取消选中此选项。

   使用 **[!UICONTROL Add]** 按钮以创建其他转换模板。

1. 单击 **[!UICONTROL Save]** 创建发布模板。

## 步骤6 — 创建内容 {#step-6---creating-contents}

您现在可以基于此发布模板创建内容。

>[!NOTE]
>
>有关创建内容的更多信息，请参阅 [使用内容模板](using-a-content-template.md).

### 在投放向导中创建内容 {#creating-content-in-the-delivery-wizard}

要直接在投放中创建内容，请应用以下步骤：

1. 首先，通过引用 **[!UICONTROL Advanced]** 选项卡。

   ![](assets/s_ncs_content_in_delivery.png)

   投放向导中添加了额外的选项卡，以便通过内容管理表单定义内容。

1. 输入新闻稿的变量信息。

   ![](assets/s_ncs_content_in_delivery_edition_tab.png)

1. 单击 **[!UICONTROL HTML preview]** 选项卡查看渲染。 您需要选择收件人以测试个性化。

   ![](assets/s_ncs_content_use_in_delivery_preview.png)
