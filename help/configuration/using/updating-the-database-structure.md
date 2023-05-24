---
product: campaign
title: 更新数据库结构
description: 更新数据库结构
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 50a89f993523f3274e87ebac740d1c121082e18c
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# 更新数据库结构{#updating-the-database-structure}



要应用对架构所做的修改，请启动数据库更新向导。 此向导可通过以下方式访问： **[!UICONTROL Tools > Advanced > Update database structure]** . 它检查数据库的物理结构是否与其逻辑描述匹配，并执行SQL更新脚本。

![](assets/d_ncs_integration_schema_update.png)

自动填充和激活数据库中的模块。

![](assets/d_ncs_integration_schema_update_select.png)

此 **[!UICONTROL Add stored procedures]** 和 **[!UICONTROL Import initialization data]** 选项用于启动初始SQL脚本以及在创建数据库时执行的数据包。

您可以从外部数据包导入一组数据。 要执行此操作，请选择 **[!UICONTROL Import a package]** 并输入包的XML文件。

按照以下步骤操作并查看数据库更新SQL脚本：

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>该代码位于编辑字段中，可以修改该代码以删除或添加SQL代码。

接下来，启动数据库更新：

![](assets/d_ncs_integration_schema_update3.png)
