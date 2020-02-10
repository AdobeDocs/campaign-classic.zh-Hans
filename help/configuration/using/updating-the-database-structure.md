---
title: 更新数据库结构
seo-title: 更新数据库结构
description: 更新数据库结构
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 更新数据库结构{#updating-the-database-structure}

要将所做的修改应用到架构，请启动数据库更新向导。 可通过访问此向导 **[!UICONTROL Tools > Advanced > Update database structure]** 。 它检查数据库的物理结构是否与其逻辑描述匹配并执行SQL更新脚本。

![](assets/d_ncs_integration_schema_update.png)

数据库中的模块会自动填充并激活。

![](assets/d_ncs_integration_schema_update_select.png)

和 **[!UICONTROL Add stored procedures]** 选项 **[!UICONTROL Import initialization data]** 用于启动初始SQL脚本以及创建数据库时执行的数据包。

您可以从外部数据包导入一组数据。 为此，请选 **[!UICONTROL Import a package]** 择并输入包的XML文件。

按照以下步骤操作并查看数据库更新SQL脚本：

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>它位于编辑字段中，可进行修改以删除或添加SQL代码。

接下来，启动数据库更新：

![](assets/d_ncs_integration_schema_update3.png)

