---
title: 更改数据源
description: 了解有关更改数据源活动的更多信息
audience: workflow
content-type: reference
topic-tags: targeting-activities
source-git-commit: 9fc4add3f12e3f06b031c4969bd8409c67e4359e
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 更改数据源 {#change-data-source}

>[!NOTE]
>
> **[!UICONTROL Change data source]**&#x200B;活动仅在&#x200B;**[!UICONTROL Access to external data (Federated Data Access)]**&#x200B;包中可用。 有关Adobe Campaign Classic内置软件包的更多信息，请参阅此[页面](../../installation/using/installing-campaign-standard-packages.md)。

利用&#x200B;**[!UICONTROL Change data source]**&#x200B;活动，可更改工作流&#x200B;**[!UICONTROL Working table]**&#x200B;的数据源。 这为跨不同数据源（如FDA、FFDA和本地数据库）管理数据提供了更大的灵活性。

**[!UICONTROL Working table]**允许Adobe Campaign Classic工作流处理数据并与工作流活动共享数据。
默认情况下， **[!UICONTROL Working table]**&#x200B;创建在与我们查询的数据源相同的数据库中。

例如，在查询存储在云数据库上的&#x200B;**[!UICONTROL Profiles]**&#x200B;表时，您将在同一云数据库上创建一个&#x200B;**[!UICONTROL Working table]**。
要更改此设置，您可以添加**[!UICONTROL Change Data Source]**&#x200B;活动，为&#x200B;**[!UICONTROL Working table]**&#x200B;选择其他数据源。

请注意，使用&#x200B;**[!UICONTROL Change Data Source]**&#x200B;活动时，您需要切换回云数据库以继续执行工作流。

要使用&#x200B;**[!UICONTROL Change Data Source]**&#x200B;活动，请执行以下操作：

1. 创建工作流.

1. 通过&#x200B;**[!UICONTROL Query]**&#x200B;活动查询目标收件人。

   有关&#x200B;**[!UICONTROL Query]**&#x200B;活动的更多信息，请参阅此[页面](../../workflow/using/query.md#creating-a-query)。

1. 在&#x200B;**[!UICONTROL Targeting]**&#x200B;选项卡中，添加&#x200B;**[!UICONTROL Change data source]**&#x200B;活动。

   ![](assets/change-data-source.png)

1. 双击&#x200B;**[!UICONTROL Change data source]**&#x200B;活动以选择&#x200B;**[!UICONTROL Default data source]**。

   将包含查询结果的工作表移到默认的PostgreSQL数据库。

   ![](assets/change-data-source_2.png)

1. 从&#x200B;**[!UICONTROL Actions]**&#x200B;选项卡中，拖放&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动以对工作表执行统一操作。

   有关&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动的更多信息，请参阅[JavaScript代码和高级JavaScript代码](../../workflow/using/sql-code-and-javascript-code.md#javascript-code)页面。

1. 添加另一个&#x200B;**[!UICONTROL Change data source]**&#x200B;活动以切换回云数据库。

1. 双击您的活动，选择&#x200B;**[!UICONTROL Active FDA external account]**，然后选择相应的&#x200B;**[!UICONTROL External database]**&#x200B;外部帐户。

   ![](assets/change-data-source_3.png)

1. 您现在可以启动工作流。