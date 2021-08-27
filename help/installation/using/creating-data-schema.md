---
product: campaign
title: 访问外部数据库
description: 访问外部数据库
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 9%

---

# 创建数据模式 {#creating-the-data-schema}

![](../../assets/v7-only.svg)

要在外部数据库上创建模式，请执行以下操作：

1. 单击数据架构列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮，然后选择&#x200B;**[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 输入架构的名称和说明，然后选择将启用与数据库连接的外部帐户。 这允许访问外部库中可用的表列表。 选择包含要收集的数据的表。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;确认。 Adobe Campaign会自动检测所选表的结构并生成逻辑架构。 请注意，Adobe Campaign不生成链接。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以确认创建。

   >[!CAUTION]
   >
   >对于Snowflake，主键是必填项。

   ![](assets/wf_new_schema_generate_fda.png)

在映射表（标准或FDA映射）时，会自动创建索引。
