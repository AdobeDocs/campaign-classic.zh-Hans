---
solution: Campaign Classic
product: campaign
title: 现有表的模式
description: 现有表的模式
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 9%

---


# 现有表的模式{#schema-of-an-existing-table}

## 概述 {#overview}

当应用程序需要访问现有表、SQL视图或来自远程数据库的数据时，请使用以下数据创建其Adobe Campaign:

* 表的名称：在“sqltable”属性中输入表的名称（使用dblink时使用其别名）,
* 模式键：引用对帐字段，
* 索引：用于生成查询,
* XML结构中的字段及其位置：仅填写应用程序中使用的字段，
* 链接：是否与基的其他表存在连接。

## 实现{#implementation}

要创建相应的模式，请应用以下阶段：

1. 编辑Adobe Campaign树的&#x200B;**[!UICONTROL Administration>Configuration>Data schemas]**&#x200B;节点，然后单击&#x200B;**[!UICONTROL New]**。
1. 选择&#x200B;**[!UICONTROL Access data from an existing table or an SQL view]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 选择表或现有视图:

   ![](assets/s_ncs_configuration_select_table.png)

1. 调整模式内容以满足您的需求。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   模式必须在`<srcSchema>`根元素上使用视图=&quot;true&quot;属性进行填充，才能生成表创建SQL脚本。

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

**联合数据访问-联合数据访问**&#x200B;选项允许您访问存储在外部数据库中的数据。

要对访问外部模式库中数据的进行的配置在[本页](../../installation/using/creating-data-schema.md)中有详细说明。
