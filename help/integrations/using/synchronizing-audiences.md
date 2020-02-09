---
title: 同步受众
seo-title: 同步受众
description: 同步受众
seo-description: null
page-status-flag: never-activated
uuid: eda67bf7-8a0a-4240-8b31-de364be5d572
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 749a084e-69ee-46b4-b09b-cb91bb1da3cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 同步受众{#synchronizing-audiences}

您可以使用Campaign v7高级功能构建一个精致的列表，并通过Campaign Standard（包括其他数据）以无缝方式直接实时地将此列表共享为受众。 然后，您的Campaign standard用户可以在Adobe Campaign standard中使用受众。

涉及未在Campaign standard中复制的其他数据的复杂定位只能使用Campaign v7实现。

您还只需共享收件人列表或通过连接器（如Microsoft Dynamics和Campaign Standard）发送的数据。

此用例说明如何准备Campaign v7中的分发目标，以及如何在使用Adobe Campaign Standard创建和发送的分发中重复使用此目标及其附加数据。

>[!NOTE]
>
>如果您需要的所有数据都已复制，您还可以在Adobe Campaign standard中使用聚合和集合来丰富数据。

## 先决条件 {#prerequisites}

要实现此目标，您需要：

* 收件人存储在Campaign v7数据库中并与Campaign Standard同步。 请参阅同步配 [置文件部分](../../integrations/using/synchronizing-profiles.md) 。
* 其他数据，如订阅或存储在与Campaign v7数据库中nms:recipients相关的表中的事务。 这些数据可以来自Campaign v7 OOB架构或自定义表。 默认情况下，Campaign standard中不提供这些选项，因为它们未同步。
* 有权在Campaign v7和Campaign standard中执行工作流。
* 在Campaign standard中创建和执行分发的权利。

## 在Campaign v7中使用其他数据创建定位工作流 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

涉及未在Campaign standard中复制的其他数据的复杂定位只能使用Campaign v7实现。

定义目标及其附加数据后，可以将其另存为可与Campaign standard共享的列表。

>[!NOTE]
>
>这是一个例子。 根据您的要求，您只需查询收件人列表并与ACS共享它，无需进一步处理。 您还可以使用其他数据管理活动来准备最终目标。

要获取最终受众及其其他数据，请执行以下操作：

1. 从 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** >创建新工作流 **[!UICONTROL Targeting workflows]**。
1. 添加活 **[!UICONTROL Query]** 动，然后选择要向其发送最终电子邮件的收件人。 例如，所有18至30岁的受助者都居住在法国。

   ![](assets/acs_connect_query1.png)

1. 从查询中添加其他数据。 有关详细信息，请参阅添 [加数据](../../workflow/using/query.md#adding-data) 。

   此示例说明如何添加汇总以计算一个收件人在一年中收到的交货数。

   在中， **[!UICONTROL Query]**&#x200B;选择 **[!UICONTROL Add data...]**。

   ![](assets/acs_connect_query2.png)

1. 选择 **[!UICONTROL Data linked to the filtering dimension]** 并单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query3.png)

1. 选 **[!UICONTROL Data linked to the filtering dimension]** 择节点，然后 **[!UICONTROL Recipient delivery logs]** 单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query4.png)

1. 在字 **[!UICONTROL Aggregates]** 段中选 **[!UICONTROL Data collected]** 择并单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query5.png)

1. 添加筛选条件，以仅考虑在过去365天内创建的日志，然后单击 **[!UICONTROL Next]**。

   ![](assets/acs_connect_query6.png)

1. 定义输出列。 此处，唯一需要的列是计算提交次数的列。 为此，请执行以下操作：

   * 在窗 **[!UICONTROL Add]** 口的右侧选择。
   * 在窗口 **[!UICONTROL Select field]** 中，单击 **[!UICONTROL Advanced selection]**。
   * 然 **[!UICONTROL Aggregate]**&#x200B;后选择 **[!UICONTROL Count]**。 选中该 **[!UICONTROL Distinct]** 选项，然后单击 **[!UICONTROL Next]**。
   * 在字段列表中，选择用于“计数”功能的 **字段** 。 选择将始终填充的字段（例如，字段）, **[!UICONTROL Primary key]** 然后单击 **[!UICONTROL Finish]**。
   * 更改列中的表达 **[!UICONTROL Alias]** 式。 此别名允许您轻松检索最终分发中添加的列。 例如 **NBdeliveries**。
   * 单击 **[!UICONTROL Finish]** 并保存活 **[!UICONTROL Query]** 动配置。
   ![](assets/acs_connect_query7.png)

1. 保存工作流。 下一节介绍如何与ACS共享人口。

## 与Campaign standard共享目标 {#share-the-target-with-campaign-standard}

定义目标人群后，您可以通过活动与ACS共享该 **[!UICONTROL List update]** 人群。

1. 在以前创建的工作流中，添 **[!UICONTROL List update]** 加活动并指定要更新或创建的列表。

   指定要在Campaign v7中保存列表的文件夹。 列表受实施过程中定义的文件夹映射的约束，一旦在Campaign standard中共享，该映射会影响其可见性。 请参阅“权 [限转换](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) ”部分。

1. 确保选中 **[!UICONTROL Share with ACS]** 了此选项。 默认情况下，此选项处于选中状态。

   ![](assets/acs_connect_listupdate1.png)

1. 保存并执行工作流。

   目标及其附加数据将保存在Campaign v7中的列表中，并立即作为列表受众在Campaign standard中共享。 只有已复制的配置文件才会与ACS共享。

如果活动发生错 **[!UICONTROL List update]** 误，则表明与Campaign standard的同步可能失败。 要查看更多关于出问题的详细信息，请转到 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**。 此文件夹包含由活动执行触发的同步 **[!UICONTROL List update]** 工作流。 请参阅“ [Troubleshooting the ACS Connector](../../integrations/using/troubleshooting-the-acs-connector.md) （ACS连接器故障诊断）”部分。

## 在Campaign standard中检索数据并将其用于分发 {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

在Campaign v7中执行定位工作流后，您便可以从Campaign Standard菜单以只读模式查找列 **[!UICONTROL Audiences]** 表受众。

![](assets/acs_connect_deliveryworkflow_audience.png)

通过在Campaign standard中创建分发工作流，可以使用此受众以及分发中包含的其他数据。

1. 从菜单创建新工作 **[!UICONTROL Marketing activities]** 流。
1. 添加活 **[!UICONTROL Read audience]** 动，然后选择您之前从Campaign v7共享的受众。

   此活动用于检索选定受众的数据。 您还可以根据需 **[!UICONTROL Source Filtering]** 要，使用此活动的相应选项卡来应用其他选项卡。

1. 添加活 **[!UICONTROL Email delivery]** 动并将其配置为任何其他电子 [邮件分发活动](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html)。
1. 打开分发内容。
1. 添加个性化字段。 从弹出窗口中，找到该 **[!UICONTROL Additional data (targetData)]** 节点。 此节点包含在初始定位工作流程中计算的受众的其他数据。 您可以将它们用作任何其他个性化字段。

   在此示例中，来自原始定位工作流的其他数据是过去365天内发送给每个收件人的提交数。 在定位工作流中指定的NBdeliveries别名在此处可见。

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. 保存交付和工作流。

   该工作流现已准备好执行。 将分析交付内容并准备发送。

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## 发送和监控交付 {#send-and-monitor-your-delivery}

交付及其内容准备就绪后，请发送交付，如本节中有更多详细 [信息所述](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html):

1. 执行交付工作流。 此步骤将准备要发送的电子邮件。
1. 从传送功能板中，手动确认可以发送传送。
1. 监控交付的报告和日志：

   * **在Campaign standard中**:访问 [与交](https://docs.adobe.com/content/help/en/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) 付相关的报 [告和日志](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) ，以便进行任何交付。
   * **在Campaign v7和Campaign standard中**:交付ID、电子邮件广泛日志和电子邮件跟踪日志均同步到Campaign v7。 然后，您可以从Campaign v7以360度视角查看您的营销活动。

      隔离会自动同步回Campaign v7。 这允许将不可交付信息考虑到在Campaign v7中执行的下一个定位。

      您可以在此部分的Campaign Standard中查找有关隔离管理的更 [多信息](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)。

