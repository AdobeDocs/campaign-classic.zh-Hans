---
title: 访问外部数据库
seo-title: 访问外部数据库
description: 访问外部数据库
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9a26ec7ed1c8463270ac9f97079f49e00d5b258e

---


# 创建数据架构 {#creating-the-data-schema}

要在外部数据库上创建架构，请执行以下操作：

1. 单击数 **[!UICONTROL New]** 据架构列表上方的按钮，然后选择 **[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 输入架构的名称和说明，然后选择将启用与数据库连接的外部帐户。 这允许访问外部基础中可用的表列表。 选择包含要收集的数据的表。

   ![](assets/wf_new_schema_select_table_fda.png)

1. Click **[!UICONTROL OK]** to confirm. Adobe Campaign会自动检测选定表的结构并生成逻辑架构。 请注意，Adobe Campaign不生成链接。

1. 单击 **[!UICONTROL Save]** 以确认创建。

   >[!CAUTION]
   >
   >有了雪花，主要的钥匙是必需的。

   ![](assets/wf_new_schema_generate_fda.png)

在映射表（标准或FDA映射）时，会自动创建索引。
