---
title: 架构结构
seo-title: 架构结构
description: 架构结构
seo-description: null
page-status-flag: never-activated
uuid: 9be70907-6154-4890-91e8-fd0fac30ab05
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: b5c8faf7-d0ae-4d95-b7fe-6ef9674a33d2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f9b3508fee3b441752648258b1bc9d5d2b919791

---


# 架构结构{#schema-structure}

其基本结 `<srcschema>` 构如下：

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

数据架构的XML文档必须包含根元素，其 **`<srcschema>`** 中包含名称 **和** namespace **属性** ，以填充架构名称及其命名空间。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

让我们使用以下XML内容来说明数据架构的结构：

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

使用其相应的数据架构：

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

## 说明 {#description}

架构的入口点是其主要元素。 它易于识别，因为它与架构同名，并且它应该是根元素的子元素。 内容的描述以此元素开头。

在我们的示例中，主元素由以下行表示：

```
<element name="recipient">
```

通过主 **`<attribute>`** 元素 **`<element>`** 和后面的元素，您可以定义XML结构中数据项的位置和名称。

在我们的示例架构中，这些是：

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

必须遵守下列规定：

* 每个 **`<element>`** 属性 **`<attribute>`** 都必须通过name属性由name **标识** 。

   >[!CAUTION]
   >
   >元素的名称应简明，最好是英文，并且仅包含符合XML命名规则的授权字符。

* 只有 **`<element>`** 元素才能在XML结 **`<attribute>`** 构中 **`<element>`** 包含元素和元素。
* 元 **`<attribute>`** 素在中必须具有唯一名称 **`<element>`**。
* 建议在多行数据字符串中使用**`<elements>`**。

## 数据类型 {#data-types}

数据类型通过和元素 **中的** type属性 **`<attribute>`** 输入 **`<element>`** 。

元素和元素的说明中提供了详细 [`<attribute>` 列表](../../configuration/using/elements-and-attributes.md#attribute--element)[`<element>` 。](../../configuration/using/elements-and-attributes.md#element--element)

如果未填充此属性，则 **字符串** 是默认数据类型，除非元素包含子元素。 如果确实如此，则它仅用于按层次结构化元素(本例中&#x200B;**`<location>`** 的元素)。

架构中支持以下数据类型：

* **字符串**:字符串。 示例：名字，城镇，等等。

   可以通过length属性指定 **大小** （可选，默认值“255”）。

* **boolean**:布尔字段。 可能的值示例：true/false、0/1、yes/no等。
* **字节**、 **短**、 **长**:整数（1字节、2字节、4字节）。 示例：年龄、帐号、积分等。
* **double**:双精度浮点数。 示例：价格、费率等。
* **date**, **datetime**:日期和日期+时间。 示例：出生日期、购买日期等。
* **datetimenotz**:日期+时间，无时区数据。
* **timespan**:持续时间。 示例：资历。
* **memo**:长文本字段（多行）。 示例：说明、评论等。
* **uuid**:用于支持GUID的“uniqueidentifier”字段（仅在Microsoft SQL server中支持）。

   >[!NOTE]
   >
   >要在Microsoft SQL server以 **外的引擎中包含uuid** 字段，必须添加“newuuid()”函数并用其默认值完成该函数。

下面是我们的示例架构，其中输入了类型：

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

### 映射Adobe Campaign/DBMS数据的类型 {#mapping-the-types-of-adobe-campaign-dbms-data}

下表列出了Adobe Campaign为不同数据库管理系统生成的数据类型的映射。

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
   <td> VARCHAR2（NVARCHAR2，如果unicode）<br /> </td> 
   <td> VARCHAR(VARCHAR字符集UNICODE（如果为Unicode）)<br /> </td> 
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
   <td> Double<br /> </td> 
   <td> 双精度<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DOUBLE<br /> </td> 
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
   <td> 时间戳<br /> </td> 
   <td> DATE<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间<br /> </td> 
   <td> 时间<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> 时间<br /> </td> 
   <td> 时间<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期时间<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> MS SQL &lt; 2008:DATETIME<br /> MS SQL &gt;= 2012:DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> TIMESTAMPZ<br /> </td> 
   <td> DATE<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> MS SQL &lt; 2008:DATETIME<br /> MS SQL &gt;= 2012:DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间平移<br /> </td> 
   <td> 双精度<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> FLOAT<br /> </td> 
   <td> DOUBLE<br /> </td> 
   <td> FLOAT<br /> </td> 
  </tr> 
  <tr> 
   <td> 备忘录<br /> </td> 
   <td> 文本<br /> </td> 
   <td> CLOB（如果为Unicode，则为NCLOB）<br /> </td> 
   <td> CLOB（如果是Unicode，则为CLOB字符集UNICODE）<br /> </td> 
   <td> CLOB(6M)<br /> </td> 
   <td> TEXT（如果是Unicode，则为NTEXT）<br /> </td> 
  </tr> 
  <tr> 
   <td> 斑点<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB(4M)<br /> </td> 
   <td> IMAGE<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 属性 {#properties}

数据 **`<elements>`** 架构 **`<attributes>`** 的元素和元素可以用各种属性进行丰富。 您可以填充标签以描述当前元素。

### 标签和说明 {#labels-and-descriptions}

* 标签 **属性** ，允许您输入简短的说明。

   >[!NOTE]
   >
   >标签与实例的当前语言相关联。

   **示例**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   可从Adobe Campaign客户端控制台输入表单中查看该标签：

   ![](assets/d_ncs_integration_schema_label.png)

* desc **属性** ，允许您输入详细说明。

   该说明可从Adobe Campaign客户端控制台主窗口状态栏的输入表单中查看。

   >[!NOTE]
   >
   >说明与实例的当前语言相关联。

   **示例**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### 默认值 {#default-values}

使用 **default** 属性可定义在内容创建时返回默认值的表达式。

该值必须是符合XPath语言的表达式。 有关详细信息，请参阅 [Referencing with XPath](../../configuration/using/schema-structure.md#referencing-with-xpath)。

**示例**:

* 当前日期：默 **认=&quot;GetDate()&quot;**
* 计数器：默 **认=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   在本例中，默认值是使用字符串的串联和使用免费计数器名称调用 **CounterValue** 函数来构造的。 每次插入时，返回的数字会增加1。

   >[!NOTE]
   >
   >在Adobe Campaign客户端控制台中，该 **[!UICONTROL Administration>Counters]** 节点用于管理计数器。

要将默认值链接到字段，您可以使用 `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` :允许您在创建实体时使用默认值预填充字段。 该值不是默认的SQL值。

`<sqldefault>` :允许您在创建字段时添加值。 此值显示为SQL结果。 在架构更新期间，只有新记录将受此值影响。

### 枚举 {#enumerations}

#### 自由枚举 {#free-enumeration}

使用 **userEnum** 属性可以定义免费枚举，以记住和显示通过此字段输入的值。 语法如下：

**userEnum=&quot;枚举的名称&quot;**

可以自由选择给定枚举的名称，并与其他字段共享。

这些值显示在输入表单的下拉列表中：

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>在Adobe Campaign客户端控制台中，该 **[!UICONTROL Administration > Enumerations]** 节点用于管理枚举。

#### 集枚举 {#set-enumeration}

enum **** 属性允许您定义在事先已知可能值列表时使用的固定枚举。

enum属 **性引用** 在主元素外的架构中填充的枚举类的定义。

枚举允许用户从下拉列表中选择一个值，而不是在常规输入字段中输入该值：

![](assets/d_ncs_integration_schema_enum.png)

数据架构中的枚举声明示例：

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

通过元素在主元素外部声明一个枚 **`<enumeration>`** 举。

枚举属性如下所示：

* **baseType**:与值关联的数据类型，
* **label**:枚举的描述，
* **name**:枚举的名称，
* **default**:枚举的默认值。

枚举值在元素中声明， **`<value>`** 并具有以下属性：

* **name**:内部存储的值的名称，
* **label**:标签。

#### dbenum枚举 {#dbenum-enumeration}

* dbenum **属性允许您定义一个枚举，其属性与enum属性的属性相** 似 **** 。

   但是，name **属性不在内部存储值** ，它存储了一个代码，通过该代码可以扩展相关表而不修改其架构。

   这些值是通过节点定 **[!UICONTROL Administration>Enumerations]** 义的。

   例如，此枚举用于指定营销活动的性质。

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### Example {#example}

下面是我们的示例架构，其中填充了属性：

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

集合是具有相同名称和相同层次结构的元素列表。

使用 **值** “true”的未绑定属性可填充集合元素。

**示例**:架构中集 **`<group>`** 合元素的定义。

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

Adobe Campaign中使用XPath语言引用属于数据架构的元素或属性。

XPath是一种语法，它允许您在XML文档的树中查找节点。

元素由其名称指定，属性由前面带有字符“@”的名称指定。

**示例**:

* **@email**:选择电子邮件，
* **location/@city**:选择元素下的“city”属 **`<location>`** 性
* **../@email**:从当前元素的父元素中选择电子邮件地址
* **用户组`[1]/@label`**:选择作为第一个集合元素的子元素的“label”**`<group>`**属性
* **用户组`[@label='test1']`**:选择作为元素子项的“label”属&#x200B;**`<group>`**性并包含值“test1”

>[!NOTE]
>
>当路径与子元素交叉时，将添加附加约束。 在这种情况下，以下表达式必须放在括号之间：
>
>* **location/@city** is not valid;请使用 **`[location/@city]`**
>* **`[@email]`** 和 **@email** 是等同的
>



还可以定义复杂的表达式，如以下算术运算：

* **@gender+1**:在性别属性的内容中 **加** 1,
* **@email + &#39;(&#39;+@created+&#39;)&#39;**:通过使用添加到创建日期的括号之间的电子邮件地址的值构造字符串（对于字符串类型，将常数加引号）。

为了丰富这种语言的潜力，在表达式中增加了高级函数。

您可以通过Adobe Campaign客户端控制台中的任何表达式编辑器访问可用函数列表：

![](assets/d_ncs_integration_schema_function.png)

**示例**:

* **GetDate()**:返回当前日期
* **Year(@created)**:返回“已创建”属性中包含的日期的年份。
* **GetEmailDomain(@email)**:返回电子邮件地址的域。

## 通过计算字符串构建字符串 {#building-a-string-via-the-compute-string}

计 **算字符串** 是XPath表达式，用于构造一个字符串，该字符串表示与该模式相关联的表中的记录。 **计算字符串** ，主要用于图形界面中显示所选记录的标签。

计算 **字符串** ，通过数据架构 **`<compute-string>`** 主要元素下的元素进行定义。 expr **属性包含** XPath表达式，用于计算显示。

**示例**:compute string of the recipient table.

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

收件人的计算字符串的结果：Doe **John(john.doe@aol.com)**

>[!NOTE]
>
>如果架构不包含计算字符串，则默认情况下将填充一个计算字符串，其中包含该架构的主键的值。

