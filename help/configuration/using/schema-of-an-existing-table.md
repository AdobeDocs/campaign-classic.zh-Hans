---
product: campaign
title: 现有表的模式
description: 现有表的模式
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 10%

---

# 现有表的模式{#schema-of-an-existing-table}

## 概述 {#overview}

当应用程序需要访问现有表的数据、SQL视图或远程数据库中的数据时，请使用以下数据在Adobe Campaign中创建其模式：

* 表的名称：输入具有“sqltable”属性的表的名称（使用dblink时带有别名），
* 模式键：引用协调字段，
* 索引：用于生成查询，
* 字段及其在XML结构中的位置：仅填写应用程序中使用的字段，
* 链接：如果与基的其他表有连接。

## 实施 {#implementation}

要创建相应的方案，请应用以下阶段：

1. 编辑 **[!UICONTROL Administration>Configuration>Data schemas]** Adobe Campaign节点，然后单击 **[!UICONTROL New]** .
1. 选择 **[!UICONTROL Access data from an existing table or an SQL view]** 选项并单击 **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 选择表或现有视图：

   ![](assets/s_ncs_configuration_select_table.png)

1. 调整架构内容以满足您的需求。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   架构必须使用view=&quot;true&quot;属性填充 `<srcSchema>` 根元素，以便不生成表创建SQL脚本。

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

此 **联合数据访问 — FDA** 选项使您可以访问存储在外部数据库中的数据。

有关对架构进行配置以访问外部数据库中的数据的详情，请参见 [此页面](../../installation/using/creating-data-schema.md).
