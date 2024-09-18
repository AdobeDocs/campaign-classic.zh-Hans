---
product: campaign
title: 数据库映射
description: 数据库映射
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 3%

---

# 数据库映射{#database-mapping}

此页面](schema-structure.md)中描述的示例架构[的SQL映射生成以下XML文档：

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

架构的根元素更改为&#x200B;**`<srcschema>`**&#x200B;至&#x200B;**`<schema>`**。

此其他类型的文档自动从源架构生成，简称为架构。

SQL名称是根据元素名称和类型自动确定的。

SQL命名规则如下：

* **表**：架构命名空间和名称的连接

  在我们的示例中，表的名称是通过&#x200B;**sqltable**&#x200B;属性中架构的主元素输入的：

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **字段**：前面有根据类型定义的前缀的元素名称：“i”表示整数，“d”表示双精度，“s”表示字符串，“ts”表示日期等。

  字段名称通过每个键入的&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;的&#x200B;**sqlname**&#x200B;属性输入：

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>可以从源架构重载SQL名称。 为此，请在相关元素中填充“sqltable”或“sqlname”属性。

用于创建从扩展模式生成的表的SQL脚本如下所示：

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL字段约束如下：

* 数字和日期字段中没有空值
* 数值字段已初始化为0

## XML字段 {#xml-fields}

默认情况下，任何&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;类型元素均映射到数据架构表的SQL字段。 但是，您可以用XML而不是SQL引用此字段，这意味着数据存储在包含所有XML字段值的表的备注字段(“mData”)中。 这些数据的存储是一个观察模式结构的XML文档。

要在XML中填充字段，您必须将值为“true”的&#x200B;**xml**&#x200B;特性添加到相关元素。

**示例**：以下是两个XML字段用法示例。

* 多行评论字段：

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* HTML格式的数据描述：

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  通过“html”类型，您可以将HTML内容存储在CDATA标记中，并在Adobe Campaign客户端界面中显示特殊的HTML编辑检查。

使用XML字段添加新字段，而无需修改数据库的物理结构。 另一个优点是，您使用的资源较少（分配给SQL字段的大小、每个表的字段数限制等）。 但是，请注意，不能索引或过滤XML字段。

## 索引字段 {#indexed-fields}

通过索引，可以优化应用程序中使用的SQL查询的性能。

从数据架构的主元素声明索引。

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

索引遵循以下规则：

* 索引可以引用表中的一个或多个字段
* 如果&#x200B;**unique**&#x200B;属性包含值“true”，则所有字段中的索引都可以是唯一的（以避免重复）
* 索引的SQL名称由表的SQL名称和索引的名称确定

>[!NOTE]
>
>* 作为标准，索引是从架构的主元素声明的第一个元素。
>
>* 在表映射期间（标准或FDA）自动创建索引。

**示例**：

* 向电子邮件地址和城市添加索引：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* 向“id”名称字段添加唯一索引：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## 了解详情

浏览以下链接以了解更多信息：

* [模式入门](about-schema-reference.md)
* [模式结构](schema-structure.md)
* [密钥管理](database-keys.md)
* [链接管理](database-links.md)
* [Campaign数据模型](about-data-model.md)