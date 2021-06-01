---
product: campaign
title: 向列表发送报告
description: 了解如何使用工作流将报表发送到列表
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: cb24aea5-f3c7-4b17-8899-1792ea18c235
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---

# 向列表发送报告{#sending-a-report-to-a-list}

此用例详细说明了如何以PDF格式生成每月开箱即用的&#x200B;**[!UICONTROL Tracking indicators]**&#x200B;报告，以及如何将其发送到收件人列表。

![](assets/use_case_report_intro.png)

此用例的主要实施步骤是：

* 创建接收投放的收件人列表(请参阅：[步骤1:创建收件人列表](#step-1--creating-the-recipient-list))。
* 创建投放模板，以便您在每次执行工作流时都生成新投放(请参阅：[步骤2:创建投放模板](#step-2--creating-the-delivery-template))。
* 创建工作流，以便您生成PDF格式的报表，并将其发送到收件人列表(请参阅：[步骤3:创建工作流](#step-3--creating-the-workflow))。

## 步骤1:创建收件人列表{#step-1--creating-the-recipient-list}

转到&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;选项卡，单击&#x200B;**[!UICONTROL Lists]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Create]**&#x200B;按钮。 选择&#x200B;**[!UICONTROL New list]**&#x200B;并为要发送到的报表创建新收件人列表。

![](assets/use_case_report_1.png)

有关创建列表的更多信息，请参阅此[部分](../../platform/using/creating-and-managing-lists.md)。

## 步骤2:创建投放模板{#step-2--creating-the-delivery-template}

1. 转到Adobe Campaign资源管理器的&#x200B;**[!UICONTROL Resources > Templates > Delivery templates]**&#x200B;节点，并复制现成的&#x200B;**[!UICONTROL Email delivery]**&#x200B;模板。

   ![](assets/use_case_report_2.png)

   有关创建投放模板的更多信息，请参阅此[部分](../../delivery/using/about-templates.md)。

1. 输入各种模板参数：标签、目标（之前创建的收件人列表）、主题和内容。

   ![](assets/use_case_report_3.png)

1. 每次执行工作流时，都会更新&#x200B;**[!UICONTROL Tracking indicators]**&#x200B;报告(请参阅[步骤3:创建工作流](#step-3--creating-the-workflow))。 要在投放中包含最新版本的报表，您需要添加&#x200B;**[!UICONTROL Calculated attachment]**:

   有关创建计算附件的更多信息，请参阅此[部分](../../delivery/using/attaching-files.md#creating-a-calculated-attachment)。

   * 单击&#x200B;**[!UICONTROL Attachments]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Add]**，然后选择&#x200B;**[!UICONTROL Calculated attachment]**。

      ![](assets/use_case_report_4.png)

   * 转到&#x200B;**[!UICONTROL Type]**&#x200B;字段并选择第四个选项：**[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**。

      ![](assets/use_case_report_5.png)

      在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入的值将不会显示在最终投放中。

   * 转到编辑区域，然后输入文件的访问路径和名称。

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >服务器上必须存在文件。 其路径和名称必须与在工作流的&#x200B;**[!UICONTROL JavaScript code]**&#x200B;类型活动中输入的路径和名称相同(请参阅：[步骤3:创建工作流](#step-3--creating-the-workflow))。

   * 选择&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡并选中&#x200B;**[!UICONTROL Script the name of the file name displayed in the mails sent]**。 转到编辑区域，然后输入要在最终投放中提供附件的名称。

      ![](assets/use_case_report_6bis.png)

## 步骤3:创建工作流{#step-3--creating-the-workflow}

为此用例创建了以下工作流。 它有三项活动：

* **[!UICONTROL Scheduler]**&#x200B;类型的活动，允许您每月执行一次工作流，
* 一个&#x200B;**[!UICONTROL JavaScript code]**&#x200B;类型的活动，用于生成PDF格式的报表，
* 一个&#x200B;**[!UICONTROL Delivery]**&#x200B;类型的活动，使用之前创建的投放模板。

![](assets/use_case_report_8.png)

1. 现在转到&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;节点并创建新工作流。

   ![](assets/use_case_report_7.png)

1. 首先，添加&#x200B;**[!UICONTROL Scheduler]**&#x200B;类型的活动并对其进行配置，以便工作流在当月的第一个星期一执行。

   ![](assets/use_case_report_9.png)

   有关配置调度程序的更多信息，请参阅[调度程序](../../workflow/using/scheduler.md)。

1. 然后添加&#x200B;**[!UICONTROL JavaScript code]**&#x200B;类型活动。

   ![](assets/use_case_report_10.png)

   在编辑区域中输入以下代码：

   ```
   var reportName = "deliveryFeedback";
   var path = "/tmp/deliveryFeedback.pdf";
   var exportFormat = "PDF";
   var reportURL = "<PUT THE URL OF THE REPORT HERE>";
   var _ctx = <ctx _context="global" _reportContext="deliveryFeedback" />
   var isAdhoc = 0;
   
   xtk.report.export(reportName, _ctx, exportFormat, path, isAdhoc);
   ```

   使用以下变量：

   * **var reportName**:在报表的内部名称中输入双引号。在这种情况下，**跟踪指示器**&#x200B;报表的内部名称为“deliveryFeedback”。
   * **var路径**:输入文件的保存路径(&quot;tmp/files/&quot;)、要为文件提供的名称(&quot;deliveryFeedback&quot;)和文件扩展名(&quot;。pdf&quot;)。在本例中，我们使用内部名称作为文件名。 值必须介于双引号之间，并由“+”字符分隔。

      >[!CAUTION]
      >
      >文件必须保存在服务器上。 必须在计算附件的编辑窗口的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中输入相同的路径和相同的名称(请参阅：[步骤2:创建投放模板](#step-2--creating-the-delivery-template))。

   * **var exportFormat**:输入文件的导出格式(“PDF”)。
   * **var _ctx** (context):在本例中，我们将在其全 **[!UICONTROL Tracking indicators]** 局范围内使用报表。

1. 通过添加&#x200B;**[!UICONTROL Delivery]**&#x200B;类型活动完成，具有以下选项：

   * **[!UICONTROL Delivery]**:选择， **[!UICONTROL New, created from a template]**&#x200B;然后选择之前创建的投放模板。
   * 对于&#x200B;**[!UICONTROL Recipients]**&#x200B;和&#x200B;**[!UICONTROL Content]**&#x200B;字段，选择&#x200B;**[!UICONTROL Specified in the delivery]**。
   * **[!UICONTROL Action to execute]**:选择 **[!UICONTROL Prepare and start]**。
   * 取消选中&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;和&#x200B;**[!UICONTROL Process errors]**。
   ![](assets/use_case_report_11.png)
