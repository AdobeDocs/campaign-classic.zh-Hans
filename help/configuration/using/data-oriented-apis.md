---
solution: Campaign Classic
product: campaign
title: 面向数据的 API
description: 面向数据的 API
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1881'
ht-degree: 0%

---


# 面向数据的 API{#data-oriented-apis}

面向数据的API允许您处理整个数据模型。

## 数据模型概述 {#overview-of-the-datamodel}

Adobe Campaign不优惠每个实体的专用读API（没有getRecipient或getDelivery函数等）。 使用查询和WRITER数据读取和修改方法访问模型数据。

Adobe Campaign允许您管理集合：查询使您能够恢复在整个基础中收集的一组信息。 与在SQL模式下访问不同，Adobe CampaignAPI返回XML树而不是数据列。 因此，Adobe Campaign会创建包含所有收集数据的复合文档。

此操作模式不优惠XML文档的属性和元素与数据库中表列之间的一对一映射。

XML文档存储在数据库的MEMO类型字段中。

## 模型的描述 {#description-of-the-model}

您必须熟悉Adobe Campaign数据模型才能在脚本中找到数据库的字段。

有关数据模型的演示，请参阅 [Adobe Campaign数据模型说明](../../configuration/using/data-model-description.md)。

要生成其结构，请参阅本文： [如何生成数据模型或数据字典](https://helpx.adobe.com/campaign/kb/generate-data-model.html)。

## 查询与作家 {#query-and-writer}

以下介绍模式详细介绍了在数据库和客户(网页或Adobe Campaign客户端控制台)之间进行读取(ExecuteQuery)和写入(Writer)的低级交换。

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

对于列和条件，您可以使用查询。

这样，您就可以隔离基础SQL。 查询语言不取决于基础引擎：某些函数将重新映射，这可能会生成多个SELECT SQL订单。

有关详细信息，请参 [阅模式“xtk:queryDef”的“ExecuteQuery”方法的示例](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-)。

ExecuteQuery **方法** (xtk: [queryDef)中显示](#executequery--xtk-querydef-)。

### 写入 {#write}

使用“写入”命令可以编写简单或复杂的文档，并在一个或多个基表中输入条目。

事务API允许您通过updateOrInsert命令管 **理对帐** :一个命令可用于创建或更新数据。 您还可以配置修改合并(**合并**):此操作模式允许您对部分更新授权。

XML结构优惠数据的逻辑视图，并允许您绕过SQL表的物理结构。

Write/WriteCollection(xtk: [session)中显示Write方法](#write---writecollection--xtk-session-)。

## ExecuteQuery(xtk:queryDef) {#executequery--xtk-querydef-}

此方法允许您从与查询关联的数据执行模式。 它采用身份验证字符串（必须登录）和XML文档，描述要作为参数提交的查询。 返回参数是一个XML文档，其中包含查询的结果，其格式为查询所引用的模式。

在“xtk:queryDef”模式中定义“ExecuteQuery”方法：

```
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>这是一种“const”方法。 输入参数以“xtk:queryDef”文档的格式包含在XML模式中。

### 输入文档的XML查询的格式 {#format-of-the-xml-document-of-the-input-query}

查询的XML文档的结构在“xtk:queryDef”模式中进行了描述。 此文档描述SQL查询的子句：“select”、“where”、“order by”、“group by”、“having”。

```
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

子查询( `<subquery>` )可在元素中定 `<condition> ` 义。 元素的语 `<subquery> ` 法基于的语法 `<querydef>`。

示例 `<subquery>  : </subquery>`

```
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

查询必须从开始属性引用模式 **模式** 。

所需的操作类型在操作属性 **中输入** ，并包含以下值之一：

* **get**:从表中检索记录，如果数据不存在，则返回错误，
* **getIfExists**:从表中检索记录，如果文档不存在，则返回空的记录，
* **选择**:创建光标以返回多个记录，并在没有数据时返回空文档,
* **计数**:返回数据计数。

XPath **语法** ，用于根据输入模式定位数据。 有关XPath的详细信息，请参阅 [数据模式](../../configuration/using/data-schemas.md)。

#### “get”操作示例 {#example-with-the--get--operation}

检索具有电子邮件上的过滤器的收件人(“nms:收件人”模式)的姓氏和名字。

```
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

#### “select”操作的示例 {#example-with-the--select--operation}

返回在文件夹和电子邮件域上筛选的收件人的列表，在出生日期按降序排序。

```
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

表达式可以是简单字段或复杂表达式，如算术运算或字符串的串联。

要限制要返回的记录数，请向 **元素** 添加 `<querydef>` lineCount属性。

将查询返回的记录数限制为100:

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

要检索接下来的100条记录，请再次运行相同的查询，并添加 **startLine** 属性。

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### “count”操作的示例 {#example-with-the--count--operation}

要计算查询上的记录数：

```
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the e-mail -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>我们再次使用上一个示例中的条件。 不 `<select>` 使用和子句。 `</select>`

#### 数据分组 {#data-grouping}

要检索引用了多次的电子邮件地址，请执行以下操作：

```
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- e-mail grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

通过将groupBy属性直接添 **加到要分组的字** 段，可以简化查询:

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>不再需要填充元 `<groupby>` 素。

#### 条件中的括号 {#bracketing-in-conditions}

以下是两个在相同条件下进行括号的示例。

* 单个表达式中的简单版本：

   ```
   <where>
     <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
   </where>
   ```

* 包含元素的结构化 `<condition>` 版本：

   ```
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

当多个条件适用于同一字段时，可以用“IN”操作替换“OR”运算符：

```
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

此语法在条件中使用两个以上数据时简化了查询。

#### 链接示例 {#examples-on-links}

* 链接1-1或N1:当表具有外键(表中的链接开始)时，可以直接过滤或检索链接表的字段。

   文件夹标签上的过滤器示例：

   ```
   <where>
     <condition expr="[folder/@label] like 'Segment%'"/>
   </where>
   ```

   要从“nms:收件人”模式检索文件夹的字段，请执行以下操作：

   ```
   <select>
     <!-- label of recipient folder -->
     <node expr="[folder/@label]"/>
     <!-- displays the string count of the folder -->
     <node expr="partition"/>
   </select>
   ```

* 集合链接(1N):必须通过EXISTS或NOT EXISTS运算符对集合表的字段 **执行****筛选** 。

   要过滤订阅“新闻快讯”收件人的信息服务，请执行以下操作：

   ```
   <where>
     <condition expr="subscription" setOperator="EXISTS">
       <condition expr="@name = 'Newsletter'"/>
     </condition>
   </where>
   ```

   不建议从子句直接检索集合链接 `<select>` 的字段，因为查询返回主产品。 仅当链接的表只包含一个记录时(示例 `<node expr="">`),

   “订阅”集合链接示例：

   ```
   <select>
     <node expr="subscription/@label"/>
   </select>
   ```

   可以检索子列表，该子包含子句中集合链接的元 `<select>` 素。 引用字段的XPaths是集合元素中的上下文相关的。

   筛选( `<orderby>` )和限制( `<where>` )元素可添加到集合元素。

   在此示例中，对于每个收件人,查询返回收件人订阅的信息服务的电子邮件和列表:

   ```
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

#### 绑定“where”和“select”子句的参数 {#binding-the-parameters-of-the--where--and--select--clause}

参数绑定允许引擎设置查询中使用的参数值。 这非常有用，因为引擎负责值的转义，而且对于要检索的参数还有缓存的额外好处。

构建查询时，“绑定”值由字符(? 在ODBC `#[index]#` 中，在postgres...)的SQL查询正文中。

```
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

要避免绑定参数，必须用值“true”填充“noSqlBind”属性。

>[!IMPORTANT]
>
>如果查询包含“订单”或“分组”说明，则数据库引擎将无法“绑定”值。 必须将@noSqlBind=&quot;true&quot;属性放置在查询的“select”和／或“where”说明中。

#### 查询构建提示： {#query-building-tip-}

要帮助处理查询的语法，可以使用Adobe Campaign客户端控制台（菜单）中的通用查询编辑器编 **[!UICONTROL Tools/ Generic query editor...]** 写查询。 操作步骤：

1. 选择要检索的数据：

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. 定义筛选条件：

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. 执行查询并按CTRL+F4视图查询源代码。

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### 输出文档格式 {#output-document-format}

返回参数是与文档关联的模式格式的XML查询。

从“nms:收件人”模式返回“get”操作的示例：

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

在“选择”操作中，返回的文档是元素的明细列表:

```
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

为“计数”类型操作返回的文档示例：

```
<recipient count="3"/>
```

#### 别名 {#alias}

别名允许您修改输出文档中数据的位置。 别名 **属性** 必须在相应字段上指定XPath。

```
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

退货：

```
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

而不是：

```
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### SOAP消息示例 {#example-of-soap-messages}

* 查询:

   ```
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

   ```
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

## Write / WriteCollection(xtk:session) {#write---writecollection--xtk-session-}

这些服务用于插入、更新或删除实体（“Write”方法）或实体集合（“WriteCollection”方法）。

要更新的实体与数据模式相关联。 输入参数是身份验证字符串（必须登录）和包含要更新的数据的XML文档。

此文档由配置写操作过程的说明补充。

除错误外，调用不返回任何数据。

“xtk:session”模式中“Write”和“WriteCollection”方法的定义：

```
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
>这是一种“静态”方法。 输入参数以要更新的文档的格式包括在XML模式中。

### 概述 {#overview}

数据对帐基于在关联模式中输入的键的定义进行。 写入过程根据输入文档中输入的数据来查找第一合格密钥。 根据实体在数据库中的存在情况插入或更新实体。

要更新的实体的模式的键基于xtkschema属性 **完成** 。

因此，可以使用包含构成键的 **XPath的合并关键项** （用逗号分隔）的列表的_key属性强制。

可以使用以下值填充 **_operation** 属性来强制操作类型：

* **插入**:强制插入记录(不使用合并关键项),
* **insertOrUpdate**:根据合并关键项（默认模式）更新或插入记录，
* **更新**:更新记录；如果数据不存在，则不执行任何操作，
* **删除**:删除记录，
* **无**:仅用于链接对帐，无需更新或插入。

### 使用“Write”方法的示例 {#example-with-the--write--method}

使用电子邮件地址、出生日期和城镇更新或插入收件人（隐式“insertOrUpdate”操作）:

```
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

删除收件人:

```
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>对于删除操作，输入文档必须只包含构成合并关键项的字段。

### 使用“WriteCollection”方法的示例 {#example-with-the--writecollection--method}

更新或插入多个收件人:

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### 链接示例 {#example-on-links}

#### Example 1 {#example-1}

根据文件夹的内部名称(@name)将文件夹与收件人关联。

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

可以在链接的元素上输入“_key”和“_operation”属性。 此元素的行为与输入模式的主元素的行为相同。

主实体(“nms:收件人”)的键的定义由链接表(元素 `<folder>` 模式“xtk:folder”)和电子邮件中的字段组成。

>[!NOTE]
>
>在文件夹元素上输入的操作“无”定义了在文件夹上进行的对帐，而无需更新或插入。

#### 示例 2 {#example-2}

从公司更新公司(“cus:收件人”模式中的链接表):

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### Example 3 {#example-3}

使用组关系表(“nms:rcpGrpRel”)向组添加收件人:

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>键的定义不在元素中输入， `<rcpgroup>` 因为在“nms:group”模式中定义了基于组名称的隐式键。

### XML集合元素 {#xml-collection-elements}

默认情况下，必须填充所有集合元素，才能更新XML集合元素。 来自文档库的数据将替换为来自输入数据的数据。 如果文档只包含要更新的元素，则必须在所有要更新的集合元素上填充“操作”属性，以强制与数据库的XML数据合并。

### SOAP消息示例 {#example-of-soap-messages-1}

* 查询:

   ```
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

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </WriteResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

   返回时出错：

   ```
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

