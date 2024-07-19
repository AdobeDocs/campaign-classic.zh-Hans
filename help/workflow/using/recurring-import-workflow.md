---
product: campaign
title: 设置循环导入
description: 了解如何为定期导入配置工作流模板
feature: Workflows, Data Management
exl-id: e6e140cb-8de0-4ab9-bddc-95abe04124c6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# 设置循环导入工作流 {#setting-up-a-recurring-import}



如果需要定期导入具有相同结构的文件，则使用工作流模板是一种最佳实践。

此示例说明如何预先设置一个可重复使用的工作流，用于导入来自Adobe Campaign数据库中CRM的用户档案。 有关每个活动的所有可能设置的详细信息，请参阅此[部分](about-activities.md)。

1. 从&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;创建新的工作流模板。
1. 添加以下活动：

   * **[!UICONTROL Data loading (file)]**：定义包含要导入的数据的文件的预期结构。
   * **[!UICONTROL Enrichment]**：使用数据库数据协调导入的数据。
   * **[!UICONTROL Split]**：创建过滤器以根据是否可以协调记录而采用不同方式处理记录。
   * **[!UICONTROL Deduplication]**：在将数据插入数据库之前，从传入文件中删除重复数据。
   * **[!UICONTROL Update data]**：使用导入的用户档案更新数据库。

   ![](assets/import_template_example0.png)

1. 配置&#x200B;**[!UICONTROL Data Loading (file)]**&#x200B;活动：

   * 通过上传样例文件来定义预期的结构。 样例文件应仅包含几行，但应包含导入所需的所有列。 检查并编辑文件格式，确保正确设置了每列的类型：文本、日期、整数等。 例如：

     ```
     lastname;firstname;birthdate;email;crmID
     Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
     ```

   * 在&#x200B;**[!UICONTROL Name of the file to load]**&#x200B;部分中，选择&#x200B;**[!UICONTROL Upload a file from the local machine]**&#x200B;并将字段留空。 每次从此模板创建新工作流时，只要该文件与定义的结构相对应，您就可以在此处指定所需的文件。

     您可以使用任何选项，但必须相应地修改模板。 例如，如果选择&#x200B;**[!UICONTROL Specified in the transition]**，您可以先添加&#x200B;**[!UICONTROL File Transfer]**&#x200B;活动，然后检索要从FTP/SFTP服务器导入的文件。 通过S3或SFTP连接，您还可以将区段数据导入Adobe实时客户数据平台的Adobe Campaign。 有关详细信息，请参阅此[文档](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html)。

     ![](assets/import_template_example1.png)

1. 配置&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动。 在此上下文中，此活动的目的是标识传入数据。

   * 在&#x200B;**[!UICONTROL Enrichment]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Add data]**&#x200B;并定义导入数据与收件人定向维度之间的链接。 在此示例中，**CRM ID**&#x200B;自定义字段用于创建连接条件。 只要允许标识唯一记录，就可以使用所需的字段或字段组合。
   * 在&#x200B;**[!UICONTROL Reconciliation]**&#x200B;选项卡中，将&#x200B;**[!UICONTROL Identify the document from the working data]**&#x200B;选项保留为未选中。

   ![](assets/import_template_example2.png)

1. 将&#x200B;**[!UICONTROL Split]**&#x200B;活动配置为在一个过渡中检索已协调的收件人，以及在第二个过渡中无法协调但具有足够数据的收件人。

   然后，可以使用包含已协调收件人的过渡来更新数据库。 如果文件中具有最小信息集，则可以使用具有未知收件人的过渡在数据库中创建新收件人条目。

   无法协调且数据不足的收件人将在补充叫客过渡中选择，并可以在单独文件中导出或直接忽略。

   * 在活动的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Use the additional data only]**&#x200B;作为筛选设置，并确保自动将&#x200B;**[!UICONTROL Targeting dimension]**&#x200B;设置为&#x200B;**[!UICONTROL Enrichment]**。

     选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项，以便能够查看数据库中是否不能插入任何记录。 如果需要，可以对补充数据执行进一步处理：文件导出、列表更新等。

   * 在&#x200B;**[!UICONTROL Subsets]**&#x200B;选项卡的第一个子集中，为集客群体添加筛选条件，以仅选择收件人主键不等于0的记录。 这样，便在该子集中选择与来自数据库的收件人协调的文件中的数据。

     ![](assets/import_template_example3.png)

   * 添加第二个子集，用于选择具有足够数据可插入数据库中的未协调记录。 例如：电子邮件地址、名字和姓氏。

     子集按其创建顺序进行处理，这意味着在处理第二个子集时，数据库中已存在的所有记录都已在第一个子集中被选择。

     ![](assets/import_template_example3_2.png)

   * 在前两个子集中未选择的所有记录都在&#x200B;**[!UICONTROL Complement]**&#x200B;中选择。

1. 配置位于先前配置的&#x200B;**[!UICONTROL Split]**&#x200B;活动的第一个叫客过渡之后的&#x200B;**[!UICONTROL Update data]**&#x200B;活动。

   * 选择&#x200B;**[!UICONTROL Update]**&#x200B;作为&#x200B;**[!UICONTROL Operation type]**，因为集客过渡仅包含数据库中已存在的收件人。
   * 在&#x200B;**[!UICONTROL Record identification]**&#x200B;部分中，选择&#x200B;**[!UICONTROL Using reconciliation keys]**&#x200B;并定义定向维度与在&#x200B;**[!UICONTROL Enrichment]**&#x200B;中创建的链接之间的键。 在此示例中，使用了&#x200B;**CRM ID**&#x200B;自定义字段。
   * 在&#x200B;**[!UICONTROL Fields to update]**&#x200B;部分中，指示收件人维度中要使用文件中对应列的值更新的字段。 如果文件列的名称与收件人维字段的名称相同或几乎相同，则可以使用魔棒按钮自动匹配不同的字段。

     ![](assets/import_template_example6.png)

1. 配置位于包含未协调收件人的过渡之后的&#x200B;**[!UICONTROL Deduplication]**&#x200B;活动：

   * 选择&#x200B;**[!UICONTROL Edit configuration]**&#x200B;并将定向维度设置为从工作流的&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动生成的临时架构。

     ![](assets/import_template_example4.png)

   * 在本例中，电子邮件字段用于查找独特的用户档案。 您可以使用任何确信已填充的字段以及唯一组合的一部分。
   * 在&#x200B;**[!UICONTROL Deduplication method]**&#x200B;屏幕中，选择&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;并选中&#x200B;**[!UICONTROL Disable automatic filtering of 0 ID records]**&#x200B;选项，以确保不排除主键等于0（应当为此过渡的所有记录）的记录。

   ![](assets/import_template_example7.png)

1. 配置位于之前配置的&#x200B;**[!UICONTROL Deduplication]**&#x200B;活动之后的&#x200B;**[!UICONTROL Update data]**&#x200B;活动。

   * 选择&#x200B;**[!UICONTROL Insert]**&#x200B;作为&#x200B;**[!UICONTROL Operation type]**，因为集客过渡仅包含数据库中不存在的收件人。
   * 在&#x200B;**[!UICONTROL Record identification]**&#x200B;部分中，选择&#x200B;**[!UICONTROL Directly using the targeting dimension]**&#x200B;并选择&#x200B;**[!UICONTROL Recipients]**&#x200B;维度。
   * 在&#x200B;**[!UICONTROL Fields to update]**&#x200B;部分中，指示收件人维度中要使用文件中对应列的值更新的字段。 如果文件列的名称与收件人维字段的名称相同或几乎相同，则可以使用魔棒按钮自动匹配不同的字段。

     ![](assets/import_template_example8.png)

1. 在&#x200B;**[!UICONTROL Split]**&#x200B;活动的第三个过渡之后，如果要跟踪数据库中未插入的数据，请添加&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活动和&#x200B;**[!UICONTROL File transfer]**&#x200B;活动。 配置这些活动以导出所需的列，并在FTP或SFTP服务器上传输文件，以便检索。
1. 添加&#x200B;**[!UICONTROL End]**&#x200B;活动并保存工作流模板。

现在可以使用该模板，并且该模板可用于每个新工作流。 然后，只需在&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活动中指定包含导入数据的文件即可。

![](assets/import_template_example9.png)
