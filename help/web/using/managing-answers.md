---
title: 管理答案
seo-title: 管理答案
description: 管理答案
seo-description: null
page-status-flag: never-activated
uuid: 329e2f4a-c5bc-4654-bdef-71a0818fc2b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: affecd87-00a3-4d50-92d3-31ac6228948b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 管理答案{#managing-answers}

## 存储收集的答案 {#storing-collected-answers}

除了Adobe Campaign中所有Web表单（数据库字段和本地变量）通用的标准存储模式之外，调查还支持使用归档字段动态扩展数据模型。

>[!CAUTION]
>
>此选项仅对 **Survey类型** Web应用程序可用。 它不适用于其他类型的Web表单。

### 存储在存档字段中 {#storing-in-an-archived-field}

通过添加新的存储空间来保存调查中提供的响应，可轻松扩展数据模板。 为此，请在创建输 **[!UICONTROL Store answers to a question]** 入字段时选择选项。 单击链 **[!UICONTROL New field...]** 接并指定其属性：

![](assets/s_ncs_admin_survey_new_space.png)

输入字段的标签和名称，然后选择字段类型：文本、布尔值、整数或小数、日期等。

所选字段的类型涉及用户输入响应时对数据的控制。 对于 **文本字段** ，可以添加约束（大小写、格式）或指向现有枚举的链接以强制进行选择。

要添加约束，请从下拉列表中选择它。 约束有两种类型：

1. 字符大小写

   输入的信息可以以下列格式存储在字段中：全部大写、全小写或初始大写。 此约束不要求用户以选定格式输入数据，但在保存字段中输入的内容时，将转换。

1. 数据格式

如果在列表中使用此字段，则可以使用值列表上方的链接在值表中自动检索 **[!UICONTROL Initialize the list of values from the database]** 枚举的值。

例如，您可以为用户创建一个下拉列表以选择其本地语言。 相应的存档字段可以与包含语 **言列表** （语言枚举）相关联：

![](assets/s_ncs_admin_survey_database_values_2b.png)

位 **[!UICONTROL Edit link]** 于字段右侧的图标允许您编辑此枚举的内容：

![](assets/s_ncs_admin_survey_database_values_2c.png)

在字段 **[!UICONTROL General]** 的选项卡中，该链 **[!UICONTROL Initialize the list of values from the database]** 接允许您自动输入提供的标签列表。

![](assets/s_ncs_admin_survey_database_values_2.png)

**示例**:将收件人的合同存储在一个字段中

要在一个字段中存储不同类型的合同，请创建一个输 **[!UICONTROL Text]** 入字段，然后选择 **[!UICONTROL Store answers to a question]** 选项。

单击链 **[!UICONTROL New field...]** 接并输入字段属性。 选择 **[!UICONTROL Multiple values]** 此选项可启用多个值的存储。

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

为其他合同创建条目字段，并将数据存储在同一存档字段中。

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

用户批准调查后，其答案将存储在字段 **[!UICONTROL Contracts]** 中。

在我们的示例中，对于以下答案：

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

被申请人的个人资料将包含输入的四个合同。

可通过显示相关列在调 **[!UICONTROL Answers]** 查的选项卡中查看这些字段。

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

您还可以根据答案筛选收件人，以仅显示您感兴趣的用户。 为此，请创建定位工作流并使用该 **[!UICONTROL Survey responses]** 框。

![](assets/s_ncs_admin_survey_read_responses_wf.png)

根据要恢复的配置文件创建查询。 在以下示例中，通过查询，您可以选择至少具有两个合同（包括A类合同）的配置文件。

![](assets/s_ncs_admin_survey_read_responses_edit.png)

对于每个表单，提供的答案可用于字段或标签中。 对存储在存档字段中的内容使用以下语法：

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>对于其他类型的字段，本节将详细介绍 [语法](../../platform/using/about-queries-in-campaign.md)。

### 存储设置 {#storage-settings}

可以以XML格式存档调查的答案。 这样，您可以保存收集的答案的原始副本，在项目化列表中数据过度标准化的情况下(有关详细信息，请参阅标准化数据 [](../../web/using/publish--track-and-use-collected-data.md#standardizing-data))，这非常有用。

>[!CAUTION]
>
>归档原始响应会大大增加所需的存储空间。 谨慎使用此选项。

操作步骤：

* 通过选项卡的按钮 **[!UICONTROL Properties]** 编辑调查属 **[!UICONTROL Edit]** 性。
* 单击链 **[!UICONTROL Advanced parameters]** 接并选中该 **[!UICONTROL Save a copy of raw answers]** 选项。

![](assets/s_ncs_admin_survey_xml_archive_option.png)

默认情况下，您可以为所有调查启用此选项（发布调查时会应用此选项）。 为此，请创建选 **[!UICONTROL NmsWebApp_XmlBackup]** 项并为其赋 **[!UICONTROL 1]** 值，如下所示：

![](assets/s_ncs_admin_survey_xml_global_option.png)

## 得分管理 {#score-management}

您可以为表单页面中提供的选项分配分数。 得分只能链接到已结束的问题：复选框、下拉列表中的值、订阅等。

>[!CAUTION]
>
>得分管理仅适用于 **调查** 。

![](assets/s_ncs_admin_survey_score_create.png)

当确认页面时（即当用户单击或按钮时），分数会累积并保存在服 **[!UICONTROL Next]** 务器 **[!UICONTROL Finish]** 端。

>[!NOTE]
>
>可以使用正值或负值、整数值或非整数值。

得分可用于测试或脚本。

>[!CAUTION]
>
>分数不能用于同一页面上字段的可见性条件。 但是，它们可以在后续页面中使用。

* 要在测试中使用分数，请使 **[!UICONTROL Score]** 用测试计算公式中的字段，如下所示：

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* 您可以在脚本中使用得分。

**示例**:计算分数，并将其用作显示下一页的条件：

* 在调查中，下一页允许您根据下拉列表中选择的值为用户分配不同的分数：

   ![](assets/s_ncs_admin_survey_score_exa.png)

* 您可以将此得分与第二个值合并，具体取决于选定的选项：

   ![](assets/s_ncs_admin_survey_score_exb.png)

* 当用户单击该按 **[!UICONTROL Next]** 钮时，这两个值相加。

   ![](assets/s_ncs_admin_survey_score_exe.png)

* 可以根据得分为要显示的页面应用条件。 此配置如下：

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

