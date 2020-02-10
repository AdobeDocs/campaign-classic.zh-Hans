---
title: 创建摘要列表
seo-title: 创建摘要列表
description: 创建摘要列表
seo-description: null
page-status-flag: never-activated
uuid: ea9d097d-d474-47e6-b0d7-08d587666a55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6b0acb6b-0808-4972-b2a2-15fab29b3861
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 创建摘要列表{#creating-a-summary-list}

此用例详细介绍了工作流的创建过程，在收集文件并进行多个增强后，您可以创建摘要列表。 该示例基于在商店中购买的联系人列表。

![](assets/uc2_enrich_overview.png)

使用以下数据结构：

![](assets/uc2_enrich_data.png)

其目的是：

* 使用浓缩活动的各种选项
* 在对帐之后更新数据库中的数据
* 创建丰富数据的全局“视图”

要创建摘要列表，您需要执行以下步骤：

1. 在工作流的工作表中收集和加载“购买”文件
1. 通过创建指向参考表的链接来丰富导入的数据
1. 使用丰富的数据更新“购买”表
1. 从“采购”表中用汇总计算来丰富“联系人”数据
1. 创建摘要列表

## 第1步：加载文件并协调导入的数据 {#step-1--loading-the-file-and-reconciling-the-imported-data}

要加载的数据是与“购买”相关的数据，其格式如下：

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

1. 将“文件” **收集器****和“数据加载（文件）** ”活动添加到工作流。

   “文 **件”收集器** (File collector)活动允许您从Adobe Campaign服务器收集文件并将其发送到Adobe Campaign服务器。

   通过 **数据加载（文件）** ，您可以使用收集的数据丰富工作流的工作表。

   有关此活动的详细信息，请参阅 [从文件加载数据](../../workflow/using/importing-data.md#loading-data-from-a-file)。

1. 将“文 **件”(File** )收集器活动配置为从所选目录收集文本(*.txt)类型文件。

   ![](assets/uc2_enrich_collecteur.png)

   “文 **件”(File** )收集器活动允许您管理源目录中文件的缺失情况。 要执行此操作，请选中该 **[!UICONTROL Process file nonexistence]** 选项。 在此工作流中，如果 **** 在集合时的目录中缺少另一个文件集合，则会添加一个等待活动以尝试其他文件集合。

1. 使用与 **** 要导入的数据格式相同的示例文件配置数据加载（文件）活动。

   ![](assets/uc2_enrich_chargement1.png)

   单击链 **[!UICONTROL Click here to change the file format...]** 接以使用“购买”表的内部名称和标签重命名这些列。

   ![](assets/uc2_enrich_chargement2.png)

导入数据后，通过创建与“商店”模式匹配的引用表的链接来进行扩充。

添加丰富化活动并进行如下配置：

1. 从“数据加载（文件）”活动中选择由 **数据组成的主集** 。

   ![](assets/uc2_enrich_enrich1.png)

1. 单 **[!UICONTROL Add data]**&#x200B;击，然后选择选 **[!UICONTROL A link]** 项。

   ![](assets/uc2_enrich_enrich2.png)

1. 选择选 **[!UICONTROL Define a collection]** 项。
1. 选择“商店”架构作为目标。

   ![](assets/uc2_enrich_enrich3.png)

有关各种链接类型的详细信息，请参阅 [丰富和修改数据](../../workflow/using/targeting-data.md#enriching-and-modifying-data)。

在以下窗口中，您需要通过选择源字段（在主集中）和目标字段（属于“商店”架构）来创建连接条件，以配置数据协调。

![](assets/uc2_enrich_enrich4.png)

现在，链接已创建，我们将从“商店”架构向工作流的工作表添加一列：“ZipCode Reference”字段。

1. 打开浓缩活动。
1. 单击 **[!UICONTROL Edit additional data]**.
1. 将“ZipCode Reference”字段添加到 **[!UICONTROL Output columns]**。

![](assets/uc2_enrich_enrich5.png)

此次扩充后，工作流的工作表中的数据将如下：

![](assets/uc2_enrich_population1.png)

## 第2步：将丰富的数据写入“购买”表 {#step-2--writing-enriched-data-to-the--purchases--table}

此步骤详细说明如何将导入的丰富数据写入“购买”表。 为此，我们需要使用“更新” **数据活动** 。

必须在更新“购买”( **Purchases** )表中的数据之前，对工作流的工作表中的数据与“购买”( **Purchases** )定位维之间的对帐。

1. 单击丰 **[!UICONTROL Reconciliation]** 富化活动的选项卡。
1. 选择定位维，在此例中为“购买”架构。
1. 为工作流表中的数据选择“源表达式”（本例中为“storeName”字段）。
1. 在“购买”表（本例中为“storename”字段）中为数据选择“目标表达式”。
1. 选中该 **[!UICONTROL Keep unreconciled data coming from the work table]** 选项。

![](assets/uc2_enrich_reconciliation.png)

在“更 **新数据** ”活动中，需要以下配置：

1. 在字段 **[!UICONTROL Insert or update]** 中选择该选 **[!UICONTROL Operation type]** 项，以避免每次收集文件时创建新记录。
1. 选择 **[!UICONTROL By directly using the targeting dimension]** 选项的 **[!UICONTROL Record identification]** 值。
1. 选择“购买”架构作为 **[!UICONTROL Document type]**。
1. 指定要更新的字段列表。 通过 **[!UICONTROL Destination]** 该列可定义“购买”架构的字段。 该 **[!UICONTROL Expression]** 列允许您选择工作表中的字段以执行映射。
1. 单击选 **[!UICONTROL Generate an outbound transition]** 项。

![](assets/uc2_enrich_miseajour.png)

## 第3步：丰富“联系人”数据 {#step-3--enriching--contact--data-}

“联系人”架构物理上链接到“购买”架构。 这意味着您可以使用“丰富化”选项的其他选项：添加链接到过滤维的数据。

第二次扩充的目的是在购买架构上创建聚合，以计算每个已识别联系人的总购买量。

1. 添加查 **询类型** ，以便恢复存储的所 **有Contact** 。
1. 添加丰 **富化** ，然后选择上一个查询生成的主集。
1. 单击“添加” **[!UICONTROL Data]**。
1. 单击选 **[!UICONTROL Data linked to the targeting dimension]** 项。
1. 单击窗 **[!UICONTROL Data linked to the filtering dimension]** 口中的选 **[!UICONTROL Select fields to add]** 项。
1. 选择节 **[!UICONTROL Purchases]** 点，然后单击 **[!UICONTROL Next]**。

   ![](assets/uc2_enrich_enrich9.png)

1. 通过选 **[!UICONTROL Collected data]** 择选项更改字 **[!UICONTROL Aggregates]** 段。

   ![](assets/uc2_enrich_enrich10.png)

1. 单击 **[!UICONTROL Next]**.
1. 添加以下表达式来计算每个联系人的购买总数：&quot;Sum(@prodprice)&quot;。

   ![](assets/uc2_enrich_enrich6.png)

要准备摘要列表，您需要从“购买”字段和第一个丰富内容添加字段：“ZipCode Reference”字段。

1. 单击丰 **[!UICONTROL Edit additional data...]** 富化活动中的链接。
1. 添加“商店名称”和“购买／邮政编码参考”字段。

   ![](assets/uc2_enrich_enrich7.png)

1. 单击选 **[!UICONTROL Properties]** 项卡。
1. 更改第二个链接以仅创建一行。

   ![](assets/uc2_enrich_enrich8.png)

## 第4步：创建和添加到摘要列表 {#step-4--creating-and-adding-to-a-summary-list}

最后一步是将所有丰富数据写入列表。

1. 向工作流 **中添加** “列表”更新活动。 此活动必须与第二次浓缩活动的对外转移相关联。
1. 选择选 **[!UICONTROL Create the list if necessary (Calculated name)]** 项。
1. 为计算的名称选择一个值。 为列表选择的标签是当前日期：&lt;%= formatDate(new Date(), &quot;%2D/%2M/%2Y&quot;)%>。

执行工作流后，列表将包括：

* 联系人名单，
* “购买总数”列，
* “商店名称”列，
* 为包含在商店引用架构中的所有商店输入“邮政编码引用”列。

![](assets/uc2_enrich_listfinal.png)

