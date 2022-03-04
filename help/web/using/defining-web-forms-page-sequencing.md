---
product: campaign
title: 定义Web窗体页面排序
description: 定义Web窗体页面排序
feature: Web Forms
exl-id: c5b5c398-c13b-4ebe-88b2-8ff84741422e
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# 定义Web窗体页面排序{#defining-web-forms-page-sequencing}

![](../../assets/common.svg)

表单可以包含一个或多个页面。 它是通过图表构建的，图表允许您对页面进行排序、测试、脚本执行、页面跳转和记录步骤。 全局图设计模式与Campaign工作流的模式相同。

## 关于上一页和下一页 {#about-previous-page-and-next-page}

对于每个页面，您可以删除 **[!UICONTROL Next]** 或 **[!UICONTROL Previous]** 按钮。 为此，请选择相关页面并选择选项 **[!UICONTROL Disable next page]** 或 **[!UICONTROL Disallow returning to the previous page]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

您可以将这些按钮替换为链接。 请参阅 [插入HTML内容](static-elements-in-a-web-form.md#inserting-html-content).

## 插入跳转 {#inserting-a-jump}

的 **[!UICONTROL Jump]** 当用户单击某个页面或其他表单时，该对象授予对另一个页面或其他表单的访问权限 **[!UICONTROL Next]**.

目标可以是：

* 表单的另一个页面。 要执行此操作，请选择 **[!UICONTROL Internal activity]** ，然后指定所需的页面，如下所示：

   ![](assets/s_ncs_admin_jump_param1.png)

* 另一种形式。 为此，请选择 **[!UICONTROL Explicit]** 选项，然后指定目标表单。

   ![](assets/s_ncs_admin_jump_param2.png)

* 目标可以存储在变量中。 在这种情况下，请从下拉列表中选择它，如下所示：

   ![](assets/s_ncs_admin_jump_param3.png)

* 的 **[!UICONTROL Comment]** 选项卡，可让您输入操作员在单击图表中的对象时将显示的信息。

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## 示例：根据URL的参数访问其他表单 {#example--accessing-another-form-according-to-a-parameter-of-the-url}

在以下示例中，我们要配置一个Web窗体，在获得批准后，该窗体将显示URL参数指定的其他窗体。 要执行此操作，请应用以下步骤：

1. 在表单末尾插入跳转：这取代了 **[!UICONTROL End]** 框中。

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. 在表单属性中，添加参数(**下一步**)存储在本地变量(**下一步**)。 本地变量在 [将数据存储在本地变量中](web-forms-answers.md#storing-data-in-a-local-variable).

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. 编辑 **[!UICONTROL Jump]** 对象，选择 **[!UICONTROL Stored in a variable]** 选项，然后选择 **下一步** 变量。

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. 投放URL必须包含目标表单的内部名称，例如：

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   用户单击 **[!UICONTROL Approve]** 按钮，窗体 **APP22** 中。

## 插入指向表单其他页面的链接 {#inserting-a-link-to-another-page-of-the-form}

您可以插入指向表单其他页面的链接。 为此，请添加 **[!UICONTROL Link]** 在页面中键入静态元素。 有关更多信息，请参阅 [插入链接](static-elements-in-a-web-form.md#inserting-a-link).

## 条件页面显示 {#conditional-page-display}

### 根据响应显示 {#display-based-on-responses}

的 **[!UICONTROL Test]** 框中，可设置页面排序条件。 它允许您根据测试结果定义各种分支行。 这样，您就可以根据用户提供的答案显示不同的页面。

例如，您可以为已在线订购的客户显示一个不同的页面，为已订购十个以上的客户显示另一个页面。 为此，请在表单的第一页中插入 **[!UICONTROL Number]** 为用户键入输入字段，以说明他们已下达的订单数。

![](assets/s_ncs_admin_survey_test_ex0.png)

您可以将此信息存储在数据库的字段中，也可以使用本地变量。

>[!NOTE]
>
>存储模式详见 [响应存储字段](web-forms-answers.md#response-storage-fields).

在本例中，我们要使用一个变量：

![](assets/s_ncs_admin_survey_test_ex1.png)

在表单的图表中，插入一个测试框以定义条件。 对于每个条件，都将在测试框的输出中添加一个新分支。

![](assets/s_ncs_admin_survey_test_ex2.png)

选择 **[!UICONTROL Activate the default branching]** 选项，以在无条件的情况下添加过渡。 如果定义的条件涵盖了所有可能的情况，则无需使用此选项。

接下来，定义当一个或其他条件为true时的页面排序，例如：

![](assets/s_ncs_admin_survey_test_ex3.png)

### 根据参数显示 {#display-based-on-parameters}

您还可以根据Web窗体的初始化参数或数据库中存储的值，对页面排序进行个性化。 请参阅 [表单URL参数](defining-web-forms-properties.md#form-url-parameters).

## 添加脚本 {#adding-scripts}

的 **[!UICONTROL Script]** 对象允许您直接输入JavaScript脚本，例如修改字段值、从数据库检索数据或调用Adobe Campaign API。

## 个性化结束页面 {#personalizing-the-end-page}

必须在图的末尾放置一个结束页面。 当用户单击 **[!UICONTROL Approve]** 按钮。

要个性化此页面，请双击 **[!UICONTROL End]** 并在中央编辑器中输入页面内容。

![](assets/s_ncs_admin_survey_end_page_edit.png)

* 您可以复制并粘贴现有HTML内容。 为此，请单击 **[!UICONTROL Display source code]** 并插入HTML代码。
* 您可以使用外部URL;为此，请选择相应的选项，然后输入要显示的页面的URL。
