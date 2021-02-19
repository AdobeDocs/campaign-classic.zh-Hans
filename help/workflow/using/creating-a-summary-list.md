---
solution: Campaign Classic
product: campaign
title: 创建摘要列表
description: 创建摘要列表
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: bb7e3ce726e2c589c033686cf3ab2960de140d91
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 2%

---


# 创建摘要列表{#creating-a-summary-list}

此用例详细介绍了工作流的创建过程，在收集文件并执行多个扩充后，您可以创建摘要列表。 此示例基于在商店中购买的联系人的列表。

![](assets/uc2_enrich_overview.png)

使用以下数据结构：

![](assets/uc2_enrich_data.png)

其目的是：

* 使用扩充活动的各种选项
* 在对帐后更新数据库中的数据
* 创建丰富数据的全球“视图”

要创建摘要列表，您需要执行以下步骤：

1. 在工作流的工作表中收集和加载“购买”文件
1. 通过创建指向参考表的链接来丰富导入的数据
1. 使用丰富的数据更新“购买”表
1. 通过“购买”表中的聚合计算来丰富“联系人”数据
1. 创建摘要列表

## 第1步：加载文件并协调导入的数据{#step-1--loading-the-file-and-reconciling-the-imported-data}

要加载的数据是“购买”相关数据，其格式如下：

```
Product Name;Product price;Store
Computer;2000;London 3
Tablet;600;Cambridge
Computer;2000;London 5
Comptuer;2000;London 8
Tablet;600;Cambridge
Phone;500;London 5
```

此数据包含在“Purchases.txt”文本文件中。

1. 将&#x200B;**文件收集器**&#x200B;和&#x200B;**数据加载（文件）**&#x200B;活动添加到工作流中。

   使用&#x200B;**文件收集器**&#x200B;活动，您可以从Adobe Campaign服务器收集文件并将文件发送到该服务器。

   **数据加载（文件）**&#x200B;活动允许您使用收集的数据丰富工作流的工作表。

   有关此活动的详细信息，请参阅[从文件](../../platform/using/import-export-workflows.md#loading-data-from-a-file)加载数据。

1. 配置&#x200B;**文件收集器**&#x200B;活动，从所选目录收集文本(*.txt)类型文件。

   ![](assets/uc2_enrich_collecteur.png)

   使用&#x200B;**文件收集器**&#x200B;活动，可以管理源目录中缺少文件的情况。 要执行此操作，请选中&#x200B;**[!UICONTROL Process file nonexistence]**&#x200B;选项。 在此工作流中，如果集合时目录中缺少&#x200B;**Wait**&#x200B;活动，则已添加 Wait以尝试其他文件集合。

1. 使用与要导入的数据格式相同的示例文件配置&#x200B;**数据加载（文件）**&#x200B;活动。

   ![](assets/uc2_enrich_chargement1.png)

   单击&#x200B;**[!UICONTROL Click here to change the file format...]**&#x200B;链接，使用“购买”表的内部名称和标签重命名列。

   ![](assets/uc2_enrich_chargement2.png)

导入数据后，通过创建与“存储”模式匹配的引用表的链接来执行扩充。

添加扩充活动并进行如下配置：

1. 从&#x200B;**数据加载（文件）**&#x200B;活动中选择由数据组成的主集。

   ![](assets/uc2_enrich_enrich1.png)

1. 单击&#x200B;**[!UICONTROL Add data]**，然后选择&#x200B;**[!UICONTROL A link]**&#x200B;选项。

   ![](assets/uc2_enrich_enrich2.png)

1. 选择&#x200B;**[!UICONTROL Define a collection]**&#x200B;选项。
1. 选择“商店”模式作为目标。

   ![](assets/uc2_enrich_enrich3.png)

有关各种链接类型的详细信息，请参阅[丰富和修改数据](../../workflow/using/targeting-data.md#enriching-and-modifying-data)。

在以下窗口中，您需要通过选择源字段（在主集中）和目标字段(属于“商店”模式)来创建连接条件来配置数据协调。

![](assets/uc2_enrich_enrich4.png)

现在，链接已创建，我们将从“商店”模式向工作流的工作表中添加一列：“邮政编码参考”字段。

1. 打开扩充活动。
1. 单击 **[!UICONTROL Edit additional data]**.
1. 在&#x200B;**[!UICONTROL Output columns]**&#x200B;中添加“ZipCode Reference”字段。

![](assets/uc2_enrich_enrich5.png)

此扩充后工作流的工作表中的数据将如下：

![](assets/uc2_enrich_population1.png)

## 第2步：将丰富数据写入“购买”表{#step-2--writing-enriched-data-to-the--purchases--table}

此步骤详细说明了如何将导入和丰富的数据写入“购买”表。 为此，我们需要使用&#x200B;**更新数据**&#x200B;活动。

在更新&#x200B;**Purchases**&#x200B;表中的数据之前，必须对工作流的工作表中的数据与&#x200B;**Purchases**&#x200B;定位维度进行协调。

1. 单击扩充活动的&#x200B;**[!UICONTROL Reconciliation]**&#x200B;选项卡。
1. 在此例中，选择定位维度“购买”模式。
1. 为工作流表中的数据（本例中为“storeName”字段）选择“源表达式”。
1. 在“购买”表（本例中为“storename”字段）中为数据选择“目标表达式”。
1. 勾选 **[!UICONTROL Keep unreconciled data coming from the work table]** 选项。

![](assets/uc2_enrich_reconciliation.png)

在&#x200B;**更新数据**&#x200B;活动中，需要以下配置：

1. 在&#x200B;**[!UICONTROL Operation type]**&#x200B;字段中选择&#x200B;**[!UICONTROL Insert or update]**&#x200B;选项，以避免每次收集文件时创建新记录。
1. 为&#x200B;**[!UICONTROL Record identification]**&#x200B;选项选择&#x200B;**[!UICONTROL By directly using the targeting dimension]**&#x200B;值。
1. 选择“购买”模式作为&#x200B;**[!UICONTROL Document type]**。
1. 指定要更新的字段的列表。 **[!UICONTROL Destination]**&#x200B;列允许您定义“购买”模式的字段。 **[!UICONTROL Expression]**&#x200B;列允许您选择工作表中的字段以执行映射。
1. 单击&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;选项。

![](assets/uc2_enrich_miseajour.png)

## 第3步：丰富“联系人”数据{#step-3--enriching--contact--data-}

“联系人”模式实际上链接到“购买”模式。 这意味着您可以使用“扩充”选项的其他选项：添加链接到过滤维度的数据。

此第二个扩充的目的是为购买模式创建一个聚合，以计算每个已识别联系人的总购买量。

1. 添加&#x200B;**查询**&#x200B;类型活动，可恢复所有存储的&#x200B;**联系人**。
1. 添加&#x200B;**扩充**&#x200B;活动，然后选择前一个查询生成的主集。
1. 单击“添加&#x200B;**[!UICONTROL Data]**”。
1. 单击&#x200B;**[!UICONTROL Data linked to the targeting dimension]**&#x200B;选项。
1. 单击&#x200B;**[!UICONTROL Select fields to add]**&#x200B;窗口中的&#x200B;**[!UICONTROL Data linked to the filtering dimension]**&#x200B;选项。
1. 选择&#x200B;**[!UICONTROL Purchases]**&#x200B;节点，然后单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/uc2_enrich_enrich9.png)

1. 通过选择&#x200B;**[!UICONTROL Aggregates]**&#x200B;选项更改&#x200B;**[!UICONTROL Collected data]**&#x200B;字段。

   ![](assets/uc2_enrich_enrich10.png)

1. 单击 **[!UICONTROL Next]**.
1. 添加以下表达式以计算每个联系人的购买总额：&quot;Sum(@prodprice)&quot;。

   ![](assets/uc2_enrich_enrich6.png)

要准备摘要列表，您需要从“购买”字段和第一个扩充添加字段：“邮政编码参考”字段。

1. 单击扩充活动中的&#x200B;**[!UICONTROL Edit additional data...]**&#x200B;链接。
1. 添加“商店名称”和“购买/邮政编码参考”字段。

   ![](assets/uc2_enrich_enrich7.png)

1. 单击&#x200B;**[!UICONTROL Properties]**&#x200B;选项卡。
1. 更改第二个链接，仅创建一行。

   ![](assets/uc2_enrich_enrich8.png)

## 第4步：创建并添加到摘要列表{#step-4--creating-and-adding-to-a-summary-list}

最后一步是将所有丰富数据写入列表。

1. 将&#x200B;**列表更新**&#x200B;活动添加到工作流。 此活动必须链接到第二个扩充活动的出站过渡。
1. 选择&#x200B;**[!UICONTROL Create the list if necessary (Calculated name)]**&#x200B;选项。
1. 为计算的名称选择一个值。 为列表选择的标签是当前日期：&lt;%= formatDate(new Date(), &quot;%2D/%2M/%2Y&quot;)%>。

执行工作流后，列表将包括：

* 一列表人，
* “购买总数”栏，
* “商店名称”列，
* 为包含在商店参考模式中的所有商店输入“邮政编码参考”列。

![](assets/uc2_enrich_listfinal.png)

