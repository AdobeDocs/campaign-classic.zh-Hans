---
product: campaign
title: 架构元素和属性 — 元素元素
description: 元素元素
feature: Schema Extension
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 0%

---

# 元素元素 {#element--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-4}

元素：==(属性 | 计算字符串 | dbindex | 默认 | 元素 | 帮助 | 加入 | 键 | sysFilter | translateddefault)

## 属性 {#attributes-4}

_operation (string)、advanced (boolean)、aggregate (string)、applicateIf (string)、autopk (boolean)、fellsTo (string)、convDate (string)、dataPolicy (string)、dataSource (string)、dbEnum (string)、defOnDuplicate (boolean)、default (string)、desc (string)、displayAsField (boolean)、doesNotDiff (boolean)、edit (string)、edit (string)、emptyKeyValue (string)、enum (string(string)、enum (string(string) target （字符串）、expr （字符串）、externalJoin （布尔值）、feature （字符串）、featureDate （布尔值）、filterPath （字符串）、folderLink （字符串）、folderModel （字符串）、folderProcess （字符串）、fullLoad （布尔值）、hierarchical （布尔值）、hierarchicalPath （字符串）、img （字符串）、inout （字符串）、完整性（字符串）、label （字符串）、labelSingular （字符串）、length （字符串）、localizable （布尔值）、name (布尔值（布尔值）、name (MNTOKEN)、NODbIndex （布尔值）、NOKeY （布尔值） 、OVERFLOWTABLE （布尔值）、PKSeQUENCE （字符串）、PKGStATUS （字符串）、REF （字符串）、REVAdVANCED （布尔值）、REVCarDINALITY （字符串）、REVDeSC （字符串）、REVExTERNALJoIN （布尔值）、REVIntEGRITY （字符串）、REVLABEL （字符串）、REVVisIBLEIf （字符串）、SQL （布尔值）、SQLNAME （字符串）、SQLTABLE （字符串）、TABLESpACE （字符串）、TABLESpACEIndex （字符串）、TARGET (MNING （字符串）、TARGET (目标(MNNN TOKEN)、TEMPLATE（字符串）、TEMPLATETABLE（布尔值）、TRANSLATEDDefAULT（字符串）、TRANSLATEDExPR（字符串）、TYPE(MNTOKEN)、unbound（布尔值）、user（布尔值）、userEnum（字符串）、visibleIf（字符串）、xml（布尔值）、xmlChildren（布尔值）

## 父项 {#parents-4}

`<srcschema>`

`<element>`

## 子项 {#children-4}

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

## 说明 {#description-4}

Adobe Campaign中有四种类型的`<element>`元素：

* 根`<element>` ：定义与架构匹配的SQL表的名称。
* 结构`<element>` ：定义一组`<element>`   或   `<attribute>`    元素。
* 链接`<element>` ：定义链接。 此元素必须包含“@type=link”属性。
* XML `<element>` ：定义文本类型“mData”字段。 此元素必须包含“@type=xml”属性。

## 属性说明 {#attribute-description-4}

* **_operation (string)**：定义在数据库中写入的类型。

  此属性主要用于扩展现成架构。

  可访问值包括：

   * “无”：仅和解。 这意味着Adobe Campaign将恢复元素，而不更新它，如果元素不存在则生成错误。
   * &quot;insertOrUpdate&quot;：使用insertion更新。 这意味着Adobe Campaign将更新元素，如果它不存在，则创建它。
   * &quot;insert&quot;： insertion. 这意味着Adobe Campaign将插入元素而不检查元素是否存在。
   * &quot;update&quot;：更新。 这意味着Adobe Campaign将更新元素，如果它不存在，则产生错误。
   * &quot;delete&quot;：删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔值）**：激活此选项(@advanced=&quot;true&quot;)后，您可以在可用于配置表单列表的可用字段列表中隐藏该属性。
* **聚合（字符串）**：允许您通过其他架构复制`<element>`的定义。 此属性接收格式为“namespace：name”的架构声明。
* **applicableIf （字符串）**：应用索引的条件。 此属性接收XTK表达式。
* **autopk （布尔值）**：如果激活此选项(autopk=&quot;true&quot;)，将自动定义唯一键。 此选项只能用于架构的主元素。 警告，Adobe Campaign仅保证生成的键是唯一的。 不能保证键值是连续和增量的。
* **dataPolicy （字符串）**：允许您对SQL字段中允许的值指定批准约束。 此属性的值为：

   * &quot;none&quot;：无值
   * &quot;smartCase&quot;：第一字母大写
   * &quot;lowerCase&quot;：全部为小写
   * &quot;upperCase&quot;：全部大写
   * &quot;email&quot;：电子邮件地址
   * &quot;phone&quot;：电话号码
   * &quot;identifier&quot;：标识符名称
   * &quot;resIdentifier&quot;：文件名

* **dbEnum （字符串）**：接收“已关闭”枚举的内部名称。 必须在`<srcschema>`中定义枚举值。
* **defOnDuplicate （布尔值）**：如果激活此属性，则在复制记录时，默认值(在@default中定义)将自动重新应用于记录。
* **默认（字符串）**：用于定义元素行为（调用函数，默认值）。 此属性接收XTK表达式。
* **desc （字符串）**：允许您插入元素的说明。 此描述将显示在界面的状态栏中。
* **displayAsField （布尔值）**：如果激活此属性，则“链接”类型`<element>`将作为字段显示在架构的树视图中（“结构”选项卡）。 这样，便可以将链接显示为本地字段，并在查询期间更改其行为。 当在查询的SELECT中找到元素时，将使用链接目标的值。 在查询的WHERE中找到元素时，将使用链接的基础键。
* **编辑（字符串）**：此属性指定将在链接到架构的表单中使用的输入类型。
* **枚举（字符串）**：接收链接到该字段的枚举的名称。 枚举可以插入到同一模式或远程模式中。
* **expr （字符串）**：此属性定义计算字段，表中没有存储任何定义。 它接收Xpath或XTK（字符串）表达式。
* **externalJoin （布尔值）**： “link”类型元素中的外部联接。
* **功能（字符串）**：定义特性字段：这些字段用于扩展现有表中的数据，但存储在附件表中。 接受的值包括：

   * “共享”：根据数据类型将内容存储在共享表中
   * &quot;dedicated&quot;：内容存储在专用表中

  SQL特性表是根据以下特性类型自动构建的：

   * 专用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 已共享：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  有两种类型的特性字段：简单字段，其中在特性上授权单个值；以及多选字段，其中特性链接到可能包含多个值的收集要素。

  在架构中定义特征时，此架构必须具有基于单个字段的主键（复合键未授权）。

* **featureDate （布尔值）**：链接到“@feature”特性字段的属性。 如果其值为“true”，则可让您了解该值的上次更新时间。
* **filterPath （字符串）**：此属性接收Xpath并允许您在字段上定义过滤器。
* **folderLink (string)**：此属性接收链接的名称，该链接允许您恢复包含实体的文件。
* **folderModel （字符串）**：定义启用实体存储的文件夹类型。 此属性仅在存在“@folderLink”时才定义。
* **folderProcess (string)**：定义实体模型实例的存储链接。 此属性仅在存在“@folderLink”时才定义。
* **fullLoad （布尔值）**：在表单中选择字段时，此属性强制显示表中的所有记录。
* **img （字符串）**：接收链接到元素的图像的路径。 此属性的值为“namespace：image name”类型。 例如：img=&quot;cus：myImage.jpg&quot;。 在物理上，必须将映像导入到应用程序服务器。
* **完整性（字符串）**：指向目标表的源表出现的参照完整性。

  可访问值包括：

   * &quot;define&quot;：如果实体是通过链接引用的，Adobe Campaign不会删除该实体
   * &quot;normal&quot;：删除源具体值会在目标具体值（默认模式）上初始化链接的键，这种类型的完整性会初始化所有外键
   * &quot;own&quot;：删除源具体值触发目标具体值的删除
   * &quot;owncopy&quot;：与&quot;own&quot;（如果删除）类似或重复发生次数（如果重复）
   * “中立”：不执行任何操作

* **标签（字符串）**：元素标签。
* **labelSingular （字符串）**：在界面的某些部分中使用的元素的标签（奇异形式）。
* **长度（字符串）**：最大值。 为“字符串”类型SQL字段的值授权的字符数。
* **可本地化（布尔值）**：如果激活此属性，则此属性会告知收集工具恢复“@label”属性的值以进行翻译（内部使用）。
* **name (MNTOKEN)**：与表的名称匹配的元素的内部名称。 “@name”属性的值必须较短，最好是英文，并符合链接到XML的命名约束。

  当架构写入数据库时，Adobe Campaign会自动将前缀添加到字段名称中。

   * &quot;i&quot;：&quot;integer&quot;类型的前缀。
   * &quot;d&quot;：&quot;double&quot;类型的前缀。
   * “s”：字符串类型的前缀。
   * &quot;ts&quot;：&quot;date&quot;类型的前缀。

  要以自主方式定义表的名称，您需要在主架构元素的定义中使用“@sqltable”属性。

* **noDbIndex （布尔值）**：用于指定不对元素编制索引。
* **ordered （布尔值）**：如果激活了属性(ordered=&quot;true&quot;)，Adobe Campaign会将元素声明序列保留在XML集合元素中。
* **pkSequence （字符串）**：接收用于计算自动增量键的序列的名称。 仅当在架构的根元素上定义了自动增量键时，才能使用此属性。
* **pkgStatus （字符串）**：在导出包期间，将考虑值作为此属性值的函数：

   * &quot;always&quot;：元素将始终存在
   * &quot;never&quot;：元素将永远不存在
   * &quot;default(or nothing)&quot;：除非元素是默认元素，或者不是内部字段并且与其他实例不兼容，否则将导出元素

* **ref （字符串）**：此属性定义对由多个架构共享的>element>元素的引用（定义分解）。 该定义将不会复制到当前架构中。
* **必需（布尔值）**：如果激活此属性(@required=&quot;true&quot;)，则接口中会高亮显示该字段。 字段的标签在表单中将为红色。
* **revAdvanced （布尔值）**：激活时，此属性指定相反链接是“高级”链接。
* **revCardinality （字符串）**：此属性定义两个表之间链接的基数。 它用于“链接”类型`<element>`。

  可能的值包括：

   * &quot;single&quot; ：简单的1-1类型链接
   * &quot;unbound&quot;： 1-N类型收藏集链接

  默认情况下，如果在创建链接期间未指定属性，则基数将为1-N。

* **revDesc （字符串）**：此属性接收链接到相反链接的描述。
* **revExternalJoin （布尔值）**：激活此属性后，您可以强制将外部联接置于相反的链接上。
* **revIntegrity （字符串）**：此属性定义目标架构上的完整性。 将授权与“@integrity”属性相同的值。 默认情况下，Adobe Campaign会为此属性提供“正常”值。
* **revLabel （字符串）**：相反链接的标签。
* **revLink （字符串）**：相反链接的名称。 如果值为“_NONE_”，则不会在目标架构中创建相反的链接。
* **revTarget （字符串）**：相反链接的目标。
* **sql （布尔值）**：如果激活了此属性(@sql=&quot;true&quot;)，则强制存储SQL元素，即使该元素具有xml=&quot;true&quot;属性。
* **sqlname (string)**：表创建期间字段的名称。 如果未指定“@sqlname”，则默认使用“@name”属性的值。 将架构写入表时，将根据字段类型自动添加前缀。
* **sqltable （字符串）**：对于架构的主元素，此属性会重载默认生成的SQL表的名称。 如果未指定“@sqltable”，则默认名称的结构将如下所示：命名空间（第一个字母大写），后跟SrcSchema的值“@name”。
* **tableSpace （字符串）**：此属性允许您为表指定新的数据存储表空间（在根`<element>`上有效）。
* **tableSpaceIndex (string)**：此属性允许您为表指定新的索引存储表空间（在根`<element>`上有效）。
* **目标(MNTOKEN)**：在表之间创建链接时接收目标架构的名称。 此属性仅对“链接”类型元素有效。
* **模板（字符串）**：此属性定义对由多个架构共享的`<element>`元素的引用。 该定义会自动复制到当前架构中。
* **translatedDefault （字符串）**：如果找到“@default”属性，“@translatedDefault”将允许您重新定义表达式以匹配@default中定义的表达式，该表达式将由翻译工具收集（内部使用）。
* **translatedExpr （字符串）**：如果找到“@expr”属性，“@translatedExpr”属性允许您重新定义与“@expr”中定义的表达式匹配的表达式，该表达式将由翻译工具（内部使用）收集。
* **type (MNTOKEN)**：定义存储在元素中的数据类型。

  可用类型列表：

   * 任何
   * 纸盒
   * blob
   * 布尔值
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * 日期
   * double
   * 枚举
   * float
   * html
   * int64
   * 链接
   * 长
   * 备忘
   * MNTOKEN
   * 百分比
   * 主密钥
   * 短
   * 字符串
   * time
   * timespan
   * uuid

* **未绑定（布尔值）**：如果激活了属性(unbound=&quot;true&quot;)，则该链接将声明为1-N基数的集合元素。
* **userEnum （字符串）**：接收“open”枚举的内部名称。 枚举值可由用户在界面中定义。
* **xml（布尔值）**：如果激活此选项，则元素中定义的所有值都将存储在TEXT类型“mData”字段的XML中。 这意味着这些字段将不进行筛选或排序。
* **xmlChildren （布尔值）**：强制存储每个子项(`<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`)
