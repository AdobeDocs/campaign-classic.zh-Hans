---
product: campaign
title: 个性化字段
description: 了解如何使用个性化字段
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Personalization
exl-id: 67fd9a67-cb05-46cd-acd5-e42fde6f4d4f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 10%

---

# 个性化字段{#personalization-fields}



个性化字段用于投放消息内容的一级个性化。在主内容中插入的字段显示插入选定数据源中数据的位置。

例如，个性化字段具有 **&lt;%= recipient.LastName %>** 语法告知Adobe Campaign将收件人的名称插入到数据库（收件人表）。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](#personalization-fields-video)

>[!CAUTION]
>
>个性化字段内容不能超过1024个字符。

## 数据源 {#data-sources}

根据所选的投放模式，个性化字段可以来自两种类型的数据源：

* Adobe Campaign数据库是数据源。 这是最常见的情况，例如“收件人个性化字段”。 这些是收件人表中定义的所有字段，无论是标准字段（通常是：姓氏、名字、地址、城镇、出生日期等）， 或用户定义的字段。
* 外部文件是数据源。 这些都是使用外部文件中找到的数据在投放期间作为输入呈现的文件列中定义的字段。

>[!NOTE]
>
>Adobe Campaign个性化标记始终具有以下形式 **&lt;%=table.field%>**.

## 插入个性化字段 {#inserting-a-personalization-field}

要插入个性化字段，请单击可从任何标头、主题或邮件正文编辑字段访问的下拉图标。

![](assets/s_ncs_user_add_custom_field.png)

在选择数据源（收件人字段或文件字段）后，此插入采用命令形式，该命令将由Adobe Campaign解释并替换为给定收件人的字段值。 然后可以在中查看物理更换 **[!UICONTROL Preview]** 选项卡。

## 个性化字段示例 {#personalization-fields-example}

我们将创建一个电子邮件，首先在其中插入收件人的姓名，然后在邮件正文中添加用户档案创建日期。 操作步骤：

1. 创建新投放或打开现有的电子邮件类型投放。
1. 在投放向导中，单击 **[!UICONTROL Subject]** 编辑消息的主题并输入主题。
1. 输入&quot; **[!UICONTROL Special offer for]** ”并使用工具栏中的按钮插入个性化字段。 选择 **[!UICONTROL Recipients>Title]**。

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 重复操作以插入收件人的名称。 在所有个性化字段之间插入空格。
1. 单击 **[!UICONTROL OK]** 进行验证。
1. 在消息正文中插入个性化设置。 要实现此目的，请单击消息内容，然后单击字段插入按钮。
1. 选择 **[!UICONTROL Recipient>Other...]**。

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 选择要显示信息的字段，然后单击 **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 单击 **[!UICONTROL Preview]** 选项卡以查看个性化结果。 您必须选择一个收件人以显示该收件人的消息。

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >当投放属于工作流的一部分时，您可以使用临时工作流表中的数据。 此数据分组在 **[!UICONTROL Target extension]** 菜单。 如需详细信息，请参阅[此部分](../../workflow/using/data-life-cycle.md#target-data)。

## 优化个性化 {#optimizing-personalization}

您可以使用专用选项优化个性化： **[!UICONTROL Prepare the personalization data with a workflow]**，可在 **[!UICONTROL Analysis]** 选项卡中显示的投放属性。 有关分析投放的更多信息，请参阅 [本节](steps-validating-the-delivery.md#analyzing-the-delivery).

在投放分析期间，此选项会自动创建并执行一个工作流，该工作流会将链接到目标的所有数据（包括来自FDA中链接的表的数据）存储在临时表中。

当处理大量数据时，尤其是当个性化数据通过FDA来自外部表时，选中此选项可以极大地提高投放分析性能。 有关此内容的更多信息，请参阅 [访问外部数据库（联合数据访问）](../../installation/using/about-fda.md).

例如，如果您在向大量收件人投放消息时遇到了性能问题，而您的消息内容中使用了大量个性化字段和/或个性化块，则此选项可以加快个性化处理，从而加快消息的投放。

要使用此选项，请执行以下步骤：

1. 创建营销策划. 如需详细信息，请参阅[此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)。
1. 在 **[!UICONTROL Targeting and workflows]** 选项卡，添加 **查询** 活动添加到工作流。 有关使用此活动的更多信息，请参阅 [本节](../../workflow/using/query.md).
1. 添加 **[!UICONTROL Email delivery]** 活动以打开工作流。 有关使用此活动的更多信息，请参阅 [本节](../../workflow/using/delivery.md).
1. 转到 **[!UICONTROL Analysis]** 的选项卡 **[!UICONTROL Delivery properties]** 并选择 **[!UICONTROL Prepare the personalization data with a workflow]** 选项。

   ![](assets/perso_optimization.png)

1. 配置投放并启动工作流以启动分析。

分析完成后，个性化数据将通过分析期间动态创建的临时技术工作流存储在临时表中。

此工作流在Adobe Campaign界面中不可见。 它仅仅是一种快速存储和处理个性化数据的技术手段。

分析完成后，转到工作流 **[!UICONTROL Properties]** 并选择 **[!UICONTROL Variables]** 选项卡。 您可以在此处看到可用于进行SQL调用的临时表的名称，以显示它包含的ID。

![](assets/perso_optimization_temp_table.png)

## 个性化阶段超时 {#timing-out-personalization}

要改进投放保护，您可以为个性化阶段设置超时期限。

在 **[!UICONTROL Delivery]** 的选项卡 **[!UICONTROL Delivery properties]**，为选择最大值（以秒为单位） **[!UICONTROL Maximum personalization run time]** 选项。

在预览或发送期间，如果个性化阶段超过您在此字段中设置的最大时间，则该过程将中止，并出现一条错误消息，投放将失败。

![](assets/perso_time-out.png)

默认值为5秒。

如果将此选项设置为0，则个性化阶段将没有时间限制。

## 教程视频 {#personalization-fields-video}

了解如何在主题行中添加个性化字段，以及如何添加电子邮件投放的内容。

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
