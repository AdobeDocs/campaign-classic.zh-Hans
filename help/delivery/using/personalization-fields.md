---
solution: Campaign Classic
product: campaign
title: 个性化字段
description: 个性化字段
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 8%

---


# 个性化字段{#personalization-fields}

个性化字段用于投放消息内容的一级个性化。在主内容中插入的字段显示插入选定数据源中数据的位置。

例如，具有&#x200B;**&lt;%= 收件人.LastName %>**&#x200B;语法的个性化字段告知Adobe Campaign将收件人的名称插入数据库(收件人表)。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#personalization-fields-video)

>[!CAUTION]
>
>个性化字段内容不能超过1024个字符。

## 数据源{#data-sources}

个性化字段可以来自两种类型的数据源，具体取决于所选的投放模式：

* Adobe Campaign数据库是数据源。 这是最常见的情况，例如“收件人个性化字段”。 这些是“收件人”表中定义的所有字段，无论是标准字段(通常为：姓氏、名字、地址、镇、出生日期等) 或用户定义的字段。
* 外部文件是数据源。 这些是在使用外部文件中找到的数据进行投放时作为输入的文件列中定义的所有字段。

>[!NOTE]
>
>Adobe Campaign个性化标记始终具有以下形式：**&lt;%=table.field%>**。

## 插入个性化字段 {#inserting-a-personalization-field}

要插入个性化字段，请单击可从任何标题、主题或邮件正文编辑字段访问的下拉图标。

![](assets/s_ncs_user_add_custom_field.png)

在选择数据源(收件人字段或文件字段)后，此插入采用命令的形式，该命令将由Adobe Campaign解释并替换为给定收件人的字段值。 然后可以在&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中查看物理替换。

## 个性化字段示例{#personalization-fields-example}

我们会创建一封电子邮件，我们会首先在邮件中插入收件人的名称，然后在邮件正文中添加用户档案创建日期。 操作步骤：

1. 创建新投放或打开现有电子邮件类型投放。
1. 在投放向导中，单击&#x200B;**[!UICONTROL Subject]**&#x200B;编辑邮件的主题并输入主题。
1. 输入“ **[!UICONTROL Special offer for]** ”，然后使用工具栏中的按钮插入个性化字段。 选择 **[!UICONTROL Recipients>Title]**。

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重复该操作以插入收件人的名称。 在所有个性化字段之间插入空格。
1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;以验证。
1. 在邮件正文中插入个性化。 要执行此操作，请单击消息内容，然后单击字段插入按钮。
1. 选择 **[!UICONTROL Recipient>Other...]**。

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 选择包含要显示的信息的字段，然后单击&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以视图个性化结果。 必须选择收件人才能显示该收件人的消息。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >当投放是工作流的一部分时，您可以使用临时工作流表中的数据。 此数据将在&#x200B;**[!UICONTROL Target extension]**&#x200B;菜单中分组。 如需详细信息，请参阅[此部分](../../workflow/using/data-life-cycle.md#target-data)。

## 优化个性化{#optimizing-personalization}

您可以使用专用选项优化个性化：**[!UICONTROL Prepare the personalization data with a workflow]**，位于投放属性的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡中。 有关分析投放的详细信息，请参阅[此部分](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在投放分析期间，此选项会自动创建并执行一个工作流，该工作流将链接到目标的所有数据存储在临时表中，包括来自链接到联合数据访问的表的数据。

选中此选项可以在处理大量数据时大幅提高投放分析性能，尤其是当个性化数据通过联合数据访问来自外部表时。 有关详细信息，请参阅[访问外部数据库(联合数据访问)](../../installation/using/about-fda.md)。

例如，如果您在向大量收件人传送消息时遇到性能问题，而在消息内容中使用大量个性化字段和/或个性化块，此选项可加快个性化处理，从而加快消息传送。

要使用此选项，请按照以下步骤操作：

1. 创建营销策划. 如需详细信息，请参阅[此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在活动的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中，向工作流中添加&#x200B;**查询**&#x200B;活动。 有关使用此活动的详细信息，请参阅[此部分](../../workflow/using/query.md)。
1. 将&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动添加到工作流并将其打开。 有关使用此活动的详细信息，请参阅[此部分](../../workflow/using/delivery.md)。
1. 转到&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡，然后选择&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;选项。

   ![](assets/perso_optimization.png)

1. 配置投放并开始工作流以启动分析。

分析完成后，个性化数据通过在分析期间动态创建的临时技术工作流存储在临时表中。

此工作流在Adobe Campaign界面中不可见。 它只是用于作为快速存储和处理个性化数据的技术手段。

分析完成后，转到工作流&#x200B;**[!UICONTROL Properties]**&#x200B;并选择&#x200B;**[!UICONTROL Variables]**&#x200B;选项卡。 您可以在此处看到临时表的名称，该临时表可用于进行SQL调用以显示它包含的ID。

![](assets/perso_optimization_temp_table.png)

## 在个性化阶段{#timing-out-personalization}结束

要改进投放保护，您可以为个性化阶段设置超时时间。

在&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡中，为&#x200B;**[!UICONTROL Maximum personalization run time]**&#x200B;选项选择最大值（以秒为单位）。

在预览或发送过程中，如果个性化阶段超过您在此字段中设置的最长时间，则会中止该过程，并显示错误消息，投放将失败。

![](assets/perso_time-out.png)

默认值为5秒。

如果将此选项设置为0，则个性化阶段不会有时间限制。

## 教程视频{#personalization-fields-video}

了解如何将个性化字段添加到主题行和电子邮件投放的内容。

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

其他Campaign Classic操作视频[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)可用。
