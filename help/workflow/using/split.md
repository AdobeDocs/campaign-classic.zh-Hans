---
product: campaign
title: 拆分
description: 了解有关拆分工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1935'
ht-degree: 0%

---

# 拆分{#split}



A **Split**-type活动允许您将目标拆分为多个子集。 使用所有接收的结果构建目标：因此，必须完成所有以前的活动，才能执行此活动。

此活动不会触发集客群体的联合。 如果多个过渡登陆在一个拆分活动中，我们建议插入 **[!UICONTROL Union]** 前面的活动。

有关正在使用的拆分活动的示例，请参阅 [使用拆分活动创建子集](targeting-data.md#creating-subsets-using-the-split-activity).

有关说明如何使用拆分活动通过筛选条件将目标分段为不同群体的示例，请参见 [本节](cross-channel-delivery-workflow.md).

有关如何在拆分活动中使用实例变量的示例，请参阅 [本节](javascript-scripts-and-templates.md).

要配置此活动，请在 **[!UICONTROL Subsets]** 选项卡，然后在中选择目标维度 **[!UICONTROL General]** 选项卡。

## 创建子集 {#creating-subsets}

要创建子集，请执行以下操作：

1. 单击匹配字段中的标签，然后选择要应用的过滤器。
1. 要筛选集客群体，请选择 **[!UICONTROL Add a filtering condition]** 选项，然后单击 **[!UICONTROL Edit...]** 链接。

   选择要应用于要包含在此集中的数据的过滤器类型。

   该过程与 **查询**&#x200B;类型活动。

   >[!NOTE]
   >
   >您最多可以筛选两个外部数据库(FDA)中的数据。

1. 您可以指定从目标提取的最大记录数以创建子集。 要执行此操作，请查看 **[!UICONTROL Limit the selected records]** 选项，然后单击 **[!UICONTROL Edit...]** 链接。

   向导允许您为此子集的记录选择模式。 这些步骤可在以下位置找到： [限制子集记录的数量](#limiting-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. 如果您愿意，可以 **添加其他子集** 使用 **[!UICONTROL Add]** 按钮。

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable overlapping of output populations]** 选项未选中，子集将按选项卡的顺序创建。 使用此窗口右上方的箭头移动它们。 例如，如果第一个子集恢复初始群体的70%，则下一个子集将仅对其余30%应用其选择标准，依此类推。

   对于创建的每个子集，叫客过渡都将添加到拆分活动中。

   ![](assets/s_user_segmentation_partage_add2.png)

   您可以选择生成单个叫客过渡（例如，使用段代码标识集）：要执行此操作，请选择 **[!UICONTROL Generate subsets in the same table]** 中的选项 **[!UICONTROL General]** 选项卡。

   如果完成，则每个子集的段代码将自动存储在一个附加列中。 可在投放级别的个性化字段中访问此列。

## 限制子集记录的数量 {#limiting-the-number-of-subset-records}

如果不希望使用子集中包含的整个群体，则可以限制它包含的记录数。

1. 在子集编辑窗口中，选中 **[!UICONTROL Limit the selected records]** 选项，然后单击 **[!UICONTROL Edit...]** 链接。
1. 为您的选择选择选择限制类型：

   * **[!UICONTROL Activate random sampling]**：此选项对记录进行随机取样。 应用的随机抽样类型取决于数据库引擎。
   * **[!UICONTROL Keep only the first records after sorting]**：利用此选项可根据一个或多个排序顺序定义限制。 如果您选择 **[!UICONTROL Age]** 字段作为排序标准，100作为限制，将仅保留最年轻的100个收件人。
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**：此选项是前两个选项的组合。 它允许您根据一个或多个排序顺序定义限制，然后在某些记录具有与定义的标准相同的值时，对第一个记录应用随机选择。

      例如，如果您选择 **[!UICONTROL Age]** 字段作为排序标准，然后您定义限制100，但数据库中2000个最年轻的收件人全部为18人，将从这些2000名收件人中随机选择100名。
   ![](assets/s_user_segmentation_partage_wz1.png)

1. 如果要定义排序标准，还可以通过额外的步骤来定义列和排序顺序。

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 然后选择数据限制方法。

   ![](assets/s_user_segmentation_partage_wz2.png)

   有多种方法可以做到这一点：

   * **[!UICONTROL Size (in %)]**：记录的百分比。 例如，以下配置提取了总人口的10%。

      百分比适用于初始群体，而不是活动结果。

   * **[!UICONTROL Size (as a % of the segment)]**：仅与子集而非初始群体相关的记录的百分比。
   * **[!UICONTROL Maximum size]**：最大记录数。
   * **[!UICONTROL By data grouping]**：您可以根据集客群体的指定字段中的值设置记录数限制。 有关此主题的更多信息，请参阅 [按数据分组限制子集记录的数量](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data grouping (in %)]**：您可以根据集客群体的指定字段中的值，使用百分比设置记录数限制。 有关此主题的更多信息，请参阅 [按数据分组限制子集记录的数量](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data distribution]**：如果分组字段的值太多，或者如果您希望避免为每个新的拆分活动再次输入值，可使用Adobe Campaign配置 **[!UICONTROL By data distribution]** 限制（可选分布式营销模块）。 有关更多信息，请参阅 [限制每个数据分布的子集记录数](#limiting-the-number-of-subset-records-per-data-distribution).

1. 单击 **[!UICONTROL Finish]** 批准记录选择标准。 然后，定义的配置将显示在编辑器的中间窗口中。

## 按数据分组限制子集记录的数量 {#limiting-the-number-of-subset-records-by-data-grouping}

您可以按数据分组限制记录数。 可使用固定值或百分比执行此限制。

例如，如果您选择 **[!UICONTROL Language]** 字段作为组字段，您可以为每种语言定义记录列表。

1. 选择数据限制值后，选择 **[!UICONTROL By data grouping]** 或 **[!UICONTROL By data grouping (as a %)]** 并单击 **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 然后选择分组字段( **[!UICONTROL Language]** 字段)，然后单击 **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 最后，指定数据分组阈值（使用固定值或百分比，具体取决于之前选择的分组方法）。 要为每个值设置相同的阈值，例如，如果您希望将每种语言的记录数设置为10，请选择 **[!UICONTROL All data groupings are the same size]** 选项。 要为每个值设置不同的限制，请选择 **[!UICONTROL Limitations by grouping value]** 选项。 这将允许您为英语、法语等语言选择不同的限制。

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 单击 **[!UICONTROL Finish]** 以批准该限制并返回到编辑拆分活动。

## 限制每个数据分布的子集记录数 {#limiting-the-number-of-subset-records-per-data-distribution}

如果您的分组字段包含的值过多，或者如果您希望避免为每个新的拆分活动重置值，则可以使用Adobe Campaign为每次数据分配创建一个限制。 选择数据限制值时(有关此主题的更多信息，请参阅 [创建子集](#creating-subsets) 部分)，选择 **[!UICONTROL By data distribution]** 选项并从下拉菜单中选择模板。 下面演示了如何创建数据分发模板。

例如， **[!UICONTROL Local approval]** 使用分发模板的活动，请参阅 [使用本地审批活动](using-the-local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>要使用此函数，您需要购买分布式营销模块，这是一个Campaign选项。 请核实您的许可协议。

通过数据分发模板，您可以使用分组值列表限制记录数。 要创建数据分发模板，请应用以下步骤：

1. 要创建数据分发模板，请转到 **[!UICONTROL Resources > Campaign management > Data distribution]** 节点并单击 **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. 此 **[!UICONTROL General]** 选项卡允许您输入分发的标签和执行上下文（定向维度、分发字段）。

   ![](assets/local_validation_data_distribution_2.png)

   需要输入以下字段：

   * **[!UICONTROL Label]**：分发模板的标签。
   * **[!UICONTROL Targeting dimension]**：输入数据分发将应用到的定向维度， **[!UICONTROL Recipient]** 例如。 此架构必须始终与定位工作流中使用的数据兼容。
   * **[!UICONTROL Distribution field]**：通过定向维度选择字段。 例如，如果您选择 **[!UICONTROL Email domain]** 字段中，收件人列表将按域细分。
   * **[!UICONTROL Distribution type]**：选择在中划分目标限制值的方式 **[!UICONTROL Distribution]** 选项卡： **[!UICONTROL Percentage]** 或 **[!UICONTROL Set]**.
   * **[!UICONTROL Assignment type]**：选择数据分发分配类型。 您可以在按组或操作员分配或按本地实体分配之间进行选择。 按本地实体进行的分配用于 **分布式营销**. 有关更多信息，请参阅此 [部分](../../distributed/using/about-distributed-marketing.md).
   * **[!UICONTROL Approval storage]**：如果您使用 **[!UICONTROL Local approval]** 定位工作流中的活动(请参阅 [本地审批](local-approval.md))，输入将存储审批结果的架构。 您必须为每个定位架构指定一个存储架构。 如果您使用 **[!UICONTROL Recipients]** 定位架构，输入默认值 **[!UICONTROL Local approval of recipients]** 存储模式。

      如果由于数据分组而没有本地批准而存在简单限制，则无需输入 **[!UICONTROL Approvals storage]** 字段。

1. 如果您使用 **[!UICONTROL Local approval]** 活动(请参阅 [本地审批](local-approval.md))，输入 **[!UICONTROL Advanced settings]** 对于分发模板：

   ![](assets/local_validation_data_distribution_3.png)

   需要输入以下字段：

   * **[!UICONTROL Approve targeted messages]**：如果您希望从要批准的收件人列表中预选所有收件人，请选中此选项。 如果未选中此选项，则不会预先选择任何收件人。

      >[!NOTE]
      >
      >此选项默认处于选中状态。

      ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**：可让您定义一个表达式，以便在退货通知中显示投放标签。 默认表达式提供有关投放的标准标签（计算字符串）的信息。 您可以修改此表达式。

      ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**：利用此字段，可定义用于在批准和返回通知中显示收件人的分组。

      ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**：用于将Web应用程序链接到收件人列表。 在批准和返回通知中，每个收件人都可点击，并将链接到选定的Web应用程序。 此 **[!UICONTROL Parameters]** 字段(例如 **[!UICONTROL recipientId]**)可让您配置要在URL和Web应用程序中使用的其他参数。

      ![](assets/local_validation_notification_5.png)

1. 此 **[!UICONTROL Breakdown]** 选项卡用于定义分发值的列表。

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**：输入分布值。
   * **[!UICONTROL Percentage / Set]**：输入链接到每个值的记录限制（固定或百分比）。

      此列由 **[!UICONTROL Distribution type]** 中的字段 **[!UICONTROL General]** 选项卡。

   * **[!UICONTROL Label]**：输入链接到每个值的标签。
   * **[!UICONTROL Group or operator]**：如果您使用的是 **[!UICONTROL Local approval]** 活动(请参阅 [本地审批](local-approval.md))，选择分配给每个分发值的运算符或运算符组。

      如果由于数据分组而没有本地批准而存在简单限制，则无需输入 **[!UICONTROL Group or operator]** 字段。

      >[!IMPORTANT]
      >
      >确保为操作员分配了适当的权限。

   * **[!UICONTROL Local entity]**：选择分配给每个分发值的本地实体。 本地实体用于 **分布式营销**. 有关更多信息，请参阅此 [部分](../../distributed/using/about-distributed-marketing.md).

## 筛选参数 {#filtering-parameters}

单击 **[!UICONTROL General]** 选项卡，输入活动标签。 为此拆分选择目标和筛选维度。 如有必要，可以更改给定子集的这些维度。

![](assets/s_user_segmentation_partage_general.png)

查看 **[!UICONTROL Generate complement]** 选项。 补充是集客目标减去子集的并集。 然后，将向该活动添加其他叫客过渡，如下所示：

![](assets/s_user_segmentation_partage_compl.png)

要使此选项正常工作，集客数据必须具有主键。

例如，如果数据是通过Netezza（不支持索引的概念）从外部数据库直接读取的， **[!UICONTROL Data loading (RDBMS)]** 活动，由生成的补充 **[!UICONTROL Split]** 活动将不正确。

要避免此情况，您可以拖放 **[!UICONTROL Enrichment]** 之前的活动 **[!UICONTROL Split]** 活动。 在 **[!UICONTROL Enrichment]** 活动，请检查 **[!UICONTROL Keep all additional data from the main set]** 并在附加数据中指定要用于配置过滤器的 **[!UICONTROL Split]** 活动。 来自集客过渡的数据 **[!UICONTROL Split]** 然后，活动将本地存储在Adobe Campaign服务器上的临时表中，并且补充可以正确生成。

此 **[!UICONTROL Enable overlapping of output populations]** 选项允许您管理属于多个子集的群体：

* 如果未选中该框，则拆分活动可确保收件人无法出现在多个输出转换中，即使它满足多个子集的条件也是如此。 它们将位于第一个选项卡的目标中，并带有匹配条件。
* 选中该框后，如果收件人满足筛选条件，则可以在多个子集中找到他们。 Adobe Campaign建议使用排他性标准。

## 输入参数 {#input-parameters}

* 表名
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* 表名
* 架构
* recCount

这组三个值标识排除项导致的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是群体的模式（通常为nms：recipient）和 **[!UICONTROL recCount]** 是表中的元素数。

与补充关联的过渡具有相同的参数。
