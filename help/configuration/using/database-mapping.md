---
product: campaign
title: 数据库映射
description: 数据库映射
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: bd1007ffcfa58ee60fdafa424c7827e267845679
workflow-type: tm+mt
source-wordcount: '1984'
ht-degree: 0%

---

# 数据库映射{#database-mapping}

描述的示例架构的SQL映射 [本页内容](schema-structure.md) 生成以下XML文档：

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

## 说明 {#description}

架构的根元素已更改为 **`<srcschema>`** 到 **`<schema>`**.

此其他类型的文档自动从源架构生成，简称为架构。

SQL名称是根据元素名称和类型自动确定的。

SQL命名规则如下：

* **表**：架构命名空间和名称的连接

  在本例中，表的名称是通过以下位置的架构主元素输入的： **sqltable** 属性：

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **字段**：前面有前缀的元素的名称，前缀根据类型定义：“i”表示整数，“d”表示双精度，“s”表示字符串，“ts”表示日期等。

  字段名称是通过 **sqlname** 每种类型属性 **`<attribute>`** 和 **`<element>`**：

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

默认情况下，任意  **`<attribute>`** 和 **`<element>`** -typed元素映射到数据架构表的SQL字段。 但是，您可以用XML而不是SQL引用此字段，这意味着数据存储在包含所有XML字段值的表的备注字段(“mData”)中。 这些数据的存储是一个观察模式结构的XML文档。

要在XML中填充字段，您必须添加 **xml** 对于相关元素，属性值为“true”。

**示例**：以下是两个XML字段用法的示例。

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
* 在以下情况下，索引可以在所有字段中是唯一的（以避免重复） **独特** 属性包含值“true”
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

## 密钥管理 {#management-of-keys}

表必须具有至少一个用于标识表中记录的键。

从数据架构的主元素中声明了一个键。

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

以下规则适用于键：

* 键可以引用表中的一个或多个字段
* 当某个键是架构中第一个要填充的键或包含 **内部** 值为“true”的属性
* 为每个键定义隐式声明唯一索引。 可以通过添加以下内容来阻止在键上创建索引 **noDbIndex** 值为“true”的属性

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

### 自动增量键 {#auto-incremental-key}

大多数Adobe Campaign表的主键是由数据库引擎自动生成的32位长整数。 键值的计算取决于序列(默认情况下， **XtkNewId** SQL函数)生成在整个数据库中唯一的编号。 在插入记录时自动输入密钥的内容。

增量键的优点在于，它为表之间的连接提供了不可修改的技术键。 此外，此键不会占用太多内存，因为它使用双字节整数。

您可以在源架构中指定要与配合使用的序列的名称 **pk序列** 属性。 如果源架构中未提供此属性，则 **XtkNewId** 将使用默认序列。 应用程序使用专用序列来 **nms：broadLog** 和 **nms：trackingLog** 架构(**NmsBroadLogId** 和 **NmsTrackingLogId** 分别)，因为这些是包含最多记录的表。

从ACC 18.10， **XtkNewId** 不再是现成架构中序列的默认值。 您现在可以使用专用序列构建模式或扩展现有模式。

>[!IMPORTANT]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

>[!NOTE]
>
>Adobe Campaign架构中引用的序列(**NmsTrackingLogId** 例如)必须与返回参数中ID数的SQL函数关联（用逗号分隔）。 必须调用此函数 **GetNew** XXX **Id**，其中 **XXX** 是序列的名称(**GetNewNmsTrackingLogIds** 例如)。 查看 **postgres-nms.sql**， **mssql-nms.sql** 或 **oracle-nms.sql** 随应用程序提供的文件 **datakit/nms/eng/sql/** 目录，以恢复为每个数据库引擎创建“NmsTrackingLogId”序列的示例。

要声明唯一键，请填充 **autopk** 属性（值为“true”）。

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

## 链接：表之间的关系 {#links--relation-between-tables}

链接描述一个表与另一个表之间的关联。

各种类型的关联（称为“基数”）如下所示：

* 基数1-1：源表格的一个存在最多可以具有目标表格的一个对应存在。
* 基数1-N：源表格的一个存在可以具有目标表格的多个对应存在，但目标表格的一个存在最多可以具有源表格的一个对应存在。
* 基数N-N：源表格的一个存在可以具有目标表格的多个对应存在，反之亦然。

在界面中，通过图标可以轻松区分不同类型的关系。

对于与Campaign表/数据库的连接关系：

* ![](assets/join_with_campaign11.png) ：基数1-1。 例如，在收件人和当前订单之间。 收件人一次只能与当前订单表的一个实例相关。
* ![](assets/externaljoin11.png) ：基数1-1，外部连接。 例如，在收件人与其国家/地区之间。 收件人只能与表国家/地区的一个匹配项相关。 将不会保存国家表的内容。
* ![](assets/join_with_campaign1n.png) ：基数1-N。例如，在收件人和订阅表之间。 收件人可能与订阅表中的多次发生次数相关。

对于使用联合数据库访问的联接关系：

* ![](assets/join_fda_11.png) ：基数1-1
* ![](assets/join_fda_1m.png) ：基数1-N

有关FDA表的详细信息，请参阅 [访问外部数据库](../../installation/using/about-fda.md).

必须在包含通过主元素链接的表的外键的架构中声明链接：

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

链接遵循以下规则：

* 链接的定义输入于 **链接**-type **`<element>`** 具有以下属性：

   * **name**：源表中的链接的名称，
   * **目标**：目标架构的名称，
   * **标签**：链接标签，
   * **revLink** （可选）：目标模式中的反向链接的名称（默认情况下自动推导得出），
   * **完整性** （可选）：源表的出现位置与目标表的出现位置之间的参照完整性。 可能的值如下：

      * **定义**：如果源具体值不再由目标具体值引用，则可以删除该源具体值，
      * **普通**：删除源具体值将初始化指向目标具体值的链接的键（默认模式），此类型的完整性将初始化所有外键，
      * **所有者**：删除源具体值会导致删除目标具体值，
      * **owncopy**：与 **所有者** （在删除的情况下）或重复发生次数（在重复发生的情况下），
      * **中性**：不执行任何操作。

   * **revIntegrity** （可选）：目标模式上的完整性（可选，默认为“正常”），
   * **revCardinality** （可选）：值为“single”时，将使用1-1类型填充基数（默认情况下为1-N）。
   * **externalJoin** （可选）：强制外部连接
   * **revExternalJoin** （可选）：强制反向链接上的外部连接

* 链接从源表向目标表引用一个或多个字段。 构成连接的字段( `<join>`  元素)，因为它们默认使用目标架构的内部键自动推导。
* 索引会自动添加到扩展模式中链接的外键中。
* 链接由两个半链接组成，其中第一个链接是从源架构中声明的，第二个链接是在目标架构的扩展架构中自动创建的。
* 连接可以是外部连接，如果 **externalJoin** 添加了属性，其值为“true”（PostgreSQL支持）。

>[!NOTE]
>
>作为标准，链接是在架构末尾声明的元素。

### 示例1 {#example-1}

与“cus：company”架构表相关的1-N关系：

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

* **name**：自动从源架构的名称推导得出（可以在源架构的链接定义中使用“revLink”属性强制执行）
* **revLink**：反向链接的名称
* **目标**：链接模式的键（“cus：recipient”模式）
* **未绑定**：链接声明为1-N基数的收集要素（默认情况下）
* **完整性**：默认情况下，“定义”（可以在源架构上的链接定义中使用“revIntegrity”属性强制执行）。

### 示例2 {#example-2}

在本例中，我们将声明指向“nms：address”模式表的链接。 连接是外部连接，使用收件人的电子邮件地址和链接表的“@address”字段(“nms：address”)显式填充。

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

### 示例3 {#example-3}

与“cus：extension”架构表的1-1关系：

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### 示例4 {#example-4}

链接到文件夹（“xtk：folder”架构）：

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

默认值返回在“DefaultFolder(&#39;nmsFolder&#39;)”函数中输入的第一个符合条件的参数类型文件的标识符。

### 示例5 {#example-5}

在本例中，我们希望使用在链接（“company”到“cus：company”架构）上创建键 **xlink** （“电子邮件”）表的属性和字段：

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
