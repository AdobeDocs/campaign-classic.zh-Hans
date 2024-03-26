---
product: campaign
title: 设置循环导入
description: 了解如何为定期导入配置工作流模板
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Data Management
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 1%

---

# 设置循环导入工作流 {#setting-up-a-recurring-import}



如果需要定期导入具有相同结构的文件，则使用工作流模板是一种最佳实践。

此示例说明如何预先设置一个可重复使用的工作流，用于导入来自Adobe Campaign数据库中CRM的用户档案。 有关每个活动的所有可能设置的详细信息，请参阅此 [部分](about-activities.md).

1. 从创建新工作流模板 **[!UICONTROL Resources > Templates > Workflow templates]**.
1. 添加以下活动：

   * **[!UICONTROL Data loading (file)]**：定义包含导入数据的文件的预期结构。
   * **[!UICONTROL Enrichment]**：使用数据库数据协调导入的数据。
   * **[!UICONTROL Split]**：创建过滤器以根据是否可以协调记录而采用不同方式处理记录。
   * **[!UICONTROL Deduplication]**：在将数据插入数据库之前，请删除传入文件中的重复数据。
   * **[!UICONTROL Update data]**：使用导入的用户档案更新数据库。

   ![](assets/import_template_example0.png)

1. 配置 **[!UICONTROL Data Loading (file)]** 活动：

   * 通过上传样例文件来定义预期的结构。 样例文件应仅包含几行，但应包含导入所需的所有列。 检查并编辑文件格式，确保正确设置了每列的类型：文本、日期、整数等。 例如：

     ```
     lastname;firstname;birthdate;email;crmID
     Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
     ```

   * 在 **[!UICONTROL Name of the file to load]** 部分，选择 **[!UICONTROL Upload a file from the local machine]** 并将字段留空。 每次从此模板创建新工作流时，只要该文件与定义的结构相对应，您就可以在此处指定所需的文件。

     您可以使用任何选项，但必须相应地修改模板。 例如，如果您选择 **[!UICONTROL Specified in the transition]**，您可以添加 **[!UICONTROL File Transfer]** 之前的活动，以检索要从FTP/SFTP服务器导入的文件。 通过S3或SFTP连接，您还可以将区段数据导入Adobe实时客户数据平台的Adobe Campaign。 有关详细信息，请参阅此 [文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

     ![](assets/import_template_example1.png)

1. 配置 **[!UICONTROL Enrichment]** 活动。 在此上下文中，此活动的目的是标识传入数据。

   * 在 **[!UICONTROL Enrichment]** 选项卡，选择 **[!UICONTROL Add data]** 和定义导入数据与收件人定向维度之间的链接。 在此示例中， **CRM ID** 自定义字段用于创建连接条件。 只要允许标识唯一记录，就可以使用所需的字段或字段组合。
   * 在 **[!UICONTROL Reconciliation]** 选项卡，离开 **[!UICONTROL Identify the document from the working data]** 选项未选中。

   ![](assets/import_template_example2.png)

1. 配置 **[!UICONTROL Split]** 用于在某个过渡中检索已协调的收件人以及在第二个过渡中无法协调但具有足够数据的收件人的活动。

   然后，可以使用包含已协调收件人的过渡来更新数据库。 如果文件中具有最小信息集，则可以使用具有未知收件人的过渡在数据库中创建新收件人条目。

   无法协调且数据不足的收件人将在补充叫客过渡中选择，并可以在单独文件中导出或直接忽略。

   * 在 **[!UICONTROL General]** 选项卡中，选择 **[!UICONTROL Use the additional data only]** 作为筛选设置，并确保 **[!UICONTROL Targeting dimension]** 自动设置为 **[!UICONTROL Enrichment]**.

     查看 **[!UICONTROL Generate complement]** 选项，用于查看数据库中是否不能插入任何记录。 如果需要，可以对补充数据执行进一步处理：文件导出、列表更新等。

   * 在 **[!UICONTROL Subsets]** 选项卡，为集客群体添加筛选条件，以仅选择收件人主键不等于0的记录。 这样，便在该子集中选择与来自数据库的收件人协调的文件中的数据。

     ![](assets/import_template_example3.png)

   * 添加第二个子集，用于选择具有足够数据可插入数据库中的未协调记录。 例如：电子邮件地址、名字和姓氏。

     子集按其创建顺序进行处理，这意味着在处理第二个子集时，数据库中已存在的所有记录都已在第一个子集中被选择。

     ![](assets/import_template_example3_2.png)

   * 在前两个子集中未选择的所有记录都会在 **[!UICONTROL Complement]**.

1. 配置 **[!UICONTROL Update data]** 位于的第一个叫客过渡之后的活动 **[!UICONTROL Split]** 之前配置的活动。

   * 选择 **[!UICONTROL Update]** 作为 **[!UICONTROL Operation type]** 由于集客过渡仅包含数据库中已存在的收件人。
   * 在 **[!UICONTROL Record identification]** 部分，选择 **[!UICONTROL Using reconciliation keys]** 并定义定向维度与中创建的链接之间的键 **[!UICONTROL Enrichment]**. 在此示例中， **CRM ID** 自定义字段。
   * 在 **[!UICONTROL Fields to update]** 部分，指示收件人维度中要使用文件中对应列的值更新的字段。 如果文件列的名称与收件人维字段的名称相同或几乎相同，则可以使用魔棒按钮自动匹配不同的字段。

     ![](assets/import_template_example6.png)

1. 配置 **[!UICONTROL Deduplication]** 位于包含未协调收件人的过渡之后的活动：

   * 选择 **[!UICONTROL Edit configuration]** 并将定向维度设置为从生成的临时架构 **[!UICONTROL Enrichment]** 工作流活动。

     ![](assets/import_template_example4.png)

   * 在本例中，电子邮件字段用于查找独特的用户档案。 您可以使用任何确信已填充的字段以及唯一组合的一部分。
   * 在 **[!UICONTROL Deduplication method]** 屏幕，选择 **[!UICONTROL Advanced parameters]** 并查看 **[!UICONTROL Disable automatic filtering of 0 ID records]** 用于确保不排除主键等于0（应当为此过渡的所有记录）的记录的选项。

   ![](assets/import_template_example7.png)

1. 配置 **[!UICONTROL Update data]** 位于活动之后 **[!UICONTROL Deduplication]** 之前配置的活动。

   * 选择 **[!UICONTROL Insert]** 作为 **[!UICONTROL Operation type]** 由于集客过渡仅包含数据库中不存在的收件人。
   * 在 **[!UICONTROL Record identification]** 部分，选择 **[!UICONTROL Directly using the targeting dimension]** 并选择 **[!UICONTROL Recipients]** 维度。
   * 在 **[!UICONTROL Fields to update]** 部分，指示收件人维度中要使用文件中对应列的值更新的字段。 如果文件列的名称与收件人维字段的名称相同或几乎相同，则可以使用魔棒按钮自动匹配不同的字段。

     ![](assets/import_template_example8.png)

1. 在第三个过渡之后 **[!UICONTROL Split]** 活动，添加 **[!UICONTROL Data extraction (file)]** 活动和 **[!UICONTROL File transfer]** 活动。 配置这些活动以导出所需的列，并在FTP或SFTP服务器上传输文件，以便检索。
1. 添加 **[!UICONTROL End]** 活动并保存工作流模板。

现在可以使用该模板，并且该模板可用于每个新工作流。 然后只需指定包含要在中导入的数据的文件 **[!UICONTROL Data loading (file)]** 活动。

![](assets/import_template_example9.png)
