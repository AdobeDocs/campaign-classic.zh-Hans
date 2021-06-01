---
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---

# 元素元素{#element--element}

## 内容模型{#content-model-4}

element:==(attribute) | compute-string | dbindex |默认 |元素 |帮助 |加入 |键 | sysFilter | translatedDefault)

## 属性{#attributes-4}

_operation（字符串）、高级（布尔）、聚合（字符串）、autopk（布尔）、convTo（字符串）、convDate（字符串）、dataPolicy（字符串）、dataSource（字符串）、dbEnum（字符串）、defOnDuplicate（布尔）、desc（字符串）、displayAsField（布尔）、doesNotSupportBoolean（布尔）、编辑（字符串）、emptyKeyValue（枚举字符串）、enumpon（图像）SchemaTarget（字符串）、expr（字符串）、externalJoin（布尔）、功能（字符串）、featureDate（布尔）、filterPath（字符串）、filterLink（字符串）、folderModel（字符串）、folderProcess（字符串）、fullLoad（布尔）、层次结构（布尔）、hiercaricalPath（字符串）、inout（字符串）、完整性（字符串）、标签（字符串）、长度（字符串）、可本地化（布尔值）、MNNONoIndex(NoNo)键（布尔）、有序（布尔）、溢流表（布尔）、pkSequence（字符串）、pkgStatus（字符串）、ref（字符串）、必需（布尔）、revAdvanced（布尔）、revCardinal（字符串）、revExternalJoin（布尔）、revIntegrity（字符串）、revLink（字符串）、revTarget（字符串）、revIsibleIf（字符串）、布尔（字符串）、名（字符串）、sql表名、sql表SpaceIndex（字符串）、Target(MNTOKEN)、模板（字符串）、临时表（布尔）、TranslatedDefault（字符串）、TranslatedExpr（字符串）、类型(MNTOKEN)、未绑定（布尔）、用户（布尔）、用户枚举（字符串）、visibleIf（字符串）、xml（布尔）、xmlChildren（布尔）

## 父项{#parents-4}

`<srcschema>`

`<element>`

## 子项{#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

## 说明{#description-4}

Adobe Campaign中有四种类型的`<element>`元素：

* 根`<element>` :定义与架构匹配的SQL表的名称。
* 结构`<element>` :定义一组`<element>`   或   `<attribute>`    元素。
* 链接`<element>` :定义链接。 此元素必须包含“@type=link”属性。
* XML `<element>` :定义文本类型“mData”字段。 此元素必须包含“@type=xml”属性。

## 属性描述{#attribute-description-4}

* **_operation（字符串）**:定义在数据库中写入的类型。

   此属性主要用于扩展即装即用架构。

   可访问的值包括：

   * &quot;none&quot;:单独协调。 这意味着Adobe Campaign将在不更新元素的情况下恢复该元素，或者在元素不存在时生成错误。
   * &quot;insertOrUpdate&quot;:使用插入进行更新。 这意味着Adobe Campaign将更新元素，或在元素不存在时创建元素。
   * &quot;insert&quot;:插入。 这意味着Adobe Campaign将插入元素，而不检查它是否存在。
   * &quot;update&quot;:更新。 这意味着Adobe Campaign将更新元素，或在元素不存在时生成错误。
   * &quot;delete&quot;:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔）**:激活此选项(@advanced=&quot;true&quot;)后，您可以隐藏可用字段列表中的属性，这些字段可用于在表单中配置列表。
* **聚合（字符串）**:允许您通过其他架构复 `<element>`  制的定义。此属性将以“namespace:name”的形式接收模式声明。
* **appliableIf（字符串）**:应用索引的条件。此属性接收XTK表达式。
* **autopk（布尔值）**:如果激活了此选项(autopk=&quot;true&quot;)，则将自动定义唯一键。此选项只能用于架构的主元素。 警告，Adobe Campaign仅保证生成的键是唯一的。 无法保证键值是连续的和增量的。
* **dataPolicy(string)**:允许您指定对SQL字段中允许的值的批准约束。此属性的值包括：

   * &quot;none&quot;:无值
   * &quot;smartCase&quot;:首字母大写
   * &quot;lowerCase&quot;:全部小写
   * &quot;upperCase&quot;:全部大写
   * &quot;email&quot;:电子邮件地址
   * &quot;phone&quot;:电话号码
   * &quot;identifier&quot;:标识符名称
   * &quot;resIdentifier&quot;:文件名

* **dbEnum（字符串）**:接收“已关闭”枚举的内部名称。枚举值必须在`<srcschema>`中定义。
* **defOnDuplicate（布尔）**:如果激活此属性，则在记录重复时，默认值(在@default中定义)会自动重新应用于记录。
* **默认（字符串）**:允许您定义元素行为（调用函数、默认值）。此属性接收XTK表达式。
* **desc（字符串）**:允许您插入元素的描述。此描述显示在界面的状态栏中。
* **displayAsField（布尔）**:如果激活此属性，则“链接”类 `<element>`  型将在架构的树视图（“结构”选项卡）中显示为字段。这样，就可以将链接显示为本地字段，并在查询期间更改其行为。 在查询的SELECT中找到元素后，将使用链接目标的值。 在查询的WHERE中找到元素后，将使用链接的基础键。
* **编辑（字符串）**:此属性指定将在链接到架构的表单中使用的输入类型。
* **枚举（字符串）**:接收链接到字段的枚举的名称。枚举可以插入到同一架构或远程架构中。
* **expr（字符串）**:此属性定义一个计算字段，该表中没有存储任何定义。它接收Xpath或XTK（字符串）表达式。
* **externalJoin（布尔）**:“link”类型元素中的外部连接。
* **功能（字符串）**:定义特征字段：这些字段用于扩展现有表中的数据，但存储在附件表中。接受的值包括：

   * &quot;shared&quot;:按数据类型将内容存储在共享表中
   * “专用”：内容存储在专用表中

   SQL特征表是根据特征类型自动构建的：

   * 专用：`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特征字段有两种类型：在特征上授权单个值的简单字段和在特征上链接到可能包含多个值的集合元素的多个选择字段。

   当在模式中定义特征时，此模式必须具有基于单个字段的主键（组合键未授权）。

* **featureDate（布尔）**:属性。如果其值为“true”，则可让您了解该值的上次更新时间。
* **filterPath（字符串）**:此属性接收Xpath并允许您在字段上定义过滤器。
* **folderLink（字符串）**:此属性将接收用于恢复包含实体的文件的链接名称。
* **folderModel（字符串）**:定义启用实体存储的文件夹类型。仅当存在“@folderLink”时，才定义此属性。
* **folderProcess（字符串）**:定义存储实体模型实例的链接。仅当存在“@folderLink”时，才定义此属性。
* **fullLoad（布尔）**:此属性在表单的字段选择期间强制显示表中的所有记录。
* **img（字符串）**:接收链接到元素的图像的路径。此属性的值为“namespace:image name”类型。 例如：img=&quot;cus:myImage.jpg&quot;。 实际上，必须将映像导入应用程序服务器。
* **完整性（字符串）**:源表对目标表的出现的引用完整性。

   可访问的值包括：

   * &quot;define&quot;:Adobe Campaign不会删除通过链接引用的实体
   * &quot;normal&quot;:删除源实例将初始化目标实例上链接的键（默认模式），此类型的完整性将初始化所有外键
   * &quot;own&quot;:删除源实例会触发删除目标实例
   * &quot;owncopy&quot;:与“自有”（如果是删除）或重复出现（如果是重复）类似
   * &quot;中性&quot;:不执行任何操作

* **标签（字符串）**:元素标签。
* **labelSingular（字符串）**:在界面的某些部分中使用的元素的标签（单数形式）。
* **length（字符串）**:max为“字符串”类型SQL字段的值授权的字符数。
* **localizable（布尔）**:如果激活了该属性，则此属性将告知收集工具恢复“@label”属性的值以进行翻译（内部使用）。
* **name(MNTOKEN)**:与表名称匹配的元素的内部名称。“@name”属性的值必须很短，最好是英文，并符合链接到XML的命名约束。

   当架构写入数据库时，前缀会由Adobe Campaign自动添加到字段名称中。

   * “i”：为“integer”类型的前缀。
   * &quot;d&quot;:为“double”类型添加前缀。
   * &quot;s&quot;:字符串类型的前缀。
   * &quot;ts&quot;:为“date”类型添加前缀。

   要以自主方式定义表的名称，您需要在主架构元素的定义中使用“@sqltable”属性。

* **noDbIndex（布尔）**:可让您指定将不对元素进行索引。
* **ordered（布尔）**:如果激活了属性(ordered=&quot;true&quot;)，则Adobe Campaign会将元素声明序列保留在XML收集元素中。
* **pkSequence（字符串）**:接收用于计算自动增量键的序列的名称。仅当在架构的根元素上定义了自动增量键时，才能使用此属性。
* **pkgStatus（字符串）**:在资源包导出过程中，值将作为此属性值的函数来考虑：

   * &quot;always&quot;:元素将始终存在
   * &quot;never&quot;:元素将永远不存在
   * &quot;default（或nothing）&quot;:除非该元素是默认元素，或者它不是内部字段，并且与其他实例不兼容，否则将导出该元素

* **ref（字符串）**:此属性定义对由多个架构共享的>element>元素的引用（定义保理）。定义不会复制到当前架构中。
* **必需（布尔）**:如果激活此属性(@required=&quot;true&quot;)，则界面中会突出显示该字段。字段的标签将以红色显示。
* **revAdvanced（布尔）**:激活后，此属性会指定相对的链接为“高级”链接。
* **revCardinality（字符串）**:此属性定义两个表之间链接的基数。它用在“link”类型`<element>`中。

   可能的值包括：

   * &quot;single&quot; :简单的1-1类型链接
   * &quot;未绑定&quot;:1-N类型集合链接

   默认情况下，如果在链接创建期间未指定属性，则基数将为1-N。

* **revDesc（字符串）**:此属性接收链接到相反链接的描述。
* **revExternalJoin（布尔）**:激活后，此属性允许您强制外部连接到相对的链接。
* **revIntegrity（字符串）**:此属性定义目标架构上的完整性。与“@integrity”属性的值相同。 默认情况下，Adobe Campaign会为此属性提供“正常”值。
* **revLabel（字符串）**:标签。
* **revLink（字符串）**:相对链接的名称。如果值为“_NONE_”，则目标架构中不会创建相反的链接。
* **revTarget（字符串）**:目标。
* **sql（布尔）**:如果激活此属性(@sql=&quot;true&quot;)，则强制存储SQL元素，即使元素具有xml=&quot;true&quot;属性也是如此。
* **sqlname（字符串）**:表创建期间字段的名称。如果未指定“@sqlname”，则默认使用“@name”属性的值。 将架构写入表时，将根据字段类型自动添加前缀。
* **sqltable（字符串）**:对于架构的主要元素，此属性将覆盖默认生成的SQL表的名称。如果未指定“@sqltable”，则默认名称的结构将如下所示：命名空间（大写字母），后跟SrcSchema的值“@name”。
* **tableSpace（字符串）**:此属性允许您为表指定用于存储表空间的新数据(在根上有 `<element>`效)。
* **tableSpaceIndex（字符串）**:此属性允许您为表指定新的索引存储表空间(在根上有 `<element>`效)。
* **target(MNTOKEN)**:在表之间创建链接时接收目标架构的名称。此属性仅对“link”类型元素处于活动状态。
* **模板（字符串）**:此属性定义对由多个架 `<element>` 构共享的元素的引用。定义会自动复制到当前架构中。
* **translatedDefault（字符串）**:如果找到“@default”属性，则“@translatedDefault”将允许您重新定义表达式以匹配@default中定义的表达式，该表达式将由翻译工具收集（内部使用）。
* **translatedExpr（字符串）**:如果找到“@expr”属性，则“@translatedExpr”属性允许您重新定义与“@expr”中定义的属性匹配的表达式，该表达式将由翻译工具收集（内部使用）。
* **类型(MNTOKEN)**:定义存储在元素中的数据类型。

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

* **未绑定（布尔）**:如果激活了属性(unbound=&quot;true&quot;)，则该链接将声明为1-N基数的集合元素。
* **userEnum（字符串）**:接收“open”枚举的内部名称。枚举值可由用户在界面中定义。
* **xml（布尔）**:如果激活此选项，则元素中定义的所有值都将以XML形式存储在TEXT类型“mData”字段中。这意味着这些字段将不进行过滤或排序。
* **xmlChildren（布尔）**:强制存储每个子代(  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
