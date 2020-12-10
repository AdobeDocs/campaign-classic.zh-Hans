---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '2011'
ht-degree: 0%

---


# `<element>` 元素  {#element--element}

## 内容模型{#content-model-4}

元素：==(属性 | compute-string | dbindex |默认 |元素 |帮助 |加入 |密钥 | sysFilter | translatedDefault)

## 属性{#attributes-4}

_operation(string)、advanced(boolean)、聚合(string)、appliableIf(string)、autopk(boolean)、tellessTo(string)、convDate(string)、dataPolicy(string)、dataSource(string)、dfOnDuplicate(boolean)、defaultic(stry)、desc(string)、desc(string(string)、desc(string)、displayAs字段（布尔）、doesNotSupportDiff（布尔）、edit(string)、emptyKeyValue(string)、enum(string)、enumImage(string)、expandSchemaTarget(string)、expr(string)、externalJoin(boolean)、功能(string)、featureDate(boolean)、filterPath(string)、folderLink(folderLinkstring)、folderModel(string)、folderProcess(string)、fullLoad(boolean)、hierarchical(boolean)、hierarchicalPath(string)、img(string)、inout(string)、完整性(string)、label(sing)、labelSingular(string)、localizable(boolean)、noDbIndex(boolean)、no键（布尔）、有序（布尔）、溢流表（布尔）、pkSequence（字符串）、pkgStatus（字符串）、ref（字符串）、必需（布尔）、revAdvanced（布尔）、revCardinality（字符串）、revExternalJoin（布尔）、revIntegrity（字符串）、revLabel（字符串）、rev链接（字符串）、revTarget（字符串）、revVisibleIf（字符串）、sql（布尔）、sqlname（字符串）、sqltable（字符串）、tableSpace（字符串）、tableSpaceIndex（字符串）、目标(MNTOKEN)、模板（字符串）、temporaryTable（布尔值）、translatedExpr（字符串）、type(MNTOKEN)、unbound(boolean)、user(boolean)、userEnum(string)、visibleIf(string)、xml(boolean)、xmlChildren(boolean)

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

Adobe Campaign中有四种`<element>`元素类型：

* 根`<element>` :定义与模式匹配的SQL表的名称。
* 结构`<element>`:定义`<element>`的组   或   `<attribute>`    元素。
* 链接`<element>` :定义链接。 此元素必须包括“@type=link”属性。
* XML `<element>` :定义“mData”文本类型字段。 此元素必须包含“@type=xml”属性。

## 属性描述{#attribute-description-4}

* **_operation(string)**:定义数据库中写入的类型。

   此属性主要用于扩展现成模式。

   可访问值包括：

   * “无”:和解。 这意味着Adobe Campaign将恢复元素，而不更新它，如果元素不存在，也将生成错误。
   * &quot;insertOrUpdate&quot;:插入更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会创建它。
   * “插入”:插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”:更新。 这意味着Adobe Campaign将更新元素，如果元素不存在，则会生成错误。
   * “删除”:删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔值）**:激活此选项(@advanced=&quot;true&quot;)后，可以在可用于在表单中配置列表的可用字段的列表中隐藏该属性。
* **聚合（字符串）**:允许您通过其他模式复 `<element>`  制定义。此属性以“模式:name”的形式接收命名空间声明。
* **applicableIf(string)**:条件。此属性接收XTK表达式。
* **autopk（布尔值）**:如果激活了此选项(autopk=&quot;true&quot;)，则会自动定义唯一键。此选项只能用于模式的主元素。 警告，Adobe Campaign仅保证生成的密钥是唯一的。 不能保证密钥值是连续的和递增的。
* **dataPolicy(string)**:允许您对SQL字段中允许的值指定批准约束。此属性的值为：

   * “无”:无值
   * “smartCase”:大写字母大写
   * &quot;lowerCase&quot;:全部小写
   * “upperCase”:全部大写
   * “电子邮件”:电子邮件地址
   * “电话”:电话号码
   * &quot;标识符&quot;:标识符名称
   * &quot;resIdentifier&quot;:文件名

* **dbEnum（字符串）**:接收“已关闭”明细列表的内部名称。明细列表值必须在`<srcschema>`中定义。
* **defOnDuplicate（布尔值）**:如果激活了此属性，则当记录重复时，默认值（在@default中定义）会自动重新应用于记录。
* **default(string)**:允许您定义元素行为（调用函数、默认值）。此属性接收XTK表达式。
* **desc(string)**:允许您插入元素的说明。此说明显示在接口的状态栏中。
* **displayAsField（布尔值）**:如果激活了此属性，则“链接”类 `<element>`  型将在模式的树视图（“结构”选项卡）中显示为一个字段。这样，就可以将链接显示为本地字段，并在查询期间更改其行为。 在查询的SELECT中找到元素时，将使用链接目标的值。 在查询的WHERE中找到元素时，将使用链接的基础键。
* **edit(string)**:此属性指定将在链接到模式的表单中使用的输入类型。
* **枚举(字符串**):接收链接到该字段的明细列表的名称。明细列表可以插入到同一模式或远程模式。
* **expr(string)**:此属性定义一个计算字段，该字段的定义不存储在表中。它接收Xpath或XTK（字符串）表达式。
* **externalJoin（布尔值）**:“link”类型元素中的外部连接。
* **功能（字符串）**:定义特征字段：这些字段用于扩展现有表中的数据，但在附件表中存储。接受的值为：

   * “共享”:内容按数据类型存储在共享表中
   * “专用”:内容存储在专用表中

   SQL特征表是根据特征类型自动构建的：

   * 专用：`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特征字段有两种类型：在特征上授权单个值的简单字段和在特征上链接到可能包含多个值的集合元素的多选择字段。

   在模式中定义特性时，此模式必须具有基于单个字段的主密钥（未授权复合密钥）。

* **featureDate（布尔值）**:链接到“@feature”特征字段的属性。如果其值为“true”，则允许您查找该值上次更新的时间。
* **filterPath（字符串）**:此属性接收Xpath，并允许您在字段上定义过滤器。
* **folderLink(string)**:此属性接收链接的名称，该链接允许您恢复包含实体的文件。
* **folderModel(string)**:定义启用实体存储的文件夹类型。仅当存在“@folderLink”时，才定义此属性。
* **folderProcess(string)**:定义实体模型实例存储位置的链接。仅当存在“@folderLink”时，才定义此属性。
* **fullLoad（布尔值）**:此属性强制在表单的字段选择期间显示表中的所有记录。
* **img(string)**:接收链接到元素的图像的路径。此属性的值为“命名空间：图像名称”类型。 例如：img=&quot;cus:myImage.jpg&quot;。 实际上，映像必须导入到应用程序服务器。
* **完整性（字符串）**:源表对目标表的出现的引用完整性。

   可访问值包括：

   * “定义”:Adobe Campaign不删除通过链接引用的实体
   * “正常”:删除源出现项将初始化目标出现时链接的键（默认模式），此类型的完整性将初始化所有外键
   * “拥有”:删除源事件会触发删除目标事件
   * “owncopy”:类似于“拥有”（删除时）或重复（复制时）
   * “中性”:什么也不做

* **label(string)**:元素标签。
* **labelSingular(string)**:在接口的某些部分中使用的元素的标签（单数形式）。
* **length(string)**:max。为“字符串”类型SQL字段的值授权的字符数。
* **localizable（布尔值）**:如果激活了该属性，则此属性会告知集合工具恢复“@label”属性的值以进行转换（内部使用）。
* **name(MNTOKEN)**:与表名称匹配的元素的内部名称。“@name”属性的值必须是短的，最好是英文，并且符合链接到XML的命名限制。

   将模式写入数据库时，前缀会按Adobe Campaign自动添加到字段名称。

   * “i”:“integer”类型的前缀。
   * “d”:“多次”类型的前缀。
   * “s”:字符串类型的前缀。
   * “ts”:“date”类型的前缀。

   要以自治方式定义表的名称，您需要在主模式元素的定义中使用“@sqltable”属性。

* **noDbIndex（布尔值）**:允许您指定元素将不进行索引。
* **有序（布尔值）**:如果属性被激活(ordered=&quot;true&quot;),Adobe Campaign会将元素声明序列保留在XML集合元素中。
* **pkSequence(string)**:接收要用于计算自动增量密钥的序列的名称。仅当在模式的根元素上定义了自动增量键时，才能使用此属性。
* **pkgStatus(string)**:在包导出过程中，值将作为此属性值的函数考虑：

   * “always”:元素将始终存在
   * “从不”:元素永远不会出现
   * “默认（或无）”:除非元素是默认元素，或者它不是内部字段并且与其他实例不兼容，否则将导出该元素

* **ref(string)**:此属性定义对由多个模式共享的>element>元素的引用（定义因子化）。定义未复制到当前模式。
* **必需（布尔值）**:如果激活了此属性(@required=&quot;true&quot;)，则在界面中突出显示该字段。字段的标签将以红色显示在表单中。
* **revAdvanced（布尔值）**:激活后，此属性指定相反的链接为“高级”链接。
* **revCardinality（字符串）**:此属性定义两个表之间链接的基数。它用于“link”类型`<element>`。

   可能的值有：

   * “single”:简单的1-1类型链接
   * “未绑定”:1-N类型集合链接

   默认情况下，如果在创建链接时未指定属性，则基数将为1-N。

* **revDesc（字符串）**:此属性接收链接到相反链接的描述。
* **revExternalJoin（布尔值）**:激活后，此属性允许您在相反的链接上强制使用外部连接。
* **revIntegrity(string)**:此属性定义目标模式的完整性。授权的值与“@integrity”属性相同。 默认情况下，Adobe Campaign为此属性提供“正常”值。
* **revLabel（字符串）**:相反链接的标签。
* **revLink（字符串）**:相反链接的名称。如果值为“_NONE_”，则目标模式中不会创建相反的链接。
* **revTarget（字符串）**:目标相反的链接。
* **sql（布尔值）**:如果激活了此属性(@sql=&quot;true&quot;)，则会强制存储SQL元素，即使元素具有xml=&quot;true&quot;属性也是如此。
* **sqlname(string)**:表创建期间字段的名称。如果未指定“@sqlname”，则默认使用“@name”属性的值。 将模式写入表时，前缀会根据字段类型自动添加。
* **sqltable(string)**:对于模式的主元素，此属性会过载默认生成的SQL表的名称。如果未指定“@sqltable”，则默认名称的结构将如下所示：命名空间（首字母大写），后跟SrcSchema &quot;@name&quot;的值。
* **tableSpace(string)**:此属性允许您为表指定存储表空间的新数据(在根上有 `<element>`效)。
* **tableSpaceIndex（字符串）**:此属性允许您为表指定新的索引存储表空间(在根上有 `<element>`效)。
* **目标(MNTOKEN)**:在表之间创建链接时接收目标模式的名称。此属性仅对“链接”类型元素处于活动状态。
* **模板(字符串**):此属性定义对由多个模式 `<element>` 共享的元素的引用。定义会自动复制到当前模式。
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
* **userEnum（字符串）**:接收“open”明细列表的内部名称。明细列表值可由用户在界面中定义。
* **xml（布尔值）**:如果激活了此选项，则元素中定义的所有值都以XML格式存储在TEXT类型“mData”字段中。这意味着这些字段将不进行筛选或排序。
* **xmlChildren(boolean)**:强制存储每个孩子(  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
