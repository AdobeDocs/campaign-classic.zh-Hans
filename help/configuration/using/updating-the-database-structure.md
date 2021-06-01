---
product: campaign
title: 更新数据库结构
description: 更新数据库结构
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# 更新数据库结构{#updating-the-database-structure}

要应用对架构所做的修改，请启动数据库更新向导。 可通过&#x200B;**[!UICONTROL Tools > Advanced > Update database structure]**&#x200B;访问此向导。 它检查数据库的物理结构是否与其逻辑描述匹配，并执行SQL更新脚本。

![](assets/d_ncs_integration_schema_update.png)

数据库中的模块会自动填充和激活。

![](assets/d_ncs_integration_schema_update_select.png)

**[!UICONTROL Add stored procedures]**&#x200B;和&#x200B;**[!UICONTROL Import initialization data]**&#x200B;选项用于启动初始SQL脚本以及创建数据库时执行的数据包。

您可以从外部数据包导入一组数据。 要执行此操作，请选择&#x200B;**[!UICONTROL Import a package]**&#x200B;并输入包的XML文件。

按照以下步骤查看数据库更新SQL脚本：

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>它位于编辑字段中，可进行修改以删除或添加SQL代码。

接下来，启动数据库更新：

![](assets/d_ncs_integration_schema_update3.png)
