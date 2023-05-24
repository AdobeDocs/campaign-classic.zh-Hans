---
product: campaign
title: 管理答案
description: 了解如何管理调查答案
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Surveys
exl-id: 0b5dc602-e16f-4bf1-bd8f-352e0bc78996
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 1%

---

# 管理答案{#managing-answers}



## 存储收集的答案 {#storing-collected-answers}

除了Adobe Campaign中所有Web窗体通用的标准存储模式（数据库字段和本地变量）之外，调查还允许使用存档字段动态扩展数据模型。

>[!CAUTION]
>
>此选项可用于 **调查** 仅键入Web应用程序。 它不适用于其他类型的Web窗体。

### 存储在已存档字段中 {#storing-in-an-archived-field}

通过添加新的存储空间以保存调查中提供的响应，可以轻松扩展数据模板。 要执行此操作，请选择 **[!UICONTROL Store answers to a question]** 选项。 单击 **[!UICONTROL New field...]** 链接并提供其属性：

![](assets/s_ncs_admin_survey_new_space.png)

输入字段的标签和名称，然后选择字段类型：文本、布尔值、整数或小数、日期等。

所选字段的类型涉及用户输入响应时的数据控制。 对象 **text** 字段，可以添加约束（大小写、格式）或指向现有枚举的链接以强制选择。

要添加约束条件，请从下拉列表中选择它。 有两种类型的约束：

1. 字符大小写

   输入的信息可以以下列格式存储在字段中：全部大写、全部小写或初始大写。 此约束不要求用户以所选格式输入数据，但在字段中输入的内容在保存时将进行转换。

1. 数据格式

如果在列表中使用此字段，则可以使用自动检索值表中的枚举值 **[!UICONTROL Initialize the list of values from the database]** 值列表上方的链接。

例如，您可以创建一个下拉列表，让用户选择其母语。 对应的已存档字段可以与 **语言** 包含语言列表的明细列表：

![](assets/s_ncs_admin_survey_database_values_2b.png)

此 **[!UICONTROL Edit link]** 通过字段右侧的图标，可编辑此枚举的内容：

![](assets/s_ncs_admin_survey_database_values_2c.png)

在 **[!UICONTROL General]** 选项卡中， **[!UICONTROL Initialize the list of values from the database]** 链接允许您自动输入提供的标签列表。

![](assets/s_ncs_admin_survey_database_values_2.png)

**示例**：将收件人的合同存储在一个字段中

要在一个字段中存储不同类型的合同，请创建 **[!UICONTROL Text]** 输入字段并选择 **[!UICONTROL Store answers to a question]** 选项。

单击 **[!UICONTROL New field...]** 链接并输入字段属性。 选择 **[!UICONTROL Multiple values]** 选项来存储多个值。

![](assets/s_ncs_admin_survey_storage_multi_ex1.png)

为其它合同创建录入字段，并将数据存储在同一存档字段中。

![](assets/s_ncs_admin_survey_storage_multi_ex2.png)

当用户批准调查时，他们的答案将存储在 **[!UICONTROL Contracts]** 字段。

在我们的示例中，针对以下答案：

![](assets/s_ncs_admin_survey_storage_multi_ex3.png)

被申请人的简介将包含所签的4份合同。

它们可在以下位置查看： **[!UICONTROL Answers]** 选项卡中的任意位置（通过显示相关列）。

![](assets/s_ncs_admin_survey_storage_multi_ex4.png)

您还可以根据答案筛选收件人，以仅显示您感兴趣的用户。 要实现此目的，请创建定位工作流并使用 **[!UICONTROL Survey responses]** 盒子。

![](assets/s_ncs_admin_survey_read_responses_wf.png)

根据要恢复的用户档案创建查询。 在以下实例中，查询允许您选择至少具有两个合同的用户档案，包括A类型合同。

![](assets/s_ncs_admin_survey_read_responses_edit.png)

对于每个表单，提供的答案都可用于字段或标签。 对存储在已存档字段中的内容使用以下语法：

```
<%= ctx.webAppLogRcpData.name of the archived field %
```

>[!NOTE]
>
>对于其他类型的字段，有关语法的详情，请参见 [本节](../../platform/using/about-queries-in-campaign.md).

### 存储设置 {#storage-settings}

您可以以XML格式存档调查答案。 这允许您保存所收集答案的原始副本，当逐项列表中的数据过度标准化时，这将很有用。 [了解详情](../../surveys/using/publish--track-and-use-collected-data.md#standardizing-data)

>[!CAUTION]
>
>存档原始响应会影响所需的存储空间。 使用此选项时请务必谨慎。

操作步骤：

* 通过编辑调查属性 **[!UICONTROL Properties]** 的按钮 **[!UICONTROL Edit]** 选项卡。
* 单击 **[!UICONTROL Advanced parameters]** 链接并检查 **[!UICONTROL Save a copy of raw answers]** 选项。

![](assets/s_ncs_admin_survey_xml_archive_option.png)

您可以为所有调查默认启用此选项（发布调查时应用此选项）。 为此，请创建 **[!UICONTROL NmsWebApp_XmlBackup]** 选项并分配值 **[!UICONTROL 1]** ，如下所示：

![](assets/s_ncs_admin_survey_xml_global_option.png)

## 得分管理 {#score-management}

您可以为表单页面中提供的选项分配一个分数。 分数只能链接到已关闭的问题：复选框、下拉列表中的值、订阅等。

![](assets/s_ncs_admin_survey_score_create.png)

在确认页面时，即用户单击 **[!UICONTROL Next]** 或 **[!UICONTROL Finish]** 按钮。

>[!NOTE]
>
>可以使用正或负、整数或非整数值。

分数可用于测试或脚本。

>[!CAUTION]
>
>不能在位于同一页面上的字段的可见性条件中使用得分。 但是，它们可以在后续页面中使用。

* 要在测试中使用得分，请使用 **[!UICONTROL Score]** 字段中的值，如下所示：

   ![](assets/s_ncs_admin_survey_score_in_a_test.png)

* 您可以在脚本中使用得分。

**示例**：计算一个分数，并将其用作显示下一页的条件：

* 在调查中，您可以通过下一页根据在下拉列表中选择的值，为用户分配不同的分数：

   ![](assets/s_ncs_admin_survey_score_exa.png)

* 您可以根据所选的选项，将此分数与第二个值组合：

   ![](assets/s_ncs_admin_survey_score_exb.png)

* 当用户单击 **[!UICONTROL Next]** 按钮时，两个值相加。

   ![](assets/s_ncs_admin_survey_score_exe.png)

* 可以根据分数对要显示的页面应用条件。 其配置如下：

   ![](assets/s_ncs_admin_survey_score_exd.png)

   ![](assets/s_ncs_admin_survey_score_exg.png)
