---
product: campaign
title: 个性化字段
description: 个性化字段
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 67fd9a67-cb05-46cd-acd5-e42fde6f4d4f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 8%

---

# 个性化字段{#personalization-fields}

个性化字段用于投放消息内容的一级个性化。在主内容中插入的字段显示插入选定数据源中数据的位置。

例如，使用&#x200B;**&lt;%= recipient.LastName %>**&#x200B;语法的个性化字段告知Adobe Campaign将收件人的名称插入数据库（收件人表）。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#personalization-fields-video)

>[!CAUTION]
>
>个性化字段内容不能超过1024个字符。

## 数据源{#data-sources}

根据所选的提交模式，个性化字段可以来自两种类型的数据源：

* Adobe Campaign数据库是数据源。 这是最常见的情况，例如“收件人个性化字段”。 无论标准字段(通常为：姓氏、名字、地址、城镇、出生日期等) 或用户定义的字段。
* 外部文件是数据源。 这些是文件列中定义的所有字段，在使用外部文件中找到的数据进行投放时作为输入显示。

>[!NOTE]
>
>Adobe Campaign个性化标记始终具有以下形式&#x200B;**&lt;%=table.field%>**。

## 插入个性化字段 {#inserting-a-personalization-field}

要插入个性化字段，请单击可从任何标题、主题或消息正文编辑字段访问的下拉图标。

![](assets/s_ncs_user_add_custom_field.png)

在选择数据源（收件人字段或文件字段）后，此插入采用命令的形式，该命令将由Adobe Campaign解释并替换为给定收件人的字段值。 然后，可以在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中查看物理替换。

## 个性化字段示例{#personalization-fields-example}

我们会创建一封电子邮件，我们将首先在其中插入收件人的姓名，然后在邮件正文中添加用户档案创建日期。 操作步骤：

1. 创建新投放或打开现有电子邮件类型投放。
1. 在投放向导中，单击&#x200B;**[!UICONTROL Subject]**&#x200B;以编辑消息的主题并输入主题。
1. 输入“ **[!UICONTROL Special offer for]** ”，然后使用工具栏中的按钮插入个性化字段。 选择 **[!UICONTROL Recipients>Title]**。

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重复操作以插入收件人的名称。 在所有个性化字段之间插入空格。
1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;以验证。
1. 在消息正文中插入个性化。 为此，请单击消息内容中的，然后单击字段插入按钮。
1. 选择 **[!UICONTROL Recipient>Other...]**。

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 选择包含要显示的信息的字段，然后单击&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以查看个性化结果。 您必须选择一个收件人以显示该收件人的消息。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >当投放是工作流的一部分时，您可以使用临时工作流表中的数据。 此数据分组到&#x200B;**[!UICONTROL Target extension]**&#x200B;菜单中。 如需详细信息，请参阅[此部分](../../workflow/using/data-life-cycle.md#target-data)。

## 优化个性化{#optimizing-personalization}

您可以使用专用选项优化个性化：**[!UICONTROL Prepare the personalization data with a workflow]**，位于投放属性的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡中。 有关分析投放的更多信息，请参阅[此部分](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在投放分析期间，此选项会自动创建并执行一个工作流，该工作流将链接到目标的所有数据存储在临时表格中，包括来自FDA中链接表格的数据。

选中此选项可在处理大量数据时大大提高投放分析性能，尤其是当个性化数据通过FDA来自外部表时。 有关更多信息，请参阅[访问外部数据库(FDA)](../../installation/using/about-fda.md)。

例如，如果您在消息内容中使用大量个性化字段和/或个性化块时向大量收件人投放内容时遇到性能问题，则此选项可以加快个性化处理，从而加快消息投放。

要使用此选项，请执行以下步骤：

1. 创建营销策划. 如需详细信息，请参阅[此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在营销活动的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中，向工作流中添加&#x200B;**查询**&#x200B;活动。 有关使用此活动的更多信息，请参阅[此部分](../../workflow/using/query.md)。
1. 向工作流中添加&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动并将其打开。 有关使用此活动的更多信息，请参阅[此部分](../../workflow/using/delivery.md)。
1. 转到&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡，然后选择&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;选项。

   ![](assets/perso_optimization.png)

1. 配置投放并启动工作流以启动分析。

完成分析后，个性化数据会通过临时技术工作流存储在临时表格中，该工作流在分析过程中会即时创建。

此工作流在Adobe Campaign界面中不可见。 它仅是快速存储和处理个性化数据的技术手段。

分析完成后，转到工作流&#x200B;**[!UICONTROL Properties]**&#x200B;并选择&#x200B;**[!UICONTROL Variables]**&#x200B;选项卡。 在此处，您可以看到可用于进行SQL调用以显示其所包含ID的临时表的名称。

![](assets/perso_optimization_temp_table.png)

## 个性化阶段{#timing-out-personalization}超时

要改进投放保护，您可以为个性化阶段设置超时期限。

在&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡中，为&#x200B;**[!UICONTROL Maximum personalization run time]**&#x200B;选项选择最大值（以秒为单位）。

在预览或发送期间，如果个性化阶段超过了您在此字段中设置的最长时间，则该过程将中止，并显示一条错误消息，且投放将失败。

![](assets/perso_time-out.png)

默认值为5秒。

如果将此选项设置为0，则个性化阶段将没有时间限制。

## 教程视频{#personalization-fields-video}

了解如何向电子邮件投放的主题行和内容添加个性化字段。

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

其他Campaign Classic操作方法视频可在[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)获取。
