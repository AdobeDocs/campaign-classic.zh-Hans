---
product: campaign
title: "用例：显示在线调查的答案报告"
description: "用例：显示在线调查的答案报告"
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting, Surveys
exl-id: 6be12518-86d1-4a13-bbc2-b2ec5141b505
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 6%

---

# 用例：显示在线调查的答案报告{#use-case-displaying-report-on-answers-to-an-online-survey}



Adobe Campaign调查的答案可以使用专门的报告进行收集和分析。

在以下示例中，我们希望收集在线调查的回答并将其显示在数据透视表中

应用以下步骤：

1. 创建工作流以恢复调查答案并将其存储到列表中。
1. 使用列表中的数据创建多维数据集。
1. 使用数据透视表创建报表并查看答案的细分。

在开始使用此用例之前，您需要有权访问调查和一组可分析的答案。

>[!NOTE]
>
>仅当您已获得 **调查管理器** 选项。 请核实您的许可协议。

## 步骤1 — 创建数据收集和存储工作流 {#step-1---creating-the-data-collection-and-storage-workflow}

要收集调查的答案，请应用以下步骤：

1. 创建工作流并放置 **[!UICONTROL Answers to a survey]** 活动。 有关使用此活动的更多信息，请参阅 [本节](../../surveys/using/publish--track-and-use-collected-data.md#using-the-collected-data).
1. 编辑活动并选择要分析其答案的调查。
1. 启用 **[!UICONTROL Select all the answer data]** 用于收集所有信息的选项。

   ![](../../surveys/using/assets/reporting_usecase_1_01.png)

1. 选择要提取的列（在此例中：选择：所有已存档字段）。 这些是包含答案的字段。

   ![](../../surveys/using/assets/reporting_usecase_1_02.png)

1. 配置应答收集框后，将 **[!UICONTROL List update]** 键入activity以保存数据。

   ![](../../surveys/using/assets/reporting_usecase_1_04.png)

   在此活动中，指定要更新的列表并取消选中 **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** 选项：将答案添加到现有表中。 利用此选项，可引用多维数据集中的列表。 每次更新都不会重新生成链接到列表的架构，从而确保使用此列表的多维数据集的完整性。

   ![](../../surveys/using/assets/reporting_usecase_1_03.png)

1. 启动工作流以确认其配置。

   ![](../../surveys/using/assets/reporting_usecase_1_05.png)

   将创建指定的列表，并包含调查答案的架构。

1. 添加调度程序以自动每日收集答案并更新列表。

   此 **[!UICONTROL List update]** 和 **[!UICONTROL Scheduler]** 有关活动的详情，请参阅。

## 步骤2 — 创建多维数据集、其度量及其指示器 {#step-2---creating-the-cube--its-measures-and-its-indicators}

然后，可以创建立方并配置其度量：它们将用于创建将在报告中显示的指标。 有关创建和配置多维数据集的更多信息，请参阅 [关于多维数据集](../../reporting/using/ac-cubes.md).

在此示例中，多维数据集基于先前创建的工作流馈送的列表中的数据。

![](../../surveys/using/assets/reporting_usecase_2_01.png)

定义要在报告中显示的维度和度量。 在这里，我们要显示合同日期和被申请人的国家/地区。

![](../../surveys/using/assets/reporting_usecase_2_02.png)

此 **[!UICONTROL Preview]** 选项卡可让您控制报告的呈现。

## 第3步 — 创建报告并配置表中的数据布局 {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

然后，您可以基于此多维数据集创建报告，并处理数据和信息。

![](../../surveys/using/assets/reporting_usecase_3_01.png)

根据您的需求调整信息以显示。

![](../../surveys/using/assets/reporting_usecase_3_02.png)
