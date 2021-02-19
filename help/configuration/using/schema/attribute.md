---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%

---


# 属性元素{#attribute--element}

## 内容模型{#content-model}

attribute:==help

## 属性{#attributes}

_operation(string)、advanced(boolean)、applicableIf(string)、autoIncrement(boolean)、gelsTo(string)、dataPolicy(string)、dbEnum(string)、defOnDuplicate(boolean)、default(string)、desc(string)、expr(string)、feature(string)、feature(string)、feature(string)、feature(string)、featureDatring、featureDateDater)、featureDate(string)、img(string)、inout(string)、label(string)、length(string)、localizable(boolean)、name(MNTOKEN)、notNull(boolean)、pkgStatus(string)、ref(string)、必需(boolean)、sqlDefault(string)、sqlname(string)、sqltable(string)、目标（stringMNTOKEN、模板）、translatedDefault（字符串）、translatedExpr（字符串）、type(MNTOKEN)、user(boolean)、userEnum(string)、visibleIf(string)、xml(boolean)

## 父项{#parents}

`<element>`

## 子项{#children}

`<help>`

## 说明{#description}

`<attribute>` elements允许您在数据库中定义字段。

## 使用和上下文{#use-and-context-of-use}

`<attribute>` 元素必须在元素中声 `<element>` 明。

在`<srcschema>`中定义`<attribute>`元素的序列不会影响数据库中的字段创建序列。 创建顺序将按字母顺序排列。

## 属性描述{#attribute-description}

* **_operation(string)**:定义在数据库中写入的类型。

   此属性主要用于扩展现成模式。

   可访问的值有：

   * “无”：单独和解。 这意味着Adobe Campaign将在不更新元素的情况下恢复该元素，如果元素不存在，则会生成错误。
   * &quot;insertOrUpdate&quot;:插入时更新。 这意味着，Adobe Campaign将更新元素，或在元素不存在时创建元素。
   * “插入”：插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”：更新。 这意味着，如果元素不存在，Adobe Campaign将更新该元素或生成错误。
   * “删除”：删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔值）**:激活此选项(@advanced=&quot;true&quot;)后，可在表单中配置列表的可用字段列表中隐藏该属性。
* **applicableIf(string)**:此属性允许您使字段成为可选字段。在符合约束时更新数据库时，将考虑`<attribute>`元素。 “appliableIf”接收XTK表达式。
* **autoIncrement（布尔值）**:如果激活了此选项，则字段将变为计数器。这样，您就可以增加一个值（大部分是ID）。 （外部使用）
* **wellersTo(string)**:获取共享该字段的表的名称和命名空间，并在声明属性的模式中填充该字段。（仅在`<schema>`中使用）。
* **dataPolicy(string)**:允许您对SQL或XML字段中允许的值指定批准约束。此属性的值为：

   * “无”：无值
   * “smartCase”：大写
   * &quot;lowerCase&quot;:全部小写
   * &quot;upperCase&quot;:全部大写
   * “电子邮件”：电子邮件地址
   * “电话”：电话号码
   * &quot;标识符&quot;:标识符名称
   * &quot;resIdentifier&quot;:文件名

* **dbEnum（字符串）**:接收“已关闭”明细列表的内部名称。必须在`<srcschema>`中定义明细列表值。
* **defOnDuplicate（布尔值）**:如果激活了此属性，则当记录重复时，默认值(在@default中定义)会自动重新应用于记录。
* **default(string)**:允许您定义默认字段的值（调用函数、默认值）。此属性接收XTK表达式。
* **desc(string**):允许您插入属性的描述。此说明显示在接口的状态栏中。
* **edit(string**):此属性指定将在链接到模式的表单中使用的输入类型。
* **enum(string)**:接收链接到该字段的明细列表的名称。该明细列表可以插入同一模式或远程模式。
* **expr(字符串**):定义字段计算表达式。此属性接收Xpath或XTK表达式。
* **功能(字符串**)定义特征字段：这些字段用于扩展现有表中的数据，但在附件表中具有存储。接受的值为：

   * “共享”：内容按数据类型存储在共享表中
   * “专用”：内容存储在专用表中

   SQL特征表是根据特征类型自动构建的：

   * 专用：`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   有两种类型的特征字段：“简单”oà¹其中在特征上授权了单个值的字段，而“简单”¹多个选择字段，其中特征链接到可能包含多个值的集合元素。

   在模式中定义特性时，此模式必须具有基于单个字段的主键（未授权复合键）。

* **featureDate（布尔值）**:属性链接到“@feature”特征字段。如果其值为“true”，则允许您查看上次更新该值的时间。
* **img(string)**:允许您为链接到字段的图像定义路径(命名空间+图像名称)(示例：img=&quot;cus:mypicture.jpg&quot;)。实际上，映像必须导入到应用程序服务器。
* **label(string**):链接到字段的标签，主要发往界面中的用户。它使您能避免命名限制。
* **length(string**):maxSQL字段“字符串”类型值的字符数。 如果未指定“@length”属性，Adobe Campaign将自动创建一个255个字符的字段。
* **localizable（布尔值）**:如果激活了该属性，则此属性会告知收集工具恢复“@label”属性的值，以用于翻译（内部使用）。
* **name(MNTOKEN)**:与表中字段名称匹配的属性的名称。“@name”属性的值必须很短，最好是英文，并符合XML命名约束。

   将模式写入Adobe Campaign库时，前缀会通过数据库自动添加到字段名称：

   * “i”：“integer”类型的前缀。
   * “d”：“多次”类型的前缀。
   * “s”：字符串类型的前缀。
   * “ts”：前缀。

   要完全定义表中字段的名称，请在定义属性时使用“@sqlname”选项。

* **notNull（布尔值）**:允许您重新定义Adobe Campaign中有关管理数据库中NULL记录的行为。默认情况下，数字字段不为null，字符串和日期类型字段可以为null。
* **pkgStatus(string)**:在包导出过程中，会根据“@pkgStatus”的值考虑以下值：

   * “always”：始终存在
   * “never”：从
   * &quot;default（或nothing）&quot;:将导出该值，除非它是默认值，或者它不是与其他实例不兼容的内部字段。

* **ref(string)**:此属性定义对由多个模式 `<attribute>` 共享的元素的引用（定义因子分配）。定义未复制到当前模式。
* **必需(布尔值**):如果激活了此属性(@required=&quot;true&quot;)，则界面中将突出显示该字段。该字段的标签将以红色显示。
* **sql（布尔值）**:如果激活了此属性(@sql=&quot;true&quot;)，则会强制存储SQL属性，即使包含该属性的元素具有xml=&quot;true&quot;属性时也是如此。
* **sqlDefault（字符串）**:此属性允许您定义在激活@notNull属性时更新数据库时考虑的默认值。如果在属性创建后添加了此属性，则即使对于新记录，模式行为也不会更改。 要更改模式并更新新记录的值，您需要删除并再次创建该属性。
* **sqlname(string)**:。如果未指定@sqlname，则默认使用&quot;@name&quot;属性的值。 当模式写入数据库时，会根据字段类型自动添加前缀。
* **模板(字符串**):此属性定义对由多个模式 `<attribute>` 共享的元素的引用。定义会自动复制到当前模式。
* **translatedDefault(string)**:如果找到“@default”属性，则“@translatedDefault”将允许您重新定义表达式以匹配在@default中定义的属性，并由转换工具收集（内部使用）。
* **translatedExpr(string)**:如果存在“@expr”属性，则“@translatedExpr”属性允许您重新定义表达式以匹配在@expr中定义的属性，该属性将由转换工具收集（内部使用）。
* **type(MNTOKEN)**:字段类型。

   字段类型是通用的。 根据所安装的数据库类型，Adobe Campaign会将定义的类型更改为在结构更新期间所安装数据库的特定值。

   列表可用类型：

   * 任意
   * 宾
   * blob
   * 布尔
   * 字节
   * CDATA
   * date
   * datetimetz
   * datetimenotz
   * 日期
   * 多次
   * 枚举
   * 浮
   * html
   * int64
   * 链接
   * 长
   * 备忘录
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字符串
   * 时间
   * 时间平移
   * uuid

   如果&quot;@type&quot;属性留空，则默认情况下，Adobe Campaign会将长度为100的字符串(STRING)链接到字段。

   如果字段为STRING类型，且字段名称未由“@sqlname”属性的存在指定，则数据库中字段的名称将自动在“s”前面。 此操作模式将与INTEGER(i)、多次(d)和DATES(ts)类型字段类似。

* **userEnum（字符串）**:接收“open”明细列表的内部名称。明细列表的值可由用户在界面中定义。
* **visibleIf(string)**:以XTK表达式的形式定义一个条件，以显示或隐藏属性。

   >[!IMPORTANT]
   >
   >属性已隐藏，但仍可以访问其数据。

* **xml（布尔值）**:如果激活了此选项，则字段的值没有链接的SQL字段。Adobe Campaign为记录存储创建文本类型“mData”字段。 这意味着不对这些字段进行筛选或排序。

### 示例{#examples}

其值存储在明细列表库中的值示例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

使用“@datapolicy”声明XML字段：

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

示例为&quot;@applicableIf&quot;:仅当国家/地区数大于20时，才会创建“contains”属性。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

“@feature”类型为“shared”的示例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

“@feature”为“dedicated”类型的示例：

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
