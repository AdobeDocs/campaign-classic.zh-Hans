---
title: 发布、跟踪和使用收集的数据
seo-title: 发布、跟踪和使用收集的数据
description: 发布、跟踪和使用收集的数据
seo-description: null
page-status-flag: never-activated
uuid: eac16f2c-0423-4727-a2da-3af1d6c616ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 434a4bda-0907-42a7-8a75-2db658bba046
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 发布、跟踪和使用收集的数据{#publish-track-and-use-collected-data}

创建、配置和发布表单后，您可以与受众共享该链接并跟踪响应。

>[!NOTE]
>
>Adobe Campaign中调查的生命周期及其发布和交付模式与Web表单的生命周期相似：本节详细介绍 [了这些内容](../../web/using/about-web-forms.md)。

## 调查仪表板 {#survey-dashboard}

每个调查都有其自己的仪表板，通过仪表板可以查看其状态、描述、公共URL和可用性计划。 它还允许您查看可用的报告。 有关详细信息，请参阅调 [查报告](#reports-on-surveys)。

仪表板中显示调查的公共URL:

![](assets/survey_public_url.png)

## 响应跟踪 {#response-tracking}

您可以在日志和报告中跟踪对调查的响应。

### 调查日志 {#survey-logs}

对于提交的每个调查，您都可以在选项卡中跟踪响 **[!UICONTROL Logs]** 应。 此选项卡显示已完成调查的用户列表及其来源：

![](assets/s_ncs_admin_survey_logs.png)

双击某行以显示由答复者填写的调查表单。 您可以全面浏览调查并完整访问答案。 这些文件可导出到外部文件中。 For more on this, refer to [Exporting answers](#exporting-answers).

调查URL中会添加以下字符来指示来源：

```
?origin=xxx
```

在编辑调查时，其URL包含参数 **[!UICONTROL __uuid]**，这表示调查处于测试阶段且尚未联机。 通过此URL访问调查时，在跟踪（报告）中不会考虑创建的记录。 将原点强制为值 **[!UICONTROL Adobe Campaign]**。

For more on URL parameters, refer to [this page](../../web/using/defining-web-forms-properties.md#form-url-parameters).

### 调查报告 {#reports-on-surveys}

使用功能板选项卡可访问调查报告。 单击报告名称可查看它。

![](assets/s_ncs_admin_survey_report_doc.png)

调查的结构可见于报 **[!UICONTROL Documentation]** 告。

有关网络调查的另外两份报告可在调查 **[!UICONTROL Reports]** 的选项卡中找到： **[!UICONTROL General]** 和 **[!UICONTROL Breakdown of responses]**。

* 常规

   本报告载有调查的一般信息：答复数随时间的变化情况以及按来源和语言的分布情况。

   一般报告示例：

   ![](assets/s_ncs_admin_survey_report_0.png)

* 答复的细分

   此报告显示每个问题的答复细分。 此细分仅对类型容器中存储的字段给出的 **[!UICONTROL Question]** 答案可用。 它仅对选择控件有效（例如，不对文本字段进行划分）。

   ![](assets/s_ncs_admin_survey_report_2.png)

## 导出答案 {#exporting-answers}

可以将调查的答案导出到外部文件中，以便以后处理。 有两种方法可以实现此目的：

1. 导出报告数据

   要导出报告数据，请单击 **[!UICONTROL Export]** 按钮并选择导出格式。

   有关导出报告数据的详细信息，请参 [阅此部分](../../reporting/using/about-reports-creation-in-campaign.md)。

1. 导出答案

   要导出答案，请单击 **[!UICONTROL Responses]** 调查的选项卡，然后右键单击。 Select **[!UICONTROL Export...]**.

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   然后输入要导出的信息和存储文件。

   您可以在导出向导中配置输出文件的内容和格式。

   这样，您可以：

   * 向输出文件添加列并恢复收件人（存储在数据库中）的信息，
   * 格式化导出的数据，
   * 为文件中的信息选择编码格式。
   如果要导出的调查包含多个或字 **[!UICONTROL Multi-line text]** 段， **[!UICONTROL HTML text]** 则必须以格式导出调查 **[!UICONTROL XML]** 。 为此，请在字段的下拉列表中选择此格 **[!UICONTROL Output format]** 式，如下所示：

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   单击 **[!UICONTROL Start]** 以运行导出。

   >[!NOTE]
   >
   >本节详细介绍了数据导出及其配置的 [各个阶段](../../platform/using/generic-imports-and-exports.md)。

## 使用收集的数据 {#using-the-collected-data}

通过在线调查收集的信息可以在定位工作流程的框架内被恢复。 为此，请使用框 **[!UICONTROL Survey responses]** 。

在以下示例中，我们希望为至少有两个子女的五个收件人提供Web选件，并在在线调查中获得最高分。 此次调查的答案是：

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

在定位工作流中，将 **[!UICONTROL Survey responses]** 按如下方式配置：

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

首先选择相关调查，然后在窗口的中央部分提取数据。 在这种情况下，我们至少需要提取得分列，因为它将用在拆分框中以恢复最高的五分。

单击链接以指示答案的筛选 **[!UICONTROL Edit query...]** 条件。

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

启动定位工作流。 查询将恢复8个收件人。

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

右键单击集合框的输出过渡可查看它们。

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

然后，在工作流中放置一个拆分框，以恢复得分最高的5个收件人。

编辑拆分框以进行配置：

* 首先，在选项卡中选择适当的架 **[!UICONTROL General]** 构，然后配置子集：

   ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* 转到选项卡 **[!UICONTROL Sub-sets]** 并选择相应的 **[!UICONTROL Limit the selected records]** 选项，然后单击链 **[!UICONTROL Edit...]** 接。

   ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* 选择选 **[!UICONTROL Keep only the first records after sorting]** 项，然后选择排序列。 选中该 **[!UICONTROL Descending sort]** 选项。

   ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* 单击 **[!UICONTROL Next]** 按钮，将记录数限制为5。

   ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* 单击 **[!UICONTROL Finish]** 然后重新启动工作流以批准定位。

## 标准化数据 {#standardizing-data}

可以在Adobe Campaign中为使用别名收集的数据设置标准化流程。 这使您能够标准化存储在数据库中的数据：为此，请在包含相关信息的分项列表中定义别名。

有关详细信息，请参见[此页面](../../platform/using/managing-enumerations.md#about-enumerations)。
