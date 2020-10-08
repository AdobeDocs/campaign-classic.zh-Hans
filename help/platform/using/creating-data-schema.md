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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---


# 创建数据模式 {#creating-the-data-schema}

要在外部模式库上创建数据：

1. 单击数 **[!UICONTROL New]** 据列表模式上方的按钮并选择 **[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 输入模式的名称和说明，然后选择启用与外部帐户库连接的。 这允许访问外部基中可用表的列表。 选择包含要收集的数据的表。

   ![](assets/wf_new_schema_select_table_fda.png)

1. Click **[!UICONTROL OK]** to confirm. Adobe Campaign会自动检测所选表的结构并生成逻辑模式。 请注意，Adobe Campaign不生成链接。

1. 单击 **[!UICONTROL Save]** 以确认创建。

   >[!CAUTION]
   >
   >对于Snowflake，主键是必填项。

   ![](assets/wf_new_schema_generate_fda.png)

在映射表(标准或联合数据访问映射)时，将自动创建索引。
