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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f5062117b5cefbdd2570018f6803f114c14a3fae

---


# 个性化字段{#personalization-fields}

个性化字段用于对已交付消息的内容进行一级个性化。 在主内容中插入的字段显示从所选数据源插入数据的位置。

例如，具有 **** &lt;%= recipient.LastName %>语法的个性化字段告知Adobe Campaign将收件人的名称插入数据库（收件人表）。

>[!NOTE]
>
>个性化字段内容不能超过1024个字符。

## 数据源 {#data-sources}

个性化字段可能来自两种类型的数据源，具体取决于所选的交付模式：

* Adobe Campaign数据库是数据源。 这是最常见的情况，例如“收件人个性化字段”。 这些是收件人表中定义的所有字段，无论是标准字段(通常为：姓氏、名字、地址、城镇、出生日期等)或用户定义的字段。
* 外部文件是数据源。 这些是在文件列中定义的所有字段，这些字段在交付过程中使用外部文件中找到的数据显示为输入。

>[!NOTE]
>
>Adobe Campaign个性化标签始终具有以下 **形式&lt;%=table.field%>**。

## 插入个性化字段 {#inserting-a-personalization-field}

要插入个性化字段，请单击可从任何标题、主题或正文编辑字段访问的下拉图标。

![](assets/s_ncs_user_add_custom_field.png)

在选择数据源（收件人字段或文件字段）后，此插入采用命令的形式，该命令将由Adobe Campaign解释并替换为给定收件人的字段值。 然后，可以在选项卡中查看物理替 **[!UICONTROL Preview]** 换。

## 个性化字段示例 {#personalization-fields-example}

我们会创建一封电子邮件，首先插入收件人的姓名，然后在邮件正文中添加个人资料创建日期。 操作步骤：

1. 创建新的分发或打开现有电子邮件类型的分发。
1. 在传送向导中，单 **[!UICONTROL Subject]** 击以编辑邮件的主题并输入主题。
1. 输入“ **[!UICONTROL Special offer for]** ”并使用工具栏中的按钮插入个性化字段。 Select **[!UICONTROL Recipients>Title]**.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重复此操作以插入收件人的姓名。 在所有个性化字段之间插入空格。
1. Click **[!UICONTROL OK]** to validate.
1. 在邮件正文中插入个性化。 为此，请单击消息内容，然后单击字段插入按钮。
1. Select **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 选择包含要显示的信息的字段，然后单击 **[!UICONTROL OK]**。

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 单击选 **[!UICONTROL Preview]** 项卡以查看个性化结果。 您必须选择一个收件人才能显示该收件人的消息。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >当交付是工作流的一部分时，您可以使用临时工作流表中的数据。 此数据将在菜单中分 **[!UICONTROL Target extension]** 组。 如需详细信息，请参阅[此部分](../../workflow/using/executing-a-workflow.md#target-data)。

## 优化个性化 {#optimizing-personalization}

您可以使用专用选项优化个性化：在 **[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;交付属性的 **[!UICONTROL Analysis]** 选项卡中提供。

在分发分析过程中，此选项会自动创建并执行一个工作流，该工作流将链接到目标的所有数据存储在临时表中，包括FDA中链接的表中的数据。

通过选中此选项，您可以显着提高执行个性化的性能。

例如，如果您在邮件内容中使用大量个性化字段和／或个性化基块时向大量收件人发送邮件时遇到性能问题，此选项可加快个性化处理，从而加快邮件的发送。

要使用此选项，请按照以下步骤操作：

1. 创建营销活动。 如需详细信息，请参阅[此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在营销 **[!UICONTROL Targeting and workflows]** 活动的选项卡中，将查询 **** 活动添加到工作流中。 For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. 向工作 **[!UICONTROL Email delivery]** 流中添加活动并将其打开。 For more on using this activity, refer to [this section](../../workflow/using/delivery.md).
1. 转到选项 **[!UICONTROL Analysis]** 卡并选 **[!UICONTROL Delivery properties]** 择相应的 **[!UICONTROL Prepare the personalization data with a workflow]** 选项。

   ![](assets/perso_optimization.png)

1. 配置交付并启动工作流以启动分析。

分析完成后，个性化数据通过在分析期间动态创建的临时技术工作流存储在临时表中。

此工作流程在Adobe Campaign界面中不可见。 它只是用来作为快速存储和处理个性化数据的技术手段。

分析完成后，转到工作流并 **[!UICONTROL Properties]** 选择选项 **[!UICONTROL Variables]** 卡。 您可以在此处看到临时表的名称，该表可用于进行SQL调用以显示它包含的ID。

![](assets/perso_optimization_temp_table.png)

## 超时个性化阶段 {#timing-out-personalization}

要改进交付保护，您可以为个性化阶段设置超时时间。

在的选 **[!UICONTROL Delivery]** 项卡中，选 **[!UICONTROL Delivery properties]****[!UICONTROL Maximum personalization run time]** 择选项的最大值（以秒为单位）。

在预览或发送过程中，如果个性化阶段超过您在此字段中设置的最大时间，则该过程将中止，并显示一条错误消息，且传送将失败。

![](assets/perso_time-out.png)

默认值是5秒。

如果将此选项设置为0，则个性化阶段将没有时间限制。