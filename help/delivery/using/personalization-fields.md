---
title: 个性化字段
seo-title: 个性化字段
description: 个性化字段
seo-description: null
page-status-flag: never-activated
uuid: 3a94a50e-259e-40c3-ae67-8a2c42e9fad7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 27c8e443-ee6b-4d58-bc2d-81cf8391c5de
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 9%

---


# 个性化字段{#personalization-fields}

个性化字段用于投放消息内容的一级个性化。在主内容中插入的字段显示插入选定数据源中数据的位置。

例如，具有&lt;%=收件人.LastName **%>语法的个性化字段** ，会告知Adobe Campaign将收件人的名称插入数据库(收件人表)。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#personalization-fields-video)

>[!CAUTION]
>
>个性化字段内容不能超过1024个字符。

## Data sources {#data-sources}

个性化字段可以来自两种类型的数据源，根据所选的投放模式：

* Adobe Campaign库是数据源。 这是最常见的情况，例如&quot;收件人个性化字段&quot;。 这些是收件人表中定义的所有字段，无论是标准字段(通常为：姓氏、名字、地址、镇、出生日期等) 或用户定义字段。
* 外部文件是数据源。 这些是在使用外部文件中找到的数据投放时作为输入的文件列中定义的所有字段。

>[!NOTE]
>
>Adobe Campaign个性化标签始终具有以下 **形式&lt;%=table.field%>**。

## 插入个性化字段 {#inserting-a-personalization-field}

要插入个性化字段，请单击可从任何标题、主题或邮件正文编辑字段访问的下拉图标。

![](assets/s_ncs_user_add_custom_field.png)

在选择数据源(收件人字段或文件字段)后，此插入采用命令的形式，该命令将由Adobe Campaign解释，并替换为给定收件人的字段值。 然后，可在选项卡中查看物理替 **[!UICONTROL Preview]** 换。

## 个性化字段示例 {#personalization-fields-example}

我们会创建一封电子邮件，首先插入收件人的名称，然后在邮件正文中添加用户档案创建日期。 操作步骤：

1. 创建新投放或打开现有电子邮件类型投放。
1. 在投放向导中，单 **[!UICONTROL Subject]** 击以编辑邮件的主题并输入主题。
1. 输入“ **[!UICONTROL Special offer for]** ”并使用工具栏中的按钮插入个性化字段。 选择 **[!UICONTROL Recipients>Title]**。

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重复此操作以插入收件人的名称。 在所有个性化字段之间插入空格。
1. Click **[!UICONTROL OK]** to validate.
1. 在邮件正文中插入个性化。 为此，请单击消息内容，然后单击字段插入按钮。
1. 选择 **[!UICONTROL Recipient>Other...]**。

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 选择包含要显示的信息的字段，然后单击 **[!UICONTROL OK]**。

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 单击选 **[!UICONTROL Preview]** 项卡以视图个性化结果。 必须选择收件人才能显示该收件人的消息。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >当投放是工作流的一部分时，您可以使用临时工作流表中的数据。 此数据将在菜单中进 **[!UICONTROL Target extension]** 行分组。 如需详细信息，请参阅[此部分](../../workflow/using/data-life-cycle.md#target-data)。

## 优化个性化 {#optimizing-personalization}

您可以使用专用选项优化个性化： **[!UICONTROL Prepare the personalization data with a workflow]**，位于投放 **[!UICONTROL Analysis]** 属性的选项卡中。 有关分析投放的详细信息，请参 [阅本节](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在投放分析期间，此选项自动创建并执行一个工作流，该工作流将链接到目标的所有数据存储在临时表中，包括来自链接到联合数据访问的表的数据。

选中此选项可以在处理大量数据时大幅提高投放分析性能，尤其是当个性化数据通过联合数据访问从外部表时。 有关此方面的详细信息，请 [参阅访问外部数据库(联合数据访问)](../../installation/using/about-fda.md)。

例如，如果您在邮件内容中使用大量收件人和／或个性化块时向大量个性化字段传送时遇到性能问题，此选项可加快个性化处理，从而加快邮件传送。

要使用此选项，请按照以下步骤操作：

1. 创建营销策划. 如需详细信息，请参阅[此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在活动 **[!UICONTROL Targeting and workflows]** 的选项卡中，将查询 **活动** 添加到工作流。 For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. 向工作 **[!UICONTROL Email delivery]** 流中添加活动并将其打开。 For more on using this activity, refer to [this section](../../workflow/using/delivery.md).
1. 转到选 **[!UICONTROL Analysis]** 项卡并 **[!UICONTROL Delivery properties]** 选择选 **[!UICONTROL Prepare the personalization data with a workflow]** 项。

   ![](assets/perso_optimization.png)

1. 配置投放并开始工作流以启动分析。

分析完成后，个性化数据通过在分析期间动态创建的临时技术工作流存储在临时表中。

此工作流在Adobe Campaign界面中不可见。 它只是用于快速存储和处理个性化数据的技术手段。

分析完成后，转到工作流并 **[!UICONTROL Properties]** 选择选 **[!UICONTROL Variables]** 项卡。 您可以看到临时表的名称，该表可用于进行SQL调用以显示它包含的ID。

![](assets/perso_optimization_temp_table.png)

## 超时个性化阶段 {#timing-out-personalization}

要改进投放保护，您可以为个性化阶段设置超时时间。

在选项 **[!UICONTROL Delivery]** 卡中，选 **[!UICONTROL Delivery properties]**&#x200B;择选项的最大值(以秒为单 **[!UICONTROL Maximum personalization run time]** 位)。

在预览或发送过程中，如果个性化阶段超过您在此字段中设置的最长时间，则会中止该过程并显示错误消息，投放将失败。

![](assets/perso_time-out.png)

默认值为5秒。

如果将此选项设置为0，则个性化阶段将没有时间限制。

## 如何使用个性化字段个性化电子邮件 {#personalization-fields-video}

了解如何将个性化字段添加到主题行和电子邮件投放的内容。

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)
