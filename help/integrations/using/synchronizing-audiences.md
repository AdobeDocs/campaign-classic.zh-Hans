---
solution: Campaign Classic
product: campaign
title: 同步受众
description: 同步受众
audience: integrations
content-type: reference
topic-tags: acs-connector
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 1%

---


# 同步受众{#synchronizing-audiences}

您可以使用活动v7高级功能构建复杂的列表，并以无缝方式将此列表直接实时共享为Campaign Standard（包括其他数据）。 您的Campaign Standard用户随后可以在Adobe Campaign Standard使用受众。

复杂目标定位涉及Campaign Standard中未复制的其他数据，只能使用活动v7实现。

您还只需与Campaign Standard共享通过连接器（如Microsoft Dynamics）获得的列表收件人或数据。

此用例说明如何在v7活动中准备投放的目标，以及如何在与Adobe Campaign Standard一起创建和发送的投放中重用此目标及其附加数据。

>[!NOTE]
>
>如果您需要的所有数据都已复制，您还可以使用Adobe Campaign Standard的聚合和集合来丰富数据。

## 先决条件{#prerequisites}

要实现此目标，您需要：

* 收件人存储在活动v7数据库中并与Campaign Standard同步。 请参阅同 [步用户档案](../../integrations/using/synchronizing-profiles.md) 部分。
* 其他订阅，如存储在与v7活动库中nms:收件人相关的表中的或事务。 这些数据可以来自活动v7 OOB模式或自定义表。 它们默认在Campaign Standard中不可用，因为它们未同步。
* 有权在活动v7和Campaign Standard中执行工作流。
* 创建并执行Campaign Standard投放的权利。

## 在活动v7中创建包含其他数据的定位工作流 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

复杂目标定位涉及Campaign Standard中未复制的其他数据，只能使用活动v7实现。

定义目标及其附加数据后，可以将其另存为可与Campaign Standard共享的列表。

>[!NOTE]
>
>这是一个例子。 根据您的要求，您只需查询一列表收件人并与ACS共享，无需进一步处理。 您还可以使用其他数据管理活动来准备最终目标。

要获取最终受众及其附加数据：

1. 从> >创建新工 **[!UICONTROL Profiles and Targets]** 作 **[!UICONTROL Jobs]** 流 **[!UICONTROL Targeting workflows]**。
1. 添加 **[!UICONTROL Query]** 活动，然后选择要向其发送最终电子邮件的收件人。 例如，所有18到30岁的收件人都住在法国。

   ![](assets/acs_connect_query1.png)

1. 从查询中添加其他数据。 For more information, refer to the [Adding data](../../workflow/using/query.md#adding-data) section.

   此示例说明如何添加聚合，以计算收件人在一年中收到的投放数。

   In the **[!UICONTROL Query]**, select **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. 选择 **[!UICONTROL Data linked to the filtering dimension]** 并单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query3.png)

1. 选 **[!UICONTROL Data linked to the filtering dimension]** 择，然后选择 **[!UICONTROL Recipient delivery logs]** 节点并单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query4.png)

1. 在字 **[!UICONTROL Aggregates]** 段中选 **[!UICONTROL Data collected]** 择并单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query5.png)

1. 添加筛选条件，以仅考虑过去365天内创建的日志，然后单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query6.png)

1. 定义输出列。 此处，唯一需要的列是计数投放数的列。 为此：

   * 在窗 **[!UICONTROL Add]** 口的右侧选择。
   * From the **[!UICONTROL Select field]** window, click **[!UICONTROL Advanced selection]**.
   * 选择 **[!UICONTROL Aggregate]**，然后 **[!UICONTROL Count]**。 选中选 **[!UICONTROL Distinct]** 项，然后单击 **[!UICONTROL Next]**。
   * 在字段列表中，选择用于Count函数的 **字段** 。 选择将始终填充的字段（例如字段）, **[!UICONTROL Primary key]** 然后单击 **[!UICONTROL Finish]**。
   * 更改列中的 **[!UICONTROL Alias]** 表达式。 此别名将允许您在最终投放中轻松检索添加的列。 例如 **NBdeliveries**。
   * 单击 **[!UICONTROL Finish]** 并保存 **[!UICONTROL Query]** 活动配置。

   ![](assets/acs_connect_query7.png)

1. 保存工作流。下一节将介绍如何与ACS共享人口。

## 与Campaign Standard共享目标 {#share-the-target-with-campaign-standard}

定义目标群后，您可以通过活动与ACS共 **[!UICONTROL List update]** 享。

1. 在以前创建的工作流中，添 **[!UICONTROL List update]** 加活动并指定要更新或创建的列表。

   指定要在活动v7中保存列表的文件夹。 列表受实施过程中定义的文件夹映射的约束，一旦在Campaign Standard中共享，该映射会影响其可见性。 请参阅“权 [限转换](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) ”部分。

1. 确保选中 **[!UICONTROL Share with ACS]** 了该选项。 默认情况下，选中此选项。

   ![](assets/acs_connect_listupdate1.png)

1. 保存并执行工作流。

   目标及其附加数据保存在活动v7的列表中，并立即作为Campaign Standard受众共享。 只有已复制的用户档案才会与ACS共享。

如果活动上发 **[!UICONTROL List update]** 生错误，则表示与Campaign Standard的同步可能失败。 要查看有关出错情况的更多详细信息，请转 **[!UICONTROL Administration]** 到> **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此文件夹包含由工作流执行触发的 **[!UICONTROL List update]** 同步活动。 请参阅“Troubleshooting [the ACS Connector(ACS连接器故障诊断](../../integrations/using/troubleshooting-the-acs-connector.md) )”部分。

## 在Campaign Standard中检索数据并在投放中使用 {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

在活动v7中执行定位工作流后，您可以从列表菜单以只读模式查找Campaign Standard **[!UICONTROL Audiences]** 受众。

![](assets/acs_connect_deliveryworkflow_audience.png)

通过在Campaign Standard中创建投放工作流，可以使用此受众以及它包含在投放中的其他数据。

1. 从菜单创建新的工 **[!UICONTROL Marketing activities]** 作流。
1. 添加一 **[!UICONTROL Read audience]** 个活动，然后选择您之前从活动v7共享的受众。

   此活动用于检索所选受众的数据。 您还可以根据需 **[!UICONTROL Source Filtering]** 要使用此活动的选项卡来应用其他选项。

1. 添加活动 **[!UICONTROL Email delivery]** 并将其配置为任何其他电子邮件 [投放活动](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)。
1. 打开投放内容。
1. 添加个性化字段。从弹出窗口中，找到 **[!UICONTROL Additional data (targetData)]** 节点。 此节点包含在初始定位工作流中计算的受众的附加数据。 您可以将它们用作任何其他个性化字段。

   对于此示例，来自原始定位工作流的附加数据是过去365天内发送给每个投放的收件人数。 在定位工作流中指定的NBdeliveries别名在此处可见。

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. 保存投放和工作流。

   该工作流现已准备好执行。 将分析投放并准备发送。

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## 发送和监视投放 {#send-and-monitor-your-delivery}

投放及其内容准备就绪后，请发送投放，如本节中有更多详细 [信息所述](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html):

1. 执行投放工作流。 此步骤将准备要发送的电子邮件。
1. 从投放仪表板中，手动确认可以发送投放。
1. 监视投放的报告和日志：

   * **Campaign Standard**:访问 [与](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) 投放 [相关的报](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) 告和日志，与任何投放相同。
   * **在活动v7和Campaign Standard中**:投放ID、电子邮件广泛日志和电子邮件跟踪日志已同步到活动v7。 然后，您可以从v7活动获得360°视图的营销活动。

      隔离自动同步回活动v7。 这允许考虑在活动v7中执行的下一个定位的不可交付信息。

      您可以在此部分中查找有关隔离管理的 [更多信息](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)。

