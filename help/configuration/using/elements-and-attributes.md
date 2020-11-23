---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '6019'
ht-degree: 0%

---


# 元素和属性 {#elements-and-attributes}

编辑模式时，可使用基于源模式(xtk:srcSchema)的审批系统。 在使用“数据库结构更新……”更新数据库时，也会发现一些错误。 向导。

默认情况下，在Adobe Campaign模式中，所有布尔类型属性都为“false”。 要激活它们，您需要在模式中指定属性并将其值设置为“true”。

## `<attribute>` 元素 {#attribute--element}

### 内容模型 {#content-model}

attribute:==help

### 属性 {#attributes}

_operation(string)、advanced(boolean)、applicableIf(string)、autoIncrement(boolean)、tlasenTo(string)、dataPolicy(string)、dbEnum(string)、defOnDuplicate(boolean)、default(string)、desc(string)、expr(string)、feature(string)、fooleateatureateateateate(string)、featureDateDate)、img(string)、inout(string)、label(string)、length(string)、localizable(boolean)、name(boolean)、notNull(pkgStatus(string)、ref(string)、必需(boolean)、sql(boolean)、sqlDefault(string)、sqlname(string)、目标(string)、模板)、translatedDefault（字符串）、translatedExpr（字符串）、类型(MNTOKEN)、用户（布尔值）、userEnum（字符串）、visibleIf（字符串）、xml（布尔值）

### 父母 {#parents}

`<element>`

### 儿童 {#children}

`<help>`

### 说明{#description}

`<attribute>` elements允许您在数据库中定义字段。

### 使用和使用环境 {#use-and-context-of-use}

`<attribute>` 元素必须在元素中声 `<element>` 明。

元素在中定 `<attribute>` 义的顺序不 `<srcschema>` 会影响数据库中的字段创建顺序。 创建顺序将按字母顺序排列。

### 属性描述 {#attribute-description}

* **_operation(string)**:定义数据库中写入的类型。

   此属性主要用于扩展现成模式。

   可访问值包括：

   * “无”:和解。 这意味着Adobe Campaign将恢复元素，而不更新它，如果元素不存在，也将生成错误。
   * &quot;insertOrUpdate&quot;:插入更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会创建它。
   * “插入”:插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”:更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会生成错误。
   * “删除”:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔值）**:激活此选项(@advanced=&quot;true&quot;)后，可以在可用于在表单中配置列表的可用字段的列表中隐藏该属性。
* **applicableIf(string)**:此属性允许您使字段成为可选字段。 在 `<attribute>` 遵守约束时更新数据库时将考虑元素。 “applicableIf”接收XTK表达式。
* **autoIncrement（布尔值）**:如果激活了此选项，则该字段将变为计数器。 这使您能够增加一个值（大多数是ID）。 （外部使用）
* **属于（字符串）**:获取共享字段的表的名称和命名空间，并填充声明属性的模式。 (仅在a中使 `<schema>`用)。
* **dataPolicy(string)**:允许您对SQL或XML字段中允许的值指定批准约束。 此属性的值为：

   * “无”:无值
   * “smartCase”:大写字母大写
   * &quot;lowerCase&quot;:全部小写
   * “upperCase”:全部大写
   * “电子邮件”:电子邮件地址
   * “电话”:电话号码
   * &quot;标识符&quot;:标识符名称
   * &quot;resIdentifier&quot;:文件名

* **dbEnum（字符串）**:接收“已关闭”明细列表的内部名称。 明细列表值必须在中定义 `<srcschema>`。
* **defOnDuplicate（布尔值）**:如果激活了此属性，则当记录重复时，默认值（在@default中定义）会自动重新应用于记录。
* **default(string)**:允许您定义默认字段的值（调用函数、默认值）。 此属性接收XTK表达式。
* **desc(string)**:允许您插入属性的描述。 此说明显示在接口的状态栏中。
* **edit(string)**:此属性指定将在链接到模式的表单中使用的输入类型。
* **枚举(字符串**):接收链接到该字段的明细列表的名称。 明细列表可以插入到同一模式或远程模式。
* **expr(string)**:定义字段预计算表达式。 此属性接收Xpath或XTK表达式。
* **功能（字符串）**:定义特征字段：这些字段用于扩展现有表中的数据，但在附件表中存储。 接受的值为：

   * “共享”:内容按数据类型存储在共享表中
   * “专用”:内容存储在专用表中

   SQL特征表是根据特征类型自动构建的：

   * 专用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特征字段有两种类型：简单的oà¹在特征上授权单个值的字段，并且oà¹在多个选择字段中，特征链接到可能包含多个值的集合元素。

   在模式中定义特性时，此模式必须具有基于单个字段的主密钥（未授权复合密钥）。

* **featureDate（布尔值）**:链接到“@feature”特征字段的属性。 如果其值为“true”，则允许您查找该值上次更新的时间。
* **img(string)**:允许您为链接到字段的图像定义路径(命名空间+图像名称)(示例：img=&quot;cus:mypicture.jpg&quot;)。 实际上，映像必须导入到应用程序服务器。
* **label(string)**:链接到字段的标签，主要发往界面中的用户。 它可以避免命名限制。
* **length(string)**:max。 “字符串”类型SQL字段值的字符数。 如果未指定“@length”属性，Adobe Campaign将自动创建一个255个字符的字段。
* **localizable（布尔值）**:如果激活了该属性，则此属性会告知集合工具恢复“@label”属性的值以进行转换（内部使用）。
* **name(MNTOKEN)**:与表中字段名称匹配的属性的名称。 “@name”属性的值必须是短的（最好是英文），并且符合XML命名限制。

   将模式写入数据库时，前缀会按Adobe Campaign自动添加到字段名称：

   * “i”:“integer”类型的前缀。
   * “d”:“多次”类型的前缀。
   * “s”:字符串类型的前缀。
   * “ts”:“date”类型的前缀。

   要完全定义表中字段的名称，请在定义属性时使用“@sqlname”选项。

* **notNull（布尔值）**:允许您重新定义Adobe Campaign中与管理数据库中NULL记录相关的行为。 默认情况下，数字字段不为null，字符串和日期类型字段可为null。
* **pkgStatus(string)**:在包导出过程中，根据“@pkgStatus”的值考虑以下值：

   * “always”:始终存在
   * “从不”:永远
   * “默认（或无）”:除非该值是默认值，或者它不是与其他实例不兼容的内部字段，否则将导出该值。

* **ref(string)**:此属性定义对由多个模式共 `<attribute>` 享的元素的引用（定义因子化）。 定义未复制到当前模式。
* **必需（布尔值）**:如果激活了此属性(@required=&quot;true&quot;)，则在界面中突出显示该字段。 字段的标签将以红色显示在表单中。
* **sql（布尔值）**:如果激活了此属性(@sql=&quot;true&quot;)，它将强制存储SQL属性，即使包含该属性的元素具有xml=&quot;true&quot;属性时也是如此。
* **sqlDefault（字符串）**:如果激活了@notNull属性，则此属性允许您定义更新数据库时考虑的默认值。 如果在属性创建后添加了此属性，则即使对于新记录，模式行为也不会更改。 要更改模式并更新新记录的值，您需要删除并再次创建属性。
* **sqlname(string)**:的双曲余切值。 如果未指定@sqlname，则默认使用“@name”属性的值。 当模式写入数据库时，前缀会根据字段类型自动添加。
* **模板(字符串**):此属性定义对由多个模式共 `<attribute>` 享的元素的引用。 定义会自动复制到当前模式。
* **translatedDefault（字符串）**:如果找到“@default”属性，则“@translatedDefault”将允许您重新定义表达式以与@default中定义的属性匹配，该属性将由翻译工具收集（内部使用）。
* **translatedExpr（字符串）**:如果存在“@expr”属性，则“@translatedExpr”属性允许您重新定义与@expr中定义的表达式匹配的，该属性将由翻译工具收集（内部使用）。
* **type(MNTOKEN)**:字段类型。

   字段类型是通用的。 根据所安装的Adobe Campaign库类型，会将定义的类型更改为在结构更新期间所安装数据库特有的值。

   列表可用类型：

   * 任意
   * 宾
   * 斑点
   * 布尔
   * 字节
   * CDATA
   * datetime
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

   如果“@type”属性为空，则默认情况下，Adobe Campaign将将长度为100的字符串(STRING)链接到该字段。

   如果字段类型为STRING，且字段名称未由存在“@sqlname”属性指定，则数据库中字段的名称将自动前面有“s”。 此操作模式与INTEGER(i)、多次(d)和DATES(ts)类型字段类似。

* **userEnum（字符串）**:接收“open”明细列表的内部名称。 明细列表的值可由用户在界面中定义。
* **visibleIf(string)**:以XTK表达式的形式定义一个条件以显示或隐藏属性。

   >[!IMPORTANT]
   >
   >属性已隐藏，但仍可以访问其数据。

* **xml（布尔值）**:如果激活了此选项，则字段的值没有链接的SQL字段。 Adobe Campaign为记录存储创建文本类型“mData”字段。 这意味着不对这些字段进行筛选或排序。

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

XML字段的声明与“@datapolicy”:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

“@applicableIf”示例：仅当国家数量大于20时，才会创建“contains”属性。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

“共享”类型的“@feature”示例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

“专用”类型的“@feature”示例：

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```

## `<compute-string>` 元素 {#compute-string--element}

### 内容模型 {#content-model-1}

compute-string:==EMPTY

### 属性 {#attributes-1}

@expr

### 父母 {#parents-1}

`<element>`

### 儿童 {#children-1}

无

### 说明{#description-1}

元 `<compute-string>` 素允许您根据XTK表达式生成字符串，以根据多个值在界面中显示“内置”标签。

### 使用和使用环境 {#use-and-context-of-use-1}

如果未 `<compute-string>` 定义， `<compute-string>` 则默认情况下会输入元素，并在模式中输入主键的值。

### 属性描述 {#attribute-description-1}

* **expr(string)**:XTK和／或Xpath表达式

### 示例{#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

在收件人上计算的字符串结果：“John Doe(john.doe@aol.com)”:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` 元素 {#condition--element}

### 内容模型 {#content-model-2}

条件：==EMPTY

### 属性 {#attributes-2}

* @boolOperator（字符串）
* @enabledIf（字符串）
* @expr（字符串）

### 父母 {#parents-2}

`<sysfilter>`

### 儿童 {#children-2}

无

### 说明{#description-2}

此元素允许您定义筛选条件。

### 使用和使用环境 {#use-and-context-of-use-2}

一个 `<sysfiler>` 元素可包含多个过滤条件。

### 属性描述 {#attribute-description-2}

* **boolOperator(string)**:如果在同 `<conditions>` 一元素中定义了多 `<sysfilter>` 个元素，则此属性允许您合并它们。 默认情况下，元素之间的逻 `<condition>` 辑链接为“AND”。 “@boolOperator”属性允许您组合“OR”和“AND”类型链接。
* **enabledIf（字符串）**:条件激活测试。
* **expr(string)**:XTK表达式。

### 示例{#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` 元素 {#dbindex--element}

### 内容模型 {#content-model-3}

dbindex:==keyfield

### 属性 {#attributes-3}

* @_operation（字符串）
* @applicableIf（字符串）
* @label(string)
* @name(MNTOKEN)
* @unique（布尔值）

### 父母 {#parents-3}

`<element>`

### 儿童 {#children-3}

`<keyfield>`

### 说明{#description-3}

此元素允许您定义链接到表的索引。

### 使用和使用环境 {#use-and-context-of-use-3}

可以定义多个索引。 一个索引可以引用表的一个或多个字段。 索引声明通常遵循主模式元素的定义。

在中定义 `<keyfield>` 的元素的顺序 `<dbindex>` 很重要。 第一 `<keyfield>` 个必须是查询主要基于的索引标准。

数据库中索引的名称是通过连接表的名称和索引的名称来计算的。 例如：在创建索引查询期间，表名“Sample”、命名空间“Cus”、索引名“MyIndex”->索引字段的名称：&quot;CusSample_myIndex&quot;。

### 属性描述 {#attribute-description-3}

* **_operation(string)**:定义数据库中写入的类型。

   此属性主要用于扩展现成模式。

   可访问值包括：

   * “无”:和解。 这意味着Adobe Campaign将恢复元素，而不更新它，如果元素不存在，也将生成错误。
   * &quot;insertOrUpdate&quot;:插入更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会创建它。
   * “插入”:插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”:更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会生成错误。
   * “删除”:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **applicableIf(string)**:考虑索引的条件——接收XTK表达式。
* **label(string)**:索引标签。
* **name(MNTOKEN)**:唯一索引名称。
* **唯一（布尔值）**:如果激活了此选项(@unique=&quot;true&quot;)，则属性将保证索引在其整个字段中的唯一性。

### 示例{#examples-3}

在“id”字段上创建索引。 (元素上的“@unique”属性 `<dbindex>` 会触发在数据库(查询)中创建索引时添加“UNIQUE” SQL关键字。)

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

在“@mail”和“@phoneNumber”字段上创建复合索引：

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```

## `<element>` 元素 {#element--element}

### 内容模型 {#content-model-4}

元素：==(属性 | compute-string | dbindex |默认 |元素 |帮助 |加入 |密钥 | sysFilter | translatedDefault)

### 属性 {#attributes-4}

_operation(string)、advanced(boolean)、聚合(string)、appliableIf(string)、autopk(boolean)、tellessTo(string)、convDate(string)、dataPolicy(string)、dataSource(string)、dfOnDuplicate(boolean)、defaultic(stry)、desc(string)、desc(string(string)、desc(string)、displayAs字段（布尔）、doesNotSupportDiff（布尔）、edit(string)、emptyKeyValue(string)、enum(string)、enumImage(string)、expandSchemaTarget(string)、expr(string)、externalJoin(boolean)、功能(string)、featureDate(boolean)、filterPath(string)、folderLink(folderLinkstring)、folderModel(string)、folderProcess(string)、fullLoad(boolean)、hierarchical(boolean)、hierarchicalPath(string)、img(string)、inout(string)、完整性(string)、label(sing)、labelSingular(string)、localizable(boolean)、noDbIndex(boolean)、no键（布尔）、有序（布尔）、溢流表（布尔）、pkSequence（字符串）、pkgStatus（字符串）、ref（字符串）、必需（布尔）、revAdvanced（布尔）、revCardinality（字符串）、revExternalJoin（布尔）、revIntegrity（字符串）、revLabel（字符串）、rev链接（字符串）、revTarget（字符串）、revVisibleIf（字符串）、sql（布尔）、sqlname（字符串）、sqltable（字符串）、tableSpace（字符串）、tableSpaceIndex（字符串）、目标(MNTOKEN)、模板（字符串）、temporaryTable（布尔值）、translatedExpr（字符串）、type(MNTOKEN)、unbound(boolean)、user(boolean)、userEnum(string)、visibleIf(string)、xml(boolean)、xmlChildren(boolean)

### 父母 {#parents-4}

`<srcschema>`

`<element>`

### 儿童 {#children-4}

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

### 说明{#description-4}

Adobe Campaign中有四种 `<element>` 类型的元素：

* 根 `<element>` :定义与模式匹配的SQL表的名称。
* 结构 `<element>` :定义一组 `<element>` 或元 `<attribute>` 素。
* 链接 `<element>` :定义链接。 此元素必须包括“@type=link”属性。
* XML `<element>` :定义“mData”文本类型字段。 此元素必须包含“@type=xml”属性。

### 属性描述 {#attribute-description-4}

* **_operation(string)**:定义数据库中写入的类型。

   此属性主要用于扩展现成模式。

   可访问值包括：

   * “无”:和解。 这意味着Adobe Campaign将恢复元素，而不更新它，如果元素不存在，也将生成错误。
   * &quot;insertOrUpdate&quot;:插入更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会创建它。
   * “插入”:插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”:更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会生成错误。
   * “删除”:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔值）**:激活此选项(@advanced=&quot;true&quot;)后，可以在可用于在表单中配置列表的可用字段的列表中隐藏该属性。
* **聚合（字符串）**:允许您通过其他模式复 `<element>` 制定义。 此属性以“模式:name”的形式接收命名空间声明。
* **applicableIf(string)**:条件。 此属性接收XTK表达式。
* **autopk（布尔值）**:如果激活了此选项(autopk=&quot;true&quot;)，则会自动定义唯一键。 此选项只能用于模式的主元素。 警告，Adobe Campaign仅保证生成的密钥是唯一的。 不能保证密钥值是连续的和递增的。
* **dataPolicy(string)**:允许您对SQL字段中允许的值指定批准约束。 此属性的值为：

   * “无”:无值
   * “smartCase”:大写字母大写
   * &quot;lowerCase&quot;:全部小写
   * “upperCase”:全部大写
   * “电子邮件”:电子邮件地址
   * “电话”:电话号码
   * &quot;标识符&quot;:标识符名称
   * &quot;resIdentifier&quot;:文件名

* **dbEnum（字符串）**:接收“已关闭”明细列表的内部名称。 明细列表值必须在中定义 `<srcschema>`。
* **defOnDuplicate（布尔值）**:如果激活了此属性，则当记录重复时，默认值（在@default中定义）会自动重新应用于记录。
* **default(string)**:允许您定义元素行为（调用函数、默认值）。 此属性接收XTK表达式。
* **desc(string)**:允许您插入元素的说明。 此说明显示在接口的状态栏中。
* **displayAsField（布尔值）**:如果激活了此属性，则“链接”类 `<element>` 型将在模式的树视图（“结构”选项卡）中显示为一个字段。 这样，就可以将链接显示为本地字段，并在查询期间更改其行为。 在查询的SELECT中找到元素时，将使用链接目标的值。 在查询的WHERE中找到元素时，将使用链接的基础键。
* **edit(string)**:此属性指定将在链接到模式的表单中使用的输入类型。
* **枚举(字符串**):接收链接到该字段的明细列表的名称。 明细列表可以插入到同一模式或远程模式。
* **expr(string)**:此属性定义一个计算字段，该字段的定义不存储在表中。 它接收Xpath或XTK（字符串）表达式。
* **externalJoin（布尔值）**:“link”类型元素中的外部连接。
* **功能（字符串）**:定义特征字段：这些字段用于扩展现有表中的数据，但在附件表中存储。 接受的值为：

   * “共享”:内容按数据类型存储在共享表中
   * “专用”:内容存储在专用表中

   SQL特征表是根据特征类型自动构建的：

   * 专用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特征字段有两种类型：在特征上授权单个值的简单字段和在特征上链接到可能包含多个值的集合元素的多选择字段。

   在模式中定义特性时，此模式必须具有基于单个字段的主密钥（未授权复合密钥）。

* **featureDate（布尔值）**:链接到“@feature”特征字段的属性。 如果其值为“true”，则允许您查找该值上次更新的时间。
* **filterPath（字符串）**:此属性接收Xpath，并允许您在字段上定义过滤器。
* **folderLink(string)**:此属性接收链接的名称，该链接允许您恢复包含实体的文件。
* **folderModel(string)**:定义启用实体存储的文件夹类型。 仅当存在“@folderLink”时，才定义此属性。
* **folderProcess(string)**:定义实体模型实例存储位置的链接。 仅当存在“@folderLink”时，才定义此属性。
* **fullLoad（布尔值）**:此属性强制在表单的字段选择期间显示表中的所有记录。
* **img(string)**:接收链接到元素的图像的路径。 此属性的值为“命名空间：图像名称”类型。 例如：img=&quot;cus:myImage.jpg&quot;。 实际上，映像必须导入到应用程序服务器。
* **完整性（字符串）**:源表对目标表的出现的引用完整性。

   可访问值包括：

   * “定义”:Adobe Campaign不删除通过链接引用的实体
   * “正常”:删除源出现项将初始化目标出现时链接的键（默认模式），此类型的完整性将初始化所有外键
   * “拥有”:删除源事件会触发删除目标事件
   * “owncopy”:类似于“拥有”（删除时）或重复（复制时）
   * “中性”:什么也不做

* **label(string)**:元素标签。
* **labelSingular(string)**:在接口的某些部分中使用的元素的标签（单数形式）。
* **length(string)**:max。 为“字符串”类型SQL字段的值授权的字符数。
* **localizable（布尔值）**:如果激活了该属性，则此属性会告知集合工具恢复“@label”属性的值以进行转换（内部使用）。
* **name(MNTOKEN)**:与表名称匹配的元素的内部名称。 “@name”属性的值必须是短的，最好是英文，并且符合链接到XML的命名限制。

   将模式写入数据库时，前缀会按Adobe Campaign自动添加到字段名称。

   * “i”:“integer”类型的前缀。
   * “d”:“多次”类型的前缀。
   * “s”:字符串类型的前缀。
   * “ts”:“date”类型的前缀。

   要以自治方式定义表的名称，您需要在主模式元素的定义中使用“@sqltable”属性。

* **noDbIndex（布尔值）**:允许您指定元素将不进行索引。
* **有序（布尔值）**:如果属性被激活(ordered=&quot;true&quot;),Adobe Campaign会将元素声明序列保留在XML集合元素中。
* **pkSequence(string)**:接收要用于计算自动增量密钥的序列的名称。 仅当在模式的根元素上定义了自动增量键时，才能使用此属性。
* **pkgStatus(string)**:在包导出过程中，值将作为此属性值的函数考虑：

   * “always”:元素将始终存在
   * “从不”:元素永远不会出现
   * “默认（或无）”:除非元素是默认元素，或者它不是内部字段并且与其他实例不兼容，否则将导出该元素

* **ref(string)**:此属性定义对由多个模式共享的>element>元素的引用（定义因子化）。 定义未复制到当前模式。
* **必需（布尔值）**:如果激活了此属性(@required=&quot;true&quot;)，则在界面中突出显示该字段。 字段的标签将以红色显示在表单中。
* **revAdvanced（布尔值）**:激活后，此属性指定相反的链接为“高级”链接。
* **revCardinality（字符串）**:此属性定义两个表之间链接的基数。 它用于“链接”类型 `<element>`。

   可能的值有：

   * “single”:简单的1-1类型链接
   * “未绑定”:1-N类型集合链接

   默认情况下，如果在创建链接时未指定属性，则基数将为1-N。

* **revDesc（字符串）**:此属性接收链接到相反链接的描述。
* **revExternalJoin（布尔值）**:激活后，此属性允许您在相反的链接上强制使用外部连接。
* **revIntegrity(string)**:此属性定义目标模式的完整性。 授权的值与“@integrity”属性相同。 默认情况下，Adobe Campaign为此属性提供“正常”值。
* **revLabel（字符串）**:相反链接的标签。
* **revLink（字符串）**:相反链接的名称。 如果值为“_NONE_”，则不会在目标模式中创建相反的链接。
* **revTarget（字符串）**:目标相反的链接。
* **sql（布尔值）**:如果激活了此属性(@sql=&quot;true&quot;)，则会强制存储SQL元素，即使元素具有xml=&quot;true&quot;属性也是如此。
* **sqlname(string)**:表创建期间字段的名称。 如果未指定“@sqlname”，则默认使用“@name”属性的值。 将模式写入表时，前缀会根据字段类型自动添加。
* **sqltable(string)**:对于模式的主元素，此属性会过载默认生成的SQL表的名称。 如果未指定“@sqltable”，则默认名称的结构将如下所示：命名空间（首字母大写），后跟SrcSchema &quot;@name&quot;的值。
* **tableSpace(string)**:此属性允许您为表指定存储表空间的新数据(在根上有 `<element>`效)。
* **tableSpaceIndex（字符串）**:此属性允许您为表指定新的索引存储表空间(在根上有 `<element>`效)。
* **目标(MNTOKEN)**:在表之间创建链接时接收目标模式的名称。 此属性仅对“链接”类型元素处于活动状态。
* **模板(字符串**):此属性定义对由多个模式共 `<element>` 享的元素的引用。 定义会自动复制到当前模式。
* **translatedDefault（字符串）**:如果找到“@default”属性，则“@translatedDefault”将允许您重新定义表达式以与@default中定义的属性匹配，该属性将由翻译工具收集（内部使用）。
* **translatedExpr（字符串）**:如果找到“@expr”属性，则“@translatedExpr”属性允许您重新定义与“@expr”中定义的属性匹配的表达式，该属性将由转换工具收集（内部使用）。
* **type(MNTOKEN)**:定义元素中存储的数据类型。

   列表可用类型：

   * 任意
   * 宾
   * 斑点
   * 布尔
   * 字节
   * CDATA
   * datetime
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

* **未绑定（布尔值）**:如果属性已激活(unboind=&quot;true&quot;)，则链接将声明为1-N基数的集合元素。
* **userEnum（字符串）**:接收“open”明细列表的内部名称。 明细列表值可由用户在界面中定义。
* **xml（布尔值）**:如果激活了此选项，则元素中定义的所有值都以XML格式存储在TEXT类型“mData”字段中。 这意味着这些字段将不进行筛选或排序。
* **xmlChildren(boolean)**:强制存储每个孩子( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` 元素 {#enumeration--element}

### 内容模型 {#content-model-5}

明细列表:==(help| value)

### 属性 {#attributes-5}

* @basetype（字符串）
* @default（字符串）
* @desc（字符串）
* @label(string)
* @name（字符串）
* @template(string)

### 父母 {#parents-5}

`<srcschema>`

### 儿童 {#children-5}

* `<help>`
* `<value>`

### 说明{#description-5}

此元素使我们能够定义值明细列表。 明细列表属于在中定义的模式，但可通过其他模式访问。

### 使用和使用环境 {#use-and-context-of-use-4}

明细列表在模式的开始下定义（在定义主要元素之前）。

### 属性描述 {#attribute-description-5}

* **basetype(string)**:存储在明细列表中的值的类型。

   列表可用类型：

   * 任意
   * 宾
   * 斑点
   * 布尔
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * 日期
   * DOMDocument
   * DOMElement
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

* **default(string)**:默认值。 默认值也可以是明细列表中定义的值之一。
* **desc(string)**:明细列表描述。
* **label(string)**:明细列表标签。
* **name(string)**:明细列表的内部名称。
* **模板(字符串**):此属性定义对由多个模式共 `<enumeration>` 享的元素的引用。 定义会自动复制到当前模式。

### 示例{#examples-4}

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

具有默认值的明细列表的定义：

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` 元素 {#help--element}

### 内容模型 {#content-model-6}

help:==EMPTY

### 属性 {#attributes-6}

无

### 父母 {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### 儿童 {#children-6}

无

### 说明{#description-6}

通过此元素可以描述 `<element>` 或元 `<attribute>` 素。 它只能包含文本，并以XML格式存储在数据库中。

### 属性描述 {#attribute-description-6}

此元素没有属性。

### 示例{#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` 元素 {#join--element}

### 内容模型 {#content-model-7}

join:==EMPTY

### 属性 {#attributes-7}

* @dstFilterExpr（字符串）
* @xpath-dst（字符串）
* @xpath-src（字符串）

### 父母 {#parents-7}

`<element>`

### 儿童 {#children-7}

无

### 说明{#description-7}

允许您定义在SQL表之间创建连接的字段。

### 使用和使用环境 {#use-and-context-of-use-5}

元 `<join>` 素仅在父元素类型为“ `<element>` 链接”时才可使用。 这意味着父元素必须声明“@type=link”属性。

无需在元素中指定远程表的名称和命名空间 `<join>` 符。 它们需要在父项中指定 `<element>`。

根据惯例，链接在模式末尾定义。

如果 `<join>` 定义链接类型元素时未指定该元素，则链接将自动放置在两个表的主键上。

### 属性描述 {#attribute-description-7}

* **dstFilterExpr（字符串）**:此属性允许您限制远程表中合格值的数量。
* **xpath-dst（字符串）**:此属性接收Xpath（远程表的@name属性）。
* **xpath-src（字符串）**:此属性接收Xpath(当前模式中的@name属性)。

### 示例{#examples-6}

在当前表的“email”字段与远程表的“@compagny-id”字段之间的链接：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根据必须包含“EN”值的“@country”字段的内容，筛选指向“cus:Country”表的链接：

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` 元素 {#key--element}

### 内容模型 {#content-model-8}

key:==keyfield

### 属性 {#attributes-8}

* @allowEmptyPart（布尔值）
* @applicableIf（字符串）
* @internal（布尔值）
* @label(string)
* @name(MNTOKEN)
* @noDbIndex（布尔值）

### 父母 {#parents-8}

`<element>`

### 儿童 {#children-8}

`<keyfield>`

### 说明{#description-8}

此元素允许您定义用于标识表中记录的键。

表必须至少具有一个键。

### 使用和使用环境 {#use-and-context-of-use-6}

通常，键在模式的主元素和索引之后声明。

如果密钥包含多个字段（即多个子字段），则该密钥称为 `<keyfield>` 复合。 请勿使用复合键定义主键。

如果模式的主元素包含“@autopk=true”属性，则主键是唯一的。 每个模式只能有一个主键。

保留前1000个标识符，因此如果需要为键定义一系列值，开始为1000。

### 属性描述 {#attribute-description-8}

* **allowEmptyPart（布尔值）**:在组合键的情况下，如果激活了此属性，则如果其至少一个键不为空，则将其键视为有效。 如果出现这种情况，则空概念值为“0”（布尔值或所有类型的数值数据）。 默认情况下，需要输入组成复合键的所有键。
* **applicableIf(string)**:此属性允许您使键成为可选项。 它定义将应用密钥定义的条件。 此属性接收XTK表达式。
* **内部（布尔值）**:如果激活了此属性，则此属性会告知Adobe Campaign该密钥是主密钥。
* **label(string)**:键的标签。
* **name(MNTOKEN)**:密钥的内部名称。
* **noDbIndex（布尔值）**:如果激活了该字段(noDbIndex=&quot;true&quot;)，则将不对与该键匹配的字段编制索引。

### 示例{#examples-------}

授权“@expr”或“别名”字段为空的复合密钥的声明：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

在STRING类型的“Name”字段中声明主键，并 `<srcschema>` 在匹配的SQL查询中：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` 元素 {#keyfield--element}

### 内容模型 {#content-model-9}

keyfield:==EMPTY

### 属性 {#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

### 父母 {#parents-9}

`<key>`  ,  `<dbindex />`

### 儿童 {#children-9}

无

### 说明{#description-9}

此元素定义要集成到索引或键中的字段。

### 属性描述 {#attribute-description-9}

* **xlink(MNTOKEN)**:允许您自动引用在关系表（N-N链接）的连接中定义的外键。
* **xpath(MNTOKEN)**:对元素的索引或键的定 `<attribute>` 义。 此属性接收一个Xpath，它定义模式属性的路径，该属性定义键或索引。

### 示例{#examples-}

在索引中选择“sName”字段，该索引的Xpath位于“@name”上：

```
<keyfield xpath="@name"/>
```

## `<method>` 元素 {#method--element}

### 内容模型 {#content-model-10}

方法：==(帮助 |参数)

### 属性 {#attributes-10}

* @_operation（字符串）
* @access(string)
* @const（布尔值）
* @hidden（布尔值）
* @label(string)
* @library(string)
* @name(MNTOKEN)
* @pkonly（布尔值）
* @static（布尔值）

### 父母 {#parents-10}

`<methods>`  ,  `<interface />`

### 儿童 {#children-10}

* `<help>`
* `<parameters>`

### 说明{#description-10}

此元素允许您定义SOAP方法。

### 使用和使用环境 {#use-and-context-of-use-7}

SOAP方法启用应用程序进程。

声明新方法（非本机）时必须使用“@library”:命名空间和用于库的名称与声明所在的命名空间和模式的名称无关。

### 属性描述 {#attribute-description-10}

* **access(string)**:此属性定义使用方法的访问控制。 如果此属性缺失，则标识是必填的。 可用值包括：“anonymous”、“admin”和“sql”。
* **const（布尔值）**:如果激活了该属性，则此属性意味着声明的方法将更改实体
* **label(string)**:方法的标签。
* **库（字符串）**:此方法不是应用程序固有的。 此属性采用找到方法定义的方法库的值(nms:mylibrary.js)。
* **name(MNTOKEN)**:唯一方法名称。
* **静态（布尔值）**:如果激活了此属性，则该方法被视为自治方法，调用该属性时必须为该方法指定所有参数。

### 示例{#examples-7}

“订阅”现成方法的定义：

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

## `<methods>` 元素 {#methods--element}

### 内容模型 {#content-model-11}

方法：==方法

### 属性 {#attributes-11}

无

### 父母 {#parents-11}

`<srcschema>`

### 儿童 {#children-11}

方法

### 说明{#description-11}

此元素允许您定义元 `<method>` 素。 声明方法是强制的。

### 属性描述 {#attribute-description-11}

此元素没有属性。

### 示例{#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` 元素 {#param--element}

### 内容模型 {#content-model-12}

param:==帮助

### 属性 {#attributes-12}

* @_operation（字符串）
* @desc（字符串）
* @enum（字符串）
* @inout（字符串）
* @label(string)
* @localizable（字符串）
* @name(MNTOKEN)
* @命名空间(MNTOKEN)
* @type（字符串）

### 父母 {#parents-12}

`<parameters>`

### 儿童 {#children-12}

`<help>`

### 说明{#description-12}

此元素允许您定义用于调用SOAP方法的参数。

### 属性描述 {#attribute-description-12}

* **desc(string)**:与元素相关的 `<param>` 说明。
* **inout（字符串）**:此属性定义参数是否位于SOAP调用的输入（输入）或输出（输出）。 如果未指定此属性，则输入默认参数(&quot;@inout=in&quot;)。
* **label(string)**: `<param>` 标签
* **localizable（字符串）**:如果激活了该属性，则此属性会告知集合工具恢复“@label”属性的值以进行转换（内部使用）。
* **name(MNTOKEN)**:内部名称 `<param>`
* **type(string)**:此属性定义元素的类 `<param>` 型

   列表可用类型：

   * 任意
   * 宾
   * 斑点
   * 布尔
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * 日期
   * DOMDocument
   * DOMElement
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

### 示例{#examples-9}

字符串类型“serviceName”入站设置的定义：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` 元素 {#parameters--element}

### 内容模型 {#content-model-13}

参数：==param

### 属性 {#attributes-13}

无

### 父母 {#parents-13}

`<method>`

### 儿童 {#children-13}

`<param>`

### 说明{#description-13}

此元素定义一组 `<parameter>` 元素。

### 使用和使用环境 {#use-and-context-of-use-8}

此元素是必需的，即使对于元素 `<param>` 的单个子元素 `<method>` 也是。

### 属性描述 {#attribute-description-13}

无

### 示例{#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` 元素 {#srcschema--element}

### 内容模型 {#content-model-14}

srcSchema:==(attribute |创建者 |数据 |元素 |明细列表 |帮助 |界面 |方法 |修改者)

### 属性 {#attributes-14}

created(datetime)、createdBy-id(long)、desc(string)、entitySchema(string)、extendedSchema(string)、img(string)、implements(string)、label(string)、lastModified(datetime)、lastModified(boolean)、mappingType(string)、modifiedBy-id(long)、name(string(string)、命名空间(string)、)、useRecycleBin（布尔）、视图（布尔）、xtkschema（字符串）

### 父母 {#parents-14}

无

### 儿童 {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### 说明{#description-14}

是 `<srcschema>` 模式的根元素。 它是定义模式的输入点。

### 使用和使用环境 {#use-and-context-of-use-9}

模式演示在“关于 [模式参考](../../configuration/using/about-schema-reference.md) ”和 [模式结构中可用](../../configuration/using/schema-structure.md)。

### 属性描述 {#attribute-description-14}

* **created(datetime)**:此属性提供有关创建模式的日期和时间的信息。 它有一个“日期时间”表单。 显示的值取自服务器。 时间以UTC格式显示。
* **createdBy-id（长）**:是创建模式的运算符的标识符。
* **desc(string)**:模式描述
* **entitySchema（字符串）**:基本模式(默认情况下，Adobe Campaign基于哪些语法和批准：xtk:srcSchema)。 保存当前模式时，Adobe Campaign将使用@xtkschema属性中声明的模式批准其语法。
* **extendedSchema（字符串）**:接收当前模式扩展所基于的现成模式的名称。 表单为“命名空间：名称”。
* **img(string)**:链接到模式的图标(可在模式创建向导中定义)。
* **label(string)**:模式标签。
* **labelSingular(string)**:标签（单数），用于在界面中显示。
* **lastModified(datetime)**:此属性提供有关上次修改的日期和时间的信息。 它有一个“日期时间”表单。 显示的值取自服务器。 时间以UTC格式显示。
* **库（布尔值）**:将模式用作库而非实体。 因此，由于“@ref”和“@template”属性，此模式可能被其他模式引用。
* **mappingType(string)**:

   * &quot;sql&quot;:数据库映射
   * &quot;textFile&quot;:文本文件映射
   * &quot;xmlFile&quot;:XML格式文本文件映射
   * &quot;binaryFile&quot;:二进制文件映射

* **modifiedBy-id（长）**:匹配更改模式的运算符的标识符。
* **name(string)**:唯一模式名。
* **命名空间（字符串）**:命名空间模式(默认：nms, xtk, nl)。 为项目创建新模式时，建议您使用专用命名空间。
* **useRecycleBin（布尔值）**:在应用程序中激活垃圾桶功能。 删除的记录将放在垃圾桶中，最后删除。 此函数仅在“投放”模式下可用。
* **视图（布尔值）**:如果激活(@视图=&quot;true&quot;)，则模式将用作视图。 模式库结构更新向导将不考虑数据。 此选项主要用于引用外部表。
* **xtkschema(string)**:定义模式语法的模式的名称（默认情况下为xtk:srcSchema）。

### 示例{#examples-11}

`<srcschema>` “nms:投放”元素开箱即用模式

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` 元素 {#sysfilter--element}

### 内容模型 {#content-model-15}

sysFilter:==condition

### 属性 {#attributes-15}

无

### 父母 {#parents-15}

`<element>`

### 儿童 {#children-15}

`<condition>`

### 说明{#description-15}

此元素允许您定义筛选器。

### 属性描述 {#attribute-description-15}

此元素没有属性。

### 示例{#examples-12}

具有@name属性条件的过滤器的定义：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` 元素 {#value--element}

### 内容模型 {#content-model-16}

value:==帮助

### 属性 {#attributes-16}

* @applicableIf（字符串）
* @desc（字符串）
* @enabledIf（字符串）
* @img（字符串）
* @label(string)
* @name（字符串）
* @value(string)

### 父母 {#parents-16}

`<enumeration>`

### 儿童 {#children-16}

`<help>`

### 说明{#description-16}

此元素允许您定义存储在明细列表中的值。

### 属性描述 {#attribute-description-16}

* **applicableIf(string)**:此属性允许您使明细列表值成为可选值。 它接收XTK表达式。
* **desc(string)**:明细列表值的描述。
* **enabledIf（字符串）**:激活明细列表值的条件。
* **img(string)**:链接到“明细列表:image_name”表单中的命名空间的图像。 映像必须导入到应用程序服务器上。
* **label(string)**:明细列表值的标签。
* **name(string)**:明细列表值的内部名称。
* **value(string)**:明细列表值的值。 值类型根据明细列表类型定义。 如果明细列表为字符串类型，则只能包含字符串类型值。

### 示例{#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
