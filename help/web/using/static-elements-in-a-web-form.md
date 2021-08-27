---
product: campaign
title: Web 窗体中的静态元素
description: Web 窗体中的静态元素
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 3%

---

# Web 窗体中的静态元素{#static-elements-in-a-web-form}

![](../../assets/common.svg)

您可以在表单的页面中包含用户没有交互的元素；这些是静态元素，如图像、HTML内容、水平条或超文本链接。 通过选择&#x200B;**[!UICONTROL Static elements]**，可通过工具栏中的第一个按钮创建这些元素。

![](assets/s_ncs_admin_survey_add_static_element.png)

提供以下类型的字段：

* 值基于先前提供的答案（在表单的上下文中）或数据库。
* 超文本链接、HTML、水平条。 请参阅[插入HTML内容](#inserting-html-content)。
* 保存在资源库或用户可访问的服务器上的图像。 请参阅[插入图像](#inserting-images)。
* 在客户端和/或服务器端执行的脚本。 它必须使用JavaScript编写，并且与大多数浏览器兼容，以确保在客户端正确执行。

   >[!NOTE]
   >
   >在服务器端，脚本可以使用[Campaign JSAPI文档](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)中定义的函数。

## 插入HTML内容 {#inserting-html-content}

您可以在表单页面中包含HTML内容：超文本链接、图像、带格式的段落、视频等。

HTML编辑器允许您输入要插入表单页面的内容。 要打开编辑器，请单击&#x200B;**[!UICONTROL Static elements]** > **[!UICONTROL HTML]** 。

您可以直接输入内容并设置其格式，也可以显示要粘贴到某些外部内容中的源代码窗口。 要切换到“源代码”模式，请单击工具栏中的第一个图标：

![](assets/s_ncs_admin_survey_html_editor.png)

要插入数据库字段，请使用个性化按钮。

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>只有在&#x200B;**[!UICONTROL Texts]**&#x200B;子选项卡中定义了在HTML编辑器中输入的字符串时，才会进行翻译。 否则，将不会收集这些量度。 有关更多信息，请参阅[翻译Web窗体](translating-a-web-form.md)。

### 插入链接 {#inserting-a-link}

按照以下示例所示，填写编辑窗口中的字段：

要添加超文本链接，请转到&#x200B;**[!UICONTROL Static elements]** > **[!UICONTROL Link]**。

![](assets/s_ncs_admin_survey_add_link.png)

* **[!UICONTROL Label]**&#x200B;是超文本链接的内容，它将显示在表单页面上。
* **[!UICONTROL URL]**&#x200B;是所需的地址，例如：[https://www.adobe.com](https://www.adobe.com)（网站）或[info@adobe.com](mailto:info@adobe.com)（网站）发送消息。
* 利用&#x200B;**[!UICONTROL Window]**&#x200B;字段，可选择站点中链接的显示模式。 您可以决定在新窗口、当前窗口或其他窗口中打开链接。
* 您可以添加工具提示，如下所示：

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* 您可以选择将链接显示为按钮或图像。 为此，请在&#x200B;**[!UICONTROL Type]**&#x200B;字段中选择显示类型。

### 链接类型 {#types-of-links}

默认情况下，这些链接与URL类型操作相关联，因此可以在URL字段中输入链接目标地址。

![](assets/s_ncs_admin_survey_link_url.png)

您可以为链接定义其他操作，以便用户单击该链接可执行以下操作：

* 刷新页面

   要执行此操作，请在&#x200B;**[!UICONTROL Action]**&#x200B;字段的下拉框中选择&#x200B;**[!UICONTROL Refresh page]**&#x200B;选项。

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* 显示下一页/上一页

   要执行此操作，请在&#x200B;**[!UICONTROL Action]**&#x200B;字段的下拉框中选择&#x200B;**[!UICONTROL Next page]**&#x200B;或&#x200B;**[!UICONTROL Previous page]**&#x200B;选项。

   ![](assets/s_ncs_admin_survey_link_next.png)

   如果&#x200B;**[!UICONTROL Next]**&#x200B;和/或&#x200B;**[!UICONTROL Back]**&#x200B;按钮要替换为链接，则可以隐藏它们。 请参见此[页面](defining-web-forms-page-sequencing.md)。

   该链接将替换默认使用的&#x200B;**[!UICONTROL Next]**&#x200B;按钮。

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* 显示其他页面

   使用&#x200B;**[!UICONTROL Enable a transition]**&#x200B;选项可显示与在&#x200B;**[!UICONTROL Transition]**&#x200B;字段中选择的传出过渡相关联的特定页面。

   ![](assets/s_ncs_admin_survey_link_viral.png)

   默认情况下，页面只有一个输出过渡。 要创建新过渡，请选择页面，然后单击&#x200B;**[!UICONTROL Output transitions]**&#x200B;部分中的&#x200B;**[!UICONTROL Add]**&#x200B;按钮，如下所示：

   ![](assets/s_ncs_admin_survey_add_transition.png)

   在图中，此添加项将如下所示：

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >有关Web窗体中页面排序的更多信息，请参阅[定义Web窗体页面排序](defining-web-forms-page-sequencing.md)。

### 个性化HTML内容 {#personalizing-html-content}

您可以使用上一页记录的数据，将表单页面的HTML内容个性化。 例如，您可以创建一个汽车保险Web窗体，其首页允许您提供联系信息和汽车品牌。

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

使用个性化字段将用户名和密码重新注入到下一页。 要使用的语法取决于信息存储模式。 有关更多信息，请参阅[使用收集的信息](web-forms-answers.md#using-collected-information)。

>[!NOTE]
>
>出于安全考虑，在&#x200B;**`<%=`**&#x200B;公式中输入的值将替换为转义字符。

在我们的示例中，收件人的名字和姓氏存储在数据库的字段中，而其汽车品牌存储在变量中。 在第2页上个性化的消息的语法如下：

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

这会产生以下结果：

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### 使用文本变量 {#using-text-variables}

通过&#x200B;**[!UICONTROL Text]**&#x200B;选项卡，可以创建变量字段，这些字段可在HTML中使用以下语法：**$(IDENTIFIER)**。

使用此方法可轻松将字符串本地化。 请参阅[翻译Web窗体](translating-a-web-form.md)

例如，您可以创建一个&#x200B;**Contact**&#x200B;字段，以便在HTML内容中显示“上次联系日期：”字符串。 为此请执行以下操作步骤：

1. 单击HTML文本的&#x200B;**[!UICONTROL Text]**&#x200B;选项卡。
1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;图标。
1. 在&#x200B;**[!UICONTROL Identifier]**&#x200B;列中，输入变量的名称
1. 在&#x200B;**[!UICONTROL Text]**&#x200B;列中，输入默认值。

   ![](assets/s_ncs_admin_survey_html_text.png)

1. 在HTML内容中，通过&#x200B;**&lt;%= $（联系人）%>**&#x200B;语法插入此文本变量。

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >如果在HTML编辑器中输入这些字符，则&#x200B;****&#x200B;和&#x200B;**>**&#x200B;字段将替换为其转义字符。 在这种情况下，您需要通过单击HTML文本编辑器的&#x200B;**[!UICONTROL Display source code]**&#x200B;图标来更正源代码。

1. 打开表单的&#x200B;**[!UICONTROL Preview]**&#x200B;标签以查看在HTML中输入的值：

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

此操作模式允许您仅定义Web窗体文本一次，并使用集成的翻译工具管理翻译。 有关更多信息，请参阅[翻译Web窗体](translating-a-web-form.md)。

## 插入图像 {#inserting-images}

对于要包含在表单中的图像，必须将其保存在可从外部访问的服务器上。

选择&#x200B;**[!UICONTROL Static elements]** > **[!UICONTROL Image]**&#x200B;菜单。

选择要插入的图像源：它可以来自公共资源库，也可以存储在外部可访问的外部服务器上。

![](assets/s_ncs_admin_survey_add_img.png)

如果这是库中的图像，请在字段的组合框中选择该图像；如果它位于外部文件中，请输入访问路径。 标签将通过在图像上传递光标来显示（与HTML中的ALT字段一致），或者在图像未显示时显示。

可以在编辑器的中央部分查看图像。
