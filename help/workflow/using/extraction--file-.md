---
product: campaign
title: 数据提取（文件）
description: 了解有关数据提取（文件）工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Data Management Activity
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: 58998fa2480a33776507a434ed846541ac19e58b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 3%

---

# 数据提取（文件）{#extraction-file}



您可以使用从外部文件的工作流表中提取数据 **[!UICONTROL Data extraction (file)]** 活动。

>[!CAUTION]
>
>此活动必须始终具有包含要提取的数据的集客过渡。

要配置数据提取，请应用以下步骤：

1. 指定输出文件的名称：此名称可以包含变量，这些变量通过字段右侧的个性化按钮插入。
1. 单击 **[!UICONTROL Edit the file format...]** 以选择要提取的数据。

   ![](assets/s_advuser_extract_file_param.png)

   此 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 选项会添加额外的步骤来筛选聚合的最终结果，例如，对于给定的采购订单类型、已订购超过10次的客户等。

1. 如有必要，可以向输出文件添加新列，例如计算或处理结果。 要执行此操作，请单击 **[!UICONTROL Add]** 图标。

   ![](assets/s_advuser_extract_file_add_col.png)

   在其他行中，单击 **[!UICONTROL Edit expression]** 图标来定义新列的内容。

   ![](assets/s_advuser_extract_file_add_exp.png)

   然后，您将访问选择窗口。 单击 **[!UICONTROL Advanced selection]** 选择要应用于数据的进程。

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   从列表中选择所需的公式。

   ![](assets/s_advuser_extract_file_agregate_values.png)

您可以定义在数据提取期间执行的后处理，从而允许您压缩或加密文件。 要实现此目的，必须将所需的命令添加到 **[!UICONTROL Script]** 选项卡中。

有关更多信息，请参阅此章节： [压缩或加密文件](../../platform/using/zip-encrypt.md)

![](assets/postprocessing_dataextraction.png)

## 集合函数列表 {#list-of-aggregate-functions}

以下是可用集合函数的列表：

* **[!UICONTROL Count]** 要计算要聚合的字段的所有非空值，包括（聚合字段的）重复值，请执行以下操作：

  **[!UICONTROL Distinct]** 要计算要聚合的字段的不同和非空值的总数（在计算之前将排除重复值），请执行以下操作：

* **[!UICONTROL Sum]** 计算数值域值的和，
* **[!UICONTROL Minimum value]** 计算字段的最小值（数字或其他），
* **[!UICONTROL Maximum value]** 计算字段的最大值（数字或其他），
* **[!UICONTROL Average]** 计算数值字段值的平均值。
