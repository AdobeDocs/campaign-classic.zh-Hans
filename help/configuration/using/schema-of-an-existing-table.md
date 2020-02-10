---
title: 现有表的架构
seo-title: 现有表的架构
description: 现有表的架构
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# 现有表的架构{#schema-of-an-existing-table}

## 概述 {#overview}

当应用程序需要访问现有表、SQL视图或远程数据库中的数据时，请使用以下数据在Adobe Campaign中创建其架构：

* 表的名称：使用“sqltable”属性输入表的名称（使用dblink时使用其别名）,
* 架构密钥：引用对帐字段，
* 索引：用于生成查询，
* XML结构中的字段及其位置：只填写应用程序中使用的字段，
* 链接：如果与基的其他表存在连接。

## 实施 {#implementation}

要创建相应的架构，请应用以下阶段：

1. 编辑Adobe **[!UICONTROL Administration>Configuration>Data schemas]** Campaign树的节点，然后单击 **[!UICONTROL New]** 。
1. 选择选 **[!UICONTROL Access data from an existing table or an SQL view]** 项并单击 **[!UICONTROL Next]** 。

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 选择表或现有视图：

   ![](assets/s_ncs_configuration_select_table.png)

1. 调整架构内容以满足您的需求。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   必须在根元素上使用view=&quot;true&quot;属性填充架构，才 `<srcSchema>` 能不生成表创建SQL脚本。

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

利用 **Federated Data Access - FDA** 选项，您可以访问存储在外部数据库中的数据。

本页详细介绍了架构上用于访问外部数据库中数据的 [配置](../../platform/using/accessing-an-external-database.md#creating-the-data-schema)。
