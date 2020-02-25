---
title: Web表单中的静态元素
seo-title: Web表单中的静态元素
description: Web表单中的静态元素
seo-description: null
page-status-flag: never-activated
uuid: 628e2252-16a2-4c8a-a178-60a9441d3198
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: ca3377c6-a120-4cd0-aaf4-80248f4f5918
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 963aaa81971a8883b944bfcf4d1a00d729627916

---


# Web表单中的静态元素{#static-elements-in-a-web-form}

您可以在表单的页面中包含用户没有交互的元素；这些是静态元素，如图像、HTML内容、水平栏或超文本链接。 这些元素是通过工具栏中的第一个按钮通过单击菜单创建 **[!UICONTROL Add static element]** 的。

![](assets/s_ncs_admin_survey_add_static_element.png)

有以下类型的字段可用：

* 值基于先前提供的答案（在表单的上下文中）或数据库。
* 超文本链接、HTML、水平栏。 请参阅 [插入HTML内容](#inserting-html-content)。
* 保存在资源库中或用户可访问的服务器上的图像。 请参阅 [插入图像](#inserting-images)。
* 在客户端和／或服务器端执行的脚本。 它必须用JavaScript编写，并且与大多数浏览器兼容，以确保在客户端正确执行。

   >[!NOTE]
   >
   >在服务器端，脚本可以使用 [Campaign JSAPI文档中定义的函数](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

## 插入HTML内容 {#inserting-html-content}

可以在表单页面中包含HTML内容：超文本链接、图像、格式化段落、视频或Flash对象等。

HTML编辑器允许您输入要插入表单页面的内容。 要打开编辑器，请转到 **[!UICONTROL Static elements>HTML]** 。

您可以直接输入内容并设置其格式，或显示要粘贴到某些外部内容中的源代码窗口。 要切换到“源代码”模式，请单击工具栏中的第一个图标：

![](assets/s_ncs_admin_survey_html_editor.png)

要插入数据库字段，请使用个性化按钮。

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>只有在子选项卡中定义了在HTML编辑器中输入的字符串，才 **[!UICONTROL Texts]** 能转换它们。 否则，将不会收集这些内容。 有关此内容的详细信息，请参 [阅翻译Web表单](../../web/using/translating-a-web-form.md)。

### 插入链接 {#inserting-a-link}

填写编辑窗口中的字段，如下例所示：

要添加超文本链接，请转至 **[!UICONTROL Static elements>Link]**。

![](assets/s_ncs_admin_survey_add_link.png)

* 超文 **[!UICONTROL Label]** 本链接的内容将显示在表单页面上。
* 该 **[!UICONTROL URL]** 地址是所需的地址，例如： [https://www.adobe.com](https://www.adobe.com) （用于网站）或info@adobe.com [(用于发送消息](mailto:info@adobe.com) )。
* 该 **[!UICONTROL Window]** 字段允许您选择站点链接的显示模式。 您可以决定在新窗口、当前窗口或其他窗口中打开链接。
* 您可以添加工具提示，如下所示：

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* 您可以选择将链接显示为按钮或图像。 为此，请在字段中选择显示类 **[!UICONTROL Type]** 型。

### 链接类型 {#types-of-links}

默认情况下，链接与URL类型操作相关联，因此可以在URL字段中输入链接目标地址。

![](assets/s_ncs_admin_survey_link_url.png)

您可以为链接定义其他操作，以便用户单击该链接可执行以下操作：

* 刷新页面

   为此，请在字 **[!UICONTROL Refresh page]** 段的下拉框中选择选 **[!UICONTROL Action]** 项。

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* 显示下一页／上一页

   为此，请在字 **[!UICONTROL Next page]** 段的 **[!UICONTROL Previous page]** 下拉框中选择或选 **[!UICONTROL Action]** 项。

   ![](assets/s_ncs_admin_survey_link_next.png)

   如果要将和/ **[!UICONTROL Next]** 或按钮 **[!UICONTROL Back]** 替换为链接，则可以隐藏这些按钮。 Refer to this [page](../../web/using/defining-web-forms-page-sequencing.md).

   该链接将替换默 **[!UICONTROL Next]** 认使用的按钮。

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* 显示其他页面

   通过 **[!UICONTROL Enable a transition]** 此选项，可显示与字段中选定的传出过渡相关联的特定 **[!UICONTROL Transition]** 页面。

   ![](assets/s_ncs_admin_survey_link_viral.png)

   默认情况下，页面只有一个输出过渡。 要创建新过渡，请选择页面，然后单击部 **[!UICONTROL Add]** 分中的按 **[!UICONTROL Output transitions]** 钮，如下所示：

   ![](assets/s_ncs_admin_survey_add_transition.png)

   在图中，此添加内容将如下：

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >有关Web表单中页面排序的详细信息，请参阅定 [义Web表单页面排序](../../web/using/defining-web-forms-page-sequencing.md)。

* 预载表单的字段，其中包含从Facebook配置文件获取的数据

   >[!CAUTION]
   >
   >此功能仅在您安装了应用程序时才可 **[!UICONTROL Social Marketing]** 用。 要使用此选项，您需要创建Facebook应用程序以及类型外 **[!UICONTROL Facebook Connect]** 部帐户。 有关详细信息，请参见[此页面](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   通过 **[!UICONTROL Preload with Facebook]** 此选项，您可以在表单中插入一个按钮，以使用Facebook配置文件信息预载字段。

   ![](assets/web_social_webapp_037.png)

   当用户单击该按 **[!UICONTROL Fill in automatically]** 钮时，Facebook将打开权限请求窗口。

   ![](assets/web_social_webapp_029.png)

   >[!NOTE]
   >
   >在配置外部帐户时，可以更改扩展权限列表。 如果您未输入任何扩展权限，则默认情况下，Facebook会转发基本的配置文件信息。\
   >要查看扩展权限列表及其语法，请单击此处： [https://developers.facebook.com/docs/reference/api/permissions/](https://developers.facebook.com/docs/reference/api/permissions/)

   如果用户同意共享其信息，则会预加载表单的字段。

   ![](assets/web_social_webapp_030.png)

对于此用例，我们创建了一个由以下元素组成的Web应用程序：

* 包含表单的页面
* 活 **[!UICONTROL Record]** 动
* 活 **[!UICONTROL End]** 动

![](assets/social_webapp_031.png)

要添加预载按钮，请应用以下步骤：

1. 创建表单。

   ![](assets/social_webapp_032.png)

1. 转到与表单中的字段相同的级别并添加链接。

   ![](assets/social_webapp_033.png)

1. 输入标签并选择类 **[!UICONTROL Button]** 型。

   ![](assets/social_webapp_034.png)

1. 转到字段 **[!UICONTROL Action]** 并选择 **[!UICONTROL Preload with Facebook]**。

   ![](assets/social_webapp_035.png)

1. 转到字段， **[!UICONTROL Application]** 然后选择之前创 **[!UICONTROL Facebook Connect]** 建的外部帐户类型。 有关详细信息，请参见[此页面](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   ![](assets/social_webapp_036.png)

### 个性化HTML内容 {#personalizing-html-content}

您可以使用在上一页记录的数据个性化表单页面的HTML内容。 例如，您可以创建汽车保险Web表单，其第一页允许您提供联系信息和汽车品牌。

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

使用个性化字段将用户名和选定品牌重新注入到下一页。 要使用的语法取决于信息存储模式。 有关此信息的详细信息，请参阅 [使用收集的信息](../../web/using/web-forms-answers.md#using-collected-information)。

>[!NOTE]
>
>出于安全原因，在公式中输入的 **`<%=`** 值将替换为转义字符。 要避免这种情况，并且仅在必要时使用以下语法： **`<%=`**.

在我们的示例中，收件人的名字和姓氏存储在数据库的字段中，而其汽车品牌存储在变量中。 第2页个性化消息的语法如下：

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

这将产生以下结果：

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### 使用文本变量 {#using-text-variables}

通过 **[!UICONTROL Text]** 该选项卡可以创建变量字段，这些字段可在HTML中使用&lt;%=和%>字符，语法如下： **$(IDENTIFIER)**。

使用此方法可轻松将字符串本地化。 请参 [阅翻译Web表单](../../web/using/translating-a-web-form.md)

例如，您可以创建一个 **Contact** （联系人）字段，该字段允许您在HTML内容中显示“上次联系日期：”字符串。 为此请执行以下操作步骤：

1. 单击HTML文 **[!UICONTROL Text]** 本的选项卡。
1. 单击该 **[!UICONTROL Add]** 图标。
1. 在列 **[!UICONTROL Identifier]** 中，输入变量的名称
1. 在列 **[!UICONTROL Text]** 中，输入默认值。

   ![](assets/s_ncs_admin_survey_html_text.png)

1. 在HTML内容中，通过 **&lt;%= $（联系人）%>语法插入此文本变量** 。

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >如果在HTML编辑器中输入这些字符，则 **&lt;** and **>** fields将替换为转义字符。 在这种情况下，您需要通过单击HTML文本编辑器 **[!UICONTROL Display source code]** 的图标来更正源代码。

1. 打开表 **[!UICONTROL Preview]** 单的标签以查看在HTML中输入的值：

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

通过此操作模式，您可以分解Web表单的文本，并使用集成的翻译工具管理翻译。 有关此内容的详细信息，请参 [阅翻译Web表单](../../web/using/translating-a-web-form.md)。

## 插入图像 {#inserting-images}

要将图像包含在表单中，它们必须保存在可从外部访问的服务器上。

选择菜 **[!UICONTROL Static elements>Image]** 单。

选择要插入的图像源：它可以来自公共资源库，也可以存储在外部可访问的外部服务器上。

![](assets/s_ncs_admin_survey_add_img.png)

如果这是库中的图像，请在字段的组合框中选择它；如果它位于外部文件中，请输入访问路径。 标签将通过将光标传递到图像上（与HTML中的ALT字段一致）或图像未显示时显示。

可在编辑器的中央部分查看图像。
