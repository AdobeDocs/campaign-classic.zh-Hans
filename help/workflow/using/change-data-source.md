---
title: 更改数据源
description: 了解有关更改数据源活动的更多信息
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: 31483bdd2e0a2dd0676ef391c5484e4b778317c1
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---

# 更改数据源 {#change-data-source}

>[!NOTE]
>
> 的 **[!UICONTROL Change data source]** 活动仅在 **[!UICONTROL Access to external data (Federated Data Access)]** 包。 有关Adobe Campaign Classic内置包的更多信息，请参阅此 [页面](../../installation/using/installing-campaign-standard-packages.md).

的 **[!UICONTROL Change data source]** 活动，用于更改工作流的数据源 **[!UICONTROL Working table]**. 这为跨不同数据源（如FDA、FFDA和本地数据库）管理数据提供了更大的灵活性。

的 **[!UICONTROL Working table]** 允许Adobe Campaign Classic工作流处理数据并与工作流活动共享数据。
默认情况下， **[!UICONTROL Working table]** 创建于与我们查询的数据源相同的数据库中。

例如，在查询 **[!UICONTROL Profiles]** 表，存储在云数据库上，您将创建一个 **[!UICONTROL Working table]** 在同一云数据库上。
要更改此设置，您可以将 **[!UICONTROL Change Data Source]** 活动，为您的 **[!UICONTROL Working table]**.

请注意，在使用 **[!UICONTROL Change Data Source]** 活动时，您需要切换回云数据库以继续执行工作流。

使用 **[!UICONTROL Change Data Source]** 活动：

1. 创建工作流.

1. 使用 **[!UICONTROL Query]** 活动。

   有关 **[!UICONTROL Query]** 活动，请参阅此 [页面](../../workflow/using/query.md#creating-a-query).

1. 从 **[!UICONTROL Targeting]** 选项卡，添加 **[!UICONTROL Change data source]** 活动。

   ![](assets/change-data-source.png)

1. 双击 **[!UICONTROL Change data source]** 活动 **[!UICONTROL Default data source]**.

   将包含查询结果的工作表移到默认的PostgreSQL数据库。

   ![](assets/change-data-source_2.png)

1. 从 **[!UICONTROL Actions]** 选项卡，拖放 **[!UICONTROL JavaScript code]** 对工作表执行统一操作的活动。

   有关 **[!UICONTROL JavaScript code]** 活动，请参阅 [JavaScript代码和高级JavaScript代码](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) 页面。

1. 添加其他 **[!UICONTROL Change data source]** 活动切换回云数据库。

1. 双击您的活动，然后选择 **[!UICONTROL Active FDA external account]** 然后是对应的 **[!UICONTROL External database]** 外部帐户。

   ![](assets/change-data-source_3.png)

1. 您现在可以启动工作流。
