---
product: campaign
title: 为FDA创建数据模式
description: 了解如何为FDA创建数据架构
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 创建数据架构 {#creating-the-data-schema}



要在外部数据库上创建方案，请执行以下操作：

1. 单击数据架构列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮，然后选择&#x200B;**[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 输入架构的&#x200B;**[!UICONTROL Namespace]**&#x200B;和&#x200B;**[!UICONTROL Name]**，然后选择将启用数据库连接的&#x200B;**[!UICONTROL External account]**。 这将允许访问外部库中可用的表列表。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 从&#x200B;**[!UICONTROL Table name]**&#x200B;字段中，选择包含要收集的数据的表。

   通过Snowflake，如果数据库用户已被授予正确的权限，则可以在此处选择您的视图。 请注意，在使用视图时，Adobe Campaign将无法自动生成XML架构，您必须自行创建。 有关视图的详细信息，请参阅[Snowflake文档](https://docs.snowflake.com/en/user-guide/views-introduction.html)。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;确认。 Adobe Campaign会自动检测选定表的结构并生成逻辑架构。 请注意，Adobe Campaign不生成链接。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;确认创建。

   >[!CAUTION]
   >
   >对于Snowflake，主键是必需的。

   ![](assets/wf_new_schema_generate_fda.png)

映射表（标准或FDA映射）时会自动创建索引。
