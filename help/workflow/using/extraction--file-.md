---
title: 数据提取（文件）
description: 进一步了解数据提取（文件）工作流活动。
page-status-flag: never-activated
uuid: c1e3fde3-183c-4602-9cef-760e4648fcf7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: fe4e6f64-eb0a-44bc-8221-6c9bfb99871f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---


# 数据提取（文件）{#extraction-file}

您可以使用该活动从外部文件中的工作流表提取数 **[!UICONTROL Data extraction (file)]** 据。

>[!CAUTION]
>
>此活动必须始终具有包含要提取的数据的入站过渡。

要配置提取，请应用以下步骤：

1. 指定输出文件的名称：此名称可包含变量，这些变量通过字段右侧的个性化按钮插入。
1. 单 **[!UICONTROL Edit the file format...]** 击以选择要提取的数据。

   ![](assets/s_advuser_extract_file_param.png)

   此选 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 项会添加一个额外的步骤来筛选聚合的最终结果，例如，在给定的采购订单类型、订购次数超过10次的客户等。

1. 如有必要，可向输出文件添加新列，例如计算或处理结果。 为此，请单击图 **[!UICONTROL Add]** 标。

   ![](assets/s_advuser_extract_file_add_col.png)

   在其他行中，单击 **[!UICONTROL Edit expression]** 图标以定义新列的内容。

   ![](assets/s_advuser_extract_file_add_exp.png)

   然后，您将访问选择窗口。 单 **[!UICONTROL Advanced selection]** 击以选择要应用于数据的进程。

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   从列表中选择所需的公式。

   ![](assets/s_advuser_extract_file_agregate_values.png)

您可以定义要在数据提取期间执行的后期进程，以便压缩或加密文件。 为此，必须在活动的选项卡中添 **[!UICONTROL Script]** 加所需的命令。

有关此内容的详细信息，请参阅此部分： [压缩或加密文件](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

![](assets/postprocessing_dataextraction.png)

## List of aggregate functions {#list-of-aggregate-functions}

以下是可用聚合函数的列表:

* **[!UICONTROL Count]** 计算要聚集的字段的所有非空值，包括重复值（聚集字段的值）,

   **[!UICONTROL Distinct]** 要计算要聚合的字段的不同值和非空值的总数(在计算之前排除重复值),

* **[!UICONTROL Sum]** 计算数值域的值和，
* **[!UICONTROL Minimum value]** 计算字段的最小值（数字或其他）,
* **[!UICONTROL Maximum value]** 计算字段的最大值（数值或其他）,
* **[!UICONTROL Average]** 计算数值字段的平均值。

