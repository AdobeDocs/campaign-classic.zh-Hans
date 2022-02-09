---
product: campaign
title: 设置定期导入
description: 了解如何为定期导入配置工作流模板。
feature: Workflows
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 0%

---

# 设置循环导入工作流 {#setting-up-a-recurring-import}

![](../../assets/common.svg)

如果您需要定期导入具有相同结构的文件，则使用工作流模板是最佳做法。

此示例说明如何预设可重复使用的工作流，以导入来自Adobe Campaign数据库中CRM的用户档案。 有关每个活动的所有可能设置的更多信息，请参阅此 [部分](about-activities.md).

1. 从创建新的工作流模板 **[!UICONTROL Resources > Templates > Workflow templates]**.
1. 添加以下活动：

   * **[!UICONTROL Data loading (file)]**:定义包含要导入数据的文件的预期结构。
   * **[!UICONTROL Enrichment]**:使用数据库数据协调导入的数据。
   * **[!UICONTROL Split]**:创建过滤器以根据记录是否可以协调而以不同方式处理记录。
   * **[!UICONTROL Deduplication]**:在将数据插入数据库之前，从传入文件中删除重复数据。
   * **[!UICONTROL Update data]**:使用导入的用户档案更新数据库。

   ![](assets/import_template_example0.png)

1. 配置 **[!UICONTROL Data Loading (file)]** 活动：

   * 通过上传样例文件定义预期结构。 样例文件应仅包含几行，但包含导入所需的所有列。 检查并编辑文件格式，以确保正确设置每列的类型：文本、日期、整数等 例如：

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * 在 **[!UICONTROL Name of the file to load]** 选择 **[!UICONTROL Upload a file from the local machine]** 并将字段留空。 每次使用此模板创建新工作流时，您都可以在此处指定所需的文件，只要该文件与定义的结构相对应。

      您可以使用任何选项，但必须相应地修改模板。 例如，如果您选择 **[!UICONTROL Specified in the transition]**，则可以 **[!UICONTROL File Transfer]** 活动，以从FTP/SFTP服务器中检索要导入的文件。 通过S3或SFTP连接，您还可以通过Adobe实时客户数据平台将区段数据导入Adobe Campaign。 有关更多信息，请参阅此 [文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

      ![](assets/import_template_example1.png)

1. 配置 **[!UICONTROL Enrichment]** 活动。 此上下文中此活动的目的是识别传入数据。

   * 在 **[!UICONTROL Enrichment]** 选项卡，选择 **[!UICONTROL Add data]** 和可定义导入数据与定向维度的收件人之间的链接。 在本例中， **CRM ID** 自定义字段用于创建连接条件。 使用您需要的字段或字段组合，只要它允许标识唯一记录。
   * 在 **[!UICONTROL Reconciliation]** 选项卡，离开 **[!UICONTROL Identify the document from the working data]** 选项。

   ![](assets/import_template_example2.png)

1. 配置 **[!UICONTROL Split]** 活动，在一个过渡中检索已协调的收件人以及无法协调但在另一个过渡中具有足够数据的收件人。

   随后可以使用包含已协调收件人的过渡来更新数据库。 如果文件中有一组最低信息，则具有未知收件人的过渡可用于在数据库中创建新收件人条目。

   在补码叫客过渡中选择无法协调且没有足够数据的收件人，这些收件人可以导出到单独的文件中，或者干脆忽略。

   * 在 **[!UICONTROL General]** ，请选择 **[!UICONTROL Use the additional data only]** 设置，并确保 **[!UICONTROL Targeting dimension]** 自动设置为 **[!UICONTROL Enrichment]**.

      检查 **[!UICONTROL Generate complement]** 选项，以查看数据库中是否无法插入任何记录。 如果需要，您随后可以对补充数据应用进一步处理：文件导出、列表更新等。

   * 在 **[!UICONTROL Subsets]** 选项卡上，为集客群体添加筛选条件，以仅选择收件人主键不等于0的记录。 这样，在该子集中选择来自与来自数据库的收件人协调的文件的数据。

      ![](assets/import_template_example3.png)

   * 添加第二个子集，以选择具有足够数据要插入数据库的未协调记录。 例如：电子邮件地址、名字和姓氏。

      子集按其创建顺序进行处理，这意味着当处理第二个子集时，数据库中已存在的所有记录都已在第一子集中选择。

      ![](assets/import_template_example3_2.png)

   * 未在前两个子集中选择的所有记录都将在 **[!UICONTROL Complement]**.

1. 配置 **[!UICONTROL Update data]** 活动，位于 **[!UICONTROL Split]** 活动。

   * 选择 **[!UICONTROL Update]** as **[!UICONTROL Operation type]** 由于集客过渡仅包含数据库中已存在的收件人。
   * 在 **[!UICONTROL Record identification]** 选择 **[!UICONTROL Using reconciliation keys]** ，并在定向维度与在 **[!UICONTROL Enrichment]**. 在本例中， **CRM ID** 使用自定义字段。
   * 在 **[!UICONTROL Fields to update]** 部分，指示“收件人”维度中的字段，以使用文件中相应列的值进行更新。 如果文件列的名称与收件人维度字段的名称相同或几乎相同，则可以使用魔棒按钮自动匹配不同的字段。

      ![](assets/import_template_example6.png)

1. 配置 **[!UICONTROL Deduplication]** 位于包含未协调收件人的过渡之后的活动：

   * 选择 **[!UICONTROL Edit configuration]** 并将定向维度设置为从 **[!UICONTROL Enrichment]** 活动。

      ![](assets/import_template_example4.png)

   * 在本例中，电子邮件字段用于查找唯一的用户档案。 您可以使用您确定已填写的任何字段以及唯一组合的一部分。
   * 在 **[!UICONTROL Deduplication method]** 屏幕，选择 **[!UICONTROL Advanced parameters]** 并检查 **[!UICONTROL Disable automatic filtering of 0 ID records]** 用于确保主键值等于0（该键值应为此过渡的所有记录）的记录不被排除的选项。

   ![](assets/import_template_example7.png)

1. 配置 **[!UICONTROL Update data]** 活动位于 **[!UICONTROL Deduplication]** 活动。

   * 选择 **[!UICONTROL Insert]** as **[!UICONTROL Operation type]** 由于集客过渡仅包含数据库中不存在的收件人。
   * 在 **[!UICONTROL Record identification]** 选择 **[!UICONTROL Directly using the targeting dimension]** 然后选择 **[!UICONTROL Recipients]** 维度。
   * 在 **[!UICONTROL Fields to update]** 部分，指示“收件人”维度中的字段，以使用文件中相应列的值进行更新。 如果文件列的名称与收件人维度字段的名称相同或几乎相同，则可以使用魔棒按钮自动匹配不同的字段。

      ![](assets/import_template_example8.png)

1. 在 **[!UICONTROL Split]** 活动，添加 **[!UICONTROL Data extraction (file)]** 活动和 **[!UICONTROL File transfer]** 活动。 配置这些活动以导出所需的列，并在FTP或SFTP服务器上传输文件，您可以在其中检索该文件。
1. 添加 **[!UICONTROL End]** 活动并保存工作流模板。

模板现在可供使用，并可用于每个新工作流。 然后，只需指定包含要在 **[!UICONTROL Data loading (file)]** 活动。

![](assets/import_template_example9.png)
