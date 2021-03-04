---
solution: Campaign Classic
product: campaign
title: '"用例：显示在线调查的答案报告"'
description: '"用例：显示在线调查的答案报告"'
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 6%

---


# 用例：显示有关在线调查答案的报告{#use-case-displaying-report-on-answers-to-an-online-survey}

可使用专用报告收集和分析Adobe Campaign调查的答案。

在以下示例中，我们要收集在线调查的答案并在透视表中显示

应用以下步骤：

1. 创建一个工作流，以恢复调查的答案并将其存储在列表中。
1. 使用多维数据集中的数据创建列表。
1. 使用透视表创建报表并查看答案划分。

在开始使用此用例之前，您需要具有访问调查和一组可分析的答案的权限。

>[!NOTE]
>
>仅当您获得了&#x200B;**调查管理器**&#x200B;选项时，才能实现此用例。 请核实您的许可协议。

## 步骤1 — 创建数据收集和存储工作流{#step-1---creating-the-data-collection-and-storage-workflow}

要收集调查的答案，请应用以下步骤：

1. 创建工作流并放置&#x200B;**[!UICONTROL Answers to a survey]**&#x200B;活动。 有关使用此活动的详细信息，请参阅[此部分](../../web/using/publish--track-and-use-collected-data.md#using-the-collected-data)。
1. 编辑活动并选择要分析其答案的调查。
1. 启用&#x200B;**[!UICONTROL Select all the answer data]**&#x200B;选项可收集所有信息。

   ![](assets/reporting_usecase_1_01.png)

1. 选择要提取的列(在本例中为：选择：所有已存档的字段。 这些字段包含答案。

   ![](assets/reporting_usecase_1_02.png)

1. 配置答案收集框后，放置&#x200B;**[!UICONTROL List update]**&#x200B;类型活动以保存数据。

   ![](assets/reporting_usecase_1_04.png)

   在此活动中，指定要更新的列表并取消选中&#x200B;**[!UICONTROL Purge and re-use the list if it exists (otherwise add to the list)]**&#x200B;选项：答案将添加到现有表中。 此选项将允许您在多维数据集中引用列表。 链接到列表的模式不会针对每次更新重新生成，这将保证使用此列表的多维数据集的完整性。

   ![](assets/reporting_usecase_1_03.png)

1. 开始工作流以确认其配置。

   ![](assets/reporting_usecase_1_05.png)

   将创建指定的列表，并包含调查答案的模式。

1. 添加调度程序，自动完成每日的答案收集和列表更新。

   **[!UICONTROL List update]**&#x200B;和&#x200B;**[!UICONTROL Scheduler]**&#x200B;活动详见。

## 第2步 — 创建多维数据集、度量及其指标{#step-2---creating-the-cube--its-measures-and-its-indicators}

然后，您可以创建多维数据集并配置其度量：它们将用于创建将在报告中显示的指标。 有关创建和配置多维数据集的详细信息，请参阅[关于多维数据集](../../reporting/using/about-cubes.md)。

在此示例中，多维数据集基于之前创建的工作流馈送的列表中的数据。

![](assets/reporting_usecase_2_01.png)

定义要在报表中显示的维和度量。 在此，我们要显示被申请人的合同日期和国家/地区。

![](assets/reporting_usecase_2_02.png)

使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡可以控制报表的呈现。

## 第3步 — 创建报表并配置表{#step-3---creating-the-report-and-configuring-the-data-layout-within-the-table}中的数据布局

然后，您可以根据此多维数据集创建报告并处理数据和信息。

![](assets/reporting_usecase_3_01.png)

根据您的需求调整信息以进行显示。

![](assets/reporting_usecase_3_02.png)

