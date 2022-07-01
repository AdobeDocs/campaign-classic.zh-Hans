---
product: campaign
title: 模式结构
description: 模式结构
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 2%

---

# 模式结构{#schema-structure}

![](../../assets/v7-only.svg)

的基本结构 `<srcschema>` 如下所示：

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

数据架构的XML文档必须包含 **`<srcschema>`** 根元素，其中 **name** 和 **命名空间** 属性来填充架构名称及其命名空间。

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

使用其相应的数据模式：

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

架构的入口点是其主要元素。 很容易识别，因为它与架构同名，并且应该是根元素的子元素。 内容的描述以此元素开头。

在本例中，主元素由以下行表示：

```
<element name="recipient">
```

元素 **`<attribute>`** 和 **`<element>`** 通过主元素后面的，可定义XML结构中数据项的位置和名称。

在我们的示例架构中，这些参数包括：

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

必须遵守下列规则：

* 每个 **`<element>`** 和 **`<attribute>`** 必须通过名称进行标识 **name** 属性。

   >[!IMPORTANT]
   >
   >元素的名称应简洁明了，最好用英文写，并且只包含符合XML命名规则的授权字符。

* 仅 **`<element>`** 元素可以包含 **`<attribute>`** 元素和 **`<element>`** 元素。
* 安 **`<attribute>`** 元素在 **`<element>`**.
* 的使用 **`<elements>`** 建议在多行数据字符串中使用。

## 数据类型 {#data-types}

数据类型通过 **type** 属性 **`<attribute>`** 和 **`<element>`** 元素。

在 [`<attribute>` 元素](../../configuration/using/schema/attribute.md) 和 [`<element>` 元素](../../configuration/using/schema/element.md))。

未填充此属性时， **字符串** 为默认数据类型，除非元素包含子元素。 如果是，则仅用于按层次结构元素(**`<location>`** 元素)。

架构支持以下数据类型：

* **字符串**:字符串。 示例：名字、城镇等。

   可以通过 **length** 属性（可选，默认值“255”）。

* **布尔**:布尔字段。 可能值的示例：true/false、0/1、yes/no等。
* **字节**, **短**, **long**:整数（1字节、2字节、4字节）。 示例：年龄、帐号、积分等。
* **多次**:双精度浮点数。 示例：价格、费率等
* **日期**, **date**:日期和日期+时间。 示例：出生日期、购买日期等。
* **datetimenotz**:日期+时间（不含时区数据）。
* **时间跨平台**:持续时间。 示例：资历。
* **备忘录**:长文本字段（多行）。 示例：描述、评论等。
* **uid**:用于支持GUID的“uniqueidentifier”字段(仅在Microsoft SQL Server中受支持)。

   >[!NOTE]
   >
   >包含 **uid** 除Microsoft SQL Server之外的引擎中的字段，必须添加并填写“newuuid()”函数及其默认值。

以下是我们输入类型的示例架构：

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

### 映射Adobe Campaign/DBMS数据类型 {#mapping-the-types-of-adobe-campaign-dbms-data}

下表列出了Adobe Campaign为不同数据库管理系统生成的数据类型的映射。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 字符串<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2（如果为unicode，则为NVARCHAR2）<br /> </td> 
   <td> VARCHAR（如果为unicode，则为NVARCHAR）<br /> </td> 
  </tr> 
  <tr> 
   <td> 布尔值<br /> </td> 
   <td> 斯马林特<br /> </td> 
   <td> 数字(3)<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 字节<br /> </td> 
   <td> 斯马林特<br /> </td> 
   <td> 数字(3)<br /> </td> 
   <td> TINYINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 短<br /> </td> 
   <td> 斯马林特<br /> </td> 
   <td> 数字(5)<br /> </td> 
   <td> 斯马林特<br /> </td> 
  </tr> 
  <tr> 
   <td> 两次<br /> </td> 
   <td> 双精度<br /> </td> 
   <td> 浮动<br /> </td> 
   <td> 浮动<br /> </td> 
  </tr> 
  <tr> 
   <td> 长<br /> </td> 
   <td> 整数<br /> </td> 
   <td> 数字(10)<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> 数字(20)<br /> </td> 
   <td> BIGINT<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
   <td> DATETIME<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间<br /> </td> 
   <td> 时间<br /> </td> 
   <td> 浮动<br /> </td> 
   <td> 浮动<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期时间<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> 日期<br /> </td> 
   <td> MS SQL &lt; 2008:DATETIME<br /> MS SQL &gt;= 2012:DATETIMEOFFSET<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> 日期<br /> </td> 
   <td> MS SQL &lt; 2008:DATETIME<br /> MS SQL &gt;= 2012:DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间跨度<br /> </td> 
   <td> 双精度<br /> </td> 
   <td> 浮动<br /> </td> 
   <td> 浮动<br /> </td> 
  </tr> 
  <tr> 
   <td> 备忘录<br /> </td> 
   <td> 文本<br /> </td> 
   <td> CLOB（如果为Unicode，则为NCLOB）<br /> </td> 
   <td> 文本（如果为Unicode，则为NTEXT）<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> 图像<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 属性 {#properties}

的 **`<elements>`** 和 **`<attributes>`** 可以使用各种属性来扩充数据架构的元素。 您可以填充标签以描述当前元素。

### 标签和描述 {#labels-and-descriptions}

* 的 **标签** 属性允许您输入简短描述。

   >[!NOTE]
   >
   >标签与实例的当前语言关联。

   **示例**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   标签可从Adobe Campaign客户端控制台输入表单中查看：

   ![](assets/d_ncs_integration_schema_label.png)

* 的 **desc** 属性允许您输入长描述。

   描述可从Adobe Campaign客户端控制台主窗口状态栏的输入表单中查看。

   >[!NOTE]
   >
   >描述与实例的当前语言关联。

   **示例**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### 默认值 {#default-values}

的 **默认** 属性允许您定义在内容创建时返回默认值的表达式。

值必须是与XPath语言兼容的表达式。 有关更多信息，请参阅 [使用XPath引用](../../configuration/using/schema-structure.md#referencing-with-xpath).

**示例**:

* 当前日期： **default=&quot;GetDate()&quot;**
* 计数器： **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   在此示例中，默认值是使用字符串的串联并调用 **计数器值** 函数，其中包含自由计数器名称。 每次插入时返回的数字都增加1。

   >[!NOTE]
   >
   >在Adobe Campaign客户端控制台中， **[!UICONTROL Administration>Counters]** 节点用于管理计数器。

要将默认值链接到字段，您可以使用 `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` :用于在创建实体时使用默认值预填字段。 该值不是默认的SQL值。

`<sqldefault>` :允许您在创建字段时添加值。 此值显示为SQL结果。 在模式更新期间，只有新记录会受此值的影响。

### 明细列表 {#enumerations}

#### 自由枚举 {#free-enumeration}

的 **userEnum** 属性允许您定义自由枚举，以记住和显示通过此字段输入的值。 语法如下所示：

**userEnum=&quot;枚举的名称&quot;**

可以自由选择给枚举的名称并与其他字段共享。

这些值显示在输入表单的下拉列表中：

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>在Adobe Campaign客户端控制台中， **[!UICONTROL Administration > Enumerations]** 节点用于管理枚举。

#### 设置枚举 {#set-enumeration}

的 **枚举** 属性允许您定义在事先已知可能值列表时使用的固定枚举。

的 **枚举** 属性是指在主元素外的架构中填充的枚举类的定义。

枚举允许用户从下拉列表中选择一个值，而不是在常规输入字段中输入该值：

![](assets/d_ncs_integration_schema_enum.png)

数据架构中枚举声明的示例：

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

枚举通过 **`<enumeration>`** 元素。

枚举属性如下所示：

* **baseType**:与值关联的数据类型，
* **标签**:列举的说明，
* **name**:枚举的名称，
* **默认**:枚举的默认值。

枚举值在 **`<value>`** 元素（具有以下属性）：

* **name**:内部存储的值的名称，
* **标签**:标签。

#### dbenum枚举 {#dbenum-enumeration}

* 的 **贝努姆** 属性允许您定义其属性与 **枚举** 属性。

   但是， **name** 属性不在内部存储值，它会存储一个代码，通过该代码，您可以扩展相关表而不修改其架构。

   这些值通过 **[!UICONTROL Administration>Enumerations]** 节点。

   例如，此枚举用于指定营销活动的性质。

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### 示例 {#example}

以下是我们的示例架构，其中填充了以下属性：

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

集合是具有相同名称和相同层次结构级别的元素列表。

的 **未绑定** 值为“true”的属性允许您填充收藏集元素。

**示例**:定义 **`<group>`** 架构中的收集元素。

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

通过XML内容的投影：

```
<group label="Group1"/>
<group label="Group2"/>
```

## 使用XPath引用 {#referencing-with-xpath}

Adobe Campaign中使用XPath语言来引用属于数据模式的元素或属性。

XPath是一种语法，用于在XML文档的树中查找节点。

元素由其名称指定，属性由名称前面的字符“@”指定。

**示例**:

* **@email**:选择电子邮件，
* **location/@city**:选择 **`<location>`** 元素
* **../@email**:从当前元素的父元素中选择电子邮件地址
* **群组`[1]/@label`**:选择作为第一个 **`<group>`** 收集元素
* **群组`[@label='test1']`**:选择作为 **`<group>`** 元素和包含值“test1”

>[!NOTE]
>
>当路径穿过子元素时，将添加附加约束。 在这种情况下，以下表达式必须置于括号之间：
>
>* **location/@city** 无效；请使用 **`[location/@city]`**
>* **`[@email]`** 和 **@email** 等于
>


也可以定义复杂的表达式，例如以下算术运算：

* **@gender+1**:在 **性别** 属性，
* **@email + &#39;(&#39;+@created+&#39;)&#39;**:通过获取添加到创建日期（在圆括号之间）的电子邮件地址值来构建字符串（对于字符串类型，将常量加引号）。

在表达式中添加了高级函数，以丰富此语言的潜力。

您可以通过Adobe Campaign客户端控制台中的任何表达式编辑器访问可用函数列表：

![](assets/d_ncs_integration_schema_function.png)

**示例**:

* **GetDate()**:返回当前日期
* **Year(@created)**:返回“已创建”属性中包含的日期年份。
* **GetEmailDomain(@email)**:返回电子邮件地址的域。

## 通过计算字符串生成字符串 {#building-a-string-via-the-compute-string}

A **计算字符串** 是XPath表达式，用于构建一个字符串，该字符串表示与该模式关联的表中的记录。 **计算字符串** 主要用于图形界面以显示所选记录的标签。

的 **计算字符串** 通过 **`<compute-string>`** 元素。 安 **expr** 属性包含用于计算显示的XPath表达式。

**示例**:收件人表的计算字符串。

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

收件人的计算字符串的结果： **多·约翰(john.doe@aol.com)**

>[!NOTE]
>
>如果架构不包含计算字符串，则默认情况下会使用架构主键的值填充计算字符串。
