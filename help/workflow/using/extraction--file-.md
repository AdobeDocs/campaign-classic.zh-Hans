---
product: campaign
title: 数据提取（文件）
description: 进一步了解数据提取（文件）工作流活动
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---

# 数据提取（文件）{#extraction-file}

![](../../assets/common.svg)

您可以使用&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活动从外部文件的工作流表中提取数据。

>[!CAUTION]
>
>此活动必须始终包含集客过渡，其中包含要提取的数据。

要配置数据提取，请应用以下步骤：

1. 指定输出文件的名称：此名称可包含变量，变量可通过字段右侧的个性化按钮插入。
1. 单击&#x200B;**[!UICONTROL Edit the file format...]**&#x200B;以选择要提取的数据。

   ![](assets/s_advuser_extract_file_param.png)

   **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;选项添加了一个额外步骤来筛选聚合的最终结果，例如，在给定的采购订单类型、订购次数超过10次的客户等上。

1. 如有必要，您可以向输出文件添加新列，例如计算或处理结果。 为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;图标。

   ![](assets/s_advuser_extract_file_add_col.png)

   在另一行中，单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标以定义新列的内容。

   ![](assets/s_advuser_extract_file_add_exp.png)

   然后，您将访问选择窗口。 单击&#x200B;**[!UICONTROL Advanced selection]**&#x200B;以选择要应用于数据的进程。

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   从列表中选择所需的公式。

   ![](assets/s_advuser_extract_file_agregate_values.png)

您可以定义在数据提取期间要执行的后处理，从而允许您压缩或加密文件。 要实现此目的，必须在活动的&#x200B;**[!UICONTROL Script]**&#x200B;选项卡中添加所需的命令。

有关更多信息，请参阅此章节：[压缩或加密文件](how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

![](assets/postprocessing_dataextraction.png)

## 聚合函数列表 {#list-of-aggregate-functions}

以下是可用聚合函数的列表：

* **[!UICONTROL Count]** 计算要聚合的字段的所有非空值，包括（聚合字段的重复值），

   **[!UICONTROL Distinct]** 要计算要聚合的字段的不同值和非空值的总数（在计算之前排除重复值），

* **[!UICONTROL Sum]** 计算数值字段值之和，
* **[!UICONTROL Minimum value]** 要计算字段的最小值（数值或其他），
* **[!UICONTROL Maximum value]** 要计算字段的最大值（数值或其他），
* **[!UICONTROL Average]** 以计算数值字段值的平均值。
