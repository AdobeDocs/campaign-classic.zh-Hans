---
product: campaign
title: 数据提取（文件）
description: 了解有关数据提取（文件）工作流活动的更多信息
feature: Workflows, Data Management Activity
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# 数据提取（文件）{#extraction-file}



您可以使用&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活动从外部文件的工作流表中提取数据。

>[!CAUTION]
>
>此活动必须始终具有包含要提取的数据的集客过渡。

要配置数据提取，请应用以下步骤：

1. 指定输出文件的名称：此名称可以包含变量，这些变量通过字段右侧的个性化按钮插入。
1. 单击&#x200B;**[!UICONTROL Edit the file format...]**&#x200B;以选择要提取的数据。

   ![](assets/s_advuser_extract_file_param.png)

   **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;选项添加了一个额外的步骤来筛选聚合的最终结果，例如对给定采购订单类型、已订购超过10次的客户等。

1. 如有必要，可以向输出文件添加新列，例如计算或处理结果。 为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;图标。

   ![](assets/s_advuser_extract_file_add_col.png)

   在其他行中，单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标以定义新列的内容。

   ![](assets/s_advuser_extract_file_add_exp.png)

   然后，您将访问选择窗口。 单击&#x200B;**[!UICONTROL Advanced selection]**&#x200B;选择要应用于数据的进程。

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   从列表中选择所需的公式。

   ![](assets/s_advuser_extract_file_agregate_values.png)

您可以定义在数据提取期间执行的后处理，从而允许您压缩或加密文件。 为此，必须在活动的&#x200B;**[!UICONTROL Script]**&#x200B;选项卡中添加所需的命令。

有关详细信息，请参阅以下部分：[压缩或加密文件](../../platform/using/zip-encrypt.md)

![](assets/postprocessing_dataextraction.png)

## 集合函数列表 {#list-of-aggregate-functions}

以下是可用集合函数的列表：

* **[!UICONTROL Count]**&#x200B;以计算要聚合的字段的所有非空值，包括（聚合字段的）重复值，

  **[!UICONTROL Distinct]**&#x200B;以计算要聚合的字段的不同值和非null值的总数（在计算之前将排除重复值），

* **[!UICONTROL Sum]**&#x200B;计算数值字段的值的总和，
* **[!UICONTROL Minimum value]**&#x200B;计算字段的最小值（数字或其他），
* **[!UICONTROL Maximum value]**&#x200B;计算字段的最大值（数字或其他），
* **[!UICONTROL Average]**&#x200B;计算数值字段值的平均值。
