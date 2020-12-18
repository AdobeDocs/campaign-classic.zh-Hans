---
solution: Campaign Classic
product: campaign
title: 访问外部数据库
description: 访问外部数据库
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 9%

---


# 创建数据模式 {#creating-the-data-schema}

要在外部模式库上创建数据：

1. 单击列表模式上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮，然后选择&#x200B;**[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 输入模式的名称和说明，然后选择启用与外部帐户库连接的。 这允许访问外部基中可用表的列表。 选择包含要收集的数据的表。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;进行确认。 Adobe Campaign会自动检测所选表的结构并生成逻辑模式。 请注意，Adobe Campaign不生成链接。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以确认创建。

   >[!CAUTION]
   >
   >对于Snowflake，主键是必填项。

   ![](assets/wf_new_schema_generate_fda.png)

在映射表(标准或联合数据访问映射)时，将自动创建索引。
