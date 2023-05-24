---
product: campaign
title: 向列表发送报告
description: 了解如何使用工作流将报告发送到列表
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: cb24aea5-f3c7-4b17-8899-1792ea18c235
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 1%

---

# 向列表发送报告{#sending-a-report-to-a-list}



此用例详细说明了如何每月生成一个现成的版本 **[!UICONTROL Tracking indicators]** PDF格式的报告，以及如何将其发送给收件人列表。

![](assets/use_case_report_intro.png)

此用例的主要实施步骤包括：

* 创建将接收投放的收件人列表(请参阅： [步骤1：创建收件人列表](#step-1--creating-the-recipient-list))。
* 创建投放模板，以便您每次执行工作流时都生成一个新投放(请参阅： [步骤2：创建投放模板](#step-2--creating-the-delivery-template))。
* 创建一个工作流，让您可以生成PDF格式的报告，并将其发送给收件人列表(请参阅： [步骤3：创建工作流](#step-3--creating-the-workflow))。

## 步骤1：创建收件人列表 {#step-1--creating-the-recipient-list}

转到 **[!UICONTROL Profiles and targets]** 选项卡，单击 **[!UICONTROL Lists]** 链接，然后 **[!UICONTROL Create]** 按钮。 选择 **[!UICONTROL New list]** 并为要发送的报告创建新的收件人列表。

![](assets/use_case_report_1.png)

有关创建列表的详细信息，请参阅此 [部分](../../platform/using/creating-and-managing-lists.md).

## 步骤2：创建投放模板 {#step-2--creating-the-delivery-template}

1. 转到 **[!UICONTROL Resources > Templates > Delivery templates]** Adobe Campaign节点并复制 **[!UICONTROL Email delivery]** 现成模板。

   ![](assets/use_case_report_2.png)

   有关创建投放模板的详细信息，请参阅此 [部分](../../delivery/using/about-templates.md).

1. 输入各种模板参数：标签、目标（以前创建的收件人列表）、主题和内容。

   ![](assets/use_case_report_3.png)

1. 每次执行工作流时， **[!UICONTROL Tracking indicators]** 报告已更新(请参阅 [步骤3：创建工作流](#step-3--creating-the-workflow))。 要在投放中包含最新版本的报表，您需要添加 **[!UICONTROL Calculated attachment]**：

   有关创建计算附件的详细信息，请参阅此 [部分](../../delivery/using/attaching-files.md#creating-a-calculated-attachment).

   * 单击 **[!UICONTROL Attachments]** 链接并单击 **[!UICONTROL Add]**，然后选择 **[!UICONTROL Calculated attachment]**.

      ![](assets/use_case_report_4.png)

   * 转到 **[!UICONTROL Type]** 字段并选择第四个选项： **[!UICONTROL File name is computed during delivery of each message (it may then depend on the recipient profile)]**.

      ![](assets/use_case_report_5.png)

      在中输入的值 **[!UICONTROL Label]** 字段不会显示在最终投放中。

   * 转到编辑区域并输入文件的访问路径和名称。

      ![](assets/use_case_report_6.png)

      >[!CAUTION]
      >
      >文件必须存在于服务器上。 其路径和名称必须与 **[!UICONTROL JavaScript code]** 工作流类型活动(请参阅： [步骤3：创建工作流](#step-3--creating-the-workflow))。

   * 选择 **[!UICONTROL Advanced]** 制表符和勾选 **[!UICONTROL Script the name of the file name displayed in the mails sent]**. 转到编辑区域，然后输入要为最终投放中的附件指定的名称。

      ![](assets/use_case_report_6bis.png)

## 步骤3：创建工作流 {#step-3--creating-the-workflow}

已为此用例创建以下工作流。 它包含三个活动：

* 一个 **[!UICONTROL Scheduler]** 键入可让您每月执行一次工作流的活动，
* 一个 **[!UICONTROL JavaScript code]** 键入可让您以PDF格式生成报表的活动，
* 一 **[!UICONTROL Delivery]** 键入使用之前创建的投放模板的活动。

![](assets/use_case_report_8.png)

1. 现在，转到 **[!UICONTROL Administration > Production > Technical workflows]** 节点并创建新工作流。

   ![](assets/use_case_report_7.png)

1. 首先添加 **[!UICONTROL Scheduler]** 键入并配置活动，以便工作流在每月第一个星期一执行。

   ![](assets/use_case_report_9.png)

   有关配置调度程序的详细信息，请参阅 [调度程序](scheduler.md).

1. 然后添加 **[!UICONTROL JavaScript code]** 键入activity。

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

   * **var reportName**：用双引号输入报表的内部名称。 在本例中， **跟踪指示器** 报告为“deliveryFeedback”。
   * **var路径**：输入文件的保存路径(“tmp/files/”)、要为文件指定的名称(“deliveryFeedback”)以及文件扩展名(“.pdf”)。 在本例中，我们使用内部名称作为文件名。 值需要位于双引号之间并以“+”字符分隔。

      >[!CAUTION]
      >
      >该文件必须保存在服务器上。 您必须在 **[!UICONTROL General]** 计算附件的“编辑”窗口的“选项卡”(请参阅： [步骤2：创建投放模板](#step-2--creating-the-delivery-template))。

   * **var exportFormat**：输入文件的导出格式(PDF)。
   * **var _ctx** （上下文）：在本例中，我们使用 **[!UICONTROL Tracking indicators]** 在其全局上下文中报告。

1. 通过添加 **[!UICONTROL Delivery]** 使用以下选项键入activity ：

   * **[!UICONTROL Delivery]**：选择 **[!UICONTROL New, created from a template]**，然后选择之前创建的投放模板。
   * 对于 **[!UICONTROL Recipients]** 和 **[!UICONTROL Content]** 字段，选择 **[!UICONTROL Specified in the delivery]**.
   * **[!UICONTROL Action to execute]**：选择 **[!UICONTROL Prepare and start]**.
   * 取消选中 **[!UICONTROL Generate an outbound transition]** 和 **[!UICONTROL Process errors]**.
   ![](assets/use_case_report_11.png)
