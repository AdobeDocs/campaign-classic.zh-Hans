---
product: campaign
title: 发布、跟踪和使用收集的数据
description: 了解如何发布、跟踪和使用调查中收集的数据
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Surveys
exl-id: 3cf3c486-6640-4d67-95cf-50d5767deb60
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 2%

---

# 发布、跟踪和使用收集的数据{#publish-track-and-use-collected-data}



创建、配置和发布表单后，您可以与受众共享该链接并跟踪响应。

>[!NOTE]
>
>Adobe Campaign中调查的生命周期及其发布和交付模式与Web窗体中的类似：这些在[此部分](../../web/using/about-web-forms.md)中有详细说明。

## 调查仪表板 {#survey-dashboard}

每个调查都有自己的信息板，允许您查看其状态、描述、公共URL和可用性计划。 它还允许您查看可用的报表。 [了解详情](#reports-on-surveys)。

调查的公共URL将显示在仪表板上：

![](assets/survey_public_url.png)

## 响应跟踪 {#response-tracking}

您可以在日志和报告中跟踪对调查的响应。

### 调查日志 {#survey-logs}

对于交付的每个调查，您可以在&#x200B;**[!UICONTROL Logs]**&#x200B;选项卡中跟踪响应。 此选项卡显示已完成调查的用户及其来源的列表：

![](assets/s_ncs_admin_survey_logs.png)

双击某行以显示由响应者填写的调查表单。 您可以完全浏览调查并完全访问答案。 这些文件可在外部文件中导出。 有关详情，请参阅[导出答案](#exporting-answers)。

调查URL中添加以下字符来指示来源：

```
?origin=xxx
```

在编辑调查时，其URL包含参数&#x200B;**[!UICONTROL __uuid]**，这表示调查处于测试阶段且尚未联机。 通过此URL访问调查时，创建的记录不会计入跟踪（报表）中。 源被强制设置为值&#x200B;**[!UICONTROL Adobe Campaign]**。

有关URL参数的详细信息，请参阅[此页面](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

### 调查报告 {#reports-on-surveys}

通过仪表板选项卡，可访问调查报表。 单击报表名称可查看它。

![](assets/s_ncs_admin_survey_report_doc.png)

调查的结构在&#x200B;**[!UICONTROL Documentation]**&#x200B;报表中可见。

调查的&#x200B;**[!UICONTROL Reports]**&#x200B;选项卡中有另外两个关于Web调查的报告可用： **[!UICONTROL General]**&#x200B;和&#x200B;**[!UICONTROL Breakdown of responses]**。

* 常规

  本报告载有调查的一般资料：答复数量如何随时间变化，以及按来源和语言的分布。

  常规报表示例：

  ![](assets/s_ncs_admin_survey_report_0.png)

* 响应的细分

  此报表显示每个问题的回复的细目。 此划分仅适用于为存储在&#x200B;**[!UICONTROL Question]**&#x200B;类型容器中的字段提供的答案。 它仅对选择控件有效（例如，不划分文本字段）。

  ![](assets/s_ncs_admin_survey_report_2.png)

## 导出答案 {#exporting-answers}

调查的答案可以导出到外部文件中以供稍后处理。 可通过两种方式来做到这一点：

1. 导出报表数据

   要导出报表数据，请单击&#x200B;**[!UICONTROL Export]**&#x200B;按钮并选择导出格式。

   有关导出报表数据的更多信息，请参阅[此章节](../../reporting/using/about-reports-creation-in-campaign.md)。

1. 导出答案

   要导出答案，请单击调查的&#x200B;**[!UICONTROL Responses]**&#x200B;选项卡并右键单击。 选择 **[!UICONTROL Export...]**。

   ![](assets/s_ncs_admin_survey_logs_export_menu.png)

   然后输入要导出的信息和存储文件。

   您可以在导出助理中配置输出文件的内容和格式。

   这允许您：

   * 向输出文件添加列，并恢复有关收件人（存储在数据库中）的信息，
   * 格式化导出的数据，
   * 选择文件中信息的编码格式。

   如果要导出的调查包含多个&#x200B;**[!UICONTROL Multi-line text]**&#x200B;或&#x200B;**[!UICONTROL HTML text]**&#x200B;字段，则必须以&#x200B;**[!UICONTROL XML]**&#x200B;格式导出该调查。 为此，请在&#x200B;**[!UICONTROL Output format]**&#x200B;字段的下拉列表中选择此格式，如下所示：

   ![](assets/s_ncs_admin_survey_logs_export_xml.png)

   单击&#x200B;**[!UICONTROL Start]**&#x200B;以运行导出。

   >[!NOTE]
   >
   >[此部分](../../platform/using/about-generic-imports-exports.md)中详细介绍了数据导出及其配置阶段。

## 使用收集的数据 {#using-the-collected-data}

通过在线调查收集的信息可在定位工作流的框架内恢复。 为此，请使用&#x200B;**[!UICONTROL Survey responses]**&#x200B;框。

在下面的示例中，我们要专门为五个在在线调查中至少有两个孩子且得分最高的收件人提供网络优惠。 本调查的答案是：

![](assets/s_ncs_admin_survey_responses_wf_box_4.png)

在定位工作流中，**[!UICONTROL Survey responses]**&#x200B;将按如下方式进行配置：

![](assets/s_ncs_admin_survey_responses_wf_box_1.png)

首先，选择相关的调查，然后在窗口的中央部分提取数据。 在这种情况下，我们至少需要提取得分列，因为它将在拆分框中用于取回五个最高分。

通过单击&#x200B;**[!UICONTROL Edit query...]**&#x200B;链接指示答案的过滤条件。

![](assets/s_ncs_admin_survey_responses_wf_box_2.png)

启动定位工作流。 查询恢复了8个收件人。

![](assets/s_ncs_admin_survey_responses_wf_box_5.png)

右键单击集合框的输出过渡可查看它们。

![](assets/s_ncs_admin_survey_responses_wf_box_6.png)

然后，在工作流中放置一个拆分框，以取回得分最高的5位收件人。

编辑拆分框以进行配置：

* 首先，在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中选择适当的架构，然后配置子集：

  ![](assets/s_ncs_admin_survey_responses_wf_box_6b.png)

* 转到&#x200B;**[!UICONTROL Sub-sets]**&#x200B;选项卡并选择&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接。

  ![](assets/s_ncs_admin_survey_responses_wf_box_7.png)

* 选择&#x200B;**[!UICONTROL Keep only the first records after sorting]**&#x200B;选项并选择排序列。 勾选 **[!UICONTROL Descending sort]** 选项。

  ![](assets/s_ncs_admin_survey_responses_wf_box_8.png)

* 单击&#x200B;**[!UICONTROL Next]**&#x200B;按钮并将记录数限制为5。

  ![](assets/s_ncs_admin_survey_responses_wf_box_9.png)

* 单击&#x200B;**[!UICONTROL Finish]**，然后重新启动工作流以批准定位。

## 标准化数据 {#standardizing-data}

可以在Adobe Campaign中为使用别名收集的数据设置标准化流程。 这使您能够标准化存储在数据库中的数据：为此，请在包含相关信息的明细列表中定义别名。 [了解详情](../../platform/using/managing-enumerations.md#about-enumerations)
