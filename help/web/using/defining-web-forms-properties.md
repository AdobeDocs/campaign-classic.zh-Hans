---
product: campaign
title: 定义 Web 窗体属性
description: 定义 Web 窗体属性
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: 1d4990917fea54e67ed23cd0771295de03a4f01a
workflow-type: tm+mt
source-wordcount: '1375'
ht-degree: 1%

---

# 定义Web窗体属性{#defining-web-forms-properties}



您可以完全配置和个性化Web窗体，以满足您的要求。 必须在属性窗口中输入参数。

可通过Web窗体工具栏中的&#x200B;**[!UICONTROL Properties]**&#x200B;按钮访问属性窗口。 通过此窗口，您可以访问特定于Web窗体的一系列设置。 某些设置可能来自模板配置。

![](assets/s_ncs_admin_survey_properties_general.png)

## 整体表单属性 {#overall-form-properties}

在属性窗口的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，您可以修改表单的&#x200B;**标签**。 强烈建议不要更改&#x200B;**内部名称**。

![](assets/s_ncs_admin_survey_properties_general_tab.png)

表单创建期间选择表单模板。 以后无法更改。 有关创建和管理表单模板的更多信息，请参阅[使用Web表单模板](using-a-web-form-template.md)。

## 表单数据存储 {#form-data-storage}

默认情况下，Web窗体的字段存储在收件人表中。 通过从&#x200B;**[!UICONTROL Document type]**&#x200B;字段中选择新表，可以更改使用的表。 **[!UICONTROL Zoom]**&#x200B;图标允许您查看选定表的内容。

默认情况下，答案存储在收件人表单的&#x200B;**答案**&#x200B;表中。

## 设置错误页面 {#setting-up-an-error-page}

您可以配置错误页面：如果在执行表单的过程中出现错误，将显示此页面。

错误页面在表单属性窗口的相应选项卡中定义。

默认情况下，它会显示以下信息：

![](assets/s_ncs_admin_survey_default_error_page.png)

显示的字符串内容在属性窗口的&#x200B;**[!UICONTROL Error page]**&#x200B;选项卡中定义。 **[!UICONTROL HTML]**&#x200B;选项卡显示渲染，**[!UICONTROL Texts]**&#x200B;选项卡允许您修改文本字符串并在必要时添加一些文本：

![](assets/s_ncs_admin_survey_error_page.png)

## 表单本地化 {#form-localization}

**[!UICONTROL Localization]**&#x200B;选项卡允许您选择Web窗体的设计和显示语言。

请参阅[翻译Web窗体](translating-a-web-form.md)。

## 表单浏览和渲染 {#form-browsing-and-rendering}

**[!UICONTROL Rendering]**&#x200B;选项卡允许您定义Web窗体页面与使用的渲染模板之间的浏览类型。

您可以选择通过链接或按钮进行导航。

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

默认情况下，按钮是导航元素。 它们允许您执行以下操作：

* 通过单击&#x200B;**[!UICONTROL Next]**&#x200B;批准当前页面并显示下一页。 此按钮将显示在所有页面上，但最后一个页面除外。
* 通过单击&#x200B;**[!UICONTROL Previous]**&#x200B;显示上一页。 此按钮将显示在除第一个按钮之外的所有页面上。
* 单击&#x200B;**[!UICONTROL Approve]**&#x200B;按钮保存表单响应。 此按钮仅在最后一页显示。

这些元素显示在每个页面的底部。 他们的立场可以改变。 要执行此操作，必须修改样式表。

>[!NOTE]
>
>可能会隐藏某些页面上的&#x200B;**[!UICONTROL Previous]**&#x200B;按钮。 为此，请转到相关页面并选中&#x200B;**[!UICONTROL Disallow returning to the previous page]**&#x200B;选项。 在选择了页面树的根目录时，可以访问此选项。

**[!UICONTROL Rendering]**&#x200B;选项卡的&#x200B;**[!UICONTROL Template]**&#x200B;字段允许您从可用的主题中选择主题。

主题保存在树的&#x200B;**[!UICONTROL Administration>Configuration>Form rendering]**&#x200B;节点中。 请参阅[选择表单渲染模板](form-rendering.md#selecting-the-form-rendering-template)

示例渲染显示在属性窗口的下部。 **[!UICONTROL Edit link]**&#x200B;图标允许您查看选定主题的配置。

![](assets/s_ncs_admin_survey_properties_render.png)

## 表单中的徽标 {#logo-in-the-form}

您可以按自己的徽标更改表单中使用的徽标。

在Web应用的&#x200B;**[!UICONTROL Properties]**&#x200B;内的&#x200B;**[!UICONTROL Rendering]**&#x200B;选项卡中，单击模板的玻璃图标：

![](assets/logo_glass.png)

在新窗口中，单击&#x200B;**[!UICONTROL Page layout]**&#x200B;链接：

![](assets/logo_pagelayout.png)

您可以在此处更改徽标图像的路径：

![](assets/logo_path.png)

可用的图像位于&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]**&#x200B;下。 您可以在此处添加徽标。

这些图像放置在实例&#x200B;*datakit\nms\fra\img\activities*&#x200B;或&#x200B;*datakit\nms\eng\img\activities*&#x200B;的后端目录中（eng或fra，具体取决于实例的语言）。

要在此目录（以及图像中）中使用新图像，请联系Adobe支持部门以更改后端目录。

对于内部部署实例，您可以自己将图像添加到Datakit。

不必从Campaign客户端看到上传的图像。 正确的路径足以用作新徽标。

## 表单中的文本 {#texts-in-the-form}

**[!UICONTROL Page]**&#x200B;选项卡允许您定义表单页眉和页脚的内容。 请参阅[定义页眉和页脚](form-rendering.md#defining-headers-and-footers)。

它还允许您管理翻译。 请参阅[翻译Web窗体](translating-a-web-form.md)。

## 表单的辅助功能 {#accessibility-of-the-form}

如果Web表单为&#x200B;**[!UICONTROL Online]**&#x200B;并且当前日期在其有效期内，则用户可以访问Web表单。 表单的状态在发布阶段被修改（请参阅[发布表单](publishing-a-web-form.md#publishing-a-form)）。 状态显示在属性窗口&#x200B;**[!UICONTROL General]**&#x200B;选项卡的&#x200B;**项目**&#x200B;部分中。

有效期从&#x200B;**[!UICONTROL Start]**&#x200B;日期到&#x200B;**[!UICONTROL End date]**&#x200B;期间运行。 如果未在这些字段中指定日期，则表单具有永久有效性。

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>如果表单已关闭，因此其有效期未达到或已过期，或者，如果表单由Adobe Campaign操作员关闭，则在用户尝试访问它时会显示一条消息。 您可以通过单击&#x200B;**[!UICONTROL Personalize the message displayed if the form is closed...]**&#x200B;将此邮件个性化。

## 表单访问控制 {#form-access-control}

默认情况下，对Web窗体的访问以匿名模式执行：访问窗体的所有操作员都分配有WebApp操作员权限。

您可以对表单显示启用访问控制，例如在Intranet站点上提交表单时，以便对用户进行身份验证。 为此，请显示相关表单的&#x200B;**[!UICONTROL Properties]**&#x200B;窗口，然后单击&#x200B;**[!UICONTROL Enable access control]**&#x200B;选项，如下所示：

![](assets/s_ncs_admin_survey_access_ctrl.png)

在访问页面时，将会出现以下身份验证表单：

![](assets/s_ncs_admin_survey_access_login.png)

登录名和密码由Adobe Campaign操作员使用。 如需详细信息，请参阅[此小节](../../platform/using/access-management.md)。

**[!UICONTROL Use a specific account]**&#x200B;选项允许您限制访问表单的操作员的读取或写入权限。 使用下拉框选择将负责授予这些权限的操作员或操作员组。

![](assets/s_ncs_admin_survey_access_op_select.png)

## 表单URL参数 {#form-url-parameters}

您可以在表单的URL中添加其他参数，以个性化其内容并初始化上下文（语言、加密的收件人ID、公司、存储在变量中的计算公式等）。 这样，您就可以通过多个不同的URL来授予对一个表单的访问权限，并根据URL中指示的参数值来个性化页面内容。

默认情况下，Adobe Campaign提供用于预览表单和检查错误的参数。 您可以创建链接到表单的新设置，这些设置可能使用数据库中字段或本地变量的值。

## 标准参数 {#standard-parameters}

默认情况下，以下参数可用：

* **id**&#x200B;表示加密标识符。
* **lang**&#x200B;以更改显示语言。
* **origin**&#x200B;以指定响应者的来源。
* **_uuid**&#x200B;允许在发布和错误跟踪之前查看表单。 此参数供内部使用（创建和调试）：通过此URL访问Web窗体时，创建的记录不会包含在跟踪（报表）中。 源被强制设置为&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;值。

  它与&#x200B;**_preview**&#x200B;参数和/或&#x200B;**_debug**&#x200B;一起使用：

  **_preview**&#x200B;以显示上次保存的版本。 此参数必须仅在测试阶段使用。

  **_debug**&#x200B;以显示表单页面中输入或计算的数据的跟踪。 用于获取有关错误的更多信息，包括发布表单后的信息。

  >[!CAUTION]
  >
  >当通过带有&#x200B;**_uuid**&#x200B;参数的URL显示表单时，**[!UICONTROL origin]**&#x200B;参数的值将被强制设置为&#x200B;**Adobe Campaign**。

## 添加参数 {#adding-parameters}

可以通过窗体“属性”窗口中的&#x200B;**[!UICONTROL Parameters...]**&#x200B;选项卡添加参数。 可以将它们设为必选项，如下所示：

![](assets/s_ncs_admin_survey_properties_param.png)

您必须指定从中检索参数值的存储位置。 为此，请选择其中一个存储选项，然后单击&#x200B;**[!UICONTROL Storage]**&#x200B;选项卡以选择相关字段或变量。 [响应存储字段](web-forms-answers.md#response-storage-fields)中详细介绍了存储选项。

然后，可以将响应者状态（0、1或任何其他值）添加到用于访问表单的URL中。 此信息可在表单页面或测试框中重复使用。 显示的页面可以根据上下文的值设置条件，如下所示：

1. 客户主页（**状态=1**）：

   ![](assets/s_ncs_admin_survey_test_client.png)

1. 潜在客户主页（**状态=0**）：

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. 其他配置文件的主页（例如，**状态=12**）：

   ![](assets/s_ncs_admin_survey_test_other.png)

要配置此表单，请创建一个测试框并将其放在图的开头，如下所示：

![](assets/s_ncs_admin_survey_test.png)

利用测试框，可配置页面排序条件：

![](assets/s_ncs_admin_survey_test_box.png)
