---
solution: Campaign Classic
product: campaign
title: 管理答案
description: 管理答案
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 1%

---


# 管理答案{#managing-answers}

## 存储收集的答案 {#storing-collected-answers}

除了存储（数据库字段和本地变量）中所有Web 窗体通用的标准Adobe Campaign模式外，调查还允许使用归档字段动态扩展数据模型。

>[!CAUTION]
>
>此选项仅对调查 **类型** Web 应用程序可用。 它不提供给其他类型的Web 窗体。

### 存储在存档字段中 {#storing-in-an-archived-field}

通过添加新的存储空间来保存调查中提供的响应，可以轻松扩展数据模板。 为此，请在创建输 **[!UICONTROL Store answers to a question]** 入字段时选择选项。 单击链 **[!UICONTROL New field...]** 接并为其属性：

![](assets/s_ncs_admin_survey_new_space.png)

输入字段的标签和名称，然后选择字段类型：文本、布尔、整数或小数、日期等。

所选字段的类型涉及在用户输入响应时控制数据。 对 **于文本** 字段，您可以添加约束（大小写、格式）或链接到现有明细列表以强制进行选择。

要添加约束，请从下拉列表中选择它。 约束有两种类型：

1. 字符大小写

   输入的信息可以以下列格式存储在字段中：全部为大写、全小写或初始为大写。 此约束不要求用户以选定格式输入数据，但在保存时将转换在字段中输入的内容。

1. 数据格式

如果此字段用在列表中，则可以使用值列表上方的链接在值表中自 **[!UICONTROL Initialize the list of values from the database]** 动检索明细列表的值。

例如，您可以为用户创建一个下拉列表以选择其本地语言。 相应的存档字段可以与语言 **明细列表关联** ，该语言列表包含语言：

![](assets/s_ncs_admin_survey_database_values_2b.png)

通 **[!UICONTROL Edit link]** 过位于字段右侧的图标，您可以编辑此明细列表的内容：

![](assets/s_ncs_admin_survey_database_values_2c.png)

在字 **[!UICONTROL General]** 段的选项卡中，链 **[!UICONTROL Initialize the list of values from the database]** 接允许您自动输入提供的标签列表。

![](assets/s_ncs_admin_survey_database_values_2.png)

**示例**:将收件人合同存储在一个领域

要在一个字段中存储不同类型的合同，请创建一 **[!UICONTROL Text]** 个输入字段并选择 **[!UICONTROL Store answers to a question]** 选项。

单击链 **[!UICONTROL New field...]** 接并输入字段属性。 选择选 **[!UICONTROL Multiple values]** 项以启用要存储的多个值。

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

为其他合同创建条目字段，并将数据存储在同一存档字段中。

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

用户批准调查后，其答案将存储在字段 **[!UICONTROL Contracts]** 中。

在我们的示例中，以下答案为：

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

被申请人的用户档案将包含所输入的四个合同。

通过显示相关列， **[!UICONTROL Answers]** 可在调查的选项卡中查看它们。

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

您还可以根据答案筛选收件人，以仅显示您感兴趣的用户。 为此，请创建定位工作流并使用 **[!UICONTROL Survey responses]** 框。

![](assets/s_ncs_admin_survey_read_responses_wf.png)

根据要恢复的查询创建用户档案。 在以下示例中，查询允许您选择至少具有两个合同的用户档案，包括A类型合同。

![](assets/s_ncs_admin_survey_read_responses_edit.png)

对于每个表单，提供的答案可用于字段或标签中。 对存储在存档字段中的内容使用以下语法：

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>对于其他类型的字段，本节将详细介绍 [语法](../../platform/using/about-queries-in-campaign.md)。

### 存储设置 {#storage-settings}

可以将答案以XML格式存档给调查。 这样，您可以保存所收集答案的原始副本，在分项列表中数据过度标准化时，这非常有用(有关详细信息，请参阅标准 [化](../../web/using/publish--track-and-use-collected-data.md#standardizing-data))。

>[!CAUTION]
>
>归档原始响应大大增加了所需的存储空间。 谨慎使用此选项。

操作步骤：

* 通过选项卡的按 **[!UICONTROL Properties]** 钮编辑调查 **[!UICONTROL Edit]** 属性。
* 单击链 **[!UICONTROL Advanced parameters]** 接并选中 **[!UICONTROL Save a copy of raw answers]** 选项。

![](assets/s_ncs_admin_survey_xml_archive_option.png)

默认情况下，您可以为所有调查启用此选项(在调查发布时应用此选项)。 为此，请创建选 **[!UICONTROL NmsWebApp_XmlBackup]** 项并为其赋 **[!UICONTROL 1]** 值，如下所示：

![](assets/s_ncs_admin_survey_xml_global_option.png)

## 分数管理 {#score-management}

您可以为表单页面中提供的选项分配分数。 得分只能链接到已结束的问题：复选框、来自下拉列表的值、订阅等。

>[!CAUTION]
>
>得分管理仅适 **用于调查** 。

![](assets/s_ncs_admin_survey_score_create.png)

当确认页面时（即当用户单击或按钮时），分数会累积并保存在服 **[!UICONTROL Next]** 务器 **[!UICONTROL Finish]** 端。

>[!NOTE]
>
>可以使用正值或负值、整数值或非整数值。

分数可用于测试或脚本。

>[!CAUTION]
>
>分数不能用于同一页面上字段的可见性条件。 但是，它们可以在后续页面中使用。

* 要在测试中使用分数，请使 **[!UICONTROL Score]** 用测试计算公式中的字段，如下所示：

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* 您可以在脚本中使用得分。

**示例**:计算分数，并将其用作显示下一页的条件：

* 在调查中，下一页允许您根据在下拉列表中选择的值为用户分配不同的分数：

   ![](assets/s_ncs_admin_survey_score_exa.png)

* 您可以根据所选选项将此得分与第二个值组合：

   ![](assets/s_ncs_admin_survey_score_exb.png)

* 当用户单击该按 **[!UICONTROL Next]** 钮时，这两个值相加。

   ![](assets/s_ncs_admin_survey_score_exe.png)

* 可以根据得分对要显示的页面应用条件。 配置如下：

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)

