---
title: 数据库映射
seo-title: 数据库映射
description: 数据库映射
seo-description: null
page-status-flag: never-activated
uuid: a51df3eb-cae6-4e8d-8386-d62defc1b610
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: bc06c00d-f421-452e-bde0-b4ecc12c72c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

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

架构的根元素不再是， **`<srcschema>`**&#x200B;而是 **`<schema>`**。

这将我们带到另一类型的文档，它是从源架构自动生成的，简称为架构。 此架构将由Adobe Campaign应用程序使用。

SQL名称会根据元素名称和类型自动确定。

SQL命名规则如下：

* 表：架构命名空间和名称的连接

   在我们的示例中，表的名称是通过sqltable属性中架构的主元素 **输入** :

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* 字段：元素的名称，前面是根据类型定义的前缀（&#39;i&#39;表示整数，&#39;d&#39;表示双精度，&#39;s&#39;表示字符串，&#39;ts&#39;表示日期，等等）

   字段名是通过每个类型的 **sqlname** 属性输入的， **`<attribute>`** 并且 **`<element>`**:

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>SQL名称可以从源架构中过载。 为此，请在相关元素上填充“sqltable”或“sqlname”属性。

用于创建从扩展架构生成的表的SQL脚本如下：

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL字段约束如下所示：

* 数字和日期字段中没有空值，
* 数字字段将初始化为0。

## XML字段 {#xml-fields}

默认情况下，任何类型 **`<attribute>`** 和元 **`<element>`** 素都会映射到数据架构表的SQL字段。 但是，您可以在XML中引用此字段，而不是SQL，这意味着数据存储在包含所有XML字段值的表的备忘录字段(“mData”)中。 这些数据的存储是一个XML文档，它观察架构结构。

要填充XML中的字段，必须向相关元 **素添加** “true”值的xml属性。

**示例**:以下是两个XML字段使用示例。

* 多行注释字段：

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* HTML格式的数据说明：

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   “html”类型允许您将HTML内容存储在CDATA标记中，并在Adobe Campaign客户端界面中显示特殊的HTML编辑检查。

使用XML字段，您无需修改数据库的物理结构即可添加字段。 另一个优势是您使用的资源较少（分配给SQL字段的大小、对每个表的字段数的限制等）。

主要缺点是无法对XML字段进行索引或过滤。

## 索引字段 {#indexed-fields}

索引使您能够优化应用程序中使用的SQL查询的性能。

从数据架构的主元素声明索引。

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

索引遵循以下规则：

* 索引可以引用表中的一个或多个字段。
* 如果唯一属性包含值“true”，则索引在所有字段中 **可以是唯一的** （以避免重复）。
* 索引的SQL名称由表的SQL名称和索引的名称决定。

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

## 密钥管理 {#management-of-keys}

表必须具有至少一个用于标识表中记录的键。

从数据架构的主元素中声明一个键。

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

按下列规则：

* 键可以引用表中的一个或多个字段。
* 当键是要填充的架构中的第一个或者它包含具有值“true”的 **internal** 属性时，它称为“primary”（或“priority”）。
* 每个键定义隐式声明唯一索引。 通过添加值为“true”的noDbIndex **属性** ，可以阻止在键上创建索引。

>[!NOTE]
>
>作为标准，键是在定义索引后从架构的主元素声明的元素。

>[!NOTE]
>
>键是在表映射（标准或FDA）过程中创建的，Adobe Campaign会查找唯一索引。

**示例**:

* 向电子邮件地址和城市添加密钥：

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

### 自动增量键 {#auto-incremental-key}

大多数Adobe Campaign表的主键是由数据库引擎自动生成的32位长整数。 键值的计算取决于生成整个数据库中唯一的数字的序列(默认情况下为 **XtkNewId** SQL函数)。 在插入记录时自动输入密钥的内容。

增量密钥的优点是它为表之间的连接提供了不可修改的技术密钥。 此外，此键不占用大量内存，因为它使用双字节整数。

您可以在源架构中指定要与 **pkSequence属性一起使用的序列的名** 称。 如果源架构中未提供此属性，则将 **使用XtkNewId** 默认序列。 应用程序将专用序列用于 **nms:broadLog** 和 **nms:trackingLog** 架构(**NmsBroadLogId和****** NmsTrackingLogIdId架构)，因为这些表包含最多记录。

从ACC 18.10开始， **XtkNewId** 不再是现成的架构中序列的默认值。 您现在可以构建架构或使用专用序列扩展现有架构。

>[!IMPORTANT]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

>[!NOTE]
>
>Adobe Campaign架构中引用的序列(例如&#x200B;**NmsTrackingLogId** )必须与SQL函数关联，该函数返回参数中的ID数（以逗号分隔）。 此函数必须称 ******为GetNewXXXIds**，其中 **XXX** 是序列的名称(例如&#x200B;**GetNewNmsTrackingLogId** )。 查看随 **** datakit/nms/eng/sql/目录中的应用程序提供的 **postgres-nms.sql** 、mssql-nms.nms **或****** oracle-nms.sql文件，以恢复为每个数据库引擎创建“NmsTrackingLogId”序列的示例。

要声明唯一键，请在数据架 **构的主元素** （带有值“true”）上填充autopk属性。

**示例**:

在源架构中声明增量密钥：

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

除了键及其索引的定义之外，还向扩展架构中添加了一个名为“id”的数字字段，以包含自动生成的主键。

>[!IMPORTANT]
>
>在创建表时，将主键设置为0的记录自动插入。 此记录用于避免外部连接，这对卷表无效。 默认情况下，所有外键都使用值0进行初始化，这样，在数据项未填充时，结果始终可以在连接时返回。

## 链接：表之间的关系 {#links--relation-between-tables}

链接描述了一个表与另一个表之间的关联。

各种类型的关联（称为“基数”）如下：

* 基数1-1:源表的一个出现最多可以具有目标表的一个对应出现。
* 基数1-N:源表的一个出现可以具有目标表的多个对应出现，但目标表的一个出现最多可以具有源表的一个对应出现。
* 基数N-N:源表的一个实例可以具有目标表的多个对应实例，反之亦然。

在界面中，您可以借助关系的图标轻松区分不同类型的关系。

对于与活动表／数据库的连接关系：

* ![](assets/join_with_campaign11.png) :基数1-1。 例如，在收件人与当前订单之间。 收件人一次只能与当前订单表的一个实例相关联。
* ![](assets/externaljoin11.png) :基数1-1，外部连接。 例如，在接收方与其国家／地区之间。 收件人只能与表国家／地区的一个实例相关联。 将不保存国家／地区表的内容。
* ![](assets/join_with_campaign1n.png) :基数1-N。例如，在收件人和订阅表之间。 收件人可以与订阅表上的多个事件相关。

对于使用Federated Database Access的连接关系：

* ![](assets/join_fda_11.png) :基数1-1
* ![](assets/join_fda_1m.png) :基数1-N

有关FDA表的详细信息，请参阅 [访问外部数据库](../../platform/using/about-fda.md)。

必须在包含通过主元素链接的表的外键的架构中声明链接：

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

链接遵守以下规则：

* 链接的定义是在具有以下属 **性的链**&#x200B;接 **`<element>`** 类型上输入的：

   * **name**:源表中链接的名称，
   * **目标**:目标架构的名称，
   * **label**:链接标签，
   * **revLink** （可选）:目标架构中反向链接的名称（默认情况下自动推断）,
   * **完整性** （可选）:源表实例与目标表实例的参照完整性。 可能的值如下：

      * **define**:如果源实例不再被目标实例引用，则可以删除它，
      * **normal**:删除源实例将初始化指向目标实例的链接密钥（默认模式），这种完整性将初始化所有外键，
      * **own**:删除源实例会导致删除目标实例，
      * **下载**:与自己 **的** （删除时）相同或重复的实例（复制时）,
      * **中性**:什么也不做。
   * **revIntegrity** （可选）:目标架构上的完整性（默认情况下为可选，“正常”）,
   * **revCardinality** （可选）:如果值为“single”，则会使用类型1-1填充基数（默认情况下为1-N）。
   * **externalJoin** （可选）:强制外连接
   * **revExternalJoin** （可选）:将外连接强制在反向连接上


* 链接将引用源表中的一个或多个字段到目标表。 组成连接（元素）的字 `<join>` 段无需填充，因为默认情况下会使用目标架构的内部键自动推断它们。
* 索引会自动添加到扩展架构中链接的外键。
* 链接由两个半链接组成，其中第一个链接从源架构声明，第二个链接在目标架构的扩展架构中自动创建。
* 如果添加了externalJoin属性，且值为“ **** true”（在PostgreSQL中受支持），则连接可以是外部连接。

>[!NOTE]
>
>作为标准，链接是在架构末尾声明的元素。

### Example 1 {#example-1}

1-与“cus:company”架构表相关：

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

链接定义由组成加入的字段补充，即主键在目标架构中具有其XPath(&quot;@id&quot;)，外键在架构中具有其XPath(&quot;@company-id&quot;)。

外键会自动添加到与目标表中的关联字段具有相同特征的元素中，并遵循以下命名约定：目标架构的名称，后跟关联字段的名称（我们示例中的“company-id”）。

目标的扩展架构(“cus:company”):

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

* **name**:根据源架构的名称自动推断（可以使用源架构上的链接定义中的“revLink”属性强制推断）
* **revLink**:反向链接的名称
* **目标**:链接架构的键（“cus:recipient”架构）
* **未绑定**:链接声明为1-N基数的集合元素（默认情况下）
* **完整性**:默认情况下为“define”（可以使用源架构上的链接定义中的“revIntegrity”属性强制执行）。

### Example 2 {#example-2}

在此示例中，我们将声明指向“nms:address”架构表的链接。 连接是外部连接，并显式填充有收件人的电子邮件地址和链接表的“@address”字段(“nms:address”)。

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

### Example 3 {#example-3}

与“cus:extension”架构表的1-1关系：

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### Example 4 {#example-4}

链接到文件夹（“xtk:folder”架构）:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

默认值返回在“DefaultFolder(&#39;nmsFolder&#39;)”函数中输入的第一个合格参数类型文件的标识符。

### Example 5 {#example-5}

在此示例中，我们希望在链接（“company”到“cus:company”架构）上创建一个键，其中包含 **xlink** 属性和(“email”)表的字段：

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

“companyEmail”名称键的定义扩展为“company”链接的外键。 此键在这两个字段上都生成唯一索引。
