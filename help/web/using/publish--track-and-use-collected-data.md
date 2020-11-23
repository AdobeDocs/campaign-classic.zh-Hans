---
solution: Campaign Classic
product: campaign
title: 发布、跟踪和使用收集的数据
description: 发布、跟踪和使用收集的数据
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---


# 发布、跟踪和使用收集的数据{#publish-track-and-use-collected-data}

创建、配置和发布表单后，您可以与受众共享该链接并跟踪响应。

>[!NOTE]
>
>Adobe Campaign调查的生命周期及其发布和投放模式与Web 窗体的生命周期相似：这些内容在本 [节中详细介绍](../../web/using/about-web-forms.md)。

## 调查仪表板 {#survey-dashboard}

每个调查都有自己的仪表板，您可以通过它视图其状态、描述、公共URL和可用性计划。 它还允许您视图可用的报表。 有关详细信息，请参阅 [调查报告](#reports-on-surveys)。

调查的公共URL显示在仪表板上：

![](assets/survey_public_url.png)

## 响应跟踪 {#response-tracking}

您可以在日志和报告中跟踪对调查的响应。

### 调查日志 {#survey-logs}

对于交付的每个调查，您都可以在选项卡中跟踪 **[!UICONTROL Logs]** 响应。 此选项卡显示已完成列表的用户的调查及其来源:

![](assets/s_ncs_admin_survey_logs.png)

多次-单击某行以显示被申请人填写的调查表单。 您可以全文浏览调查并完整访问答案。 这些文件可以导出到外部文件中。 For more on this, refer to [Exporting answers](#exporting-answers).

来源在调查URL中添加以下字符来指示：

```
?origin=xxx
```

在编辑调查时，其URL包含参 **[!UICONTROL __uuid]**&#x200B;数，该参数指示它处于测试阶段且尚未联机。 当您通过此URL访问调查时，在跟踪（报告）中不会考虑创建的记录。 来源被强制为值 **[!UICONTROL Adobe Campaign]**。

For more on URL parameters, refer to [this page](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### 调查报告 {#reports-on-surveys}

仪表板选项卡允许您访问调查报告。 单击报告名称以视图它。

![](assets/s_ncs_admin_survey_report_doc.png)

调查的结构在报告中可 **[!UICONTROL Documentation]** 见。

Web调查的其他两个报告位于 **[!UICONTROL Reports]** 调查的选项卡中： **[!UICONTROL General]** 和 **[!UICONTROL Breakdown of responses]**。

* 常规

   此报告包含有关调查的一般信息：响应数随时间的变化情况以及按来源和语言分布的情况。

   一般报告示例：

   ![](assets/s_ncs_admin_survey_report_0.png)

* 答复的细分

   此报告显示每个问题的答复细分。 此细分仅适用于对类型容器中存储的字段给出 **[!UICONTROL Question]** 的答案。 它仅对选择控件有效（例如，不对文本字段进行细分）。

   ![](assets/s_ncs_admin_survey_report_2.png)

## 导出答案 {#exporting-answers}

可将调查的答案导出到外部文件中，以备以后处理。 有两种方法可以实现此目的：

1. 导出报告数据

   要导出报告数据，请单击 **[!UICONTROL Export]** 按钮并选择导出格式。

   For more on exporting report data, refer to [this section](../../reporting/using/about-reports-creation-in-campaign.md).

1. 导出答案

   要导出答案，请单 **[!UICONTROL Responses]** 击调查的选项卡，然后右键单击。 选择 **[!UICONTROL Export...]**。

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   然后输入要导出的信息和存储文件。

   您可以在导出向导中配置输出文件的内容和格式。

   这样您可以：

   * 向输出文件添加列并恢复收件人（存储在数据库中）上的信息，
   * 格式化导出的数据，
   * 为文件中的信息选择编码格式。

   如果要导出的调查包含多个 **[!UICONTROL Multi-line text]** 或 **[!UICONTROL HTML text]** 字段，则必须以格式导 **[!UICONTROL XML]** 出。 为此，请在字段的下拉列表中选择此 **[!UICONTROL Output format]** 格式，如下所示：

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   单击 **[!UICONTROL Start]** 以运行导出。

   >[!NOTE]
   >
   >本节详细介绍数据导出及其配置 [的各个阶段](../../platform/using/generic-imports-and-exports.md)。

## 使用收集的数据 {#using-the-collected-data}

通过在线调查收集的信息可以在定位工作流的框架内恢复。 To do this, use the **[!UICONTROL Survey responses]** box.

在以下示例中，我们希望为至少有两个孩子的五个收件人制作一个Web优惠，并在一个在线调查中获得最高分。 本调查的答案是：

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

在定位工作流中， **[!UICONTROL Survey responses]** 将按如下方式配置：

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

开始，选择相关调查，然后在窗口的中央部分提取数据。 在这种情况下，我们至少需要提取得分列，因为它将用在拆分框中以恢复最高的五分。

单击链接以指示答案的筛选 **[!UICONTROL Edit query...]** 条件。

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

开始定位工作流。 查询恢复了8个收件人。

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

右键单击集合框的输出过渡以对其进行视图。

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

然后在工作流中放置一个拆分框以恢复得分最高的5个收件人。

编辑拆分框以进行配置：

* 开始，在标签中选择适当的 **[!UICONTROL General]** 模式，然后配置子集：

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* 转到选 **[!UICONTROL Sub-sets]** 项卡并选 **[!UICONTROL Limit the selected records]** 择选项，然后单击链 **[!UICONTROL Edit...]** 接。

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* 选择选 **[!UICONTROL Keep only the first records after sorting]** 项，然后选择排序列。 勾选 **[!UICONTROL Descending sort]** 选项。

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* 单击按 **[!UICONTROL Next]** 钮，将记录数限制为5。

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* 单击 **[!UICONTROL Finish]** 然后重新启动工作流以批准定位。

## 数据标准化 {#standardizing-data}

可以在Adobe Campaign中设置标准化流程，以便使用别名收集数据。 这使您能够标准化存储在数据库中的数据：为此，请在包含相关信息的分项列表中定义别名。

有关详细信息，请参见[此页面](../../platform/using/managing-enumerations.md#about-enumerations)。
