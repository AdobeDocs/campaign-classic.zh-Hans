---
title: 元素和属性
seo-title: 元素和属性
description: 元素和属性
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f9b3508fee3b441752648258b1bc9d5d2b919791

---


# 元素和属性 {#elements-and-attributes}

在编辑架构时，可以使用基于源架构(xtk:srcSchema)的审批系统。 使用“数据库结构更新……”更新数据库时，也会发现一些错误。 的子菜单。

默认情况下，在Adobe Campaign架构中，所有布尔类型属性都为“false”。 要激活它们，您需要在架构中指定属性并将其值设置为“true”。

## `<attribute>` 元素 {#attribute--element}

### 内容模型 {#content-model}

attribute:===help

### 属性 {#attributes}

_operation(string), advanced(boolean), applicableIf(string), autoIncrement(boolean), lessTo(string), dataPolicy(string), dbEnum(string), defOnDuplicate(boolean), default(string), desc(string), edit(string), enum(string(string), enum(string), expr(string(string), efature(string), feature(string), string), featureDateDate), feature)、img(string)、inout(string)、label(string)、length(string)、localizable(boolean)、name(boolean)、notNull(boolean)、pkgStatus(string)、ref(string)、required(boolean)、sqlDefault(string)、sqltable(string)、target(stroken)、template(string), translatedDefault（字符串）, translatedExpr（字符串），类型(MNTOKEN)，用户（布尔值）, userEnum（字符串）, visibleIf（字符串）, xml（布尔值）

### 父母 {#parents}

`<element>`

### 儿童 {#children}

`<help>`

### 说明 {#description}

`<attribute>` 元素允许您在数据库中定义字段。

### 使用和使用环境 {#use-and-context-of-use}

`<attribute>` 元素必须在元素中声 `<element>` 明。

元素在中定 `<attribute>` 义的顺序不影 `<srcschema>` 响数据库中的字段创建顺序。 创建序列将按字母顺序排列。

### 属性描述 {#attribute-description}

* **_operation(string)**:定义在数据库中写入的类型。

   此属性主要用于扩展现成架构。

   可访问的值有：

   * “none”:独自和解。 这意味着Adobe Campaign将恢复元素，而不更新元素，或在元素不存在时生成错误。
   * “insertOrUpdate”:插入时更新。 这意味着Adobe Campaign将更新元素或在元素不存在时创建它。
   * “插入”:插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”:更新。 这意味着，如果元素不存在，Adobe Campaign将更新该元素或生成错误。
   * “删除”:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **advanced(boolean)**:当激活此选项(@advanced=&quot;true&quot;)时，它允许您隐藏可用字段列表中的属性，这些字段可用于在表单中配置列表。
* **applicableIf(string)**:此属性允许您将字段设为可选字段。 在 `<attribute>` 满足约束时更新数据库时，将考虑元素。 “appliableIf”接收XTK表达式。
* **autoIncrement(boolean)**:如果激活了此选项，则字段将变为计数器。 这使您能够增加一个值（大多数是ID）。 （外部使用）
* **tellesTo(string)**:获取共享字段的表的名称和命名空间，并在声明属性的架构中填充该架构。 (仅在a中使 `<schema>`用)。
* **dataPolicy(string)**:允许您指定对SQL或XML字段中允许的值的批准约束。 此属性的值为：

   * “none”:无值
   * “smartCase”:大写字母
   * “lowerCase”:全小写
   * “upperCase”:全大写
   * “电子邮件”:电子邮件地址
   * “电话”:电话号码
   * “标识符”:标识符名称
   * &quot;resIdentifier&quot;:文件名

* **dbEnum（字符串）**:接收“已关闭”枚举的内部名称。 必须在中定义枚举值 `<srcschema>`。
* **defOnDuplicate(boolean)**:如果激活了此属性，则当记录重复时，默认值（在@default中定义）会自动重新应用于记录。
* **default(string)**:允许您定义默认字段的值（调用函数，默认值）。 此属性接收XTK表达式。
* **desc(string)**:允许您插入属性的描述。 此说明显示在界面的状态栏中。
* **edit(string)**:此属性指定将在链接到架构的表单中使用的输入类型。
* **enum(string)**:接收链接到字段的枚举的名称。 可以将枚举插入同一架构或远程架构中。
* **expr(string)**:定义字段预计算表达式。 此属性接收Xpath或XTK表达式。
* **feature(string)**:定义特征字段：这些字段用于扩展现有表中的数据，但存储在附件表中。 接受的值为：

   * “共享”:内容按数据类型存储在共享表中
   * “专用”:内容存储在专用表中
   SQL特征表是根据以下特征类型自动构建的：

   * 专用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   有两种类型的特征字段：简单的oà¹其中在特征上授权单个值的字段，并且oà¹多个选择字段，其中特征链接到可能包含多个值的集合元素。

   在架构中定义特征时，此架构必须具有基于单个字段的主键（未授权复合键）。

* **featureDate（布尔值）**:属性链接到“@feature”特征字段。 如果其值为“true”，则允许您查找该值上次更新的时间。
* **img(string)**:允许您为链接到字段的图像定义路径（命名空间+图像名称）(示例：img=&quot;cus:mypicture.jpg&quot;)。 实际上，映像必须导入到应用程序服务器。
* **label(string)**:链接到字段的标签，大多发往界面中的用户。 它可以避免命名限制。
* **length(string)**:max. “字符串”类型SQL字段的值的字符数。 如果未指定“@length”属性，Adobe Campaign将自动创建一个255个字符的字段。
* **localizable（布尔值）**:如果激活了该属性，则此属性会告知集合工具恢复“@label”属性的值以进行转换（内部使用）。
* **name(MNTOKEN)**:与表中字段名称匹配的属性的名称。 “@name”属性的值必须很短（最好是英文），并且符合XML命名限制。

   将架构写入数据库时，前缀由Adobe Campaign自动添加到字段名称：

   * “i”:“integer”类型的前缀。
   * “d”:“double”类型的前缀。
   * “s”:字符串类型的前缀。
   * “ts”:“date”类型的前缀。
   要完全定义表中字段的名称，请在定义属性时使用“@sqlname”选项。

* **notNull(boolean)**:允许您重新定义Adobe Campaign在管理数据库中空记录方面的行为。 默认情况下，数字字段不为null，字符串和日期类型字段可以为null。
* **pkgStatus(string)**:在包导出过程中，会根据“@pkgStatus”的值考虑以下值：

   * “always”:始终存在
   * “never”:永远
   * “default（或nothing）”:除非该值是默认值，或者它不是与其他实例不兼容的内部字段，否则将导出该值。

* **ref(string)**:此属性定义对由多个架构共享 `<attribute>` 的元素的引用（定义因子化）。 定义不会复制到当前架构中。
* **必需（布尔值）**:如果激活了此属性(@required=&quot;true&quot;)，则该字段将在界面中高亮显示。 字段的标签将在表单中为红色。
* **sql（布尔值）**:如果激活了此属性(@sql=&quot;true&quot;)，则会强制存储SQL属性，即使包含该属性的元素具有xml=&quot;true&quot;属性时也是如此。
* **sqlDefault（字符串）**:如果激活了@notNull属性，此属性允许您定义更新数据库时考虑的默认值。 如果在属性创建之后添加了此属性，则即使对于新记录，架构行为也不会更改。 要更改架构并更新新记录的值，您需要删除并再次创建属性。
* **sqlname(string)**:的双曲余切值。 如果未指定@sqlname，则默认情况下使用“@name”属性的值。 在数据库中写入架构时，前缀会根据字段的类型自动添加。
* **template(string)**:此属性定义对由多个架构共 `<attribute>` 享的元素的引用。 定义会自动复制到当前架构中。
* **translatedDefault（字符串）**:如果找到&quot;@default&quot;属性，则&quot;@translatedDefault&quot;将允许您重新定义表达式以与@default中定义的表达式匹配，该表达式将由翻译工具收集（内部使用）。
* **translatedExpr(string)**:如果存在“@expr”属性，则“@translatedExpr”属性允许您重新定义表达式以匹配@expr中定义的表达式，该表达式将由翻译工具收集（内部使用）。
* **type(MNTOKEN)**:字段类型。

   字段类型是通用的。 根据所安装数据库的类型，Adobe Campaign会将定义的类型更改为在结构更新期间所安装数据库特有的值。

   可用类型列表：

   * 任意
   * 宾
   * 斑点
   * 布尔值
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * 双倍
   * enum
   * 浮动
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
   * uid
   如果“@type”属性留空，则默认情况下，Adobe Campaign将将长度为100的字符串(STRING)链接到字段。

   如果字段类型为STRING，且字段名称未由“@sqlname”属性指定，则数据库中字段的名称将自动在“s”前面加一个“s”。 此操作模式与INTEGER(i)、DOUBLE(d)和DATES(ts)类型字段类似。

* **userEnum（字符串）**:接收“open”枚举的内部名称。 枚举的值可由用户在界面中定义。
* **visibleIf(string)**:以XTK表达式的形式定义一个条件以显示或隐藏属性。

   >[!CAUTION]
   >
   >该属性是隐藏的，但仍可访问其数据。

* **xml（布尔值）**:如果激活了此选项，则字段的值没有链接的SQL字段。 Adobe Campaign会为记录存储创建文本类型“mData”字段。 这意味着不会对这些字段进行筛选或排序。

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

示例：仅当国家／地区数量大于20时，才会创建“contains”属性。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

“@feature”类型为“shared”的示例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

“@feature”类型为“dedicated”的示例：

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

### 说明 {#description-1}

元 `<compute-string>` 素允许您根据XTK表达式生成字符串，以根据多个值在界面中显示“内置”标签。

### 使用和使用环境 {#use-and-context-of-use-1}

如果未 `<compute-string>` 定义，则默认 `<compute-string>` 情况下会输入元素，并在架构中输入主键的值。

### 属性描述 {#attribute-description-1}

* **expr(string)**:XTK和／或Xpath表达式

### 示例 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

在收件人上计算的字符串的结果：“John Doe(john.doe@aol.com)”:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` 元素 {#condition--element}

### 内容模型 {#content-model-2}

condition:==EMPTY

### 属性 {#attributes-2}

* @boolOperator（字符串）
* @enabledIf（字符串）
* @expr（字符串）

### 父母 {#parents-2}

`<sysfilter>`

### 儿童 {#children-2}

无

### 说明 {#description-2}

此元素允许您定义筛选条件。

### 使用和使用环境 {#use-and-context-of-use-2}

一个 `<sysfiler>` 元素可以包含多个过滤条件。

### 属性描述 {#attribute-description-2}

* **boolOperator(string)**:如果在同 `<conditions>` 一元素中定义了多个元 `<sysfilter>` 素，则通过此属性可以合并它们。 默认情况下，元素之间的逻辑链 `<condition>` 接为“AND”。 “@boolOperator”属性允许您组合“OR”和“AND”类型链接。
* **enabledIf（字符串）**:条件激活测试。
* **expr(string)**:XTK表达式。

### 示例 {#examples-2}

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
* @label（字符串）
* @name(MNTOKEN)
* @unique（布尔值）

### 父母 {#parents-3}

`<element>`

### 儿童 {#children-3}

`<keyfield>`

### 说明 {#description-3}

通过此元素，可以定义链接到表的索引。

### 使用和使用环境 {#use-and-context-of-use-3}

可以定义多个索引。 一个索引可以引用表的一个或多个字段。 索引声明通常遵循主架构元素的定义。

在中定义的元 `<keyfield>` 素的顺序非 `<dbindex>` 常重要。 第一 `<keyfield>` 个必须是查询所基于的索引标准。

数据库中索引的名称是通过连接表的名称和索引的名称来计算的。 例如：在创建索引查询期间，表名“Sample”、命名空间“Cus”、索引名“MyIndex”->索引字段的名称：“CusSample_myIndex”。

### 属性描述 {#attribute-description-3}

* **_operation(string)**:定义在数据库中写入的类型。

   此属性主要用于扩展现成架构。

   可访问的值有：

   * “none”:独自和解。 这意味着Adobe Campaign将恢复元素，而不更新元素，或在元素不存在时生成错误。
   * “insertOrUpdate”:插入时更新。 这意味着Adobe Campaign将更新元素或在元素不存在时创建它。
   * “插入”:插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”:更新。 这意味着，如果元素不存在，Adobe Campaign将更新该元素或生成错误。
   * “删除”:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **applicableIf(string)**:考虑索引的条件——接收XTK表达式。
* **label(string)**:索引标签。
* **name(MNTOKEN)**:唯一索引名称。
* **唯一（布尔值）**:如果激活了此选项(@unique=&quot;true&quot;)，则属性将确保索引在其整个字段中的唯一性。

### 示例 {#examples-3}

在“id”字段上创建索引。 (元素上的“@unique”属性 `<dbindex>` 在数据库（查询）中创建索引时触发添加“UNIQUE” SQL关键字。)

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

element:==(attribute| compute-string| dbindex|默认|元素|帮助|加入|密钥| sysFilter| translatedDefault)

### 属性 {#attributes-4}

_operation(string), advanced(boolean), aggregate(string), applicableIf(string), autopk(boolean), lessTo(string), convDate(string),dataPolicy(string),dataSource(string), dbEnum(string), defaultOnDuplicate(bleateate), default(streat(stre), defaual(stre), desc(string), desc(string(string(string), desc(string), desc(string(string(string), desc(string(string(string), desc(string(string), desc(string), desc(string), desc(string(string), desc(string(stringfield(boolean), doesSupportDiff(boolean), edit(string), emptyKeyValue(string), enum(string), enumImage(string), expandSchemaTarget(string), expr(string), externalJoin(boolean)，功能（字符串）,featureDate(boate), filterPath(string), filean(string), filterPath(string), folerPath(string), folerterLerLterLerLterLerLink(string), folerLink(string), flederLink(string))、folderModel(string)、folderProcess(string)、fullLoad(boolean)、hierarchicalPath(boolean)、hierarchicalPath(string)、img(string)、inout(string)、完整性(string)、标签(string)、labelSingular(string)、length(boolean)、name(booalean)、noDbIndex(boolean)、no键（布尔值）、有序（布尔值）、溢流表（布尔值）、pkSequence（字符串）、pkgStatus（字符串）、ref（字符串）、必需（布尔值）、revAdvanced（布尔值）、revCardinality（字符串）、revExternalJoin（布尔值）、revIntegrity（字符串）、revLabel（字符串）、revLabel（字符串）、relex、revLelink(string), revTarget(string), revVisibleIf(string), sql(boolean), sqlname(string), sqltable(string), tableSpace(string), tableSpaceIndex(string), target(MNTOKEN), temporaryTable(boolean), translatedDefault(string), translatedExper(stringExpr(string), type(string), typeMNTOKEN)、未绑定（布尔值）、用户（布尔值）、userEnum（字符串）、visibleIf（字符串）、xml（布尔值）、xmlChildren（布尔值）

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

### 说明 {#description-4}

Adobe Campaign中有四种 `<element>` 类型的元素：

* 根 `<element>` :定义与架构匹配的SQL表的名称。
* 结构 `<element>` :定义一组或 `<element>` 多个 `<attribute>` 元素。
* 链接 `<element>` :定义链接。 此元素必须包括“@type=link”属性。
* XML `<element>` :定义文本类型“mData”字段。 此元素必须包含“@type=xml”属性。

### 属性描述 {#attribute-description-4}

* **_operation(string)**:定义在数据库中写入的类型。

   此属性主要用于扩展现成架构。

   可访问的值有：

   * “none”:独自和解。 这意味着Adobe Campaign将恢复元素，而不更新元素，或在元素不存在时生成错误。
   * “insertOrUpdate”:插入时更新。 这意味着Adobe Campaign将更新元素或在元素不存在时创建它。
   * “插入”:插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”:更新。 这意味着，如果元素不存在，Adobe Campaign将更新该元素或生成错误。
   * “删除”:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **advanced(boolean)**:当激活此选项(@advanced=&quot;true&quot;)时，它允许您隐藏可用字段列表中的属性，这些字段可用于在表单中配置列表。
* **aggregate(string)**:允许您通过其他架构复制 `<element>` 定义。 此属性以“namespace:name”的形式接收架构声明。
* **applicableIf(string)**:条件。 此属性接收XTK表达式。
* **autopk（布尔值）**:如果激活了此选项(autopk=&quot;true&quot;)，将自动定义唯一键。 此选项只能用于架构的主元素。 警告，Adobe Campaign只保证生成的密钥是唯一的。 不保证关键值是连续的和递增的。
* **dataPolicy(string)**:允许您指定对SQL字段中允许的值的批准约束。 此属性的值为：

   * “none”:无值
   * “smartCase”:大写字母
   * “lowerCase”:全小写
   * “upperCase”:全大写
   * “电子邮件”:电子邮件地址
   * “电话”:电话号码
   * “标识符”:标识符名称
   * &quot;resIdentifier&quot;:文件名

* **dbEnum（字符串）**:接收“已关闭”枚举的内部名称。 必须在中定义枚举值 `<srcschema>`。
* **defOnDuplicate(boolean)**:如果激活了此属性，则当记录重复时，默认值（在@default中定义）会自动重新应用于记录。
* **default(string)**:允许您定义元素行为（调用函数、默认值）。 此属性接收XTK表达式。
* **desc(string)**:允许您插入元素的说明。 此说明显示在界面的状态栏中。
* **displayAsField（布尔值）**:如果激活了此属性，则“链接”类 `<element>` 型将在架构的树视图（“结构”选项卡）中显示为字段。 这样，就可以将链接显示为本地字段，并在查询期间更改其行为。 在查询的SELECT中找到元素时，将使用链接目标的值。 在查询的WHERE中找到元素时，将使用链接的基础键。
* **edit(string)**:此属性指定将在链接到架构的表单中使用的输入类型。
* **enum(string)**:接收链接到字段的枚举的名称。 可以将枚举插入同一架构或远程架构中。
* **expr(string)**:此属性定义一个计算字段，该字段的定义不存储在表中。 它接收Xpath或XTK（字符串）表达式。
* **externalJoin(boolean)**:“链接”类型元素中的外部连接。
* **feature(string)**:定义特征字段：这些字段用于扩展现有表中的数据，但存储在附件表中。 接受的值为：

   * “共享”:内容按数据类型存储在共享表中
   * “专用”:内容存储在专用表中
   SQL特征表是根据以下特征类型自动构建的：

   * 专用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   有两种类型的特征字段：其中在特征上授权单个值的简单字段，和多选字段，其中特征被链接到可能包含多个值的集合元素。

   在架构中定义特征时，此架构必须具有基于单个字段的主键（未授权复合键）。

* **featureDate（布尔值）**:属性链接到“@feature”特征字段。 如果其值为“true”，则允许您查找该值上次更新的时间。
* **filterPath（字符串）**:此属性接收Xpath并允许您在字段上定义过滤器。
* **folderLink(string)**:此属性接收链接的名称，该名称允许您恢复包含实体的文件。
* **folderModel(string)**:定义启用实体存储的文件夹类型。 仅当“@folderLink”存在时，才定义此属性。
* **folderProcess(string)**:定义存储实体模型实例的链接。 仅当“@folderLink”存在时，才定义此属性。
* **fullLoad(boolean)**:此属性强制在表单中的字段选择期间显示表中的所有记录。
* **img(string)**:接收链接到元素的图像的路径。 此属性的值为“namespace:image name”类型。 例如：img=&quot;cus:myImage.jpg&quot;。 实际上，映像必须导入到应用程序服务器。
* **完整性（字符串）**:源表对目标表的出现的引用完整性。

   可访问的值有：

   * “define”:如果通过链接引用了实体，则Adobe Campaign不会删除该实体
   * “正常”:删除源实例将初始化目标实例上的链接键（默认模式），此类型的完整性将初始化所有外键
   * “own”:删除源实例会触发删除目标实例
   * “owncopy”:与“own”（删除时）或重复的实例（复制时）类似
   * “中性”:不做任何事

* **label(string)**:元素标签。
* **labelSingular(string)**:在界面的某些部分中使用的元素的标签（奇异形式）。
* **length(string)**:max. 为“字符串”类型SQL字段的值授权的字符数。
* **localizable（布尔值）**:如果激活了该属性，则此属性会告知集合工具恢复“@label”属性的值以进行转换（内部使用）。
* **name(MNTOKEN)**:与表名称匹配的元素的内部名称。 “@name”属性的值必须很短，最好是英文，并且符合链接到XML的命名限制。

   将架构写入数据库后，前缀会由Adobe Campaign自动添加到字段名称。

   * “i”:“integer”类型的前缀。
   * “d”:“double”类型的前缀。
   * “s”:字符串类型的前缀。
   * “ts”:“date”类型的前缀。
   要以自主方式定义表的名称，您需要在主架构元素的定义中使用“@sqltable”属性。

* **noDbIndex(boolean)**:允许您指定元素不会被索引。
* **ordered(boolean)**:如果激活了属性(ordered=&quot;true&quot;),Adobe Campaign会将元素声明序列保留在XML集合元素中。
* **pkSequence(string)**:接收要用于计算自动增量密钥的序列的名称。 仅当在架构的根元素上定义了自动增量键时，才可使用此属性。
* **pkgStatus(string)**:在包导出过程中，值将作为此属性值的函数来考虑：

   * “always”:元素将始终存在
   * “never”:元素永远不会出现
   * “default（或nothing）”:除非元素是默认元素，或者它不是内部字段并且与其他实例不兼容，否则将导出元素

* **ref(string)**:此属性定义对由多个架构共享的>element>元素的引用（定义因子化）。 定义不会复制到当前架构中。
* **必需（布尔值）**:如果激活了此属性(@required=&quot;true&quot;)，则该字段将在界面中高亮显示。 字段的标签将在表单中为红色。
* **revAdvanced（布尔值）**:激活后，此属性指定相反的链接为“高级”链接。
* **revCardinality（字符串）**:此属性定义两个表之间链接的基数。 它用于“链接”类型 `<element>`。

   可能的值包括：

   * “single”:简单的1-1类型链接
   * “未捆绑”:1-N类型集合链接
   默认情况下，如果在创建链接时未指定属性，则基数为1-N。

* **revDesc（字符串）**:此属性接收链接到相反链接的描述。
* **revExternalJoin(boolean)**:激活后，此属性允许您在相反的链接上强制使用外部连接。
* **revIntegrity（字符串）**:此属性定义目标架构上的完整性。 授权的值与“@integrity”属性相同。 默认情况下，Adobe Campaign会为此属性提供“正常”值。
* **revLabel（字符串）**:标签。
* **revLink（字符串）**:相反链接的名称。 如果值为“_NONE_”，则不会在目标架构中创建相反的链接。
* **revTarget（字符串）**:目标。
* **sql（布尔值）**:如果激活了此属性(@sql=&quot;true&quot;)，则会强制存储SQL元素，即使元素具有xml=&quot;true&quot;属性也是如此。
* **sqlname(string)**:表创建过程中字段的名称。 如果未指定&quot;@sqlname&quot;，则默认情况下使用&quot;@name&quot;属性的值。 将架构写入表时，前缀会根据字段的类型自动添加。
* **sqltable(string)**:对于架构的主要元素，此属性将覆盖默认生成的SQL表的名称。 如果未指定&quot;@sqltable&quot;，则默认名称将采用如下结构：namespace（第一个字母大写），后跟SrcSchema &quot;@name&quot;的值。
* **tableSpace（字符串）**:此属性允许您指定存储表表空间的新数据(在根上有 `<element>`效)。
* **tableSpaceIndex（字符串）**:此属性允许您为表指定新的索引存储表空间(在根上有 `<element>`效)。
* **target(MNTOKEN)**:在表之间创建链接时接收目标架构的名称。 此属性仅对“链接”类型元素处于活动状态。
* **template(string)**:此属性定义对由多个架构共 `<element>` 享的元素的引用。 定义会自动复制到当前架构中。
* **translatedDefault（字符串）**:如果找到&quot;@default&quot;属性，则&quot;@translatedDefault&quot;将允许您重新定义表达式以与@default中定义的表达式匹配，该表达式将由翻译工具收集（内部使用）。
* **translatedExpr(string)**:如果找到&quot;@expr&quot;属性，则通过&quot;@translatedExpr&quot;属性，可重新定义与&quot;@expr&quot;中定义的表达式相匹配的表达式，该表达式将由翻译工具收集（内部使用）。
* **type(MNTOKEN)**:定义元素中存储的数据类型。

   可用类型列表：

   * 任意
   * 宾
   * 斑点
   * 布尔值
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * 双倍
   * enum
   * 浮动
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
   * uid

* **unbind(boolean)**:如果属性被激活(unboind=&quot;true&quot;)，则链接将声明为1-N基数的集合元素。
* **userEnum（字符串）**:接收“open”枚举的内部名称。 枚举值可由用户在界面中定义。
* **xml（布尔值）**:如果激活了此选项，则元素中定义的所有值都以XML格式存储在TEXT类型“mData”字段中。 这意味着这些字段不会进行筛选或排序。
* **xmlChildren(boolean)**:强制存储每个子级( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` 元素 {#enumeration--element}

### 内容模型 {#content-model-5}

枚举：==(help| value)

### 属性 {#attributes-5}

* @basetype（字符串）
* @default（字符串）
* @desc（字符串）
* @label（字符串）
* @name（字符串）
* @template（字符串）

### 父母 {#parents-5}

`<srcschema>`

### 儿童 {#children-5}

* `<help>`
* `<value>`

### 说明 {#description-5}

此元素允许我们定义值枚举。 枚举属于在中定义的架构，但可通过其他架构访问它。

### 使用和使用环境 {#use-and-context-of-use-4}

在架构的开始（在定义主元素之前）定义枚举。

### 属性描述 {#attribute-description-5}

* **basetype(string)**:枚举中存储的值的类型。

   可用类型列表：

   * 任意
   * 宾
   * 斑点
   * 布尔值
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * 双倍
   * enum
   * 浮动
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
   * uid

* **default(string)**:默认值。 默认值也可以是枚举中定义的值之一。
* **desc(string)**:枚举描述。
* **label(string)**:枚举标签。
* **name(string)**:枚举的内部名称。
* **template(string)**:此属性定义对由多个架构共 `<enumeration>` 享的元素的引用。 定义会自动复制到当前架构中。

### 示例 {#examples-4}

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

使用默认值定义枚举：

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

### 说明 {#description-6}

通过此元素可以描述或 `<element>` 元素 `<attribute>` 。 它只能包含文本，并以XML格式存储在数据库中。

### 属性描述 {#attribute-description-6}

此元素没有属性。

### 示例 {#examples-5}

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

### 说明 {#description-7}

允许您定义在SQL表之间创建连接的字段。

### 使用和使用环境 {#use-and-context-of-use-5}

元 `<join>` 素仅在父元素类型为“ `<element>` link”时才可使用。 这意味着父元素必须声明“@type=link”属性。

无需在元素中指定远程表的名称和命名空 `<join>` 间。 它们需要在父项中指定 `<element>`。

根据惯例，链接在架构的末尾定义。

如果在 `<join>` 定义链接类型元素时未指定该元素，则链接将自动放置在两个表的主键上。

### 属性描述 {#attribute-description-7}

* **dstFilterExpr（字符串）**:此属性允许您限制远程表中合格值的数量。
* **xpath-dst（字符串）**:此属性接收Xpath（远程表的@name属性）。
* **xpath-src（字符串）**:此属性接收Xpath（当前架构中的@name属性）。

### 示例 {#examples-6}

在当前表的“email”字段与远程表的“@compagny-id”字段之间的链接：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根据“@country”字段的内容筛选指向“cus:Country”表的链接，该字段必须包含“EN”值：

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
* @label（字符串）
* @name(MNTOKEN)
* @noDbIndex（布尔值）

### 父母 {#parents-8}

`<element>`

### 儿童 {#children-8}

`<keyfield>`

### 说明 {#description-8}

此元素允许您定义用于标识表中记录的键。

表必须至少具有一个键。

### 使用和使用环境 {#use-and-context-of-use-6}

通常，键在架构的主元素和索引之后声明。

如果键包括多个字段（即多个子字段），则称为复合 `<keyfield>` 键。 请勿使用复合键定义主键。

如果架构的主元素包含“@autopk=true”属性，则主键是唯一的。 每个架构只能有一个主键。

保留前1000个标识符，因此如果需要为键定义一系列值，从1000开始。

### 属性描述 {#attribute-description-8}

* **allowEmptyPart(boolean)**:对于复合键，如果激活了此属性，则当其至少一个键不为空时，这些键将被视为有效。 如果是这种情况，则空概念值为“0”（布尔值或所有类型的数值数据）。 默认情况下，需要输入组成复合键的所有键。
* **applicableIf(string)**:此属性允许您使键成为可选项。 它定义将应用键定义的条件。 此属性接收XTK表达式。
* **internal(boolean)**:如果激活了此属性，则此属性可让Adobe Campaign知道密钥是主密钥。
* **label(string)**:键的标签。
* **name(MNTOKEN)**:密钥的内部名称。
* **noDbIndex(boolean)**:如果激活了该字段(noDbIndex=&quot;true&quot;)，则将不索引与该键匹配的字段。

### 示例 {#examples-------}

授权“@expr”或“别名”字段为空的复合密钥声明：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

在STRING类型的“名称”字段和匹配的SQL查询中声明 `<srcschema>` 主键：

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

### 说明 {#description-9}

此元素定义要集成到索引或键中的字段。

### 属性描述 {#attribute-description-9}

* **xlink(MNTOKEN)**:允许您自动引用在关系表的连接中定义的外键（N-N链接）。
* **xpath(MNTOKEN)**:索引或元素上的键的定 `<attribute>` 义。 此属性接收一个Xpath，它定义了定义键或索引的架构属性的路径。

### 示例 {#examples-}

在索引中选择“sName”字段，并在“@name”上添加Xpath:

```
<keyfield xpath="@name"/>
```

## `<method>` 元素 {#method--element}

### 内容模型 {#content-model-10}

方法：==(帮助|参数)

### 属性 {#attributes-10}

* @_operation（字符串）
* @access（字符串）
* @const（布尔值）
* @hidden（布尔值）
* @label（字符串）
* @library(string)
* @name(MNTOKEN)
* @pkonly（布尔值）
* @static（布尔值）

### 父母 {#parents-10}

`<methods>`  ,  `<interface />`

### 儿童 {#children-10}

* `<help>`
* `<parameters>`

### 说明 {#description-10}

此元素允许您定义SOAP方法。

### 使用和使用环境 {#use-and-context-of-use-7}

SOAP方法启用应用程序进程。

声明新方法（非本机）时必须使用“@library”:用于库的命名空间和名称与声明所在的架构的命名空间和名称无关。

### 属性描述 {#attribute-description-10}

* **access(string)**:此属性定义使用该方法的访问控制。 如果缺少此属性，则必须进行标识。 可用值包括：“anonymous”、“admin”和“sql”。
* **const(boolean)**:如果激活了该属性，则此属性意味着声明的方法将更改实体
* **label(string)**:方法的标签。
* **库（字符串）**:此方法不是应用程序固有的。 此属性采用找到方法定义的方法库的值(nms:mylibrary.js)。
* **name(MNTOKEN)**:唯一方法名称。
* **static(boolean)**:如果激活了此属性，则该方法被视为自治的，则调用该属性时必须为该方法指定所有参数。

### 示例 {#examples-7}

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

### 说明 {#description-11}

此元素允许您定义元 `<method>` 素。 声明方法是必需的。

### 属性描述 {#attribute-description-11}

此元素没有属性。

### 示例 {#examples-8}

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
* @label（字符串）
* @localizable（字符串）
* @name(MNTOKEN)
* @namespace(MNTOKEN)
* @type（字符串）

### 父母 {#parents-12}

`<parameters>`

### 儿童 {#children-12}

`<help>`

### 说明 {#description-12}

通过此元素，可以定义一个参数以调用SOAP方法。

### 属性描述 {#attribute-description-12}

* **desc(string)**:与元素相关的 `<param>` 说明。
* **inout（字符串）**:此属性定义参数是否位于SOAP调用的输入(in)或输出(out)处。 如果未指定此属性，则默认参数为输入(&quot;@inout=in&quot;)。
* **label(string)**: `<param>` 标签
* **localizable（字符串）**:如果激活了该属性，则此属性会告知集合工具恢复“@label”属性的值以进行转换（内部使用）。
* **name(MNTOKEN)**:内部名称 `<param>`
* **type(string)**:此属性定义元素的类 `<param>` 型

   可用类型列表：

   * 任意
   * 宾
   * 斑点
   * 布尔值
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * date
   * DOMDocument
   * DOMElement
   * 双倍
   * enum
   * 浮动
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
   * uid

### 示例 {#examples-9}

字符串类型的“serviceName”入站设置的定义：

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

### 说明 {#description-13}

此元素定义一组元 `<parameter>` 素。

### 使用和使用环境 {#use-and-context-of-use-8}

此元素是必需的，即使对于元素的单 `<param>` 个子元素也是必 `<method>` 需的。

### 属性描述 {#attribute-description-13}

无

### 示例 {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` 元素 {#srcschema--element}

### 内容模型 {#content-model-14}

srcSchema:==(attribute|创建者|数据|元素|枚举|帮助|界面|方法| modifiedBy)

### 属性 {#attributes-14}

created(datetime), createdBy-id(long), desc(string),entitySchema(string), extendedSchema(string), img(string), implements(string)，标签(string)，标签奇异(string),lastModified(datetime)，库(string), mappingBy-id(lon, name), namespace(strace, string), strape, useRecycleBin(boolean), view(boolean), xtkschema(string)

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

### 说明 {#description-14}

是 `<srcschema>` 架构的根元素。 它是定义架构的输入点。

### 使用和使用环境 {#use-and-context-of-use-9}

架构演示在“关于架构 [引用”和“架构](../../configuration/using/about-schema-reference.md) ”结 [构中可用](../../configuration/using/schema-structure.md)。

### 属性描述 {#attribute-description-14}

* **created(datetime)**:此属性提供有关创建架构的日期和时间的信息。 它有一个“日期时间”表单。 显示的值取自服务器。 时间以UTC格式显示。
* **createdBy-id（长）**:是创建架构的运算符的标识符。
* **desc(string)**:架构描述
* **entitySchema（字符串）**:基本架构，其语法和批准基于哪些语法和批准(默认情况下，对于Adobe Campaign:xtk:srcSchema)。 保存当前架构时，Adobe Campaign将批准其语法，其中架构在@xtkschema属性中声明。
* **extendedSchema（字符串）**:接收当前架构扩展所基于的现成架构的名称。 表单为“namespace:name”。
* **img(string)**:链接到架构的图标（可以在架构创建向导中定义）。
* **label(string)**:架构标签。
* **labelSingular(string)**:标签（单个），用于在界面中显示。
* **lastModified(datetime)**:此属性提供有关上次修改的日期和时间的信息。 它有一个“日期时间”表单。 显示的值取自服务器。 时间以UTC格式显示。
* **库（布尔值）**:将架构用作库而非实体。 因此，由于&quot;@ref&quot;和&quot;@template&quot;属性，此架构可能被其他架构引用。
* **mappingType(string)**:

   * &quot;sql&quot;:数据库映射
   * &quot;textFile&quot;:文本文件映射
   * &quot;xmlFile&quot;:XML格式文本文件映射
   * &quot;binaryFile&quot;:二进制文件映射

* **modifiedBy-id（长）**:匹配更改架构的运算符的标识符。
* **name(string)**:唯一架构名称。
* **namespace(string)**:架构的命名空间(默认：nms, xtk, nl)。 为项目创建新架构时，建议您使用专用的命名空间。
* **useRecycleBin（布尔值）**:在应用程序中激活垃圾桶功能。 删除的记录将放在垃圾桶中，最后删除。 此功能仅在“交付”模式下可用。
* **view(boolean)**:如果激活了该模式(@view=&quot;true&quot;)，则此模式将用作视图。 数据库结构更新向导将不考虑此架构。 此选项主要用于引用外部表。
* **xtkschema（字符串）**:定义架构语法的架构的名称（默认情况下为xtk:srcSchema）。

### 示例 {#examples-11}

`<srcschema>` “nms:delivery”开箱即用架构的元素

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

### 说明 {#description-15}

通过此元素可定义筛选器。

### 属性描述 {#attribute-description-15}

此元素没有属性。

### 示例 {#examples-12}

定义具有@name属性条件的过滤器：

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
* @label（字符串）
* @name（字符串）
* @value（字符串）

### 父母 {#parents-16}

`<enumeration>`

### 儿童 {#children-16}

`<help>`

### 说明 {#description-16}

此元素允许您定义在枚举中存储的值。

### 属性描述 {#attribute-description-16}

* **applicableIf(string)**:此属性允许您使枚举值成为可选值。 它接收XTK表达式。
* **desc(string)**:枚举值的说明。
* **enabledIf（字符串）**:用于激活枚举值的条件。
* **img(string)**:链接到“namespace:image_name”表单中枚举的图像。 映像必须导入到应用程序服务器上。
* **label(string)**:枚举值的标签。
* **name(string)**:枚举值的内部名称。
* **value(string)**:枚举值的值。 值的类型是根据枚举的类型定义的。 如果枚举为字符串类型，则它只能包含字符串类型值。

### 示例 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
