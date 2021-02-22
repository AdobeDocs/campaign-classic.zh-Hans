---
solution: Campaign Classic
product: campaign
title: 模式结构
description: 模式结构
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: a469d275fdd768fbd098a0027b5096872dbf6d89
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 1%

---


# 模式结构{#schema-structure}

`<srcschema>`的基本结构如下：

```
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

数据模式的XML文档必须包含&#x200B;**`<srcschema>`**&#x200B;根元素，其中&#x200B;**name**&#x200B;和&#x200B;**命名空间**&#x200B;属性用于填充模式名称及其命名空间。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

让我们使用以下XML内容来说明数据模式的结构：

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

使用其相应的数据模式:

```
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

## 说明{#description}

模式的入口点是其主要元素。 由于它的名称与模式相同，并且它应该是根元素的子元素，因此易于识别。 内容的描述以此元素开头。

在我们的示例中，主元素由以下行表示：

```
<element name="recipient">
```

主元素后面的元素&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;使您能够定义XML结构中数据项的位置和名称。

在我们的示例模式中，以下是：

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

必须遵守下列规则：

* 每个&#x200B;**`<element>`**&#x200B;和&#x200B;**`<attribute>`**&#x200B;必须通过&#x200B;**name**&#x200B;属性通过名称进行标识。

   >[!IMPORTANT]
   >
   >元素的名称应简明，最好是英文，并且只包括符合XML命名规则的授权字符。

* 在XML结构中，只有&#x200B;**`<element>`**&#x200B;元素可以包含&#x200B;**`<attribute>`**&#x200B;元素和&#x200B;**`<element>`**&#x200B;元素。
* **`<attribute>`**&#x200B;元素在&#x200B;**`<element>`**&#x200B;中必须具有唯一的名称。
* 建议在多行数据字符串中使用&#x200B;**`<elements>`**。

## 数据类型 {#data-types}

数据类型是通过&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;元素中的&#x200B;**type**&#x200B;属性输入的。

[`<attribute>`元素](../../configuration/using/schema/attribute.md)和[`<element>`元素](../../configuration/using/schema/element.md)的说明中提供详细列表。

如果未填充此属性，则&#x200B;**string**&#x200B;是默认数据类型，除非元素包含子元素。 如果它这样做，则它仅用于按层次结构化元素（我们示例中的&#x200B;**`<location>`**&#x200B;元素）。

模式支持以下数据类型：

* **字符串**:字符串。示例：名字，城镇等。

   可以通过&#x200B;**length**&#x200B;属性（可选，默认值“255”）指定大小。

* **布尔**:布尔字段。可能值的示例：true/false、0/1、yes/no等。
* **字节**、 **短**、 **长**:整数（1字节、2字节、4字节）。示例：年龄、帐号、积分等。
* **多次**:多次精度浮点数。示例：价格、价格等。
* **date**,  **datetime**:日期和日期+时间。示例：出生日期、购买日期等。
* **datetimenotz**:日期+时间，无时区数据。
* **timespan**:持续时间。示例：资历。
* **memo**:长文本字段（多行）。示例：描述、注释等。
* **uuid**:“uniqueidentifier”字段以支持GUID（仅在Microsoft SQL Server中受支持）。

   >[!NOTE]
   >
   >要在Microsoft SQL Server以外的引擎中包含&#x200B;**uuid**&#x200B;字段，必须添加“newuid()”函数并用其默认值完成。

下面是我们输入的类型的示例模式:

```
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

### 映射Adobe Campaign/DBMS数据的类型{#mapping-the-types-of-adobe-campaign-dbms-data}

下表列表了Adobe Campaign为不同数据库管理系统生成的数据类型的映射。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>Teradata</strong><br /> </td> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 字符串<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2（如果unicode为NVARCHAR2）<br /> </td> 
   <td> VARCHAR（如果为Unicode，则为VARCHAR字符集UNICODE）<br /> </td> 
   <td> VARCHAR<br /> </td> 
   <td> VARCHAR(NVARCHAR if unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Boolean<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 字节<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(3)<br /> </td> 
   <td> NUMERIC(3)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 短<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> NUMBER(5)<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> SMALLINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 多次<br /> </td> 
   <td> 多次精度<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> 多次<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> 长<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> NUMBER(10)<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INTEGER<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> NUMBER(20)<br /> </td> 
   <td> NUMERIC(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> TIME<br /> </td> 
   <td> TIME<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetime<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008:DATETIME<br /> MS SQL &gt;= 2012:DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> TIMESTAMP<br /> </td> 
   <td> MS SQL &lt; 2008:DATETIME<br /> MS SQL &gt;= 2012:DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> Timespan<br /> </td> 
   <td> 多次精度<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> 多次<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> Memo<br /> </td> 
   <td> TEXT<br /> </td> 
   <td> CLOB（如果为Unicode，则为NCLOB）<br /> </td> 
   <td> CLOB（如果为Unicode，则为CLOB字符集UNICODE）<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TEXT(NTEXT if Unicode)<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> 图像<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 属性 {#properties}

数据模式的&#x200B;**`<elements>`**&#x200B;和&#x200B;**`<attributes>`**&#x200B;元素可以用各种属性进行丰富。 您可以填充标签以描述当前元素。

### 标签和说明{#labels-and-descriptions}

* 通过&#x200B;**label**&#x200B;属性可以输入简短说明。

   >[!NOTE]
   >
   >标签与实例的当前语言关联。

   **示例**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   可从Adobe Campaign客户端控制台输入表单中查看该标签：

   ![](assets/d_ncs_integration_schema_label.png)

* 使用&#x200B;**desc**&#x200B;属性可以输入长描述。

   描述可从Adobe Campaign客户端控制台主窗口状态栏的输入表单中查看。

   >[!NOTE]
   >
   >说明与实例的当前语言相关联。

   **示例**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### 默认值{#default-values}

**default**&#x200B;属性允许您定义在内容创建时返回默认值的表达式。

该值必须是符合XPath语言的表达式。 有关详细信息，请参阅[ Referencing with XPath](../../configuration/using/schema-structure.md#referencing-with-xpath)。

**示例**:

* 当前日期：**default=&quot;GetDate()&quot;**
* 计数器：**default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   在此示例中，默认值是使用字符串的串联和使用免费计数器名称调用&#x200B;**CounterValue**&#x200B;函数来构建的。 每次插入时，返回的数字递增1。

   >[!NOTE]
   >
   >在Adobe Campaign客户端控制台中，**[!UICONTROL Administration>Counters]**&#x200B;节点用于管理计数器。

要将默认值链接到字段，可以使用`<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` :允许您在创建图元时使用默认值预填充字段。该值不是默认的SQL值。

`<sqldefault>` :允许您在创建字段时具有添加值。此值显示为SQL结果。 在模式更新期间，只有新记录将受此值影响。

### 明细列表{#enumerations}

#### 免费明细列表{#free-enumeration}

使用&#x200B;**userEnum**&#x200B;属性，您可以定义一个免费明细列表，以记忆和显示通过此字段输入的值。 语法如下：

**userEnum=&quot;明细列表名称&quot;**

可以自由选择给明细列表的名称并与其他字段共享。

这些值显示在输入表单的下拉列表中：

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>在Adobe Campaign客户端控制台中，**[!UICONTROL Administration > Enumerations]**&#x200B;节点用于管理明细列表。

#### 设置明细列表{#set-enumeration}

通过&#x200B;**enum**&#x200B;属性，可以定义在预先知道可能值的列表时使用的固定明细列表。

**enum**&#x200B;属性引用在主元素外部的模式中填充的明细列表类的定义。

明细列表允许用户从下拉列表中选择一个值，而不是在常规输入字段中输入该值：

![](assets/d_ncs_integration_schema_enum.png)

数据模式中明细列表声明的示例：

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

通过&#x200B;**`<enumeration>`**&#x200B;元素在主元素外部声明明细列表。

明细列表属性如下：

* **baseType**:与值、
* **label**:明细列表,
* **name**:明细列表的名称，
* **默认**:默认明细列表值。

明细列表值在&#x200B;**`<value>`**&#x200B;元素中声明，具有以下属性：

* **name**:内部存储的值的名称，
* **label**:标签。

#### dbenum明细列表{#dbenum-enumeration}

* 通过&#x200B;**dbenum**&#x200B;属性，可以定义一个明细列表，其属性与&#x200B;**enum**&#x200B;属性的属性相似。

   但是，**name**&#x200B;属性不在内部存储值，它存储一个代码，使您可以扩展相关表而不修改其模式。

   值通过&#x200B;**[!UICONTROL Administration>Enumerations]**&#x200B;节点定义。

   例如，此明细列表用于指定活动的性质。

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### 示例{#example}

下面是我们的示例模式，其中填写了属性：

```
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

集合是具有相同名称和相同层次的元素的列表。

值为“true”的&#x200B;**unboind**&#x200B;属性允许您填充集合元素。

**示例**:集合元 **`<group>`** 素在模式中的定义。

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

对XML内容进行投影：

```
<group label="Group1"/>
<group label="Group2"/>
```

## 使用XPath引用 {#referencing-with-xpath}

Adobe Campaign中使用XPath语言来引用属于数据模式的元素或属性。

XPath是一种语法，它允许您在XML文档的树中查找节点。

元素由其名称指定，属性由字符&quot;@&quot;前的名称指定。

**示例**:

* **@email**:选择电子邮件，
* **location/@city**:选择元素下的&quot;city&quot;属 **`<location>`** 性
* **../@email**:从当前元素的父元素中选择电子邮件地址
* **组`[1]/@label`**:选择作为第一个集合元素的子项的“label” **`<group>`** 属性
* **组`[@label='test1']`**:选择作为元素子项的“label”属 **`<group>`** 性并包含值“test1”

>[!NOTE]
>
>当路径与子元素相交时，会添加附加约束。 在这种情况下，以下表达式必须放在括号之间：
>
>* **location/@** city无效；请  **`[location/@city]`**
>* **`[@email]`** 和 **@** emailare等效
>



还可以定义复杂的表达式，如以下算术运算：

* **@gender+1**:将genderattribute的内容添加 **** 1,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**:使用添加到创建日期中括号之间的电子邮件地址值（对于字符串类型，将常量加引号）来构造字符串。

为了丰富这种语言的潜力，表达式中增加了高级功能。

您可以通过Adobe Campaign客户端控制台中的任何表达式编辑器访问可用功能的列表:

![](assets/d_ncs_integration_schema_function.png)

**示例**:

* **GetDate()**:返回当前日期
* **年(@created)**:返回“created”属性中包含的日期的年份。
* **GetEmailDomain(@email)**:返回电子邮件地址的域。

## 通过计算字符串构建字符串{#building-a-string-via-the-compute-string}

**计算字符串**&#x200B;是XPath表达式，用于在与该模式相关联的表中构造表示记录的字符串。 **计** 算字符串主要用于图形界面中显示所选记录的标签。

**计算字符串**&#x200B;是通过数据模式主要元素下的&#x200B;**`<compute-string>`**&#x200B;元素定义的。 **expr**&#x200B;属性包含用于计算显示的XPath表达式。

**示例**:计算收件人表的字符串。

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

收件人的计算字符串结果：**Doe John(john.doe@aol.com)**

>[!NOTE]
>
>如果模式不包含计算字符串，则默认情况下将使用模式的主键值填充计算字符串。

