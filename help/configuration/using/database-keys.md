---
product: campaign
title: 数据架构中的密钥管理
description: 了解数据架构中的密钥管理
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 2%

---

# 架构中的密钥管理 {#management-of-keys}

与数据模式相关联的每个表必须具有至少一个用于标识表中记录的键。

从数据架构的主元素中声明了一个键。

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

如果某个键是架构中第一个要填充的键，或者包含设置为“true”的`internal`属性，则该键被称为“主键”。

以下规则适用于键：

* 键可以引用表中的一个或多个字段
* 为每个键定义隐式声明唯一索引。 通过将`noDbIndex`属性设置为“true”，可以阻止在键上创建索引。

>[!NOTE]
>
>* 作为标准，键是在定义索引后从架构的主元素声明的元素。
>
>* 键是在表映射（标准或FDA）期间创建的，Adobe Campaign查找唯一的索引。

**示例**：

* 向电子邮件地址和城市添加密钥：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  生成的架构：

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
     <dbindex name="email" unique="true">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
     </dbindex>    
  
     <key name="email">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="location/@city"/>    
     </key>    
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* 在“id”名称字段中添加主键或内部键：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  生成的架构：

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
      <key name="email">      
        <keyfield xpath="@email"/>    
      </key>    
  
      <dbindex name="id" unique="true">      
        <keyfield xpath="@id"/>    
      </dbindex>    
  
      <key internal="true" name="id">      
       <keyfield xpath="@id"/>    
      </key>    
  
      <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

## 自动增量键 {#auto-incremental-key}

大多数Adobe Campaign表的主键是由数据库引擎自动生成的32位长整数。 键值的计算取决于序列（默认情况下，**XtkNewId** SQL函数），该序列生成的数字在整个数据库中是唯一的。 在插入记录时自动输入密钥的内容。

增量键的优点在于，它为表之间的连接提供了不可修改的技术键。 此外，此键不会占用太多内存，因为它使用双字节整数。

您可以在源架构中指定要与&#x200B;**pkSequence**&#x200B;属性一起使用的序列的名称。 如果源架构中未提供此属性，则将使用&#x200B;**XtkNewId**&#x200B;默认序列。 应用程序对&#x200B;**nms：broadLog**&#x200B;和&#x200B;**nms：trackingLog**&#x200B;架构使用专用序列（分别为&#x200B;**NmsBroadLogId**&#x200B;和&#x200B;**NmsTrackingLogId**），因为这些是包含最多记录的表。

从ACC 18.10开始，**XtkNewId**&#x200B;不再是现成架构中序列的默认值。 您现在可以使用专用序列构建模式或扩展现有模式。

>[!IMPORTANT]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

在Adobe Campaign架构中引用的序列（例如&#x200B;**NmsTrackingLogId**）必须与返回参数中ID数的SQL函数关联，并以逗号分隔。 此函数必须调用&#x200B;**GetNew** XXX **Ids**，其中&#x200B;**XXX**&#x200B;是序列的名称（例如&#x200B;**GetNewNmsTrackingLogIds**）。 查看&#x200B;**datakit/nms/eng/sql/**&#x200B;目录中随应用程序提供的&#x200B;**postgres-nms.sql**、**mssql-nms.sql**&#x200B;或&#x200B;**oracle-nms.sql**&#x200B;文件，以恢复为每个数据库引擎创建“NmsTrackingLogId”序列的示例。

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

* [模式入门](about-schema-reference.md)
* [模式结构](schema-structure.md)
* [数据库映射](database-mapping.md)
* [链接管理](database-links.md)
* [Campaign 数据模型](about-data-model.md)
