---
solution: Campaign Classic
product: campaign
title: 定义 Web 窗体属性
description: 定义 Web 窗体属性
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 1%

---


# 定义 Web 窗体属性{#defining-web-forms-properties}

Web 窗体可完全配置和可个性化，以满足您的要求。 参数必须在属性窗口中输入。

通过Web表单工具栏中 **[!UICONTROL Properties]** 的按钮可访问属性窗口。 通过此窗口可访问特定于Web表单的一系列设置。 某些设置可能来自模板配置。

![](assets/s_ncs_admin_survey_properties_general.png)

## 表单整体属性 {#overall-form-properties}

在属 **[!UICONTROL General]** 性窗口的选项卡中，可以修改表 **单的** “标签”。 强烈建议不要更改内部 **名称**。

![](assets/s_ncs_admin_survey_properties_general_tab.png)

表单创建过程中将选择表单模板。 以后无法更改。 有关创建和管理表单模板的详细信息，请 [参阅使用Web表单模板](../../web/using/using-a-web-form-template.md)。

## 表单数据存储 {#form-data-storage}

默认情况下，Web 窗体字段存储在收件人表中。 您可以通过从字段中选择新表来更改所使用的 **[!UICONTROL Document type]** 表。 通过 **[!UICONTROL Zoom]** 该图标可视图选定表格的内容。

默认情况下，答案存储在表 **[!UICONTROL Answer to a recipient form]** 中。

## 设置错误页面 {#setting-up-an-error-page}

您可以配置错误页：在表单执行过程中出错时，将显示此页。

错误页面在表单属性窗口的相应选项卡中定义。

默认情况下，它显示以下信息：

![](assets/s_ncs_admin_survey_default_error_page.png)

显示的字符串内容在属性窗口的 **[!UICONTROL Error page]** 选项卡中定义。 该选 **[!UICONTROL HTML]** 项卡显示渲染，该选项卡 **[!UICONTROL Texts]** 允许您修改文本字符串并根据需要添加一些文本：

![](assets/s_ncs_admin_survey_error_page.png)

## 表单本地化 {#form-localization}

通过 **[!UICONTROL Localization]** 该选项卡可以选择Web表单的设计和显示语言。

See [Translating a web form](../../web/using/translating-a-web-form.md).

## 表单浏览和渲染 {#form-browsing-and-rendering}

通过 **[!UICONTROL Rendering]** 该选项卡，可定义Web表单的页面和所使用的呈现模板之间的浏览类型。

您可以选择通过链接或按钮进行导航。

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

按钮默认为导航元素。 它们允许您执行以下操作：

* 通过单击批准当前页面并显示下一页 **[!UICONTROL Next]**。 此按钮显示在除最后一页之外的所有页面上。
* 单击以显示上一页 **[!UICONTROL Previous]**。 除第一个按钮外，此按钮会显示在所有页面上。
* 单击按钮保存表单 **[!UICONTROL Approve]** 响应。 此按钮仅显示在最后一页上。

这些元素显示在每页的底部。 他们的立场可以改变。 为此，必须修改样式表。

>[!NOTE]
>
>可以在某些页面 **[!UICONTROL Previous]** 上隐藏按钮。 要执行此操作，请转到相关页面并选中该 **[!UICONTROL Disallow returning to the previous page]** 选项。 选择页面树的根时，可以访问此选项。

在选 **[!UICONTROL Template]** 项卡的字 **[!UICONTROL Rendering]** 段中，您可以从可用主题中选择主题。

主题保存在 **[!UICONTROL Administration>Configuration>Form rendering]** 树的节点中。 请参 [阅选择表单渲染模板](../../web/using/form-rendering.md#selecting-the-form-rendering-template)

属性窗口的下半部分会显示示例渲染。 通过 **[!UICONTROL Edit link]** 该图标可视图选定主题的配置。

![](assets/s_ncs_admin_survey_properties_render.png)

## 格式文本 {#texts-in-the-form}

使用 **[!UICONTROL Page]** 选项卡可定义表单页眉和页脚的内容。 请参 [阅定义页眉和页脚](../../web/using/form-rendering.md#defining-headers-and-footers)。

它还允许您管理翻译。 See [Translating a web form](../../web/using/translating-a-web-form.md).

## 表单的可访问性 {#accessibility-of-the-form}

如果Web表单在有效期内，且当 **[!UICONTROL Online]** 前日期在有效期内，则用户可以访问它。 在发布阶段将修改表单的状态(请参 [阅发布表单](../../web/using/publishing-a-web-form.md#publishing-a-form))。 状态显示在属性 **窗口** 选项卡 **[!UICONTROL General]** 的“项目”部分。

有效期从日期 **[!UICONTROL Start]** 到日期 **[!UICONTROL End date]**。 如果这些字段中未指定日期，则表单具有永久有效性。

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>如果表单已关闭，因此其有效期尚未达到或已过期，或者如果表单已由Adobe Campaign操作符关闭，则当用户尝试访问表单时，将显示一条消息。 您可以通过单击来个性化此消息 **[!UICONTROL Personalize the message displayed if the form is closed...]**。

## 表单访问控制 {#form-access-control}

默认情况下，以匿名模式访问Web 窗体:访问表单的所有运算符都被分配为WebApp运算符权限。

您可以启用表单显示访问控制，例如在内部网站点上传送表单时，以验证用户身份。 为此，请显示相 **[!UICONTROL Properties]** 关表单的窗口，并单击 **[!UICONTROL Enable access control]** 选项，如下所示：

![](assets/s_ncs_admin_survey_access_ctrl.png)

访问页面时，将显示以下身份验证表单：

![](assets/s_ncs_admin_survey_access_login.png)

登录名和口令是Adobe Campaign运算符使用的口令。 如需详细信息，请参阅[此部分](../../platform/using/access-management.md)。

通过 **[!UICONTROL Use a specific account]** 此选项，您可以限制访问表单的操作员的读或写权限。 使用下拉框选择负责授予这些权限的操作员或操作员组。

![](assets/s_ncs_admin_survey_access_op_select.png)

## 表单URL参数 {#form-url-parameters}

您可以在表单的URL中添加其他参数，以个性化其内容并初始化上下文(语言、加密的收件人ID、公司、存储在变量中的计算公式等)。 这样，您就可以通过多个不同的URL访问一个表单，并根据URL中指示的参数值个性化页面内容。

默认情况下，Adobe Campaign优惠参数用于预览表单和检查错误。 您可以创建链接到表单的新设置，该设置可能使用数据库中某个字段或本地变量的值。

## 标准参数 {#standard-parameters}

默认情况下，以下参数可用：

* **id** ，用于指示加密的标识符。
* **lang** 更改显示语言。
* **来源** ，指定被申请人的来源。
* **_uuid** 在发布和错误跟踪之前启用表单查看。 此参数供内部使用（创建和调试）:当您通过此URL访问Web表单时，在跟踪（报告）中不会考虑创建的记录。 来源被强制设置为 **[!UICONTROL Adobe Campaign]** 值。

   它与_ **预览参数** 和／或 **_debug一起使用**:

   **预览** ：显示上次保存的版本(_S)。 此参数只能在测试阶段使用。

   **_debug** 显示表单页面中输入或计算的数据的跟踪。 这用于获取更多有关错误的信息，包括表单发布后的信息。

   >[!CAUTION]
   >
   >当表单通过带有_uuid参数的 **URL显示** ，则参数的 **[!UICONTROL origin]** 值将强制 **Adobe Campaign**。

## 添加参数 {#adding-parameters}

可以通过表单的“属 **[!UICONTROL Parameters...]** 性”窗口中的选项卡添加参数。 可以强制使用它们，如下所示：

![](assets/s_ncs_admin_survey_properties_param.png)

必须指定从中检索参数值的存储位置。 为此，请选择一个存储选项，然后单 **[!UICONTROL Storage]** 击选项卡以选择相关字段或变量。 存储选项在响应存储字 [段中有详细说明](../../web/using/web-forms-answers.md#response-storage-fields)。

答复者状态（0、1或任何其他值）随后可添加到URL以访问表单。 此信息可在表单的页面或测试框中重新使用。 显示的页面可以根据上下文的值进行条件设置，如下所示：

1. 主页(**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. 主页(**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. 其他用户档案的主页( **如status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

要配置此表单，请创建一个测试框并将其放在图的开始，如下所示：

![](assets/s_ncs_admin_survey_test.png)

通过测试框，您可以配置页面排序条件：

![](assets/s_ncs_admin_survey_test_box.png)

