---
solution: Campaign Classic
product: campaign
title: 拆分
description: 进一步了解拆分工作流活动
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1935'
ht-degree: 0%

---


# 拆分{#split}

**Split**&#x200B;类型活动允许您将目标拆分为多个子集。 该目标由所有接收结果构成：因此，必须完成所有以前的活动才能执行此活动。

此活动不会触发入站人口的合并。 如果多个过渡以一个拆分活动着陆，我们建议在它前面插入一个&#x200B;**[!UICONTROL Union]**&#x200B;活动。

有关使用拆分活动的示例，请参阅[使用拆分活动](../../workflow/using/targeting-data.md#creating-subsets-using-the-split-activity)创建子集。

[本节](../../workflow/using/cross-channel-delivery-workflow.md)介绍了一个示例，说明如何使用“拆分”活动使用过滤条件将目标分割为不同的种群。

[此部分](../../workflow/using/javascript-scripts-and-templates.md)中提供了一个示例，说明如何在拆分活动中使用实例变量。

要配置此活动，请在&#x200B;**[!UICONTROL Subsets]**&#x200B;选项卡中定义子集内容和标签，然后在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中选择目标维。

## 创建子集{#creating-subsets}

要创建子集，请执行以下操作：

1. 单击匹配字段中的标签，然后选择要应用的过滤器。
1. 要过滤入站人口，请选择&#x200B;**[!UICONTROL Add a filtering condition]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接。

   选择要应用到数据的过滤器类型，以将其包含在此集中。

   该过程与&#x200B;**查询**&#x200B;类型活动的过程相同。

   >[!NOTE]
   >
   >最多可以过滤两个外部数据库(联合数据访问)中的数据。

1. 您可以指定要从目标中提取的最大记录数以创建子集。 要执行此操作，请选中&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接。

   通过向导，您可以选择此子集的记录的选择模式。 可在[限制子集记录数](#limiting-the-number-of-subset-records)中找到这些步骤。

   ![](assets/s_user_segmentation_partage4.png)

1. 如果您愿意，可以使用&#x200B;**[!UICONTROL Add]**&#x200B;按钮&#x200B;**添加其他子集**。

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >如果未选中&#x200B;**[!UICONTROL Enable overlapping of output populations]**&#x200B;选项，则按选项卡的顺序创建子集。 使用此窗口右上角的箭头移动它们。 例如，如果第一个子集恢复了初始种群的70%，则下一个子集将仅将其选择标准应用于其余的30%，依此类推。

   对于创建的每个子集，将向拆分过渡添加出站活动。

   ![](assets/s_user_segmentation_partage_add2.png)

   您可以选择生成单个出站过渡(例如，使用段代码标识集):要执行此操作，请在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中选择&#x200B;**[!UICONTROL Generate subsets in the same table]**&#x200B;选项。

   如果完成，则每个子集的段代码自动存储在附加列中。 此列可在投放级别的个性化字段中访问。

## 限制子集记录{#limiting-the-number-of-subset-records}

如果您不希望使用子集中包含的全部人口，可以限制将包含的记录数。

1. 在子集编辑窗口中，选中&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;选项并单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接。
1. 选择选择的限制类型：

   * **[!UICONTROL Activate random sampling]**:此选项将随机抽取记录。应用的随机采样类型取决于数据库引擎。
   * **[!UICONTROL Keep only the first records after sorting]**:此选项允许您根据一个或多个排序顺序定义限制。如果选择&#x200B;**[!UICONTROL Age]**&#x200B;字段作为排序标准，选择100作为限制，则只保留最小的100个收件人。
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**:此选项组合了前两个选项。它允许您根据一个或多个排序顺序定义限制，如果某些记录的值与定义的标准相同，则对第一个记录应用随机选择。

      例如，如果选择&#x200B;**[!UICONTROL Age]**&#x200B;字段作为排序标准，然后定义限制为100，但数据库中2000个最年轻的收件人都为18个，则将从这2000个中随机选择100个收件人。
   ![](assets/s_user_segmentation_partage_wz1.png)

1. 如果要定义排序标准，还可以通过附加步骤定义列和排序顺序。

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 然后选择数据限制方法。

   ![](assets/s_user_segmentation_partage_wz2.png)

   有多种方法可以实现此目的：

   * **[!UICONTROL Size (in %)]**:百分比的记录。例如，以下配置提取了总人口的10%。

      百分比适用于初始人口，而不是活动结果。

   * **[!UICONTROL Size (as a % of the segment)]**:仅与子集相关而与初始人口无关的记录的百分比。
   * **[!UICONTROL Maximum size]**:最大记录数。
   * **[!UICONTROL By data grouping]**:您可以根据入站人口的指定字段中的值设置记录数量限制。有关此主题的详细信息，请参阅[通过数据分组限制子集记录数](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data grouping (in %)]**:您可以根据入站人口的指定字段中的值使用百分比设置记录数量限制。有关此主题的详细信息，请参阅[通过数据分组限制子集记录数](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data distribution]**:如果分组字段的值太多，或者您希望避免为每个新拆分活动再次输入值，则Adobe Campaign允许您配置限 **[!UICONTROL By data distribution]** 制(可选分布式营销模块)。有关详细信息，请参阅[限制每个数据分发的子集记录数](#limiting-the-number-of-subset-records-per-data-distribution)。

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;以批准记录选择条件。 定义的配置随后将显示在编辑器的中间窗口中。

## 通过数据分组{#limiting-the-number-of-subset-records-by-data-grouping}限制子集记录数

您可以按数据分组限制记录数。 可以使用固定值或百分比执行此限制。

例如，如果选择&#x200B;**[!UICONTROL Language]**&#x200B;字段作为组字段，则可以为每种语言定义记录列表。

1. 选择数据限制值后，选择&#x200B;**[!UICONTROL By data grouping]**&#x200B;或&#x200B;**[!UICONTROL By data grouping (as a %)]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 然后选择分组字段（例如&#x200B;**[!UICONTROL Language]**&#x200B;字段），然后单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 最后，指定数据分组阈值（使用固定值或百分比，具体取决于先前选择的分组方法）。 要为每个值设置相同的阈值（例如，如果要将每种语言的记录数设置为10），请选择&#x200B;**[!UICONTROL All data groupings are the same size]**&#x200B;选项。 要为每个值设置不同的限制，请选择&#x200B;**[!UICONTROL Limitations by grouping value]**&#x200B;选项。 这将允许您为英语、法语等选择其他限制。

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;批准限制并返回编辑拆分活动。

## 限制每个数据分发的子集记录数{#limiting-the-number-of-subset-records-per-data-distribution}

如果您的分组字段包含的值过多，或者您希望避免重置每个新拆分活动的值，则Adobe Campaign允许您为每个数据分发创建限制。 在选择数据限制值（有关此主题的详细信息，请参阅[创建子集](#creating-subsets)部分）时，选择&#x200B;**[!UICONTROL By data distribution]**&#x200B;选项并从下拉菜单中选择模板。 创建数据分发模板如下所示。

有关具有分发模板的&#x200B;**[!UICONTROL Local approval]**&#x200B;活动的示例，请参阅[使用本地批准活动](../../workflow/using/using-the-local-approval-activity.md)。

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>要使用此函数，您需要购买分布式营销模块，这是一个活动选项。 请核实您的许可协议。

通过列表分组模板，可以限制记录数。 要创建数据分发模板，请应用以下步骤：

1. 要创建数据分发模板，请转至&#x200B;**[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;节点，然后单击&#x200B;**[!UICONTROL New]**。

   ![](assets/local_validation_data_distribution_1.png)

1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，可以输入分发的标签和执行上下文(定位维度、分发字段)。

   ![](assets/local_validation_data_distribution_2.png)

   需要输入以下字段：

   * **[!UICONTROL Label]**:“分发”模板的标签。
   * **[!UICONTROL Targeting dimension]**:例如，输入将应用数据分发的 **[!UICONTROL Recipient]** 定位维度。此模式必须始终与定位工作流中使用的数据兼容。
   * **[!UICONTROL Distribution field]**:通过定位维度选择字段。例如，如果选择&#x200B;**[!UICONTROL Email domain]**&#x200B;字段，则收件人列表将按域划分。
   * **[!UICONTROL Distribution type]**:在选项卡中选择目标的限制值划分方 **[!UICONTROL Distribution]** 式： **[!UICONTROL Percentage]** 或 **[!UICONTROL Set]**&#x200B;者
   * **[!UICONTROL Assignment type]**:选择数据分发分配类型。您可以按组或运算符进行分配或按本地实体进行分配。 在&#x200B;**分布式营销**&#x200B;中使用按本地实体赋值。 有关详细信息，请参阅此[部分](../../campaign/using/about-distributed-marketing.md)。
   * **[!UICONTROL Approval storage]**:如果您在定 **[!UICONTROL Local approval]** 位工作流中使用活动(请 [参阅本地审](../../workflow/using/local-approval.md)批)，请输入将存储审批结果的模式。必须为每个定位存储指定一个模式模式。 如果使用&#x200B;**[!UICONTROL Recipients]**&#x200B;定位模式，请输入默认的&#x200B;**[!UICONTROL Local approval of recipients]**&#x200B;存储模式。

      如果在未获得本地批准的情况下通过数据分组进行简单限制，则无需输入&#x200B;**[!UICONTROL Approvals storage]**&#x200B;字段。

1. 如果您使用&#x200B;**[!UICONTROL Local approval]**&#x200B;活动（请参阅[本地批准](../../workflow/using/local-approval.md)），请输入&#x200B;**[!UICONTROL Advanced settings]**&#x200B;作为分发模板：

   ![](assets/local_validation_data_distribution_3.png)

   需要输入以下字段：

   * **[!UICONTROL Approve targeted messages]**:如果希望从要批准的收件人的列表中预先选择所有收件人，请选中此选项。如果未选中此选项，则不会预先选择任何收件人。

      >[!NOTE]
      >
      >此选项默认处于选中状态。

      ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**:允许您定义表达式，以在返回通知中显示投放标签。默认表达式提供有关投放（计算字符串）标准标签的信息。 您可以修改此表达式。

      ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**:此字段允许您定义用于在审批和返回通知中显示收件人的分组。

      ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**:允许您将web应用程序链接到收件人列表。在批准和返回通知中，每个收件人都可单击，并将链接到选定的Web应用程序。 通过&#x200B;**[!UICONTROL Parameters]**&#x200B;字段（例如&#x200B;**[!UICONTROL recipientId]**）可配置要在URL和Web应用程序中使用的其他参数。

      ![](assets/local_validation_notification_5.png)

1. 使用&#x200B;**[!UICONTROL Breakdown]**&#x200B;选项卡可以定义分布值的列表。

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**:输入分配值。
   * **[!UICONTROL Percentage / Set]**:输入链接到每个值的记录限制（固定或百分比）。

      此列由&#x200B;**[!UICONTROL General]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Distribution type]**&#x200B;字段定义。

   * **[!UICONTROL Label]**:输入链接到每个值的标签。
   * **[!UICONTROL Group or operator]**:如果您使用的是 **[!UICONTROL Local approval]** 活动(请参 [阅本地批准](../../workflow/using/local-approval.md))，请选择分配给每个分配值的运算符或操作员组。

      如果在未获得本地批准的情况下通过数据分组进行简单限制，则无需输入&#x200B;**[!UICONTROL Group or operator]**&#x200B;字段。

      >[!IMPORTANT]
      >
      >确保已为操作员分配了适当的权限。

   * **[!UICONTROL Local entity]**:选择分配给每个分配值的本地实体。本地实体在&#x200B;**分布式营销**&#x200B;中使用。 有关详细信息，请参阅此[部分](../../campaign/using/about-distributed-marketing.md)。

## 筛选参数{#filtering-parameters}

单击&#x200B;**[!UICONTROL General]**&#x200B;选项卡以输入活动标签。 为此拆分选择目标和筛选尺寸。 如有必要，您可以更改给定子集的这些尺寸。

![](assets/s_user_segmentation_partage_general.png)

如果希望利用剩余人口，请选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。 补充是入站目标减去子集的合并。 随后将向该活动添加额外的出站过渡，如下所示：

![](assets/s_user_segmentation_partage_compl.png)

要使此选项正常工作，入站数据必须具有主键。

例如，如果通过&#x200B;**[!UICONTROL Data loading (RDBMS)]**&#x200B;活动直接从外部数据库(如Netezza，它不支持索引的概念)读取数据，则由&#x200B;**[!UICONTROL Split]**&#x200B;活动生成的补码将不正确。

要避免这种情况，可以在&#x200B;**[!UICONTROL Split]**&#x200B;活动前拖放&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动。 在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动中，检查&#x200B;**[!UICONTROL Keep all additional data from the main set]**&#x200B;并在其他数据中指定要用于配置&#x200B;**[!UICONTROL Split]**&#x200B;活动过滤器的列。 然后，来自&#x200B;**[!UICONTROL Split]**&#x200B;活动的入站过渡的数据被本地存储在Adobe Campaign服务器上的临时表中，并且可以正确生成补码。

使用&#x200B;**[!UICONTROL Enable overlapping of output populations]**&#x200B;选项可以管理属于几个子集的群体：

* 如果未选中该框，拆分活动将确保一个收件人不能出现在多个输出过渡中，即使它满足多个子集的条件也是如此。 它们将位于具有匹配条件的第一个选项卡的目标。
* 选中该框后，如果收件人符合筛选条件，则可以在多个子集中找到这些过滤器。 Adobe Campaign建议使用独占条件。

## 输入参数{#input-parameters}

* tableName
* 模式

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数{#output-parameters}

* tableName
* 模式
* recCount

这三组值标识排除所产生的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口的模式(通常是nms: **[!UICONTROL recCount]** 收件人)，是表中元素的数量。

与补码相关的过渡具有相同的参数。
