---
product: campaign
title: 了解Adobe Campaign中的架构结构
description: 模式结构
feature: Custom Resources
role: Data Engineer, Developer
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 1%

---

# 了解架构结构 {#schema-structure}

架构的基本结构如下所述。

## 数据架构  {#data-schema}

对于`<srcschema>`，结构如下：

```sql
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

数据架构的XML文档必须包含具有&#x200B;**名称**&#x200B;和&#x200B;**命名空间**&#x200B;属性的&#x200B;**`<srcschema>`**&#x200B;根元素，才能填充架构名称及其命名空间。

```sql
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

让我们使用以下XML内容来说明数据模式的结构：

```sql
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

及其相应的数据架构：

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## 说明 {#description}

架构的入口点是其主元素。 此插件易于识别，因为它与架构具有相同的名称，并且应该是根元素的子项。 内容的描述以此元素开头。

在本例中，主元素由以下行表示：

```
<element name="recipient">
```

主元素后面的&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;元素用于定义XML结构中数据项的位置和名称。

在我们的示例模式中，这些规则包括：

```sql
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

以下规则适用：

* 每个&#x200B;**`<element>`**&#x200B;和&#x200B;**`<attribute>`**&#x200B;必须通过&#x200B;**name**&#x200B;属性用名称标识。

  >[!IMPORTANT]
  >
  >元素的名称应简洁，最好是英文，并且仅包括XML命名规则中允许的字符。

* 只有&#x200B;**`<element>`**&#x200B;个元素可以在XML结构中包含&#x200B;**`<attribute>`**&#x200B;个元素和&#x200B;**`<element>`**&#x200B;个元素。
* **`<attribute>`**&#x200B;元素在&#x200B;**`<element>`**&#x200B;中必须具有唯一的名称。
* 建议在多行数据字符串中使用&#x200B;**`<elements>`**。

## 数据类型 {#data-types}

数据类型是通过&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;元素中的&#x200B;**type**&#x200B;属性输入的。

[`<attribute>`元素](../../configuration/using/schema/attribute.md)和[`<element>`元素](../../configuration/using/schema/element.md)的描述中提供了详细列表。

如果未填充此属性，则&#x200B;**string**&#x200B;是默认的数据类型，除非该元素包含子元素。 如果是，则仅将其用于分层构造元素（示例中为&#x200B;**`<location>`**&#x200B;个元素）。

架构支持以下数据类型：

* **字符串**：字符串。 示例：名字、城镇等。

  可以通过&#x200B;**length**&#x200B;属性指定大小（可选，默认值“255”）。

* **布尔值**：布尔字段。 可能值的示例：true/false、0/1、yes/no等。
* **字节**，**短**，**长**：整数（1字节、2字节、4字节）。 示例：年龄、帐号、点数等。
* **double**：双精度浮点数。 示例：价格、费率等。
* **日期**，**日期时间**：日期和日期+时间。 示例：出生日期、购买日期等。
* **datetimenotz**：没有时区数据的日期+时间。
* **时间跨度**：持续时间。 例如：资历。
* **备注**：长文本字段（多行）。 示例：描述、评论等。
* **uuid**：“uniqueidentifier”字段支持GUID(仅在Microsoft SQL Server中受支持)。

  >[!NOTE]
  >
  >若要在Microsoft SQL Server以外的RDBMS中包含&#x200B;**uuid**&#x200B;字段，必须添加`the newuuid()`函数并使用其默认值完成该函数。

以下是输入的类型的模式示例：

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### 映射Adobe Campaign/DBMS数据的类型 {#mapping-the-types-of-adobe-campaign-dbms-data}

下表列出了Adobe Campaign为各种数据库管理系统生成的数据类型的映射。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 字符串<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 （NVARCHAR2，如果是unicode）<br /> </td> 
  </tr> 
  <tr> 
   <td> 布尔值<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 数字(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 字节<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 数字(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 短<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 数字(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 双精度<br /> </td> 
   <td> 双精度<br /> </td> 
   <td> 浮点数<br /> </td> 
  </tr> 
  <tr> 
   <td> 长<br /> </td> 
   <td> 整数<br /> </td> 
   <td> 数字(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> 数字(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间<br /> </td> 
   <td> 时间<br /> </td> 
   <td> 浮点数<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期时间<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> 日期<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> 日期<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间跨度<br /> </td> 
   <td> 双精度<br /> </td> 
   <td> 浮点数<br /> </td> 
  </tr> 
  <tr> 
   <td> 备忘录<br /> </td> 
   <td> 文本<br /> </td> 
   <td> CLOB （Unicode时为NCLOB）<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 属性 {#properties}

可以使用各种属性扩充数据架构的&#x200B;**`<elements>`**&#x200B;和&#x200B;**`<attributes>`**&#x200B;元素。 您可以填充标签以描述当前元素。

### 标签和描述 {#labels-and-descriptions}

* **标签**&#x200B;属性允许您输入简短描述。

  >[!NOTE]
  >
  >标签与实例的当前语言关联。

  **示例**：

  ```sql
  <attribute name="email" type="string" length="80" label="Email"/>
  ```

  标签显示在Adobe Campaign客户端控制台输入表单中：

  ![](assets/d_ncs_integration_schema_label.png)

* **desc**&#x200B;属性允许您输入较长的描述。

  该描述将显示在Adobe Campaign客户端控制台主窗口状态栏的输入表单中。

  >[!NOTE]
  >
  >该描述与实例的当前语言相关联。

  **示例**：

  ```sql
  <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
  ```

### 默认值 {#default-values}

使用&#x200B;**default**&#x200B;属性定义在创建内容时返回默认值的表达式。

该值必须是符合XPath语言的表达式。 有关详细信息，请参阅[使用XPath引用](../../configuration/using/schema-structure.md#referencing-with-xpath)。

**示例**：

* 当前日期： **default=&quot;GetDate()&quot;**
* 计数器： **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

  在此示例中，默认值是使用字符串的串连来构造的，并使用免费计数器名称调用&#x200B;**CounterValue**&#x200B;函数。 每次插入时，返回的数字将递增1。

  >[!NOTE]
  >
  >在Adobe Campaign客户端控制台中，浏览到资源管理器的&#x200B;**[!UICONTROL Administration > Counters]**&#x200B;文件夹以管理计数器。

要将默认值链接到字段，您可以使用`<default>`或`<sqldefault>`   字段。

`<default>` ：允许您在创建实体时使用默认值预填充字段。 该值将不会是默认的SQL值。

`<sqldefault>` ：允许您在创建字段时添加值。 此值显示为SQL结果。 在架构更新期间，此值仅影响新记录。

### 明细列表 {#enumerations}

#### 打开明细列表 {#free-enumeration}

**userEnum**&#x200B;属性允许您定义一个打开的枚举，以存储和显示通过此字段输入的值。

语法如下：

`userEnum="name of enumeration"`

这些值显示在输入表单的下拉列表中：

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>在Adobe Campaign客户端控制台中，浏览到Explorer的&#x200B;**[!UICONTROL Administration > Enumerations]**&#x200B;文件夹以管理枚举。

#### 设置明细列表 {#set-enumeration}

**枚举**&#x200B;属性允许您定义预先知道可能值的列表时使用的固定枚举。

**enum**&#x200B;属性引用了在主元素之外的架构中填充的枚举类的定义。

枚举允许用户从下拉列表中选择一个值，而不是在常规输入字段中输入值：

![](assets/d_ncs_integration_schema_enum.png)

数据架构中的枚举声明示例：

```sql
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

枚举通过&#x200B;**`<enumeration>`**&#x200B;元素在主元素之外声明。

枚举属性如下：

* **baseType**：与值关联的数据类型
* **标签**：枚举的说明
* **name**：枚举的名称
* **默认值**：枚举的默认值

枚举值在&#x200B;**`<value>`**&#x200B;元素中具有以下属性：

* **name**：内部存储的值的名称
* **标签**：图形界面中显示的标签

#### dbenum枚举 {#dbenum-enumeration}

***dbenum**&#x200B;属性允许您定义属性与&#x200B;**enum**&#x200B;属性的属性相似的枚举。

但是，**name**&#x200B;属性不会在内部存储该值，它存储了一个代码，该代码允许您在不修改相关表架构的情况下扩展这些表。

例如，此枚举用于指定营销活动的性质。

![](assets/d_ncs_configuration_schema_dbenum.png)

### 示例 {#example}

以下是填充了属性的架构示例：

```sql
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## 集合 {#collections}

集合是具有相同名称和相同层次级别的元素的列表。

值为“true”的&#x200B;**unbound**&#x200B;属性允许您填充集合元素。

**示例**：架构中&#x200B;**`<group>`**&#x200B;集合元素的定义。

```sql
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

使用XML内容的投影：

```sql
<group label="Group1"/>
<group label="Group2"/>
```

## 使用XPath引用 {#referencing-with-xpath}

XPath语言在Adobe Campaign中用于引用属于数据架构的元素或属性。

XPath是一种语法，允许您在XML文档的树中查找节点。

元素由名称指定，属性由名称指定，名称前面加有字符“@”。

**示例**：

* **@email**：选择电子邮件，
* **location/@city**：选择&#x200B;**`<location>`**&#x200B;元素下的“city”属性
* **../@email**：从当前元素的父元素中选择电子邮件地址
* **组`[1]/@label`**：选择作为第一个&#x200B;**`<group>`**&#x200B;集合元素的子项的“label”属性
* **组`[@label='test1']`**：选择作为&#x200B;**`<group>`**&#x200B;元素的子项且包含值“test1”的“label”属性

>[!NOTE]
>
>当路径穿过子元素时，会添加附加约束。 在这种情况下，必须在括号之间放置以下表达式：
>
>* **位置/@city**&#x200B;无效；请使用&#x200B;**`[location/@city]`**
>* **`[@email]`**&#x200B;和&#x200B;**@email**&#x200B;是等效的
>

也可以定义复杂的表达式，例如以下算术运算：

* **@gender+1**：将1添加到&#x200B;**性别**&#x200B;属性的内容中，
* **@email + &#39;(&#39;+@created+&#39;)&#39;**：构造字符串的方法是采用添加到创建日期的电子邮件地址的值在括号之间（对于字符串类型，将常量放在引号中）。

在表达式中添加了高级函数，以丰富此语言的潜力。

您可以通过Adobe Campaign客户端控制台中的任意表达式编辑器访问可用函数的列表：

![](assets/d_ncs_integration_schema_function.png)

**示例**：

* **GetDate()**：返回当前日期
* **年(@created)**：返回“已创建”属性中包含的日期的年份
* **GetEmailDomain(@email)**：返回电子邮件地址的域

## 通过计算字符串构建字符串 {#building-a-string-via-the-compute-string}

**计算字符串**&#x200B;是用于构造表示与架构关联的表中记录的字符串的XPath表达式。 **计算字符串**&#x200B;主要用于图形界面中显示选定记录的标签。

**计算字符串**&#x200B;通过数据架构主元素下的&#x200B;**`<compute-string>`**&#x200B;元素定义。 **expr**&#x200B;属性包含用于计算显示的XPath表达式。

**示例**：收件人表的计算字符串。

```sql
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

收件人的计算字符串的结果： **Doe John (john.doe@aol.com)**

>[!NOTE]
>
>如果架构不包含计算字符串，则默认情况下将使用架构主键的值填充计算字符串。


## 了解详情

浏览以下链接以了解更多信息：

* [模式入门](about-schema-reference.md)
* [数据库映射](database-mapping.md)
* [链接管理](database-links.md)
* [密钥管理](database-keys.md)
* [Campaign 数据模型](about-data-model.md)