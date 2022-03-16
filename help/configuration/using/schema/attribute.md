---
product: campaign
title: 元素和属性 — 属性元素
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 0%

---

# 属性元素 {#attribute--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model}

属性：==帮助

## 属性 {#attributes}

_operation（字符串）、高级（布尔）、appliableIf（字符串）、autoIncrement（布尔）、string（字符串）、dbEnum（字符串）、defOnDuplicate（布尔）、desc（字符串）、编辑（字符串）、枚举（字符串）、expr（字符串）、功能（字符串）、featureDate（布尔）、img（字符串）、标签（字符串）、长度（字符串）、可本地化（布尔值）、MNOTON（令牌）、Status(Pkg)字符串)、ref（字符串）、必需（布尔）、sql（布尔）、sqlDefault（字符串）、sqlname（字符串）、sqltable（字符串）、target(MNTOKEN)、模板（字符串）、translatedDefault（字符串）、translatedExpr（字符串）、类型(MNTOKEN)、用户（布尔）、userEnum（字符串）、visibleIf（字符串）、xml（布尔）

## 父母 {#parents}

`<element>`

## 子项 {#children}

`<help>`

## 说明 {#description}

`<attribute>` 元素允许您在数据库中定义字段。

## 使用和使用上下文 {#use-and-context-of-use}

`<attribute>` 元素必须在 `<element>` 元素。

顺序 `<attribute>` 元素在 `<srcschema>` 不影响数据库中的字段创建顺序。 创建顺序将按字母顺序排列。

## 属性描述 {#attribute-description}

* **_operation（字符串）**:定义在数据库中写入的类型。

   此属性主要用于扩展即装即用架构。

   可访问的值包括：

   * &quot;none&quot;:单独协调。 这意味着Adobe Campaign将在不更新元素的情况下恢复该元素，或者在元素不存在时生成错误。
   * &quot;insertOrUpdate&quot;:使用插入进行更新。 这意味着Adobe Campaign将更新元素，或在元素不存在时创建元素。
   * &quot;insert&quot;:插入。 这意味着Adobe Campaign将插入元素，而不检查它是否存在。
   * &quot;update&quot;:更新。 这意味着Adobe Campaign将更新元素，或在元素不存在时生成错误。
   * &quot;delete&quot;:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔）**:激活此选项(@advanced=&quot;true&quot;)后，您可以隐藏可用字段列表中的属性，这些字段可用于在表单中配置列表。
* **appliableIf（字符串）**:此属性允许您将字段设为可选字段。 的 `<attribute>` 在遵守约束时更新数据库时，将考虑元素。 “appliableIf”接收XTK表达式。
* **autoIncrement（布尔值）**:如果激活此选项，则字段将变为计数器。 这样，您就可以递增一个值（主要是ID）。 （外部使用）
* **属于（字符串）**:采用共享该字段的表的名称和命名空间，并填充声明属性的架构。 (仅在 `<schema>`)。
* **dataPolicy（字符串）**:允许您指定对SQL或XML字段中允许的值的批准约束。 此属性的值包括：

   * &quot;none&quot;:无值
   * &quot;smartCase&quot;:首字母大写
   * &quot;lowerCase&quot;:全部小写
   * &quot;upperCase&quot;:全部大写
   * &quot;email&quot;:电子邮件地址
   * &quot;phone&quot;:电话号码
   * &quot;identifier&quot;:标识符名称
   * &quot;resIdentifier&quot;:文件名

* **dbEnum（字符串）**:接收“已关闭”枚举的内部名称。 枚举值必须在 `<srcschema>`.
* **defOnDuplicate（布尔值）**:如果激活此属性，则在记录重复时，默认值(在@default中定义)会自动重新应用于记录。
* **默认（字符串）**:用于定义默认字段的值（调用函数、默认值）。 此属性接收XTK表达式。
* **desc（字符串）**:允许您插入属性描述。 此描述显示在界面的状态栏中。
* **编辑（字符串）**:此属性指定将在链接到架构的表单中使用的输入类型。
* **枚举（字符串）**:接收链接到字段的枚举的名称。 枚举可以插入到同一架构或远程架构中。
* **expr（字符串）**:定义字段预计算表达式。 此属性接收Xpath或XTK表达式。
* **功能（字符串）**:定义特征字段：这些字段用于扩展现有表中的数据，但存储在附件表中。 接受的值包括：

   * &quot;shared&quot;:按数据类型将内容存储在共享表中
   * “专用”：内容存储在专用表中

   SQL特征表是根据特征类型自动构建的：

   * 专用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特征字段有两种类型：简单的oà¹字段，其中在特征上授权单个值；以及多个选择字段，其中特征链接到可能包含多个值的集合元素。oà¹

   当在模式中定义特征时，此模式必须具有基于单个字段的主键（组合键未授权）。

* **featureDate（布尔值）**:属性。 如果其值为“true”，则可让您了解该值的上次更新时间。
* **img（字符串）**:用于为链接到字段的图像定义路径（命名空间+图像名称）(示例：img=&quot;cus:mypicture.jpg&quot;)。 实际上，必须将映像导入应用程序服务器。
* **标签（字符串）**:链接到字段的标签，主要用于界面中的用户。 它可让您避免命名限制。
* **length（字符串）**:max “字符串”类型SQL字段值的字符数。 如果未指定“@length”属性，则Adobe Campaign会自动创建一个255个字符的字段。
* **可本地化（布尔）**:如果激活了该属性，则此属性将告知收集工具恢复“@label”属性的值以进行翻译（内部使用）。
* **name(MNTOKEN)**:与表中字段名称匹配的属性名称。 “@name”属性的值必须简短（最好是英文），并符合XML命名约束。

   当架构写入数据库时，前缀会由Adobe Campaign自动添加到字段名称：

   * “i”：为“integer”类型的前缀。
   * &quot;d&quot;:为“double”类型添加前缀。
   * &quot;s&quot;:字符串类型的前缀。
   * &quot;ts&quot;:为“date”类型添加前缀。

   要完全定义表中字段的名称，请在定义属性时使用“@sqlname”选项。

* **notNull（布尔值）**:用于重新定义Adobe Campaign在数据库中管理NULL记录时的行为。 默认情况下，数字字段不为空，字符串和日期类型字段可为空。
* **pkgStatus（字符串）**:在资源包导出过程中，会根据“@pkgStatus”的值考虑以下值：

   * &quot;always&quot;:始终存在
   * &quot;never&quot;:永远不存在
   * &quot;default（或nothing）&quot;:除非该值是默认值，或者它不是与其他实例不兼容的内部字段，否则会导出该值。

* **ref（字符串）**:此属性定义对 `<attribute>` 由多个架构共享的元素（定义保理）。 定义不会复制到当前架构中。
* **必需（布尔）**:如果激活此属性(@required=&quot;true&quot;)，则界面中会突出显示该字段。 字段的标签将以红色显示。
* **sql（布尔）**:如果激活此属性(@sql=&quot;true&quot;)，则强制存储SQL属性，即使包含该属性的元素具有xml=&quot;true&quot;属性时也是如此。
* **sqlDefault（字符串）**:此属性允许您定义在激活属性时更新数据库时需考虑的@notNull值。 如果在属性创建后添加此属性，则即使对于新记录，架构行为也不会更改。 要更改架构并更新新记录的值，您需要删除并再次创建属性。
* **sqlname（字符串）**:的子域。 如果@sqlname未指定，则默认使用“@name”属性的值。 当架构写入数据库时，将根据字段类型自动添加前缀。
* **模板（字符串）**:此属性定义对 `<attribute>` 由多个架构共享的元素。 定义会自动复制到当前架构中。
* **translatedDefault（字符串）**:如果找到“@default”属性，则“@translatedDefault”将允许您重新定义表达式以匹配@default中定义的表达式，该表达式将由翻译工具收集（内部使用）。
* **translatedExpr（字符串）**:如果存在“@expr”属性，则“@translatedExpr”属性允许您重新定义表达式以匹配在中定义的表达式，该表达式将由翻译工具收集（内部使用）。
* **类型(MNTOKEN)**:字段。

   字段类型是通用的。 根据所安装数据库的类型，Adobe Campaign会将定义的类型更改为在结构更新期间所安装数据库的特定值。

   可用类型列表：

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
   * 浮点
   * html
   * int64
   * 链接
   * long
   * 备忘录
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字符串
   * 时间
   * 时间跨平台
   * uuid

   如果“@type”属性留空，则Adobe Campaign会默认将长度为100的字符串（字符串）链接到字段。

   如果字段的类型为STRING，并且字段的名称未由“@sqlname”属性的存在指定，则数据库中字段的名称将自动前面加“s”。 此操作模式与INTEGER(i)、DOUBLE(d)和DATES(ts)类型字段类似。

* **userEnum（字符串）**:接收“open”枚举的内部名称。 枚举的值可由用户在界面中定义。
* **visibleIf（字符串）**:以XTK表达式的形式定义一个条件，以显示或隐藏属性。

   >[!IMPORTANT]
   >
   >该属性处于隐藏状态，但仍可以访问其数据。

* **xml（布尔）**:如果激活了此选项，则字段的值没有链接的SQL字段。 Adobe Campaign会为记录存储创建文本类型“mData”字段。 这意味着不会对这些字段进行过滤或排序。

### 示例 {#examples}

其值存储在数据库中的枚举值示例：

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

示例为“@applicableIf”：仅当国家/地区数量大于20时，才会创建“包含”属性。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

“@feature”为“shared”类型的示例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

“@feature”为“dedicated”类型的示例：

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
