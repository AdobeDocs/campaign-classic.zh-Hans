---
product: campaign
title: 数据架构中的密钥管理
description: 了解数据架构中的密钥管理
feature: Configuration, Instance Settings
role: Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
TQID: 'https://experienceleague.adobe.com/dErbfzRabMls-5x1S3eRZO94Kqcz9LRh3PaUhVD5zAU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%
---
# 架构中的密钥管理 {#management-of-keys}

与数据模式相关联的每个表必须具有至少一个用于标识表中记录的键。 本页介绍在Campaign Classic v7表中使用的自动增量键。

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关密钥管理的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-keys){target=_blank}

## 自动增量键 {#auto-incremental-key}

大多数Adobe Campaign表的主键是由数据库引擎自动生成的32位长整数。 键值的计算取决于序列（默认情况下，**XtkNewId** SQL函数），该序列生成的数字在整个数据库中是唯一的。 在插入记录时自动输入密钥的内容。

增量键的优点在于，它为表之间的连接提供了不可修改的技术键。 此外，此键不会占用太多内存，因为它使用双字节整数。

您可以在源架构中指定要与&#x200B;**pkSequence**&#x200B;属性一起使用的序列的名称。 如果源架构中未提供此属性，则将使用&#x200B;**XtkNewId**&#x200B;默认序列。 应用程序对&#x200B;**nms:broadLog**&#x200B;和&#x200B;**nms:trackingLog**&#x200B;架构使用专用序列（分别为&#x200B;**NmsBroadLogId**&#x200B;和&#x200B;**NmsTrackingLogId**），因为这些是包含最多记录的表。

从ACC 18.10开始，**XtkNewId**&#x200B;不再是现成架构中序列的默认值。 您现在可以使用专用序列构建模式或扩展现有模式。

>[!IMPORTANT]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

在Adobe Campaign架构中引用的序列（例如&#x200B;**NmsTrackingLogId**）必须与返回参数中ID数的SQL函数关联，并以逗号分隔。 此函数必须调用&#x200B;**GetNew** XXX **Ids**，其中&#x200B;**XXX**&#x200B;是序列的名称（例如&#x200B;**GetNewNmsTrackingLogIds**）。 查看随&#x200B;**datakit/nms/eng/sql/**&#x200B;目录中的应用程序提供的&#x200B;**postgres-nms.sql**、**mssql-nms.sql**&#x200B;或&#x200B;**oracle-nms.sql**&#x200B;文件，以恢复为每个数据库引擎创建“NmsTrackingLogId”序列的示例。

要声明唯一键，请在数据架构的主元素中填充&#x200B;**autopk**&#x200B;属性（值为“true”）。

**示例**：

在源模式中声明增量密钥：

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

生成的架构：

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

除了键及其索引的定义之外，还向扩展架构中添加了名为“id”的数字字段，以包含自动生成的主键。

>[!IMPORTANT]
>
>创建表时，主键设置为0的记录会自动插入。 此记录用于避免外部联接，这对于卷表无效。 默认情况下，所有外键都使用值0进行初始化，这样，当数据项未填充时，就始终可以在连接上返回结果。


## 了解详情

浏览以下链接以了解更多信息：

* [架构入门](about-schema-reference.md)
* [架构结构](schema-structure.md)
* [数据库映射](database-mapping.md)
* [链接管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"}（Campaign v8文档）
* [Campaign数据模型](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/datamodel){target="_blank"}（Campaign v8文档）
