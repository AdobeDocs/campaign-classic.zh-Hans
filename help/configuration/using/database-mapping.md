---
product: campaign
title: 数据库映射
description: 数据库映射
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1974'
ht-degree: 0%

---

# 数据库映射{#database-mapping}

我们示例架构的SQL映射提供了以下XML文档：

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## 说明 {#description}

架构的根元素不再为&#x200B;**`<srcschema>`**，而是&#x200B;**`<schema>`**。

这会将我们转到另一类文档，该文档是从源架构自动生成的，简称为架构。 此架构将由Adobe Campaign应用程序使用。

SQL名称根据元素名称和类型自动确定。

SQL命名规则如下：

* 表：架构命名空间和名称的拼接

   在本例中，表的名称是通过&#x200B;**sqltable**&#x200B;属性中模式的主元素输入的：

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* 字段：元素的名称，前面是根据类型定义的前缀（“i”表示整数，“d”表示双精度类型，“s”表示字符串，“ts”表示日期等）

   字段名称通过&#x200B;**sqlname**&#x200B;属性输入，用于每个键入的&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>SQL名称可以从源架构中重载。 要实现此目的，请在相关元素中填充“sqltable”或“sqlname”属性。

用于创建从扩展模式生成的表的SQL脚本如下所示：

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL字段约束如下：

* 数字和日期字段中没有空值，
* 数字字段已初始化为0。

## XML字段{#xml-fields}

默认情况下，任何键入的&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;元素都会映射到数据架构表的SQL字段。 但是，您可以在XML中引用此字段，而不是SQL ，这意味着数据存储在包含所有XML字段值的表的Memo字段(&quot;mData&quot;)中。 这些数据的存储是一个XML文档，用于观察架构结构。

要在XML中填充字段，必须向相关元素添加值为“true”的&#x200B;**xml**&#x200B;属性。

**示例**:以下是两个XML字段使用示例。

* 多行注释字段：

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* HTML格式的数据描述：

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   “html”类型允许您将HTML内容存储在CDATA标记中，并在Adobe Campaign客户端界面中显示特殊的HTML编辑检查。

使用XML字段，您无需修改数据库的物理结构即可添加字段。 另一个优势是使用的资源较少（分配给SQL字段的大小、对每个表的字段数的限制等）。

主要缺点是无法索引或过滤XML字段。

## 索引字段{#indexed-fields}

通过索引，可以优化应用程序中使用的SQL查询的性能。

从数据架构的主元素中声明索引。

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

索引遵循以下规则：

* 索引可以引用表中的一个或多个字段。
* 如果&#x200B;**unique**&#x200B;属性包含值“true”，则所有字段中的索引可以是唯一的（以避免重复）。
* 索引的SQL名称由表的SQL名称和索引的名称确定。

>[!NOTE]
>
>作为标准，索引是从架构的主元素声明的第一个元素。

>[!NOTE]
>
>索引在表映射（标准或FDA）期间自动创建。

**示例**:

* 向电子邮件地址和城市添加索引：

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </dbindex>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

* 向“id”名称字段添加唯一索引：

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="id" unique="true">
         <keyfield xpath="@id"/> 
       </dbindex>
   
       <dbindex name="email">
         <keyfield xpath="@email"/> 
       </dbindex>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

## 密钥管理{#management-of-keys}

表必须至少具有一个用于标识表中记录的键。

从数据架构的主元素中声明一个键。

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

密钥遵循以下规则：

* 键可以引用表中的一个或多个字段。
* 如果键是要填充的架构中的第一个键，或者它包含值为“true”的&#x200B;**internal**&#x200B;属性，则称为“primary”（或“priority”）。
* 每个键定义隐式声明一个唯一索引。 通过添加值为“true”的&#x200B;**noDbIndex**&#x200B;属性，可以阻止在键上创建索引。

>[!NOTE]
>
>作为标准，键是在定义索引后从架构的主元素中声明的元素。

>[!NOTE]
>
>在表映射（标准或FDA）期间创建键，Adobe Campaign会查找唯一索引。

**示例**:

* 向电子邮件地址和城市添加键：

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </key>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

   生成的架构：

   ```
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
   
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
      <element label="Location" name="location">      
        <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
      </element>  
     </element>
   </schema>
   ```

* 在“id”名称字段中添加主键或内部键：

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="id" internal="true">
         <keyfield xpath="@id"/> 
       </key>
   
       <key name="email" noDbIndex="true">
         <keyfield xpath="@email"/> 
       </key>
   
       <attribute name="id" type="long" label="Identifier"/>
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

   生成的架构：

   ```
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
       <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
     </element>
   </schema>
   ```

### 自动增量键{#auto-incremental-key}

大多数Adobe Campaign表的主键是由数据库引擎自动生成的32位长整数。 键值的计算取决于生成整个数据库中唯一数字的序列（默认情况下为&#x200B;**XtkNewId** SQL函数）。 在插入记录时自动输入键的内容。

增量密钥的优点是它为表之间的连接提供了不可修改的技术密钥。 此外，此键不会占用太多内存，因为它使用双字节整数。

您可以在源架构中指定要与&#x200B;**pkSequence**&#x200B;属性一起使用的序列的名称。 如果源架构中未提供此属性，则将使用&#x200B;**XtkNewId**&#x200B;默认序列。 该应用程序分别为&#x200B;**nms:broadLog**&#x200B;和&#x200B;**nms:trackingLog**&#x200B;架构（**NmsBroadLogId**&#x200B;和&#x200B;**NmsTrackingLogId**）使用专用序列，因为这些表包含最多记录。

从ACC 18.10开始， **XtkNewId**&#x200B;不再是现成架构中序列的默认值。 现在，您可以构建模式或使用专用序列扩展现有模式。

>[!IMPORTANT]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

>[!NOTE]
>
>在Adobe Campaign模式（例如&#x200B;**NmsTrackingLogId**）中引用的序列必须与返回参数中ID数的SQL函数关联，SQL函数中ID数用逗号分隔。 此函数必须名为&#x200B;**GetNew** XXX **Ids**，其中&#x200B;**XXX**&#x200B;是序列的名称（例如&#x200B;**GetNewNmsTrackingLogIds**）。 查看随&#x200B;**datakit/nms/eng/sql/**&#x200B;目录中的应用程序一起提供的&#x200B;**postgres-nmssql**、**mssql-nmssql**&#x200B;或&#x200B;**oracle-nmssql**&#x200B;文件，以恢复每个数据库引擎的“NmsTrackingLogId”序列创建示例。

要声明唯一键，请在数据架构的主元素中填充&#x200B;**autopk**&#x200B;属性（具有值“true”）。

**示例**:

在源模式中声明增量键：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

生成的架构：

```
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

除了键值及其索引的定义之外，还在扩展架构中添加了名为“id”的数字字段，以包含自动生成的主键值。

>[!IMPORTANT]
>
>在创建表时，主键设置为0的记录会自动插入。 此记录用于避免外连接，这对卷表无效。 默认情况下，所有外键都将初始化为值0，以便在未填充数据项时始终在连接时返回结果。

## 链接：表{#links--relation-between-tables}的关系

链接描述一个表与另一个表之间的关联。

各种类型的关联（称为“基数”）如下所示：

* 基数1-1:源表格的一个存在最多可以具有目标表格的一个对应存在。
* 基数1-N:源表格的一个存在可以具有目标表格的多个对应存在，但目标表格的一个存在最多可以具有源表格的一个对应存在。
* 基数N-N:源表格的一个存在可以具有目标表格的多个对应存在，反之亦然。

在界面中，您可以通过其图标轻松区分不同类型的关系。

要与促销活动表/数据库建立连接关系，请执行以下操作：

* ![](assets/join_with_campaign11.png) :基数1-1。例如，在收件人和当前订单之间。 收件人一次只能与当前订单表的一个实例相关。
* ![](assets/externaljoin11.png) :基数1-1，外部连接。例如，在收件人与其国家/地区之间。 收件人只能与表国家/地区的一个事件相关。 将不会保存国家/地区表的内容。
* ![](assets/join_with_campaign1n.png) :基数1-N。例如，在收件人和订阅表之间。收件人可以与订阅表上的多个事件相关。

对于使用联合数据库访问的连接关系：

* ![](assets/join_fda_11.png) :基数1-1
* ![](assets/join_fda_1m.png) :基数1-N

有关FDA表的详细信息，请参阅[访问外部数据库](../../installation/using/about-fda.md)。

必须在包含通过主元素链接的表的外键的架构中声明链接：

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

链接遵循以下规则：

* 链接的定义在具有以下属性的&#x200B;**link**-type **`<element>`**&#x200B;上输入：

   * **名称**:源表中链接的名称，
   * **target**:目标架构的名称，
   * **标签**:链接标签，
   * **revLink** （可选）：目标模式中反向链接的名称（默认自动推导），
   * **完整性** （可选）：源表格的出现与目标表格的出现的参照完整性。可能的值如下：

      * **定义**:如果源实例不再被目标实例引用，则可以删除该源实例，
      * **正常**:删除源实例将初始化指向目标实例的链接键（默认模式），此类型的完整性将初始化所有外键，
      * **自有**:删除源事件会导致删除目标事件，
      * **下载**:与自 **己的** （如果是删除）相同，或者重复出现（如果是重复），
      * **中性**:不执行任何操作。
   * **revIntegrity** （可选）：目标架构上的完整性（默认情况下为可选，“正常”），
   * **revCardinality** （可选）：使用值“single”填充基数类型1-1（默认情况下为1-N）。
   * **externalJoin** （可选）：强制外连接
   * **revExternalJoin** （可选）：在反向链路上强制外连接


* 链接将源表中的一个或多个字段引用到目标表。 构成连接（`<join>`元素）的字段无需填充，因为默认情况下，会使用目标架构的内部键自动推断这些字段。
* 索引会自动添加到扩展架构中链接的外键。
* 链接由两个半链接组成，其中第一个链接从源架构声明，第二个链接在目标架构的扩展架构中自动创建。
* 如果添加了&#x200B;**externalJoin**&#x200B;属性，且值为“true”（在PostgreSQL中受支持），则连接可以是外部连接。

>[!NOTE]
>
>作为标准，链接是在架构末尾声明的元素。

### 示例1 {#example-1}

1-N与“cus:company”架构表相关：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

生成的架构：

```
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

链接定义由构成连接的字段来补充，即在目标架构中使用其XPath(&quot;@id&quot;)的主键，在架构中使用其XPath(&quot;@company-id&quot;)的外键。

外键会自动添加到与目标表中关联字段使用相同特征的元素中，并遵循以下命名约定：目标架构的名称，后跟关联字段的名称（在我们的示例中为“company-id”）。

目标的扩展模式(“cus:company”):

```
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

添加了指向“cus:recipient”表的反向链接，其中包含以下参数：

* **名称**:自动从源模式的名称推断（可以使用源模式上链接定义中的“revLink”属性强制推断）
* **revLink**:反向链接名称
* **target**:链接架构的键值（“cus:recipient”架构）
* **未绑定**:链接将声明为1-N基数的集合元素（默认情况下）
* **完整性**:默认情况下为“define”（可以使用源架构上的链接定义中的“revIntegrity”属性强制进行）。

### 示例 2 {#example-2}

在本例中，我们将声明指向“nms:address”模式表的链接。 连接是外部连接，明确填充有收件人的电子邮件地址和链接表(“nms:address”)的“@address”字段。

```
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

与“cus:extension”架构表的1-1关系：

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### 示例5 {#example-4}

链接到文件夹（“xtk:folder”架构）：

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

默认值会返回在“DefaultFolder(&#39;nmsFolder&#39;)”函数中输入的第一个符合条件的参数类型文件的标识符。

### 示例5 {#example-5}

在此示例中，我们希望在链接（“company”到“cus:company”架构）上创建一个键，该键具有&#x200B;**xlink**&#x200B;属性，并且包含(“email”)表的字段：

```
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

```
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

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

“companyEmail”名称键的定义已扩展为“company”链接的外键。 此键值会在这两个字段上生成唯一索引。
