---
product: campaign
title: 数据库映射
description: 数据库映射
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: e05dcd81-bbca-4767-8da3-ea064f7f6c8e
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 1%

---

# 链接管理 {#links--relation-between-tables}

链接描述一个表与另一个表之间的关联。

关联类型（也称为基数）如下所列。

* 基数1-1：源表格的一个存在最多可以具有目标表格的一个对应存在。
* 基数1-N：源表格的一个存在可以具有目标表格的多个对应存在，但目标表格的一个存在最多可以具有源表格的一个对应存在。
* 基数N-N：源表格的一个存在可以具有目标表格的多个对应存在，反之亦然。

在使用界面中，基数使用特定图标表示。

对于与Campaign表/数据库的连接关系：

* ![](assets/join_with_campaign11.png) ：基数1-1。 例如，在收件人和当前订单之间。 收件人一次只能与当前订单表的一个实例相关。
* ![](assets/externaljoin11.png) ：基数1-1，外部联接。 例如，在收件人与其国家/地区之间。 收件人只能与表国家/地区的一个匹配项相关。 将不会保存国家表的内容。
* ![](assets/join_with_campaign1n.png) ：基数1-N。例如，在收件人和订阅表之间。 收件人可能与订阅表中的多次发生次数相关。

对于使用联合数据库访问(FDA)的联接关系：

* ![](assets/join_fda_11.png) ：基数1-1
* ![](assets/join_fda_1m.png) ：基数1-N

有关FDA表的详细信息，请参阅[访问外部数据库](../../installation/using/about-fda.md)。

必须在包含通过主元素链接的表的外键的架构中声明链接：

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

链接遵循以下规则：

* 在&#x200B;**链接**&#x200B;类型&#x200B;**`<element>`**&#x200B;上输入的链接定义具有以下属性：

   * **name**：来自源表的链接的名称
   * **target**：目标架构的名称
   * **标签**：链接标签
   * **revLink**（可选）：来自目标架构的反向链接的名称（默认自动推导）
   * **完整性**（可选）：源表的出现项与目标表的出现项之间的引用完整性。
可能的值包括：

      * **定义**：如果源实例不再由目标实例引用，则可以删除该源实例
      * **normal**：删除源具体值将初始化指向目标具体值的链接的键（默认模式），此类型的完整性将初始化所有外键
      * **拥有**：删除源具体值会导致目标具体值被删除
      * **owncopy**：与&#x200B;**own**&#x200B;相同（如果删除），或重复发生次数（如果重复）
      * **neutral**：无特定行为

   * **revIntegrity**（可选）：目标架构上的完整性（可选，默认为“正常”）
   * **revCardinality**（可选）：值为“single”时，将填充类型为1-1 （默认为1-N）的基数
   * **externalJoin**（可选）：强制外部联接
   * **revExternalJoin**（可选）：强制反向链接上的外部连接

* 链接从源表向目标表引用一个或多个字段。 无需填充构成连接（`<join>`元素）的字段，因为默认情况下，这些字段是使用目标架构的内部键自动推导的。
* 索引会自动添加到扩展模式中链接的外键中。
* 链接由两个半链接组成，其中第一个链接是从源架构中声明的，第二个链接是在目标架构的扩展架构中自动创建的。
* 如果添加了&#x200B;**externalJoin**&#x200B;属性，连接可以是外部连接，其值为“true”（在PostgreSQL中受支持）。

>[!NOTE]
>
>作为标准，链接是在架构末尾声明的元素。

## 示例：反向链接 {#example-1}

在以下示例中，我们声明与“cus：company”架构表有关的1-N关系：

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

生成的架构：

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

链接定义由组成连接的字段补充，即主键在目的架构中带有其XPath (“@id”)，外键在架构中带有其XPath (“@company-id”)。

外键会自动添加到与目标表中的关联字段使用相同特征的元素中，并遵循以下命名约定：目标架构名称后跟关联字段名称（在本例中为“company-id”）。

目标(“cus：company”)的扩展架构：

```sql
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

添加了指向“cus：recipient”表的反向链接，以及以下参数：

* **name**：从源架构的名称自动推断（可在源架构的链接定义中使用“revLink”属性强制推断）
* **revLink**：反向链接的名称
* **target**：链接架构的键（“cus：recipient”架构）
* **未绑定**：链接被声明为1-N基数的集合元素（默认情况下）
* **完整性**：默认情况下为“定义”（可在源架构上的链接定义中使用“revIntegrity”属性强制执行）。

## 示例：简单链接 {#example-2}

在此示例中，我们声明指向“nms：address”模式表的链接。 连接是外部连接，使用收件人的电子邮件地址和链接表的“@address”字段(“nms：address”)显式填充。

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

## 示例：唯一基数 {#example-3}

在本例中，我们创建了一个与“cus：extension”模式表的1-1关系：

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## 示例：指向文件夹的链接 {#example-4}

在此示例中，我们声明指向文件夹（“xtk：folder”架构）的链接：

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

默认值返回在“DefaultFolder(&#39;nmsFolder&#39;)”函数中输入的第一个符合条件的参数类型文件的标识符。

## 示例：在链接上创建键 {#example-5}

在此示例中，我们在包含&#x200B;**xlink**&#x200B;属性的链接（“company”到“cus：company”架构）上创建一个键，并在(“email”)表中创建一个字段：

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

生成的架构：

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

使用“company”链接的外键扩展了“companyEmail”名称键的定义。 此键值在两个字段中都生成一个唯一索引。

## 了解详情

浏览以下链接以了解更多信息：

* [模式入门](about-schema-reference.md)
* [模式结构](schema-structure.md)
* [数据库映射](database-mapping.md)
* [密钥管理](database-keys.md)
* [Campaign数据模型](about-data-model.md)
