---
product: campaign
title: 定义Web窗体页面排序
description: 定义Web窗体页面排序
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Forms
exl-id: c5b5c398-c13b-4ebe-88b2-8ff84741422e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# 定义Web窗体页面排序{#defining-web-forms-page-sequencing}



该表单可以包含一个或多个页面。 它通过图表构建，允许您对页面进行排序、测试、脚本执行、页面跳转和记录步骤。 全局图设计模式与Campaign工作流相同。

## 关于上一页和下一页 {#about-previous-page-and-next-page}

对于每个页面，您可以删除&#x200B;**[!UICONTROL Next]**&#x200B;或&#x200B;**[!UICONTROL Previous]**&#x200B;按钮。 为此，请选择相关页面，然后选择选项&#x200B;**[!UICONTROL Disable next page]**&#x200B;或&#x200B;**[!UICONTROL Disallow returning to the previous page]** 。

![](assets/s_ncs_admin_survey_no_next_page.png)

您可以使用链接替换这些按钮。 请参阅[插入HTML内容](static-elements-in-a-web-form.md#inserting-html-content)。

## 插入跳转 {#inserting-a-jump}

当用户单击&#x200B;**[!UICONTROL Next]**&#x200B;时，**[!UICONTROL Jump]**&#x200B;对象会提供对另一个页面或其他表单的访问权限。

目标可以是：

* 表单的另一页。 为此，请选择&#x200B;**[!UICONTROL Internal activity]**，然后指定所需页面，如下所示：

  ![](assets/s_ncs_admin_jump_param1.png)

* 另一种形式。 为此，请选择&#x200B;**[!UICONTROL Explicit]**&#x200B;选项并指定目标表单。

  ![](assets/s_ncs_admin_jump_param2.png)

* 目标可以存储在变量中。 在这种情况下，请从下拉列表中选择它，如下所示：

  ![](assets/s_ncs_admin_jump_param3.png)

* 通过&#x200B;**[!UICONTROL Comment]**&#x200B;选项卡，可输入操作员单击图中的对象时将显示的信息。

  ![](assets/s_ncs_admin_survey_jump_comment.png)

## 示例：根据URL的参数访问其他表单 {#example--accessing-another-form-according-to-a-parameter-of-the-url}

在以下示例中，我们要配置一个Web窗体，该窗体在获得批准后将显示由URL参数指定的另一个窗体。 要执行此操作，请应用以下步骤：

1. 在表单末尾插入跳转：这将替换&#x200B;**[!UICONTROL End]**&#x200B;框。

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. 在表单属性中，添加存储在局部变量(**next**)中的参数(**next**)。 在[将数据存储在局部变量](web-forms-answers.md#storing-data-in-a-local-variable)中详细介绍了局部变量。

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. 编辑&#x200B;**[!UICONTROL Jump]**&#x200B;对象，选择&#x200B;**[!UICONTROL Stored in a variable]**&#x200B;选项，然后从下拉框中选择&#x200B;**下一个**&#x200B;变量。

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. 投放URL必须包含目标表单的内部名称，例如：

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   当用户单击&#x200B;**[!UICONTROL Approve]**&#x200B;按钮时，显示表单&#x200B;**APP22**。

## 插入指向表单另一页的链接 {#inserting-a-link-to-another-page-of-the-form}

您可以插入指向表单其他页面的链接。 为此，请向页面添加&#x200B;**[!UICONTROL Link]**&#x200B;类型静态元素。 有关详细信息，请参阅[插入链接](static-elements-in-a-web-form.md#inserting-a-link)。

## 条件页面显示 {#conditional-page-display}

### 根据响应显示 {#display-based-on-responses}

**[!UICONTROL Test]**&#x200B;框允许您为表单中的页面排序设置条件。 它允许您根据测试结果定义各种分支行。 这样，您就可以根据用户提供的答案显示不同的页面。

例如，您可以为已在线订购的客户显示一个不同的页面，为已下超过10张订单的客户显示另一个页面。 为此，请在表单的第一个页面中插入一个&#x200B;**[!UICONTROL Number]**&#x200B;类型输入字段，以便用户说明他们下了多少订单。

![](assets/s_ncs_admin_survey_test_ex0.png)

您可以将此信息存储在数据库的某个字段中，或者使用局部变量。

>[!NOTE]
>
>在[响应存储字段](web-forms-answers.md#response-storage-fields)中详细介绍了存储模式。

在本例中，我们希望使用变量：

![](assets/s_ncs_admin_survey_test_ex1.png)

在表单的图表中，插入测试框以定义条件。 对于每个条件，都将在测试框的输出中添加一个新分支。

![](assets/s_ncs_admin_survey_test_ex2.png)

选择&#x200B;**[!UICONTROL Activate the default branching]**&#x200B;选项可添加过渡，以用于所有条件都不为true的情况。 如果定义的条件涵盖了所有可能的情况，则无需使用此选项。

接下来，当以下一个或多个条件为true时，定义页面排序：

![](assets/s_ncs_admin_survey_test_ex3.png)

### 根据参数显示 {#display-based-on-parameters}

您还可以根据Web窗体的初始化参数或根据数据库中存储的值对页面排序进行个性化设置。 请参阅[表单URL参数](defining-web-forms-properties.md#form-url-parameters)。

## 添加脚本 {#adding-scripts}

**[!UICONTROL Script]**&#x200B;对象允许您直接输入JavaScript脚本，例如，修改字段值，从数据库中检索数据，或调用Adobe Campaign API。

## 个性化结束页面 {#personalizing-the-end-page}

必须在图的末尾放置一个结束页面。 用户单击Web窗体中的&#x200B;**[!UICONTROL Approve]**&#x200B;按钮时将显示结束页面。

要个性化此页面，请双击&#x200B;**[!UICONTROL End]**&#x200B;并在中央编辑器中输入该页面的内容。

![](assets/s_ncs_admin_survey_end_page_edit.png)

* 您可以复制并粘贴现有HTML内容。 为此，请单击&#x200B;**[!UICONTROL Display source code]**&#x200B;并插入HTML代码。
* 您可以使用外部URL；要实现此目的，请选择相应的选项，然后输入要显示的页面的URL。
