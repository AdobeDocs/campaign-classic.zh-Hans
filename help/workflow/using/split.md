---
title: 拆分
seo-title: 拆分
description: 拆分
seo-description: null
page-status-flag: never-activated
uuid: 00dc3436-e271-4512-8f29-71a55213afc3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 9eadfda0-0614-4e4e-aed0-26f0b9222fbd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 463d2d60e8776fc0414fdb8c91dbf257e119d823

---


# 拆分{#split}

利 **用Split**-type活动，您可以将目标拆分为多个子集。 该目标是利用所有接收结果来构建的：因此，必须完成所有以前的活动才能执行此活动。

此活动不会触发入站人口的联合。 如果多个过渡在一个拆分活动中着陆，我们建议在该 **[!UICONTROL Union]** 活动前面插入一个活动。

有关使用的拆分活动的示例，请参阅使 [用拆分活动创建子集](../../workflow/using/targeting-data.md#creating-subsets-using-the-split-activity)。

本节介绍了一个示例，其中说明了如何使用拆分活动使用过滤条件将目标细分为不同 [人群](../../workflow/using/cross-channel-delivery-workflow.md)。

此部分提供了一个示例，其中显示了如何在拆分活动中使用实例 [变量](../../workflow/using/javascript-scripts-and-templates.md)。

要配置此活动，请在选项卡中定义子集内容和标 **[!UICONTROL Subsets]** 签，然后在选项卡中选择目标 **[!UICONTROL General]** 维。

## 创建子集 {#creating-subsets}

要创建子集，请执行以下操作：

1. 单击匹配字段中的标签，然后选择要应用的过滤器。
1. 要过滤入站人群，请选择选 **[!UICONTROL Add a filtering condition]** 项并单击链 **[!UICONTROL Edit...]** 接。

   选择要应用于数据的过滤器类型，以将其包含在此集中。

   该过程与 **Query**-type活动的过程相同。

   >[!CAUTION]
   >
   >最多可以过滤两个外部数据库(FDA)中的数据。

1. 您可以指定要从目标中提取的最大记录数以创建子集。 要执行此操作，请选中该 **[!UICONTROL Limit the selected records]** 选项并单击链 **[!UICONTROL Edit...]** 接。

   通过向导，您可以为此子集的记录选择选择模式。 这些步骤可在限制 [子集记录数中找到](#limiting-the-number-of-subset-records)。

   ![](assets/s_user_segmentation_partage4.png)

1. 如果您愿意，可以使 **用按钮添加其** 他子 **[!UICONTROL Add]** 集。

   ![](assets/s_user_segmentation_partage_add.png)

   >[!CAUTION]
   >
   >如果未 **[!UICONTROL Enable overlapping of output populations]** 选中此选项，则按选项卡的顺序创建子集。 使用此窗口右上角的箭头移动它们。 例如，如果第一子集恢复了初始种群的70%，则下一个子集将仅将其选择标准应用于其余的30%，依此类推。

   对于创建的每个子集，将向拆分活动添加出站过渡。

   ![](assets/s_user_segmentation_partage_add2.png)

   您可以选择生成单个出站过渡（例如，使用段代码标识集）:要执行此操作，请在选 **[!UICONTROL Generate subsets in the same table]** 项卡中选择 **[!UICONTROL General]** 选项。

   如果完成，则每个子集的段代码自动存储在附加列中。 此列可在交付级别的个性化字段中访问。

## 限制子集记录数 {#limiting-the-number-of-subset-records}

如果您不希望使用子集中包含的整个人口，则可以限制将包含的记录数。

1. 在子集编辑窗口中，选中该 **[!UICONTROL Limit the selected records]** 选项并单击该 **[!UICONTROL Edit...]** 链接。
1. 选择您选择的限制类型：

   * **[!UICONTROL Activate random sampling]**:此选项会随机抽取记录样本。 应用的随机采样类型取决于数据库引擎。
   * **[!UICONTROL Keep only the first records after sorting]**:此选项允许您根据一个或多个排序顺序定义限制。 如果选择字 **[!UICONTROL Age]** 段作为排序标准，选择100作为限制，则仅保留最小的100个收件人。
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**:此选项组合了前两个选项。 它允许您根据一个或多个排序顺序定义限制，如果某些记录的值与定义的标准相同，则可以对第一个记录应用随机选择。

      例如，如果选择字段作为排序标准，然后您定义了100的限制，但数据库中2000个最年轻的接收者都是18个，那么将从这2000个收件人中随机选择100个收件人。 **[!UICONTROL Age]**
   ![](assets/s_user_segmentation_partage_wz1.png)

1. 如果要定义排序标准，还可以通过其他步骤定义列和排序顺序。

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. 然后选择数据限制方法。

   ![](assets/s_user_segmentation_partage_wz2.png)

   可通过以下几种方式执行此操作：

   * **[!UICONTROL Size (in %)]**:百分比的记录。 例如，以下配置提取了总人口的10%。

      百分比适用于初始人口，而不是活动的结果。

   * **[!UICONTROL Size (as a % of the segment)]**:仅与子集相关而与初始群体无关的记录的百分比。
   * **[!UICONTROL Maximum size]**:最大记录数。
   * **[!UICONTROL By data grouping]**:您可以根据入站人口的指定字段中的值设置记录数量限制。 有关此主题的详细信息，请参 [阅按数据分组限制子集记录数](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data grouping (in %)]**:您可以根据入站人口的指定字段中的值使用百分比设置记录数量限制。 有关此主题的详细信息，请参 [阅按数据分组限制子集记录数](#limiting-the-number-of-subset-records-by-data-grouping)。
   * **[!UICONTROL By data distribution]**:如果您的分组字段的值过多，或者您希望避免为每个新拆分活动再次输入值，则Adobe Campaign允许您配置限制(可选的“分 **[!UICONTROL By data distribution]** 布式营销”模块)。 有关详细信息，请参 [阅限制每个数据分发的子集记录数](#limiting-the-number-of-subset-records-per-data-distribution)。

1. 单击 **[!UICONTROL Finish]** 以批准记录选择条件。 定义的配置随后将显示在编辑器的中间窗口中。

## 通过数据分组限制子集记录数 {#limiting-the-number-of-subset-records-by-data-grouping}

您可以按数据分组限制记录数。 此限制可使用固定值或百分比执行。

例如，如果选择字段作 **[!UICONTROL Language]** 为组字段，则可以为每个语言定义记录列表。

1. 选择数据限制值后，选择或 **[!UICONTROL By data grouping]** 单击 **[!UICONTROL By data grouping (as a %)]** 鼠标 **[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz3.png)

1. 然后选择分组字段(例 **[!UICONTROL Language]** 如字段)并单击 **[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_partage_wz4.png)

1. 最后，指定数据分组阈值（使用固定值或百分比，具体取决于之前选择的分组方法）。 要为每个值设置相同的阈值（例如，如果要将每种语言的记录数设置为10），请选择该选 **[!UICONTROL All data groupings are the same size]** 项。 要为每个值设置不同的限制，请选择该 **[!UICONTROL Limitations by grouping value]** 选项。 这允许您为英语、法语等选择其他限制。

   ![](assets/s_user_segmentation_partage_wz5.png)

1. 单 **[!UICONTROL Finish]** 击以批准限制并返回编辑拆分活动。

## 限制每个数据分发的子集记录数 {#limiting-the-number-of-subset-records-per-data-distribution}

如果您的分组字段包含的值过多，或者如果您希望避免重置每个新拆分活动的值，则Adobe Campaign允许您为每个数据分发创建限制。 在选择数据限制值(有关此主题的详细信息，请参阅 [Creating subsets](#creating-subsets) （创建子集）部分)时，选择 **[!UICONTROL By data distribution]** 选项，然后从下拉菜单中选择模板。 创建数据分发模板的说明如下。

有关具有分发模 **[!UICONTROL Local approval]** 板的活动的示例，请参阅 [使用本地批准活动](../../workflow/using/using-the-local-approval-activity.md)。

![](assets/s_user_segmentation_partage_wz6.png)

>[!CAUTION]
>
>要使用此功能，您需要购买“分布式营销”模块（即营销活动选项）。 请检查您的许可协议。

通过数据分发模板，您可以使用分组值列表限制记录数。 要创建数据分发模板，请应用以下步骤：

1. 要创建数据分发模板，请转到该节 **[!UICONTROL Resources > Campaign management > Data distribution]** 点并单击 **[!UICONTROL New]**。

   ![](assets/local_validation_data_distribution_1.png)

1. 在选 **[!UICONTROL General]** 项卡中，您可以输入分发的标签和执行上下文（定位维、分发字段）。

   ![](assets/local_validation_data_distribution_2.png)

   需要输入以下字段：

   * **[!UICONTROL Label]**:标签。
   * **[!UICONTROL Targeting dimension]**:例如，输入要应用数据分发的目标维 **[!UICONTROL Recipient]** 度。 此架构必须始终与定位工作流中使用的数据兼容。
   * **[!UICONTROL Distribution field]**:通过定位维度选择字段。 例如，如果您选择字 **[!UICONTROL Email domain]** 段，收件人列表将按域划分。
   * **[!UICONTROL Distribution type]**:在选项卡中选择目标限制值的划分方 **[!UICONTROL Distribution]** 式：或 **[!UICONTROL Percentage]** 者 **[!UICONTROL Set]**。
   * **[!UICONTROL Assignment type]**:选择数据分发分配类型。 您可以按组或运算符选择分配，或按本地实体选择分配。 由本地实体进行的分配用于分 **发营销**。 For more information, refer to this [section](../../campaign/using/about-distributed-marketing.md).
   * **[!UICONTROL Approval storage]**:如果您在定位 **[!UICONTROL Local approval]** 工作流中使用活动(请参 [阅本地批准](../../workflow/using/local-approval.md))，请输入将存储批准结果的架构。 必须为每个定位架构指定一个存储架构。 如果您使用定 **[!UICONTROL Recipients]** 位架构，请输入默认的存储 **[!UICONTROL Local approval of recipients]** 架构。

      如果在未经本地批准的情况下由数据分组进行简单限制，则无需输入字 **[!UICONTROL Approvals storage]** 段。

1. 如果您使用的是 **[!UICONTROL Local approval]** 活动(请参 [阅本地批准](../../workflow/using/local-approval.md))，请输入 **[!UICONTROL Advanced settings]** 分发模板的：

   ![](assets/local_validation_data_distribution_3.png)

   需要输入以下字段：

   * **[!UICONTROL Approve targeted messages]**:如果希望从收件人列表中预先选择所有收件人以进行批准，请选中此选项。 如果未选中此选项，则不会预选收件人。

      >[!NOTE]
      >
      >此选项在默认情况下处于选中状态。

      ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**:允许您定义表达式，以在返回通知中显示传送标签。 默认表达式提供有关交付的标准标签的信息（计算字符串）。 您可以修改此表达式。

      ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**:此字段允许您定义用于在批准和返回通知中显示收件人的分组。

      ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**:允许您将Web应用程序链接到收件人列表。 在批准和返回通知中，每个收件人都可单击，并将链接到选定的Web应用程序。 字 **[!UICONTROL Parameters]** 段(例如 **[!UICONTROL recipientId]**)允许您配置要在URL和Web应用程序中使用的其他参数。

      ![](assets/local_validation_notification_5.png)

1. 通过 **[!UICONTROL Breakdown]** 该选项卡可以定义分发值列表。

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**:输入分发值。
   * **[!UICONTROL Percentage / Set]**:输入链接到每个值的记录限制（固定或百分比）。

      此列由选项卡中 **[!UICONTROL Distribution type]** 的字段定 **[!UICONTROL General]** 义。

   * **[!UICONTROL Label]**:输入链接到每个值的标签。
   * **[!UICONTROL Group or operator]**:如果您使用的是 **[!UICONTROL Local approval]** 活动(请参 [阅本地批准](../../workflow/using/local-approval.md))，请选择分配给每个分配值的运算符或运算符组。

      如果在未经本地批准的情况下由数据分组进行简单限制，则无需输入字 **[!UICONTROL Group or operator]** 段。

      >[!CAUTION]
      >
      >确保已为运营商分配了相应的权限。

   * **[!UICONTROL Local entity]**:选择分配给每个分发值的本地实体。 本地实体用于分 **发营销**。 For more information, refer to this [section](../../campaign/using/about-distributed-marketing.md).

## 筛选参数 {#filtering-parameters}

单击选 **[!UICONTROL General]** 项卡以输入活动标签。 为此拆分选择目标和筛选维。 如有必要，您可以更改给定子集的这些维。

![](assets/s_user_segmentation_partage_general.png)

如果您 **[!UICONTROL Generate complement]** 希望利用剩余人口，请选中此选项。 补码是入站目标减去子集的并。 然后，将向活动添加额外的出站过渡，如下所示：

![](assets/s_user_segmentation_partage_compl.png)

要使此选项正常工作，入站数据必须具有主键。

例如，如果通过活动直接从外部数据库(如Netezza（它不支持索引的概念）)读取数据，则由活动生成的补码将 **[!UICONTROL Data loading (RDBMS)]****[!UICONTROL Split]** 不正确。

要避免这种情况，您可以在活动之前 **[!UICONTROL Enrichment]** 拖放一个活 **[!UICONTROL Split]** 动。 在活 **[!UICONTROL Enrichment]** 动中，检查 **[!UICONTROL Keep all additional data from the main set]** 并在其他数据中指定要用于配置活动过滤器的列 **[!UICONTROL Split]** 。 活动的入站过渡中的数 **[!UICONTROL Split]** 据随后将本地存储在Adobe Campaign服务器上的临时表中，并可以正确生成补充。

通过 **[!UICONTROL Enable overlapping of output populations]** 此选项，可以管理属于多个子集的人群：

* 如果未选中该框，拆分活动将确保收件人不能出现在多个输出过渡中，即使它满足多个子集的条件也是如此。 它们将位于具有匹配条件的第一个选项卡的目标中。
* 选中该框后，如果收件人满足其筛选条件，则可以在多个子集中找到收件人。 Adobe Campaign建议使用独家标准。

## 输入参数 {#input-parameters}

* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这三个值集标识了排除所导致的目标。 **[!UICONTROL tableName]** 是记录目标标识符的表的名称， **[!UICONTROL schema]** 是人口（通常nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素数。

与补码相关联的过渡具有相同的参数。
