---
product: campaign
title: 现有表的模式
description: 现有表的模式
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 9%

---

# 现有表的模式{#schema-of-an-existing-table}

![](../../assets/v7-only.svg)

## 概述 {#overview}

当应用程序需要访问现有表、SQL视图或远程数据库中的数据时，请使用以下数据在Adobe Campaign中创建其模式：

* 表名称：使用&quot;sqltable&quot;属性输入表的名称（使用dblink时的别名），
* 架构键：引用协调字段，
* 索引：用于生成查询，
* XML结构中的字段及其位置：仅填写应用程序中使用的字段，
* 链接：是否与基的其他表存在连接。

## 实施 {#implementation}

要创建相应的架构，请应用以下阶段：

1. 编辑 **[!UICONTROL Administration>Configuration>Data schemas]** Adobe Campaign树的节点，然后单击 **[!UICONTROL New]** .
1. 选择 **[!UICONTROL Access data from an existing table or an SQL view]** 选项并单击 **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 选择表或现有视图：

   ![](assets/s_ncs_configuration_select_table.png)

1. 根据您的需求调整架构内容。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   架构必须在 `<srcSchema>` 根元素，以便不生成表创建SQL脚本。

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

的 **联合数据访问 — FDA** 选项授予您访问存储在外部数据库中的数据的权限。

有关在架构上执行以访问外部数据库中数据的配置，请参见 [本页](../../installation/using/creating-data-schema.md).
