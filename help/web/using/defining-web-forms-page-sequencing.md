---
solution: Campaign Classic
product: campaign
title: 定义 Web 窗体页面排序
description: 定义 Web 窗体页面排序
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 2%

---


# 定义 Web 窗体页面排序{#defining-web-forms-page-sequencing}

表单可包含一个或多个页面。 它通过图表构建，图表允许您对页面进行排序、测试、脚本执行、页面跳转和记录步骤。 全局图设计模式与活动工作流相同。

## 关于上一页和下一页{#about-previous-page-and-next-page}

对于每个页面，可以删除&#x200B;**[!UICONTROL Next]**&#x200B;或&#x200B;**[!UICONTROL Previous]**&#x200B;按钮。 要执行此操作，请选择相关页面，然后选择选项&#x200B;**[!UICONTROL Disable next page]**&#x200B;或&#x200B;**[!UICONTROL Disallow returning to the previous page]**。

![](assets/s_ncs_admin_survey_no_next_page.png)

您可以用链接替换这些按钮。 请参阅[插入HTML内容](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

## 插入跳转{#inserting-a-jump}

当用户单击&#x200B;**[!UICONTROL Next]**&#x200B;时，**[!UICONTROL Jump]**&#x200B;对象允许访问其他页面或其他表单。

目标可以是：

* 表单的另一页。 要执行此操作，请选择&#x200B;**[!UICONTROL Internal activity]**，然后指定所需页面，如下所示：

   ![](assets/s_ncs_admin_jump_param1.png)

* 另一个表单。 要执行此操作，请选择&#x200B;**[!UICONTROL Explicit]**&#x200B;选项并指定目标表单。

   ![](assets/s_ncs_admin_jump_param2.png)

* 目标可以存储在变量中。 在这种情况下，请从下拉列表中选择它，如下所示：

   ![](assets/s_ncs_admin_jump_param3.png)

* 通过&#x200B;**[!UICONTROL Comment]**&#x200B;选项卡，可输入操作符单击图中的对象时可见的信息。

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## 示例：根据URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}的参数访问其他表单

在以下示例中，我们要配置一个Web表单，在获得批准后，该表单将显示由URL参数指定的其他表单。 为此，请应用以下步骤：

1. 在表单结尾插入跳转：这将替换&#x200B;**[!UICONTROL End]**&#x200B;框。

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. 在表单属性中，添加存储在本地变量(**next**)中的参数(**next**)。 [将数据存储在局部变量](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)中详细介绍了局部变量。

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. 编辑&#x200B;**[!UICONTROL Jump]**&#x200B;对象，选择&#x200B;**[!UICONTROL Stored in a variable]**&#x200B;选项，然后从下拉框中选择&#x200B;**next**&#x200B;变量。

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. 投放URL必须包括目标表单的内部名称，例如：

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   当用户单击&#x200B;**[!UICONTROL Approve]**&#x200B;按钮时，将显示表单&#x200B;**APP22**。

## 插入指向表单{#inserting-a-link-to-another-page-of-the-form}的其他页面的链接

您可以插入指向表单其他页面的链接。 为此，请向页面添加&#x200B;**[!UICONTROL Link]**&#x200B;类型静态元素。 有关详细信息，请参阅[插入链接](../../web/using/static-elements-in-a-web-form.md#inserting-a-link)。

## 条件页面显示{#conditional-page-display}

### 根据响应{#display-based-on-responses}显示

使用&#x200B;**[!UICONTROL Test]**&#x200B;框可以对表单中的页面顺序进行条件。 它允许您根据测试结果定义不同的分支行。 这使您能够根据用户提供的答案显示不同的页面。

例如，您可以为已在线订购的客户显示不同的页面，为已订购十个以上的客户显示另一个页面。 为此，请在表单的第一页中插入一个&#x200B;**[!UICONTROL Number]**&#x200B;类型输入字段，以便用户声明已下达的订单数。

![](assets/s_ncs_admin_survey_test_ex0.png)

您可以将此信息存储在数据库的字段中或使用本地变量。

>[!NOTE]
>
>在[响应存储字段](../../web/using/web-forms-answers.md#response-storage-fields)中详细介绍了存储模式。

在我们的示例中，我们希望使用一个变量：

![](assets/s_ncs_admin_survey_test_ex1.png)

在表单的图中，插入一个测试框以定义条件。 对于每个条件，将在测试框的输出处添加一个新分支。

![](assets/s_ncs_admin_survey_test_ex2.png)

选择&#x200B;**[!UICONTROL Activate the default branching]**&#x200B;选项，以在没有条件为真的情况下添加过渡。 如果所定义的条件涵盖了所有可能的情况，则不必使用此选项。

接下来，定义当一个或其他条件为true时的页面排序，例如：

![](assets/s_ncs_admin_survey_test_ex3.png)

### 根据参数{#display-based-on-parameters}显示

您还可以根据Web表单的初始化参数或数据库中存储的值个性化页面排序。 请参阅[表单URL参数](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

## 添加脚本{#adding-scripts}

通过&#x200B;**[!UICONTROL Script]**&#x200B;对象可以直接输入JavaScript脚本，例如修改字段值、从数据库检索数据或调用Adobe CampaignAPI。

## 个性化结束页面{#personalizing-the-end-page}

必须在图的结尾处放置一个结束页。 当用户单击Web表单中的&#x200B;**[!UICONTROL Approve]**&#x200B;按钮时，将显示结束页。

要个性化此页面，请多次单击&#x200B;**[!UICONTROL End]**，然后在中央编辑器中输入页面内容。

![](assets/s_ncs_admin_survey_end_page_edit.png)

* 可复制和粘贴现有HTML内容。 为此，请单击&#x200B;**[!UICONTROL Display source code]**&#x200B;并插入HTML代码。
* 可使用外部URL;要执行此操作，请选择相应的选项，并输入要显示的页面的URL。

