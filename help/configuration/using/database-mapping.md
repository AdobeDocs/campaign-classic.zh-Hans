---
solution: Campaign Classic
product: campaign
title: 数据库映射
description: 数据库映射
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1974'
ht-degree: 0%

---


# 数据库映射{#database-mapping}

我们示例模式的SQL映射提供了以下XML文档:

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

## 说明{#description}

模式的根元素不再为&#x200B;**`<srcschema>`**，而是&#x200B;**`<schema>`**。

这将我们带到另一种类型的文档，它是从源模式自动生成的，简称为模式。 此模式将由Adobe Campaign应用程序使用。

SQL名称会根据元素名称和类型自动确定。

SQL命名规则如下：

* 表：模式命名空间和名称的串联

   在我们的示例中，表的名称是通过&#x200B;**sqltable**&#x200B;属性中模式的主元素输入的：

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* 字段：元素的名称，前面是根据类型定义的前缀(“i”表示整数，“d”表示多次，“s”表示字符串，“ts”表示日期等)

   通过&#x200B;**sqlname**&#x200B;属性输入每个类型的&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;的字段名：

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>SQL名称可以从源模式重载。 为此，请在相关元素上填充“sqltable”或“sqlname”属性。

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

默认情况下，任何类型的&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;元素都会映射到数据模式表的SQL字段。 但是，您可以在XML中引用此字段，而不是SQL，这意味着数据存储在包含所有XML字段值的表的备忘录字段(“mData”)中。 这些存储是观察模式结构的XML文档。

要在XML中填充字段，必须将&#x200B;**xml**&#x200B;属性添加到相关元素中，并且值为“true”。

**示例**:以下是两个XML字段使用示例。

* 多行注释字段：

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* HTML格式的数据描述：

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   “html”类型允许您将HTML内容存储在CDATA标签中，并在Adobe Campaign客户端界面中显示特殊的HTML编辑检查。

使用XML字段，您无需修改数据库的物理结构即可添加字段。 另一个优势是您使用的资源较少（分配给SQL字段的大小、对每个表的字段数的限制等）。

主要缺点是无法对XML字段进行索引或筛选。

## 索引字段{#indexed-fields}

索引使您能够优化应用程序中使用的SQL查询的性能。

从数据模式的主元素中声明索引。

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

索引遵守以下规则：

* 索引可以引用表中的一个或多个字段。
* 如果&#x200B;**unique**&#x200B;属性包含值&quot;true&quot;，则索引在所有字段中都可以是唯一的(以避免重复)。
* 索引的SQL名称由表的SQL名称和索引的名称确定。

>[!NOTE]
>
>作为标准，索引是从模式的主要元素声明的第一个元素。

>[!NOTE]
>
>索引在表映射(标准或联合数据访问)期间自动创建。

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

* 将唯一索引添加到“id”名称字段：

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

## 管理键{#management-of-keys}

表必须具有至少一个用于标识表中记录的键。

从数据模式的主元素中声明密钥。

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

按键遵守以下规则：

* 键可以引用表中的一个或多个字段。
* 当键是要填充的模式中的第一个或者它包含&#x200B;**internal**&#x200B;属性且值为“true”时，称为“primary”（或“priority”）。
* 为每个键定义隐式声明一个唯一索引。 通过添加值为“true”的&#x200B;**noDbIndex**&#x200B;属性，可以阻止在键上创建索引。

>[!NOTE]
>
>作为标准，键是在定义索引后从模式的主元素声明的元素。

>[!NOTE]
>
>键是在表映射(标准或联合数据访问)期间创建的，Adobe Campaign会查找唯一索引。

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

   生成的模式:

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

   生成的模式:

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

大多数Adobe Campaign表的主键是由数据库引擎自动生成的32位长整数。 键值的计算取决于生成整个数据库中唯一的数字的序列（默认情况下，**XtkNewId** SQL函数）。 在插入记录时自动输入密钥的内容。

增量密钥的优点是它为表之间的连接提供了不可修改的技术密钥。 此外，此键不占用大量内存，因为它使用多次字节整数。

可以在源模式中指定要与&#x200B;**pkSequence**&#x200B;属性一起使用的序列的名称。 如果源模式中未提供此属性，则将使用&#x200B;**XtkNewId**&#x200B;默认序列。 应用程序将专用序列用于&#x200B;**nms:broadLog**&#x200B;和&#x200B;**nms:trackingLog**&#x200B;模式（分别为&#x200B;**NmsBroadLogId**&#x200B;和&#x200B;**NmsTrackingLogId**），因为这些表包含最多记录。

从ACC 18.10开始，**XtkNewId**&#x200B;不再是现成模式中序列的默认值。 您现在可以构建模式或使用专用序列扩展现有模式。

>[!IMPORTANT]
>
>在创建新模式或在模式扩展期间，您需要为整个模式保留相同的主键序列值(@pkSequence)。

>[!NOTE]
>
>在Adobe Campaign模式（例如&#x200B;**NmsTrackingLogId**）中引用的序列必须与SQL函数关联，该函数返回参数中的ID数（以逗号分隔）。 此函数必须称为&#x200B;**GetNew** XXX **Ids**，其中&#x200B;**XXX**&#x200B;是序列的名称（例如&#x200B;**GetNewNmsTrackingLogIds**）。 视图随&#x200B;**datakit/nms/eng/sql/**&#x200B;目录中的应用程序提供的&#x200B;**postgres-nmssql**、**mssql-nmssql**&#x200B;或&#x200B;**oracle-nms.sql**&#x200B;文件，以恢复“NmsTrackingLogId”的示例为每个数据库引擎创建序列。

要声明唯一键，请在数据模式的主元素上填充&#x200B;**autopk**&#x200B;属性（值为“true”）。

**示例**:

在源模式中声明增量键：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

生成的模式:

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

除了键及其索引的定义之外，还向扩展模式添加了一个名为“id”的数字字段，以包含自动生成的主键。

>[!IMPORTANT]
>
>在创建表时，将自动插入主键设置为0的记录。 此记录用于避免外部连接，这对卷表无效。 默认情况下，所有外键都使用值0初始化，以便在未填充数据项时，始终可以在连接时返回结果。

## 链接：表的关系{#links--relation-between-tables}

链接描述一个表与另一个表之间的关联。

各种类型的关联（称为“基数”）如下：

* 基数1-1:源表的一个出现最多可以具有目标表的一个对应出现。
* 基数1-N:源表的一个出现可以具有多个对应的目标表出现，但目标表的一个出现最多可以具有源表的一个对应出现。
* 基数N-N:源表的一个实例可以具有多个对应的目标表实例，反之亦然。

在界面中，您可以借助关系图标轻松区分不同类型的关系。

对于与活动表/数据库的连接关系：

* ![](assets/join_with_campaign11.png) :基数1-1。例如，在收件人和当前订单之间。 收件人一次只能与当前订单表的一个实例相关。
* ![](assets/externaljoin11.png) :基数1-1，外部连接。例如，在收件人与其国家之间。 收件人只能与表国家/地区的一个事件相关。 将不保存国家/地区表的内容。
* ![](assets/join_with_campaign1n.png) :基数1-N。例如，在收件人和订阅表之间。收件人可以与订阅表上的多个事件相关。

对于使用Federated Database Access建立联系：

* ![](assets/join_fda_11.png) :基数1-1
* ![](assets/join_fda_1m.png) :基数1-N

有关联合数据访问表的详细信息，请参阅[访问外部数据库](../../installation/using/about-fda.md)。

必须在包含通过主元素链接的表的外键的模式中声明链接：

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

链接遵守以下规则：

* 链接的定义是在&#x200B;**link**-type **`<element>`**&#x200B;上输入的，具有以下属性：

   * **name**:源表中链接的名称，
   * **目标**:目标模式的名称，
   * **label**:链接标签，
   * **revLink** （可选）：目标模式中反向链接的名称（默认情况下自动推断），
   * **完整性** （可选）：源表的出现与目标表的出现的参照完整性。可能的值如下：

      * **定义**:如果源实例不再被目标实例引用，则可以删除它，
      * **正常**:删除源实例将初始化指向目标实例的链接的键（默认模式），此类型的完整性将初始化所有外键，
      * **own**:删除源事件会导致删除目标事件，
      * **下载**:与 **own** （如果删除）或重复事件（如果重复）相同，
      * **中性**:什么都不做。
   * **revIntegrity** （可选）：目标模式的完整性（默认情况下为可选，“正常”），
   * **revCardinality** （可选）：值“single”将使用类型1-1（默认为1-N）填充基数。
   * **externalJoin** （可选）：强制外连接
   * **revExternalJoin** （可选）：将外连接强制在反向链路上


* 链接将引用源表中的一个或多个字段到目标表。 组成连接（`<join>`元素）的字段无需填充，因为默认情况下，它们是使用目标模式的内部键自动推断的。
* 索引会自动添加到扩展模式中链接的外键。
* 一个链接由两个半链接组成，其中第一个链接从源模式声明，第二个链接在目标模式的扩展模式中自动创建。
* 如果添加了&#x200B;**externalJoin**&#x200B;属性，且值为“true”（在PostgreSQL中受支持），则连接可以是外部连接。

>[!NOTE]
>
>作为标准，链接是在模式末尾声明的元素。

### 示例1 {#example-1}

1-N与“cus:公司”模式表：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

生成的模式:

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

链接定义由组成连接的字段补充，即在目标模式中XPath(&quot;@id&quot;)为主键，在模式中XPath(&quot;@company-id&quot;)为外键。

外键将自动添加到元素中，该元素使用与目标表中关联字段相同的特性，并具有以下命名约定：目标模式的名称，后跟关联字段的名称(我们示例中的“公司-id”)。

目标的扩展模式(“cus:公司”):

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

添加了一个指向“cus:收件人”表的反向链接，其中包含以下参数：

* **name**:自动从源模式的名称推断(可以使用源模式上的链接定义中的“revLink”属性强制推断)
* **revLink**:反向链接的名称
* **目标**:链接模式的键(“cus:收件人”模式)
* **未绑定**:链接将声明为1-N基数的集合元素（默认情况下）
* **完整性**:默认情况下为“define”(可以强制使用源模式上的链接定义中的“revIntegrity”属性)。

### 示例 2 {#example-2}

在此示例中，我们将声明指向“nms:address”模式表的链接。 连接是外部连接，并显式填充收件人的电子邮件地址和链接表(“nms:address”)的“@address”字段。

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

与“cus:extension”模式表的1-1关系：

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### 示例4 {#example-4}

链接到文件夹(“xtk:folder”模式):

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

默认值返回在“DefaultFolder(&#39;nmsFolder&#39;)”函数中输入的第一个合格参数类型文件的标识符。

### 示例5 {#example-5}

在此示例中，我们希望在具有&#x200B;**xlink**&#x200B;属性的链接(“公司”到“cus:公司”模式)和(“email”)表的字段上创建一个键：

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

生成的模式:

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

“companyEmail”名称键的定义已扩展为“公司”链接的外键。 此键在这两个字段上生成唯一索引。
