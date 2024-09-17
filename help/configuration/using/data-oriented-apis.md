---
product: campaign
title: 面向数据的 API
description: 面向数据的 API
feature: API
role: Data Engineer, Developer
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: 9d84c01b217579b5a291d5761a5dd2f8f8960df8
workflow-type: tm+mt
source-wordcount: '1811'
ht-degree: 0%

---

# 面向数据的 API{#data-oriented-apis}

面向数据的API允许您处理整个数据模型。

## 数据模型概述 {#overview-of-the-datamodel}

Adobe Campaign不为每个实体提供专用读取API（无getRecipient或getDelivery函数等）。 使用QUERY &amp; WRITER数据读取和修改方法访问模型数据。

Adobe Campaign允许您管理收藏集：通过查询，您可以恢复在整个群中收集的一组信息。 与在SQL模式下访问不同，Adobe Campaign API返回XML树而不是数据列。 因此，Adobe Campaign会创建包含所有收集数据的复合文档。

此操作模式不提供在XML文档的属性和元素与数据库中表的列之间的一对一映射。

XML文档存储在数据库的MEMO类型字段中。

## 模型的描述 {#description-of-the-model}

您必须熟悉Adobe Campaign数据模型，才能在脚本中处理数据库的字段。

有关数据模型的演示，请参阅[Adobe Campaign数据模型说明](../../configuration/using/data-model-description.md)。

## 查询和编写器 {#query-and-writer}

以下介绍模式详细介绍了数据库与客户(网页或Adobe Campaign客户端控制台)之间读取(ExecuteQuery)和写入(Writer)的低级交换。

![](assets/s_ncs_integration_webservices_schema_writer.png)

### 执行查询 {#executequery}

对于列和条件，您可以使用查询。

这使您能够隔离基础SQL。 查询语言不依赖于底层引擎：某些函数将重新映射，这些函数可能会生成多个SELECT SQL顺序。

有关详细信息，请参阅架构“xtk：queryDef”](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-)的“ExecuteQuery”方法的[示例。

**ExecuteQuery**&#x200B;方法出现在[ExecuteQuery (xtk：queryDef)](#executequery--xtk-querydef-)中。

### 写入 {#write}

“写入”命令允许您编写简单或复杂的文档，这些文档在基础的一个或多个表中具有条目。

事务型API允许您通过&#x200B;**updateOrInsert**&#x200B;命令管理协调：一个命令允许您创建或更新数据。 您还可以配置修改合并(**merge**)：此操作模式允许您授权部分更新。

XML结构提供了数据的逻辑视图，允许您绕过SQL表的物理结构。

Write方法在[Write/WriteCollection (xtk：session)](#write---writecollection--xtk-session-)中显示。

## ExecuteQuery (xtk：queryDef) {#executequery--xtk-querydef-}

此方法允许您从与架构关联的数据执行查询。 它需要验证字符串（必须登录）和描述作为参数提交的查询的XML文档。 return参数是一个XML文档，它以查询所引用的架构格式包含查询的结果。

“xtk：queryDef”架构中“ExecuteQuery”方法的定义：

```xml
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>这是“常量”方法。 输入参数以“xtk：queryDef”架构的格式包含在XML文档中。

### 输入查询的XML文档的格式 {#format-of-the-xml-document-of-the-input-query}

查询的XML文档的结构在“xtk：queryDef”模式中描述。 本文档介绍了SQL查询的子句：“select”、“where”、“order by”、“group by”、“having”。

```xml
<queryDef schema="schema_key" operation="operation_type">
  <select>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </select>
  <where> 
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ... 
  </where>
  <orderBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </orderBy>
  <groupBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </groupBy>
  <having>
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ...
  </having>
</queryDef>
```

可以在`<condition> `元素中定义子查询(`<subquery>`)。 的语法   `<subquery> `   元素基于    `<querydef>`。

`<subquery>  : </subquery>`示例

```xml
<condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
  <subQuery schema="xtk:operatorGroup">
     <select>
       <node expr="[@operator-id]" />
     </select>
     <where>
       <condition expr="[@group-id]=$long(../@owner-id)"/>
     </where>
   </subQuery>
</condition>  
  
```

查询必须引用&#x200B;**架构**&#x200B;属性的开始架构。

所需操作的类型输入到&#x200B;**operation**&#x200B;属性中，并包含以下值之一：

* **get**：从表中检索记录，如果数据不存在，则返回错误。
* **getIfExists**：从表中检索记录，如果数据不存在，则返回空文档。
* **select**：创建光标以返回多个记录，如果没有数据，则返回空文档，
* **count**：返回数据计数。

**XPath**&#x200B;语法用于根据输入架构查找数据。 有关XPath的详细信息，请参阅[数据架构](../../configuration/using/data-schemas.md)。

#### “获取”操作的示例 {#example-with-the--get--operation}

检索在电子邮件上使用过滤器的收件人（“nms：recipient”架构）的姓氏和名字。

```xml
<queryDef schema="nms:recipient" operation="get">
  <!-- fields to retrieve -->
  <select>
    <node expr="@firstName"/>
    <node expr="@lastName"/>
  </select> 

  <!-- condition on email -->
  <where>  
    <condition expr="@email= 'john.doe@aol.com'"/>
  </where>
</queryDef>
```

#### “选择”操作的示例 {#example-with-the--select--operation}

返回按文件夹和电子邮件域过滤的收件人列表，并按出生日期的降序排序。

```xml
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <!-- builds a string with the concatenation of the last name and first name separated by a dash -->      
    <node expr="@lastName+'-'+@firstName"/>
    <!-- get year of birth date -->
    <node expr="Year(@birthDate)"/>
  </select> 

  <where>  
     <condition expr="[@folder-id] = 1234 and @domain like 'Adobe%'"/>
  </where>

  <!-- order by birth date -->
  <orderBy>
    <node expr="@birthDate" sortDesc="true"/> <!-- by default sortDesc="false" -->
  </orderBy>
</queryDef>
```

表达式可以是简单字段或复杂表达式，例如算术运算或字符串的连接。

要限制要返回的记录数，请将&#x200B;**lineCount**&#x200B;属性添加到`<querydef>`元素。

要将查询返回的记录数限制为100，请执行以下操作：

```xml
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

要检索下100条记录，请再次运行同一查询，添加&#x200B;**startLine**&#x200B;属性。

```xml
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### “count”操作的示例 {#example-with-the--count--operation}

要计算查询中的记录数，请执行以下操作：

```xml
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the email -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>我们再次使用上一个示例中的条件。 未使用`<select>`和子句。`</select>`

#### 数据分组 {#data-grouping}

要检索多次引用的电子邮件地址，请执行以下操作：

```xml
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- email grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

通过将&#x200B;**groupBy**&#x200B;属性直接添加到要分组的字段，可以简化查询：

```xml
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>不再需要填充`<groupby>`元素。

#### 在条件中括起来 {#bracketing-in-conditions}

下面是两个在相同条件下使用方括号的示例。

* 单个表达式中的简单版本：

  ```xml
  <where>
    <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
  </where>
  ```

* 包含`<condition>`个元素的结构化版本：

  ```xml
  <where>
    <condition bool-operator="AND">
      <condition expr="@age > 15" bool-operator="OR"/>
      <condition expr="@age <= 45"/>
    </condition>
    <condition>
      <condition expr="@city = 'Newton'" bool-operator="OR"/>
      <condition expr="@city = 'Culver City'"/>
    </condition>
  </where>
  ```

当多个条件应用于同一字段时，可以使用“IN”操作替换“OR”运算符：

```xml
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

当条件中使用两个以上的数据时，此语法可简化查询。

#### 链接示例 {#examples-on-links}

* 链接1-1或N1：当表具有外键（链接从表开始）时，可以直接过滤或检索链接表的字段。

  文件夹标签上的过滤器示例：

  ```xml
  <where>
    <condition expr="[folder/@label] like 'Segment%'"/>
  </where>
  ```

  要从“nms：recipient”模式中检索文件夹的字段，请执行以下操作：

  ```xml
  <select>
    <!-- label of recipient folder -->
    <node expr="[folder/@label]"/>
    <!-- displays the string count of the folder -->
    <node expr="partition"/>
  </select>
  ```

* 集合链接(1N)：必须通过&#x200B;**EXISTS**&#x200B;或&#x200B;**NOT EXISTS**&#x200B;运算符对集合表的字段进行筛选。

  筛选已订阅“新闻稿”信息服务的收件人：

  ```xml
  <where>
    <condition expr="subscription" setOperator="EXISTS">
      <condition expr="@name = 'Newsletter'"/>
    </condition>
  </where>
  ```

  不建议从`<select>`子句中直接检索集合链接的字段，因为查询返回基数产品。 仅当链接表仅包含一个记录（示例`<node expr="">`）时才使用。

  “订阅”收藏集链接示例：

  ```xml
  <select>
    <node expr="subscription/@label"/>
  </select>
  ```

  可以在`<select>`子句中检索包含集合链接元素的子列表。 引用字段的XPath与收集元素相关。

  筛选( `<orderby>` )和限制( `<where>` )元素可以添加到集合元素中。

  在此示例中，对于每个收件人，查询将返回收件人订阅的信息服务的电子邮件和列表：

  ```xml
  <queryDef schema="nms:recipient" operation="select">
    <select>
      <node expr="@email"/>
  
      <!-- collection table (unbound type) -->
      <node expr="subscription">  
        <node expr="[service/@label]"/>    
        <!-- sub-condition on the collection table -->
        <where>  
          <condition expr="@expirationDate >= GetDate()"/>
        </where>
        <orderBy>
          <node expr="@expirationDate"/> 
        </orderBy>
      </node>
    </select> 
  </queryDef>
  ```

#### 绑定&#39;where&#39;和&#39;select&#39;子句的参数 {#binding-the-parameters-of-the--where--and--select--clause}

参数的绑定允许引擎设置查询中使用的参数的值。 这非常有用，因为引擎负责转义值，并且对于要检索的参数还有缓存的额外好处。

当构建查询时，“绑定”值将替换为字符(？ 在ODBC中，`#[index]#`在SQL查询正文中。

```xml
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

要避免绑定参数，必须使用值“true”填充“noSqlBind”属性。

>[!IMPORTANT]
>
>如果查询包含“order-by”或“group-by”指令，则数据库引擎将无法“绑定”值。 您必须将@noSqlBind=&quot;true&quot;属性放置在查询的&quot;select&quot;和/或&quot;where&quot;指令上。


### 输出文档格式 {#output-document-format}

返回参数是采用与查询关联的架构格式的XML文档。

从“nms：recipient”模式返回“get”操作的示例：

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

在“选择”操作中，返回的文档是元素的枚举：

```xml
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

为“count”类型操作返回的文档示例：

```xml
<recipient count="3"/>
```

#### 别名 {#alias}

别名允许您修改输出文档中数据的位置。 **别名**&#x200B;属性必须在相应的字段中指定XPath。

```xml
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

返回：

```xml
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

而非：

```xml
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### SOAP消息示例 {#example-of-soap-messages}

* 查询：

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef operation="get" schema="nms:recipient" xtkschema="xtk:queryDef">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@id = 3599"/>
            </where>
          </queryDef>
        </entity>
      </ExecuteQuery>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* 响应：

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

## 写入/写入收集(xtk：session) {#write---writecollection--xtk-session-}

这些服务用于插入、更新或删除实体（“写入”方法）或实体集合（“WriteCollection”方法）。

要更新的实体与数据模式相关联。 输入参数是身份验证字符串（必须登录）以及包含要更新的数据的XML文档。

本文档还附有配置写入过程的说明。

调用不会返回任何数据，错误除外。

“xtk：session”架构中“Write”和“WriteCollection”方法的定义：

```xml
<method name="Write" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference document"/>
  </parameters>
</method>
<method name="WriteCollection" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference collection document"/>
  </parameters>
</method>
```

>[!NOTE]
>
>这是一种“静态”方法。 输入参数以要更新的架构的格式包含在XML文档中。

### 概述 {#overview}

数据协调根据在关联模式中输入的键的定义运行。 写入过程根据输入文档中输入的数据查找第一个符合条件的键。 根据实体在数据库中的存在性插入或更新该实体。

要更新的实体的架构键是根据&#x200B;**xtkschema**&#x200B;属性完成的。

因此，可以使用包含组成协调键的XPath列表（用逗号分隔）的&#x200B;**_key**&#x200B;属性强制执行该协调键。

可以通过使用以下值填充&#x200B;**_operation**&#x200B;特性来强制执行该操作类型：

* **insert**：强制插入记录（未使用协调密钥），
* **insertOrUpdate**：根据协调密钥（默认模式）更新或插入记录，
* **更新**：更新记录；如果数据不存在，则不执行任何操作，
* **删除**：删除记录，
* **none**：仅用于链接协调，无需更新或插入。

### &#39;Write&#39;方法的示例 {#example-with-the--write--method}

使用电子邮件地址、出生日期和城镇更新或插入收件人（隐式“insertOrUpdate”操作）：

```xml
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

删除收件人：

```xml
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>对于删除操作，输入文档必须仅包含组成协调键值的字段。

### &#39;WriteCollection&#39;方法的示例 {#example-with-the--writecollection--method}

多个收件人的更新或插入：

```xml
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### 链接示例 {#example-on-links}

#### 示例1 {#example-1}

根据文件夹的内部名称(@name)将其与收件人关联。

```xml
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

可以在链接的元素上输入“_key”和“_operation”属性。 此元素上的行为与输入架构的主元素上的行为相同。

主实体(“nms：recipient”)的键的定义由链接表（元素`<folder>`架构“xtk：folder”）中的字段和电子邮件组成。

>[!NOTE]
>
>对文件夹元素输入的“none”操作定义了对文件夹的协调，无需更新或插入。

#### 示例2 {#example-2}

从收件人更新公司（在“cus：company”架构中链接的表）：

```xml
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### 示例3 {#example-3}

使用组关系表(“nms：rcpGrpRel”)将收件人添加到组：

```xml
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>未在`<rcpgroup>`元素中输入键的定义，因为在“nms：group”架构中定义了基于组名称的隐式键。

### XML收藏集元素 {#xml-collection-elements}

默认情况下，必须填写所有收集要素才能更新XML收集要素。 来自数据库的数据将替换为来自输入文档的数据。 如果文档只包含要更新的元素，则必须在所有要更新的收集元素上填充“_operation”属性，以便强制与数据库的XML数据合并。

### SOAP消息示例 {#example-of-soap-messages-1}

* 查询：

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <Write xmlns='urn:xtk:persist' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <domDoc xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient xtkschema="nms:recipient" email="rene.dupont@adobe.com" firstName="René" lastName="Dupont" _key="@email">
        </domDoc>
      </Write>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* 响应：

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
      </WriteResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

  返回错误：

  ```xml
  <?xml version='1.0'?>
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <SOAP-ENV:Fault>
        <faultcode>SOAP-ENV:Server</faultcode>
        <faultstring xsi:type="xsd:string">Error while executing the method 'Write' of service 'xtk:persist'.</faultstring>
        <detail xsi:type="xsd:string">PostgreSQL error: ERROR:  duplicate key violates unique constraint &quot;nmsrecipient_id&quot;Impossible to save document of type 'Recipients (nms:recipient)'</detail>
      </SOAP-ENV:Fault>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```
