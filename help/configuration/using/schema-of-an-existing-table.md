---
title: 现有表的模式
seo-title: 现有表的模式
description: 现有表的模式
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 11%

---


# 现有表的模式{#schema-of-an-existing-table}

## 概述 {#overview}

当应用程序需要访问现有表、SQL视图或来自远程数据库的数据时，请使用以下数据创建其Adobe Campaign:

* 表的名称：在“sqltable”属性中输入表的名称（使用dblink时使用其别名）,
* 模式键：引用对帐字段，
* 索引：用于生成查询,
* XML结构中的字段及其位置：仅填写应用程序中使用的字段，
* 链接：是否与基的其他表存在连接。

## 实施 {#implementation}

要创建相应的模式，请应用以下阶段：

1. 编辑Adobe Campaign **[!UICONTROL Administration>Configuration>Data schemas]** 树的节点，然后单击 **[!UICONTROL New]** 。
1. Select the **[!UICONTROL Access data from an existing table or an SQL view]** option and click **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 选择表或现有视图:

   ![](assets/s_ncs_configuration_select_table.png)

1. 调整模式内容以满足您的需求。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   模式必须在根元素上填充视图=&quot;true&quot;属性， `<srcSchema>` 才能不生成表创建SQL脚本。

**示例** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## 访问外部数据库 {#accessing-an-external-database}

联合数据访问 **-联合数据访问选项** ，允许您访问存储在外部数据库中的数据。

本页详细介绍了在外部模式库中访问数据的 [配置](../../platform/using/creating-data-schema.md)。
