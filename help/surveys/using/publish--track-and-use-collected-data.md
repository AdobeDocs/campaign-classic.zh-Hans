---
product: campaign
title: 发布、跟踪和使用收集的数据
description: 了解如何发布、跟踪和使用在调查中收集的数据
audience: web
content-type: reference
topic-tags: online-surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 2%

---

# 发布、跟踪和使用收集的数据{#publish-track-and-use-collected-data}

![](../../assets/v7-only.svg)

创建、配置和发布表单后，您可以与受众共享该链接并跟踪响应。

>[!NOTE]
>
>Adobe Campaign中调查的生命周期及其发布和交付模式与Web表单的生命周期类似：[此部分](../../web/using/about-web-forms.md)中详细介绍了这些参数。

## 调查仪表板 {#survey-dashboard}

每个调查都有其自己的功能板，可让您查看其状态、描述、公共URL和可用性计划。 它还允许您查看可用的报表。 [了解详情](#reports-on-surveys)。

功能板上显示了调查的公共URL:

![](assets/survey_public_url.png)

## 响应跟踪 {#response-tracking}

您可以在日志和报表中跟踪对调查的响应。

### 调查日志 {#survey-logs}

对于提交的每个调查，您可以在&#x200B;**[!UICONTROL Logs]**&#x200B;选项卡中跟踪响应。 此选项卡显示已完成调查的用户列表及其来源：

![](assets/s_ncs_admin_survey_logs.png)

双击某行，以显示答复者填写的调查表单。 您可以全面浏览调查并完整访问答案。 这些文件可导出为外部文件。 有关更多信息，请参阅[导出答案](#exporting-answers)。

通过添加以下字符，在调查URL中指示原点：

```
?origin=xxx
```

在编辑调查时，其URL包含参数&#x200B;**[!UICONTROL __uuid]**，表示调查处于测试阶段且尚未联机。 当您通过此URL访问调查时，在跟踪（报表）中不会考虑创建的记录。 源被强制设置为值&#x200B;**[!UICONTROL Adobe Campaign]**。

有关URL参数的更多信息，请参阅[此页面](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

### 调查报告 {#reports-on-surveys}

使用功能板选项卡可访问调查报表。 单击报表名称以查看报表名称。

![](assets/s_ncs_admin_survey_report_doc.png)

**[!UICONTROL Documentation]**&#x200B;报表中显示调查的结构。

在调查的&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡中提供了关于Web调查的另外两份报告：**[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Breakdown of responses]**。

* 常规

   此报表包含有关调查的一般信息：响应数随时间的变化情况，以及按来源和语言的分布情况。

   常规报表示例：

   ![](assets/s_ncs_admin_survey_report_0.png)

* 响应的划分

   此报表显示了每个问题的响应细分。 此划分仅适用于对存储在&#x200B;**[!UICONTROL Question]**&#x200B;类型容器中的字段给出的答案。 此参数仅适用于选择控件（例如，不在文本字段上划分）。

   ![](assets/s_ncs_admin_survey_report_2.png)

## 导出答案 {#exporting-answers}

可在外部文件中导出调查的答案，以供稍后处理。 可以通过两种方式来执行此操作：

1. 导出报表数据

   要导出报表数据，请单击&#x200B;**[!UICONTROL Export]**&#x200B;按钮并选择导出格式。

   有关导出报表数据的更多信息，请参阅[此部分](../../reporting/using/about-reports-creation-in-campaign.md)。

1. 导出答案

   要导出答案，请单击调查的&#x200B;**[!UICONTROL Responses]**&#x200B;选项卡并右键单击。 选择 **[!UICONTROL Export...]**。

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   然后，输入要导出的信息和存储文件。

   您可以在导出向导中配置输出文件的内容和格式。

   这样，您就可以：

   * 向输出文件添加列并恢复关于收件人的信息（存储在数据库中），
   * 格式化导出的数据，
   * 为文件中的信息选择编码格式。

   如果要导出的调查包含多个&#x200B;**[!UICONTROL Multi-line text]**&#x200B;或&#x200B;**[!UICONTROL HTML text]**&#x200B;字段，则必须以&#x200B;**[!UICONTROL XML]**&#x200B;格式导出该调查。 为此，请在&#x200B;**[!UICONTROL Output format]**&#x200B;字段的下拉列表中选择此格式，如下所示：

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   单击&#x200B;**[!UICONTROL Start]**&#x200B;以运行导出。

   >[!NOTE]
   >
   >[此部分](../../platform/using/about-generic-imports-exports.md)中详细介绍了数据导出及其配置的阶段。

## 使用收集的数据 {#using-the-collected-data}

通过在线调查收集的信息可以在定位工作流的框架内恢复。 要实现此目的，请使用&#x200B;**[!UICONTROL Survey responses]**&#x200B;框。

在以下示例中，我们希望为在线调查中至少有两个孩子且得分最高的五个收件人专门提供Web选件。 本调查的答案是：

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

在定位工作流中，**[!UICONTROL Survey responses]**&#x200B;将进行如下配置：

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

首先选择相关调查，然后在窗口的中央部分提取数据。 在这种情况下，我们需要至少提取分数列，因为它将用在拆分框中以恢复五个最高分数。

通过单击&#x200B;**[!UICONTROL Edit query...]**&#x200B;链接指示答案的筛选条件。

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

启动定位工作流。 查询取回了8个收件人。

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

右键单击收藏集框的输出过渡以查看它们。

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

然后，在工作流中放置一个拆分框，以取回分数最高的5个收件人。

编辑拆分框以对其进行配置：

* 首先，在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中选择适当的架构，然后配置子集：

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* 转到&#x200B;**[!UICONTROL Sub-sets]**&#x200B;选项卡，选择&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接。

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* 选择&#x200B;**[!UICONTROL Keep only the first records after sorting]**&#x200B;选项并选择排序列。 勾选 **[!UICONTROL Descending sort]** 选项。

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* 单击&#x200B;**[!UICONTROL Next]**&#x200B;按钮，将记录数限制为5。

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* 单击&#x200B;**[!UICONTROL Finish]**，然后重新启动工作流以批准定位。

## 数据标准化 {#standardizing-data}

可以在Adobe Campaign中为使用别名收集的数据设置标准化流程。 这样，您就可以标准化存储在数据库中的数据：为此，请在包含相关信息的分项列表中定义别名。 [了解详情](../../platform/using/managing-enumerations.md#about-enumerations)
