---
product: campaign
title: 元素和属性 — 属性元素
description: 元素和属性
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 1%

---

# attribute element {#attribute--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model}

attribute：==help

## 属性 {#attributes}

_operation (string)、advanced (boolean)、applicableIf (string)、autoIncrement (boolean)、fallsTo (string)、dataPolicy (string)、dbEnum (string)、defOnDuplicate (boolean)、default (string)、desc (string)、edit (string)、enum (string)、expr (string)、featureDate (boolean)、img (string)、inout (string)、label (string)、length (string)、localizable (boolean)、name (MNTOKEN (NTOKEN)、NOT (not)、not (not (boolean)、notNull (boolean)、pkgStatus (string (boolean) ref)、ref（字符串）、required（布尔值）、sql（布尔值）、sqlDefault（字符串）、sqlname（字符串）、sqltable（字符串）、target(MNTOKEN)、template（字符串）、translatedDefault（字符串）、translatedExpr（字符串）、type(MNTOKEN)、user（布尔值）、userEnum（字符串）、visibleIf（字符串）、xml（布尔值）

## 父项 {#parents}

`<element>`

## 子项 {#children}

`<help>`

## 说明 {#description}

`<attribute>` 利用元素，可在数据库中定义字段。

## 使用和使用环境 {#use-and-context-of-use}

`<attribute>` 元素必须在 `<element>` 元素。

序列中的 `<attribute>` 元素在 `<srcschema>` 不影响数据库中的字段创建顺序。 创建序列将按字母顺序排列。

## 属性说明 {#attribute-description}

* **操作（字符串）(_O)**：定义在数据库中写入的类型。

  此属性主要用于扩展现成架构。

  可访问值包括：

   * “无”：仅和解。 这意味着Adobe Campaign将恢复元素，而不更新它，如果元素不存在则生成错误。
   * &quot;insertOrUpdate&quot;：使用insertion更新。 这意味着Adobe Campaign将更新元素，如果它不存在，则创建它。
   * &quot;insert&quot;： insertion. 这意味着Adobe Campaign将插入元素而不检查元素是否存在。
   * &quot;update&quot;：更新。 这意味着Adobe Campaign将更新元素，如果它不存在，则产生错误。
   * &quot;delete&quot;：删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔值）**：激活此选项(@advanced=&quot;true&quot;)后，您可以在可用于配置表单列表的可用字段列表中隐藏属性。
* **appliedIf（字符串）**：此属性允许您将字段设为可选字段。 此 `<attribute>` 当满足约束时更新数据库时将考虑元素。 &quot;applicableIf&quot;接收XTK表达式。
* **autoIncrement（布尔值）**：如果激活此选项，则字段会变为计数器。 这使您可以递增值（主要是ID）。 （外部使用）
* **fallsTo（字符串）**：采用共享字段的表的名称和命名空间，并填充声明属性的架构。 (仅用于 `<schema>`)。
* **dataPolicy（字符串）**：用于在SQL或XML字段中为允许的值指定批准约束。 此属性的值为：

   * &quot;none&quot;：无值
   * &quot;smartCase&quot;：第一字母大写
   * &quot;lowerCase&quot;：全部为小写
   * &quot;upperCase&quot;：全部大写
   * &quot;email&quot;：电子邮件地址
   * &quot;phone&quot;：电话号码
   * &quot;identifier&quot;：标识符名称
   * &quot;resIdentifier&quot;：文件名

* **dbEnum（字符串）**：接收“已关闭”枚举的内部名称。 枚举值必须在 `<srcschema>`.
* **defOnDuplicate（布尔值）**：如果激活此属性，则在复制记录时，默认值(在@default中定义)将自动重新应用于记录。
* **默认（字符串）**：用于定义默认字段的值（调用函数，默认值）。 此属性接收XTK表达式。
* **desc（字符串）**：用于插入属性的描述。 此描述将显示在界面的状态栏中。
* **编辑（字符串）**：此属性指定将在链接到架构的表单中使用的输入类型。
* **枚举（字符串）**：接收链接到字段的枚举的名称。 枚举可以插入到同一模式或远程模式中。
* **expr（字符串）**：定义字段预计算表达式。 此属性接收Xpath或XTK表达式。
* **功能（字符串）**：定义特性字段：这些字段用于扩展现有表中的数据，但存储在附件表中。 接受的值包括：

   * “共享”：根据数据类型将内容存储在共享表中
   * &quot;dedicated&quot;：内容存储在专用表中

  SQL特性表是根据以下特性类型自动构建的：

   * 专用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  有两种类型的特征字段：简单oà¹字段仅授权一个特征值；以及oà¹多选字段，其中特征与可能包含多个值的收集要素相关联。

  在架构中定义特征时，此架构必须具有基于单个字段的主键（复合键未授权）。

* **featureDate（布尔值）**：链接到“@feature”特征字段的属性。 如果其值为“true”，则可让您了解该值的上次更新时间。
* **img（字符串）**：用于定义链接到字段的图像的路径（命名空间+图像名称）（例如：img=&quot;cus：mypicture.jpg&quot;）。 在物理上，必须将映像导入到应用程序服务器。
* **标签（字符串）**：链接到字段的标签，通常发往界面中的用户。 它可让您避免命名约束。
* **length（字符串）**：最大值 “字符串”类型SQL字段值的字符数。 如果未指定“@length”属性，Adobe Campaign会自动创建一个包含255个字符的字段。
* **可本地化（布尔值）**：如果激活，则此属性会告知收集工具恢复“@label”属性的值以供翻译（内部使用）。
* **名称(MNTOKEN)**：与表中字段的名称匹配的属性的名称。 “@name”属性的值必须较短，最好是英文，并符合XML命名约束。

  当架构写入数据库时，Adobe Campaign会自动将前缀添加到字段名称中：

   * &quot;i&quot;：&quot;integer&quot;类型的前缀。
   * &quot;d&quot;：&quot;double&quot;类型的前缀。
   * “s”：字符串类型的前缀。
   * &quot;ts&quot;：&quot;date&quot;类型的前缀。

  要完全定义表中字段的名称，请在定义属性时使用“@sqlname”选项。

* **notNull（布尔值）**：用于重新定义Adobe Campaign有关管理数据库中NULL记录的行为。 默认情况下，数字字段不为null，字符串和日期类型字段可以为null。
* **pkgStatus（字符串）**：在导出资源包期间，会根据“@pkgStatus”的值考虑值：

   * &quot;always&quot;：始终存在
   * “从不”：从不出现
   * &quot;default(or nothing)&quot;：导出值，除非它是默认值，或者不是与其他实例不兼容的内部字段。

* **ref（字符串）**：此属性定义对 `<attribute>` 由多个架构共享的元素（定义分解）。 该定义将不会复制到当前架构中。
* **必需（布尔值）**：如果激活此属性(@required=&quot;true&quot;)，则界面中会高亮显示字段。 字段的标签在表单中将为红色。
* **sql（布尔值）**：如果激活此属性(@sql=&quot;true&quot;)，则强制存储SQL属性，即使包含该属性的元素具有xml=&quot;true&quot;属性也是如此。
* **sqlDefault（字符串）**：利用此属性可定义在激活@notNull属性时用于更新数据库的默认值。 如果在属性创建后添加此属性，则即使对于新记录，架构行为也不会更改。 要更改架构并更新新记录的值，您需要删除并再次创建属性。
* **sqlname（字符串）**：在表创建期间为字段。 如果未指定@sqlname，则默认使用“@name”属性的值。 在数据库中写入架构时，将根据字段类型自动添加前缀。
* **模板（字符串）**：此属性定义对 `<attribute>` 由多个架构共享的元素。 该定义会自动复制到当前架构中。
* **translatedDefault（字符串）**：如果找到“@default”属性，“@translatedDefault”将允许您重新定义表达式以匹配在@default中定义的表达式，该表达式将由翻译工具收集（内部使用）。
* **translatedExpr（字符串）**：如果存在“@expr”属性，则通过“@translatedExpr”属性可重新定义要与@expr中定义的表达式匹配的表达式，该表达式将由翻译工具收集（内部使用）。
* **类型(MNTOKEN)**：字段类型。

  字段类型是通用的。 根据安装的数据库类型，Adobe Campaign会将定义的类型更改为特定于结构更新期间安装的数据库的值。

  可用类型列表：

   * 任何
   * 纸盒
   * blob
   * 布尔值
   * 字节
   * CDATA
   * 日期时间
   * datetimetz
   * datetimenotz
   * date
   * 多次
   * 枚举
   * 浮点数
   * html
   * int64
   * 链接
   * 长
   * 备忘
   * MNTOKEN
   * percent
   * 主密钥
   * 短
   * 字符串
   * 时间
   * 时间跨度
   * uuid

  如果“@type”属性留空，默认情况下，Adobe Campaign会将长度为100的字符串（字符串）链接到字段。

  如果字段为STRING类型，并且字段的名称未通过“@sqlname”属性的存在来指定，则数据库中字段的名称将自动加上“s”。 该操作模式与INTEGER (i)、DOUBLE (d)和DATES (ts)类型字段类似。

* **userEnum（字符串）**：接收“open”枚举的内部名称。 枚举的值可由用户在界面中定义。
* **visibleIf（字符串）**：以XTK表达式的形式定义条件以显示或隐藏属性。

  >[!IMPORTANT]
  >
  >属性已隐藏，但仍可以访问其数据。

* **xml（布尔型）**：如果激活此选项，则字段的值没有链接的SQL字段。 Adobe Campaign为记录存储创建文本类型“mData”字段。 这意味着没有对这些字段进行筛选或排序。

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

带有“@datapolicy”的XML字段的声明：

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

带有“@applicableIf”的示例：仅当国家/地区数量大于20时，才会创建“contains”属性。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

“共享”类型的“@feature”示例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

“dedicated”类型的“@feature”示例：

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
