---
title: '"用例：显示在线调查的答案报告"'
seo-title: '"用例：显示在线调查的答案报告"'
description: '"用例：显示在线调查的答案报告"'
seo-description: null
page-status-flag: never-activated
uuid: 2c0a5b7d-c606-4bcb-9600-8f89e6fce32a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 5404a227-6cfb-463b-9a56-af46a022eb38
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 10%

---


# 用例：显示在线调查的答案报告{#use-case-displaying-report-on-answers-to-an-online-survey}

可使用专门的报告收集和分析Adobe Campaign调查的答案。

在以下示例中，我们要收集在线调查的答案并在透视表中显示它们

应用以下步骤：

1. 创建工作流以恢复对调查的回答并将其存储在列表中。
1. 使用多维数据集中的数据创建列表。
1. 使用透视表创建报表并查看答案细分。

在开始使用此用例之前，您需要有权访问调查和一组可以分析的答案。

>[!NOTE]
>
>仅当您获得了调查管理器选项时，才可 **以实现此用** 例。 请核实您的许可协议。

## 第1步——创建数据收集和存储工作流 {#step-1---creating-the-data-collection-and-storage-workflow}

要收集调查的答案，请应用以下步骤：

1. 创建工作流并放置 **[!UICONTROL Answers to a survey]** 活动。 For more on using this activity, refer to [this section](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data).
1. 编辑活动，并选择要分析其答案的调查。
1. 启用此 **[!UICONTROL Select all the answer data]** 选项可收集所有信息。

   ![](assets/reporting_usecase_1_01.png)

1. 选择要提取的列(在本例中为：选择：所有存档字段。 这些字段包含答案。

   ![](assets/reporting_usecase_1_02.png)

1. 配置答案收集框后，放置一个 **[!UICONTROL List update]** 类型活动以保存数据。

   ![](assets/reporting_usecase_1_04.png)

   在此活动中，指定要更新的列表并取消选 **[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]** 项：答案将添加到现有表中。 此选项将允许您在列表中引用多维数据集。 链接到列表的模式不会针对每次更新重新生成，这将保证使用此列表的多维数据集的完整性。

   ![](assets/reporting_usecase_1_03.png)

1. 开始工作流以确认其配置。

   ![](assets/reporting_usecase_1_05.png)

   将创建指定的列表，并包括调查答案的模式。

1. 添加调度程序，以自动收集每日答案和列表更新。

   有关 **[!UICONTROL List update]** 和 **[!UICONTROL Scheduler]** 活动的详细信息，请参见。

## 第2步——创建多维数据集、衡量指标 {#step-2---creating-the-cube--its-measures-and-its-indicators}

然后，您可以创建多维数据集并配置其度量：它们将用于创建将在报告中显示的指标。 有关创建和配置多维数据集的详细信息，请参阅 [关于多维数据集](../../reporting/using/about-cubes.md)。

在此示例中，多维数据集基于之前创建的工作流馈送的列表中的数据。

![](assets/reporting_usecase_2_01.png)

定义要在报表中显示的维和度量。 在此，我们要显示合同日期和被申请人的国家／地区。

![](assets/reporting_usecase_2_02.png)

使用 **[!UICONTROL Preview]** 选项卡可以控制报表的呈现。

## 第3步——创建报表并在表中配置数据布局 {#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}

然后，您可以根据此多维数据集创建报告并处理数据和信息。

![](assets/reporting_usecase_3_01.png)

根据您的需求调整信息以显示。

![](assets/reporting_usecase_3_02.png)

