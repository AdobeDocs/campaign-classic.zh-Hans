---
product: campaign
title: 拆分
description: 了解有关拆分工作流活动的更多信息
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1971'
ht-degree: 3%

---

# 拆分{#split}

**拆分**&#x200B;类型的活动允许您将目标拆分为多个子集。 使用所有接收结果构建目标：因此，必须完成所有先前的活动才能执行此活动。

此活动不会触发集客群体的联合。 如果多个过渡登陆在一个拆分活动中，我们建议在其前面插入&#x200B;**[!UICONTROL Union]**&#x200B;活动。

>[!NOTE]
>
>不能对具有不同源的表执行拆分操作。 为此，您需要在&#x200B;**拆分**&#x200B;活动之前添加&#x200B;**扩充**&#x200B;活动。

* 有关正在使用的拆分活动的示例，请参阅[使用拆分活动创建子集](targeting-data.md#creating-subsets-using-the-split-activity)。
* [此部分](cross-channel-delivery-workflow.md)中介绍了如何使用拆分活动通过筛选条件将目标分段为不同群体的示例。
* [此部分](javascript-scripts-and-templates.md)中提供了如何在拆分活动中使用实例变量的示例。

要配置此活动，请在&#x200B;**[!UICONTROL Subsets]**&#x200B;选项卡中定义子集内容和标签，然后在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中选择目标维度。

## 创建子集 {#creating-subsets}

要创建子集，请执行以下操作：

1. 单击匹配字段中的标签，然后选择要应用的过滤器。
1. 要筛选入站群体，请选择&#x200B;**[!UICONTROL Add a filtering condition]**&#x200B;选项并单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接。

   选择要应用于要包含在此集中的数据的过滤器类型。

   该进程与&#x200B;**查询**&#x200B;类型的活动相同。

   >[!NOTE]
   >
   >您最多可以筛选两个外部数据库(FDA)中的数据。

1. 您可以指定从目标提取的最大记录数以创建子集。 为此，请选中&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;选项并单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接。

   借助助手，可选择此子集记录的选择模式。 可以在[限制子集记录数](#limiting-the-number-of-subset-records)中找到这些步骤。

   ![](assets/s_user_segmentation_partage4.png)

1. 如果您愿意，可以使用&#x200B;**[!UICONTROL Add]**&#x200B;按钮&#x200B;**添加其他子集**。

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >如果未选中&#x200B;**[!UICONTROL Enable overlapping of output populations]**&#x200B;选项，则子集将按选项卡的顺序创建。 使用此窗口右上角的箭头来移动它们。 例如，如果第一个子集恢复初始群体的70%，则下一个子集将只对其余30%应用其选择标准，以此类推。

   对于创建的每个子集，将向拆分活动添加叫客过渡。

   ![](assets/s_user_segmentation_partage_add2.png)

   您可以选择生成单个叫客过渡（例如使用段代码标识集）：为此，请在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中选择&#x200B;**[!UICONTROL Generate subsets in the same table]**&#x200B;选项。

   完成后，每个子集的段码将自动存储在一个附加的列中。 可在投放级别的个性化字段中访问此列。

## 限制子集记录的数量 {#limiting-the-number-of-subset-records}

如果不希望使用子集中包含的整个群体，则可以限制它包含的记录数。

1. 在子集编辑窗口中，选中&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;选项并单击&#x200B;**[!UICONTROL Edit...]**&#x200B;链接。
1. 为您的选择选择限制类型：

   * **[!UICONTROL Activate random sampling]**：此选项接受记录的随机样本。 应用的随机取样类型取决于数据库引擎。
   * **[!UICONTROL Keep only the first records after sorting]**：此选项允许您根据一个或多个排序顺序定义限制。 如果您选择&#x200B;**[!UICONTROL Age]**&#x200B;字段作为排序条件，选择100作为限制，则仅保留100个最年轻的收件人。
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**：此选项是前两个选项的组合。 它允许您根据一个或多个排序顺序定义限制，然后在某些记录具有与定义的标准相同的值时，对第一个记录应用随机选择。

     例如，如果选择&#x200B;**[!UICONTROL Age]**&#x200B;字段作为排序条件，然后定义限制100，但数据库中2000个最年轻的收件人全部为18个，则会从这2000个收件人中随机选择100个收件人。

   ![](assets/s_user_segmentation_partage_wz1.png)

1. 如果要定义排序标准，还可以通过附加步骤定义列和排序顺序。

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 然后选择数据限制方法。

   ![](assets/s_user_segmentation_partage_wz2.png)

   可通过多种方法做到这一点：

   * **[!UICONTROL Size (in %)]**：记录的百分比。 例如，以下配置提取总群体的10%。

     百分比适用于初始群体，而不是活动结果。

   * **[!UICONTROL Size (as a % of the segment)]**：只与子集相关而不与初始群体相关的记录的百分比。
   * **[!UICONTROL Maximum size]**：最大记录数。
   * **[!UICONTROL By data grouping]**：您可以根据集客群体的指定字段中的值设置记录数限制。 有关此主题的详细信息，请参阅[按数据分组限制子集记录数](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data grouping (in %)]**：您可以根据指定字段中的值（使用百分比），设置集客群体的记录数限制。 有关此主题的详细信息，请参阅[按数据分组限制子集记录数](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data distribution]**：如果分组字段的值太多，或者希望避免为每个新的拆分活动再次输入值，则可以使用Adobe Campaign配置&#x200B;**[!UICONTROL By data distribution]**&#x200B;限制（可选分布式营销模块）。 有关详细信息，请参阅[限制每个数据分发的子集记录数](#limiting-the-number-of-subset-records-per-data-distribution)。

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;以批准记录选择条件。 定义的配置随后将显示在编辑器的中间窗口中。

## 按数据分组限制子集记录的数量 {#limiting-the-number-of-subset-records-by-data-grouping}

您可以按数据分组限制记录数。 可使用固定值或百分比执行此限制。

例如，如果选择&#x200B;**[!UICONTROL Language]**&#x200B;字段作为组字段，则可以定义每种语言的记录列表。

1. 选择数据限制值后，选择&#x200B;**[!UICONTROL By data grouping]**&#x200B;或&#x200B;**[!UICONTROL By data grouping (as a %)]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 然后选择分组字段（实例的&#x200B;**[!UICONTROL Language]**&#x200B;字段）并单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 最后，指定数据分组阈值（使用固定值或百分比，具体取决于之前选择的分组方法）。 要为每个值设置相同的阈值，例如，如果您希望将每种语言的记录数设置为10，请选择&#x200B;**[!UICONTROL All data groupings are the same size]**&#x200B;选项。 要为每个值设置不同的限制，请选择&#x200B;**[!UICONTROL Limitations by grouping value]**&#x200B;选项。 这将允许您为英语、法语等语言选择不同的限制。

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;以批准该限制并返回编辑拆分活动。

## 限制每个数据分布的子集记录数 {#limiting-the-number-of-subset-records-per-data-distribution}

如果分组字段包含的值过多，或者希望避免为每个新的拆分活动重置值，则可以使用Adobe Campaign根据数据分布创建限制。 选择数据限制值（有关此主题的详细信息，请参阅[创建子集](#creating-subsets)部分）时，选择&#x200B;**[!UICONTROL By data distribution]**&#x200B;选项，然后从下拉菜单中选择模板。 下面演示了如何创建数据分发模板。

有关具有分发模板的&#x200B;**[!UICONTROL Local approval]**&#x200B;活动的示例，请参阅[使用本地审批活动](using-the-local-approval-activity.md)。

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>要使用此函数，您需要购买分布式营销模块，这是一个促销活动选项。 请核实您的许可协议。

通过数据分发模板，您可以使用分组值列表限制记录数。 要创建数据分发模板，请应用以下步骤：

1. 要创建数据分发模板，请转到&#x200B;**[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;节点并单击&#x200B;**[!UICONTROL New]**。

   ![](assets/local_validation_data_distribution_1.png)

1. **[!UICONTROL General]**&#x200B;选项卡允许您输入分发的标签和执行上下文（定向维度、分发字段）。

   ![](assets/local_validation_data_distribution_2.png)

   需要输入以下字段：

   * **[!UICONTROL Label]**：分发模板的标签。
   * **[!UICONTROL Targeting dimension]**：输入要应用数据分发的定向维度，例如&#x200B;**[!UICONTROL Recipient]**。 此架构必须始终与定位工作流中使用的数据兼容。
   * **[!UICONTROL Distribution field]**：通过定向维度选择字段。 例如，如果选择&#x200B;**[!UICONTROL Email domain]**&#x200B;字段，则收件人列表将按域细分。
   * **[!UICONTROL Distribution type]**：选择在&#x200B;**[!UICONTROL Distribution]**&#x200B;选项卡中划分目标限制值的方式： **[!UICONTROL Percentage]**&#x200B;或&#x200B;**[!UICONTROL Set]**。
   * **[!UICONTROL Assignment type]**：选择数据分发分配类型。 您可以在按组或运算符分配或按本地实体分配之间进行选择。 在&#x200B;**分布式营销**&#x200B;中使用本地实体的分配。 有关详细信息，请参阅此[部分](../../distributed/using/about-distributed-marketing.md)。
   * **[!UICONTROL Approval storage]**：如果在定位工作流中使用&#x200B;**[!UICONTROL Local approval]**&#x200B;活动（请参阅[本地审批](local-approval.md)），请输入将存储审批结果的架构。 您必须为每个定位架构指定一个存储架构。 如果您使用&#x200B;**[!UICONTROL Recipients]**&#x200B;目标架构，请输入默认的&#x200B;**[!UICONTROL Local approval of recipients]**&#x200B;存储架构。

     如果未经本地批准而通过数据分组进行简单限制，则无需输入&#x200B;**[!UICONTROL Approvals storage]**&#x200B;字段。

1. 如果您使用的是&#x200B;**[!UICONTROL Local approval]**&#x200B;活动（请参阅[本地审批](local-approval.md)），请输入分发模板的&#x200B;**[!UICONTROL Advanced settings]**：

   ![](assets/local_validation_data_distribution_3.png)

   需要输入以下字段：

   * **[!UICONTROL Approve targeted messages]**：如果您希望从要批准的收件人列表中预先选择所有收件人，请选中此选项。 如果未选中此选项，则不会预先选择任何收件人。

     >[!NOTE]
     >
     >此选项默认处于选中状态。

     ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**：允许您定义一个表达式，以在退货通知中显示交货标签。 默认表达式提供有关投放标准标签（计算字符串）的信息。 您可以修改此表达式。

     ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**：此字段允许您定义用于在审批和返回通知中显示收件人的分组。

     ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**：允许您将Web应用程序链接到收件人列表。 在批准和返回通知中，每个收件人都将可点击，并将链接到选定的Web应用程序。 **[!UICONTROL Parameters]**&#x200B;字段（例如&#x200B;**[!UICONTROL recipientId]**）允许您配置要在URL和Web应用程序中使用的其他参数。

     ![](assets/local_validation_notification_5.png)

1. **[!UICONTROL Breakdown]**&#x200B;选项卡允许您定义分发值列表。

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**：输入分布值。
   * **[!UICONTROL Percentage / Set]**：输入链接到每个值的记录限制（固定或百分比）。

     此列由&#x200B;**[!UICONTROL General]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Distribution type]**&#x200B;字段定义。

   * **[!UICONTROL Label]**：输入链接到每个值的标签。
   * **[!UICONTROL Group or operator]**：如果您使用的是&#x200B;**[!UICONTROL Local approval]**&#x200B;活动（请参阅[本地审批](local-approval.md)），请选择分配给每个分发值的运算符或运算符组。

     如果未经本地批准而通过数据分组进行简单限制，则无需输入&#x200B;**[!UICONTROL Group or operator]**&#x200B;字段。

     >[!IMPORTANT]
     >
     >确保为操作员分配了适当的权限。

   * **[!UICONTROL Local entity]**：选择分配给每个分发值的本地实体。 本地实体在&#x200B;**分布式营销**&#x200B;中使用。 有关详细信息，请参阅此[部分](../../distributed/using/about-distributed-marketing.md)。

## 过滤参数 {#filtering-parameters}

单击&#x200B;**[!UICONTROL General]**&#x200B;选项卡以输入活动标签。 为此拆分选择目标和筛选维度。 如有必要，可以更改给定子集的这些维度。

![](assets/s_user_segmentation_partage_general.png)

如果要利用剩余群体，请选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项。 补充是集客目标减去子集的并集。 然后，将向活动添加其他叫客过渡，如下所示：

![](assets/s_user_segmentation_partage_compl.png)

要使此选项正常工作，集客数据必须具有主键。

例如，如果直接通过&#x200B;**[!UICONTROL Data loading (RDBMS)]**&#x200B;活动从外部数据库(如Netezza，不支持索引的概念)读取数据，则&#x200B;**[!UICONTROL Split]**&#x200B;活动生成的补数将不正确。

为避免这种情况，您可以将&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动拖放到&#x200B;**[!UICONTROL Split]**&#x200B;活动之前。 在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动中，检查&#x200B;**[!UICONTROL Keep all additional data from the main set]**&#x200B;并在附加数据中指定要用于配置&#x200B;**[!UICONTROL Split]**&#x200B;活动的筛选器的列。 来自&#x200B;**[!UICONTROL Split]**&#x200B;活动的集客过渡的数据随后将本地存储在Adobe Campaign服务器上的临时表中，并且可正确生成补码。

通过&#x200B;**[!UICONTROL Enable overlapping of output populations]**&#x200B;选项，可管理属于多个子集的群体：

* 当未选中该框时，拆分活动将确保收件人不会出现在多个输出转换中，即使它满足多个子集的标准。它们将位于第一个选项卡的目标中，并带有匹配条件。
* 选中此框后，如果收件人符合过滤条件，则可以在多个子集中找到他们。Adobe Campaign 建议使用专属标准。

## 输入参数 {#input-parameters}

* 表名
* 模式

每个入站事件必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* 表名
* 模式
* recCount

这组三个值可标识排除项导致的目标。 **[!UICONTROL tableName]**&#x200B;是记录目标标识符的表的名称，**[!UICONTROL schema]**&#x200B;是群体的架构（通常为nms：recipient），**[!UICONTROL recCount]**&#x200B;是表中的元素数。

与补充关联的转换具有相同的参数。
