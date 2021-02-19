---
solution: Campaign Classic
product: campaign
title: 设置循环导入
description: 了解如何为重复导入配置工作流模板。
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: bb7e3ce726e2c589c033686cf3ab2960de140d91
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---


# 设置循环导入工作流 {#setting-up-a-recurring-import}

如果您需要定期导入具有相同结构的文件，则使用工作流模板是最佳做法。

此示例说明如何预先设置可重用于导入来自Adobe Campaign库中CRM的用户档案的工作流。 有关每个活动的所有可能设置的详细信息，请参阅此[部分](../../workflow/using/about-activities.md)。

1. 从&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;创建新的工作流模板。
1. 添加以下活动:

   * **[!UICONTROL Data loading (file)]**:定义包含要导入的数据的文件的预期结构。
   * **[!UICONTROL Enrichment]**:协调导入的数据与数据库数据。
   * **[!UICONTROL Split]**:创建过滤器，根据记录是否可以对帐，以不同方式处理记录。
   * **[!UICONTROL Deduplication]**:在将传入文件插入数据库之前，从传入文件中删除重复数据。
   * **[!UICONTROL Update data]**:使用导入的用户档案更新数据库。

   ![](assets/import_template_example0.png)

1. 配置&#x200B;**[!UICONTROL Data Loading (file)]**&#x200B;活动:

   * 通过上传示例文件来定义预期结构。 示例文件应仅包含几行，但包含导入所需的所有列。 检查并编辑文件格式，确保正确设置每列的类型：文本、日期、整数等。 例如：

      ```
      lastname;firstname;birthdate;email;crmID
      Smith;Hayden;23/05/1989;hayden.smith@mailtest.com;123456
      ```

   * 在&#x200B;**[!UICONTROL Name of the file to load]**&#x200B;部分，选择&#x200B;**[!UICONTROL Upload a file from the local machine]**&#x200B;并将字段留空。 每次从此模板创建新工作流时，您都可以在此处指定所需的文件，只要该文件与定义的结构相对应。

      您可以使用任何选项，但必须相应地修改模板。 例如，如果您选择&#x200B;**[!UICONTROL Specified in the transition]**，则可以在检索要从FTP/SFTP服务器导入的文件之前添加&#x200B;**[!UICONTROL File Transfer]**&#x200B;活动。 通过S3或SFTP连接，您还可以使用Adobe Real-time Customer Data平台将区段数据导入Adobe Campaign。 有关此内容的详细信息，请参阅此[文档](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html)。

      ![](assets/import_template_example1.png)

1. 配置&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动。 此活动在此上下文中的目的是识别传入数据。

   * 在&#x200B;**[!UICONTROL Enrichment]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Add data]**&#x200B;并定义导入的数据和收件人定位维度之间的链接。 在此示例中，使用&#x200B;**CRM ID**&#x200B;自定义字段创建连接条件。 只要允许标识唯一记录，就使用所需的字段或字段组合。
   * 在&#x200B;**[!UICONTROL Reconciliation]**&#x200B;选项卡中，取消选中&#x200B;**[!UICONTROL Identify the document from the working data]**&#x200B;选项。

   ![](assets/import_template_example2.png)

1. 配置&#x200B;**[!UICONTROL Split]**&#x200B;活动，以在一个过渡和收件人中检索已协调的收件人，这些和无法协调，但在第二个过渡中具有足够的数据。

   随后，具有已协调收件人的过渡可用于更新数据库。 如果文件中至少有一组信息可用，则具有未知收件人的过渡随后可用于在数据库中创建新收件人条目。

   无法协调且没有足够数据的收件人会在补充出站过渡中选择，并可以在单独的文件中导出，或只是忽略。

   * 在活动的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Use the additional data only]**&#x200B;作为筛选设置，并确保将&#x200B;**[!UICONTROL Targeting dimension]**&#x200B;自动设置为&#x200B;**[!UICONTROL Enrichment]**。

      选中&#x200B;**[!UICONTROL Generate complement]**&#x200B;选项可查看是否无法在数据库中插入任何记录。 如果需要，您随后可以对补充数据应用进一步处理：文件导出、列表更新等。

   * 在&#x200B;**[!UICONTROL Subsets]**&#x200B;选项卡的第一个子集中，在入站人口中添加过滤条件以仅选择收件人主键不等于0的记录。 这样，在该子集中选择与来自收件人库的数据协调的文件数据。

      ![](assets/import_template_example3.png)

   * 添加第二个子集，该子集选择具有足够数据要插入数据库的未协调记录。 例如：电子邮件地址、名字和姓氏。

      子集按其创建顺序被处理，这意味着当处理第二子集时，在第一子集中已经存在于数据库中的所有记录被选择。

      ![](assets/import_template_example3_2.png)

   * 在&#x200B;**[!UICONTROL Complement]**&#x200B;中选择前两个子集中未选择的所有记录。

1. 配置位于之前配置的&#x200B;**[!UICONTROL Split]**&#x200B;活动的第一个出站过渡之后的&#x200B;**[!UICONTROL Update data]**&#x200B;活动。

   * 选择&#x200B;**[!UICONTROL Update]**&#x200B;作为&#x200B;**[!UICONTROL Operation type]**，因为入站过渡仅包含数据库中已存在的收件人。
   * 在&#x200B;**[!UICONTROL Record identification]**&#x200B;部分，选择&#x200B;**[!UICONTROL Using reconciliation keys]**&#x200B;并定义定位维度与在&#x200B;**[!UICONTROL Enrichment]**&#x200B;中创建的链接之间的键。 在此示例中，使用&#x200B;**CRM ID**&#x200B;自定义字段。
   * 在&#x200B;**[!UICONTROL Fields to update]**&#x200B;部分中，指示收件人维中的字段，以使用文件中的相应列的值进行更新。 如果文件列的名称与收件人维度字段的名称相同或几乎相同，则可以使用魔棒按钮自动匹配不同的字段。

      ![](assets/import_template_example6.png)

1. 配置位于包含未协调活动的过渡之后的&#x200B;**[!UICONTROL Deduplication]**&#x200B;收件人:

   * 选择&#x200B;**[!UICONTROL Edit configuration]**&#x200B;并将定位维度设置为从工作流的&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动生成的临时模式。

      ![](assets/import_template_example4.png)

   * 在此示例中，电子邮件字段用于查找唯一用户档案。 您可以使用您确定已填充的任何字段，并且它是唯一组合的一部分。
   * 在&#x200B;**[!UICONTROL Deduplication method]**&#x200B;屏幕中，选择&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;并选中&#x200B;**[!UICONTROL Disable automatic filtering of 0 ID records]**&#x200B;选项，以确保未排除主键等于0(应为此过渡的所有记录)的记录。

   ![](assets/import_template_example7.png)

1. 配置位于之前配置的&#x200B;**[!UICONTROL Deduplication]**&#x200B;活动之后的&#x200B;**[!UICONTROL Update data]**&#x200B;活动。

   * 选择&#x200B;**[!UICONTROL Insert]**&#x200B;作为&#x200B;**[!UICONTROL Operation type]**，因为入站过渡仅包含数据库中不存在的收件人。
   * 在&#x200B;**[!UICONTROL Record identification]**&#x200B;部分，选择&#x200B;**[!UICONTROL Directly using the targeting dimension]**&#x200B;并选择&#x200B;**[!UICONTROL Recipients]**&#x200B;维度。
   * 在&#x200B;**[!UICONTROL Fields to update]**&#x200B;部分中，指示收件人维中的字段，以使用文件中的相应列的值进行更新。 如果文件列的名称与收件人维度字段的名称相同或几乎相同，则可以使用魔棒按钮自动匹配不同的字段。

      ![](assets/import_template_example8.png)

1. 在&#x200B;**[!UICONTROL Split]**&#x200B;活动的第三个过渡后，如果要跟踪未插入到库中的数据，请添加&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活动和&#x200B;**[!UICONTROL File transfer]**&#x200B;活动。 配置这些活动以导出所需的列，并在FTP或SFTP服务器上传输文件，从中可以检索文件。
1. 添加&#x200B;**[!UICONTROL End]**&#x200B;活动并保存工作流模板。

模板现在可以使用，并且可用于每个新工作流。 然后，需要全部指定包含要在&#x200B;**[!UICONTROL Data loading (file)]**&#x200B;活动中导入的数据的文件。

![](assets/import_template_example9.png)
