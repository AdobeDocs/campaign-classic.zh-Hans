---
product: campaign
title: 为FDA创建数据模式
description: 了解如何为FDA创建数据架构
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# 创建数据模式 {#creating-the-data-schema}



要在外部数据库上创建方案，请执行以下操作：

1. 单击 **[!UICONTROL New]** 按钮进行选择 **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. 输入 **[!UICONTROL Namespace]** 和  **[!UICONTROL Name]** ，然后选择 **[!UICONTROL External account]** 将启用到数据库的连接。 这样即可访问外部库中可用的表列表。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 从 **[!UICONTROL Table name]** 字段中，选择包含要收集的数据的表。

   通过Snowflake，如果数据库用户已被授予正确的权限，则可以在此处选择您的视图。 请注意，在使用视图时，Adobe Campaign将无法自动生成XML架构，您必须自行创建。 有关视图的详细信息，请参阅 [Snowflake文档](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. 单击 **[!UICONTROL OK]** 确认。Adobe Campaign会自动检测选定表的结构并生成逻辑架构。 请注意，Adobe Campaign不生成链接。

1. 单击 **[!UICONTROL Save]** 以确认创建。

   >[!CAUTION]
   >
   >对于Snowflake，主键是必需的。

   ![](assets/wf_new_schema_generate_fda.png)

映射表（标准映射或FDA映射）时会自动创建索引。
