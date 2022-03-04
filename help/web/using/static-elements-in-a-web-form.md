---
product: campaign
title: Web 窗体中的静态元素
description: Web 窗体中的静态元素
feature: Web Forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 3%

---

# Web 窗体中的静态元素{#static-elements-in-a-web-form}

![](../../assets/common.svg)

您可以在表单的页面中包含用户没有交互的元素；这些是静态元素，如图像、HTML内容、水平条或超文本链接。 这些元素是通过工具栏中的第一个按钮通过选择 **[!UICONTROL Static elements]**.

![](assets/s_ncs_admin_survey_add_static_element.png)

提供以下类型的字段：

* 值基于先前提供的答案（在表单的上下文中）或数据库。
* 超文本链接、HTML、水平条。 请参阅 [插入HTML内容](#inserting-html-content).
* 保存在资源库或用户可访问的服务器上的图像。 请参阅 [插入图像](#inserting-images).
* 在客户端和/或服务器端执行的脚本。 它必须使用JavaScript编写，并且与大多数浏览器兼容，以确保在客户端正确执行。

   >[!NOTE]
   >
   >在服务器端，脚本可以使用 [Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans).

## 插入HTML内容 {#inserting-html-content}

您可以在表单页面中包含HTML内容：超文本链接、图像、带格式的段落、视频等。

HTML编辑器允许您输入要插入表单页面的内容。 要打开编辑器，请单击 **[!UICONTROL Static elements]** > **[!UICONTROL HTML]** .

您可以直接输入内容并设置其格式，也可以显示要粘贴到某些外部内容中的源代码窗口。 要切换到“源代码”模式，请单击工具栏中的第一个图标：

![](assets/s_ncs_admin_survey_html_editor.png)

要插入数据库字段，请使用个性化按钮。

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>在HTML编辑器中输入的字符串只有在 **[!UICONTROL Texts]** 子选项卡。 否则，将不会收集这些量度。 有关更多信息，请参阅 [翻译Web窗体](translating-a-web-form.md).

### 插入链接 {#inserting-a-link}

按照以下示例所示，填写编辑窗口中的字段：

要添加超文本链接，请转到 **[!UICONTROL Static elements]** > **[!UICONTROL Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* 的 **[!UICONTROL Label]** 是超文本链接的内容，它将在表单页面上显示。
* 的 **[!UICONTROL URL]** 是所需的地址，例如： [https://www.adobe.com](https://www.adobe.com) 网站，或 [info@adobe.com](mailto:info@adobe.com) 发送消息。
* 的 **[!UICONTROL Window]** 字段中，您可以选择链接的显示模式（对于网站）。 您可以决定在新窗口、当前窗口或其他窗口中打开链接。
* 您可以添加工具提示，如下所示：

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* 您可以选择将链接显示为按钮或图像。 为此，请在 **[!UICONTROL Type]** 字段。

### 链接类型 {#types-of-links}

默认情况下，这些链接与URL类型操作相关联，因此可以在URL字段中输入链接目标地址。

![](assets/s_ncs_admin_survey_link_url.png)

您可以为链接定义其他操作，以便用户单击该链接可执行以下操作：

* 刷新页面

   为此，请选择 **[!UICONTROL Refresh page]** 选项 **[!UICONTROL Action]** 字段。

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* 显示下一页/上一页

   为此，请选择 **[!UICONTROL Next page]** 或 **[!UICONTROL Previous page]** 选项 **[!UICONTROL Action]** 字段。

   ![](assets/s_ncs_admin_survey_link_next.png)

   您可以隐藏 **[!UICONTROL Next]** 和/或 **[!UICONTROL Back]** 按钮（如果它们将被链接替换）。 请参阅 [页面](defining-web-forms-page-sequencing.md).

   该链接将替换 **[!UICONTROL Next]** 按钮。

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* 显示其他页面

   的 **[!UICONTROL Enable a transition]** 选项可显示与 **[!UICONTROL Transition]** 字段。

   ![](assets/s_ncs_admin_survey_link_viral.png)

   默认情况下，页面只有一个输出过渡。 要创建新过渡，请选择页面，然后单击 **[!UICONTROL Add]** 按钮 **[!UICONTROL Output transitions]** 部分，如下所示：

   ![](assets/s_ncs_admin_survey_add_transition.png)

   在图中，此添加项将如下所示：

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >有关Web窗体中页面排序的更多信息，请参阅 [定义Web窗体页面排序](defining-web-forms-page-sequencing.md).

### 个性化HTML内容 {#personalizing-html-content}

您可以使用上一页中记录的数据，将表单页面的HTML内容个性化。 例如，您可以创建一个汽车保险Web窗体，其首页允许您提供联系信息和汽车品牌。

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

使用个性化字段将用户名和密码重新注入到下一页。 要使用的语法取决于信息存储模式。 有关更多信息，请参阅 [使用收集的信息](web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>出于安全原因，在 **`<%=`** 公式将替换为转义字符。

在我们的示例中，收件人的名字和姓氏存储在数据库的字段中，而其汽车品牌存储在变量中。 在第2页上个性化的消息的语法如下所示：

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

这会产生以下结果：

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### 使用文本变量 {#using-text-variables}

的 **[!UICONTROL Text]** 选项卡允许您创建变量字段，这些字段可用于&lt;%=和%>字符之间的HTML，其语法如下： **$（标识符）**.

使用此方法可轻松将字符串本地化。 请参阅 [翻译Web窗体](translating-a-web-form.md)

例如，您可以创建 **联系人** 字段，用于向HTML内容显示“上次联系日期：”字符串。 为此请执行以下操作步骤：

1. 单击 **[!UICONTROL Text]** 选项卡。
1. 单击 **[!UICONTROL Add]** 图标。
1. 在 **[!UICONTROL Identifier]** 列中，输入变量的名称
1. 在 **[!UICONTROL Text]** 列，输入默认值。

   ![](assets/s_ncs_admin_survey_html_text.png)

1. 在HTML内容中，通过 **&lt;%= $（联系人）%>** 语法。

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >如果在HTML编辑器中输入这些字符，则 **&lt;** 和 **>** 字段将替换为其转义字符。 在这种情况下，您需要通过单击 **[!UICONTROL Display source code]** HTML文本编辑器的图标。

1. 打开 **[!UICONTROL Preview]** 用于查看在HTML中输入的值的表单标签：

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

此操作模式允许您仅定义Web窗体文本一次，并使用集成的翻译工具管理翻译。 有关更多信息，请参阅 [翻译Web窗体](translating-a-web-form.md).

## 插入图像 {#inserting-images}

对于要包含在表单中的图像，必须将其保存在可从外部访问的服务器上。

选择 **[!UICONTROL Static elements]** > **[!UICONTROL Image]** 菜单。

选择要插入的图像源：它可以来自公共资源库，也可以存储在外部可访问的外部服务器上。

![](assets/s_ncs_admin_survey_add_img.png)

如果这是库中的图像，请在字段的组合框中选择该图像；如果它位于外部文件中，请输入访问路径。 标签将通过在图像上传递光标(与HTML中的ALT字段一致)来显示，或者当图像未显示时。

可以在编辑器的中央部分查看图像。
