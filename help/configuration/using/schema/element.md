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
source-wordcount: '2012'
ht-degree: 0%

---


# 元素元素{#element--element}

## 内容模型{#content-model-4}

element:==(attribute |计算字符串 | dbindex |默认 |元素 |帮助 |加入 |键 | sysFilter | translatedDefault)

## 属性{#attributes-4}

_operation(string)、advanced(boolean)、聚合(string)、appliableIf(string)、autopk(boolean)、gellensTo(string)、convDate(string)、dataPolicy(string)、dataSource(string)、dbEnum(string)、defOnDuplicate(ble)、default(stric(string)、desc(string)、desc(string)、displayAsField（布尔）、doesNotSupportDiff（布尔）、edit（字符串）、emptyKeyValue（字符串）、enum（字符串）、enumImage（字符串）、expandSchemaTarget（字符串）、expr（字符串）、externalJoin（布尔值）、功能（字符串）、featureDate（布尔值）、filterPath（字符串）、folderLink(string)、folderModel(string)、folderProcess(string)、fullLoad(boolean)、hierarchicalPath(string)、img(string)、inout(string)、integrity(string)、label(string)、labelSingular(string)、length(string)、localizable(boolean)、name(boolean)、noDbIndex(boolean)、non)Key(Boolean)、ordered(boolean)、overflowtable(boolean)、pkSequence(string)、pkgStatus(string)、ref(string)、ref(boolean)、revAdvanced(boolean)、revDesc(string)、revExternalJoin(bl)、revLabel(string)、rev链接（字符串）、revTarget（字符串）、revVisibleIf（字符串）、sql（布尔值）、sqlname（字符串）、sqltable（字符串）、tableSpace（字符串）、tableSpaceIndex（字符串）、目标(MNTOKEN)、template（字符串）、temporaryTable（布尔值）、translatedEfault（字符串）、translatedExpr（字符串）、stringtype(MNTOKEN)、unboind(boolean)、user(boolean)、userEnum(string)、visibleIf(string)、xml(boolean)、xmlChildren(boolean)

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

* 根`<element>`:定义与模式匹配的SQL表的名称。
* 结构`<element>`:定义`<element>`的组   或   `<attribute>`    元素。
* 链接`<element>`:定义链接。 此元素必须包含“@type=link”属性。
* XML `<element>` :定义文本类型“mData”字段。 此元素必须包含“@type=xml”属性。

## 属性描述{#attribute-description-4}

* **_operation(string)**:定义在数据库中写入的类型。

   此属性主要用于扩展现成模式。

   可访问的值有：

   * “无”：单独和解。 这意味着Adobe Campaign将在不更新元素的情况下恢复该元素，如果元素不存在，则会生成错误。
   * &quot;insertOrUpdate&quot;:插入时更新。 这意味着，Adobe Campaign将更新元素，或在元素不存在时创建元素。
   * “插入”：插入。 这意味着Adobe Campaign将插入元素，而不检查元素是否存在。
   * “更新”：更新。 这意味着，如果元素不存在，Adobe Campaign将更新该元素或生成错误。
   * “删除”：删除。 这意味着Adobe Campaign将恢复和删除元素。

* **高级（布尔值）**:激活此选项(@advanced=&quot;true&quot;)后，可在表单中配置列表的可用字段列表中隐藏该属性。
* **聚合（字符串）**:允许您通过其他模式 `<element>`  复制定义。此属性以“模式:name”的形式接收命名空间声明。
* **applicableIf(string)**:条件。此属性接收XTK表达式。
* **autopk(布尔值**:如果激活了此选项(autopk=&quot;true&quot;)，将自动定义唯一键。此选项只能用于模式的主元素。 警告，Adobe Campaign仅保证生成的密钥是唯一的。 不能保证关键值是连续的和递增的。
* **dataPolicy(string)**:允许您对SQL字段中允许的值指定批准约束。此属性的值为：

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
* **default(string)**:允许您定义元素行为（调用函数，默认值）。此属性接收XTK表达式。
* **desc(string**):允许您插入元素的说明。此说明显示在接口的状态栏中。
* **displayAsField（布尔值）**:如果激活了此属性，则“链接”类 `<element>`  型将在模式的树视图（“结构”选项卡）中显示为一个字段。这样，就可以将链接显示为本地字段，并在查询中更改其行为。 当在查询的SELECT中找到该元素时，将使用链接目标的值。 在查询的WHERE中找到元素时，将使用链接的基础键。
* **edit(string**):此属性指定将在链接到模式的表单中使用的输入类型。
* **enum(string)**:接收链接到该字段的明细列表的名称。该明细列表可以插入同一模式或远程模式。
* **expr(字符串**):此属性定义一个计算字段，该表中没有存储任何定义。它接收Xpath或XTK（字符串）表达式。
* **externalJoin(boolean)**:“link”类型元素中的外部联接。
* **功能(字符串**)定义特征字段：这些字段用于扩展现有表中的数据，但在附件表中具有存储。接受的值为：

   * “共享”：内容按数据类型存储在共享表中
   * “专用”：内容存储在专用表中

   SQL特征表是根据特征类型自动构建的：

   * 专用：`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共享：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   有两种类型的特征字段：对特征授权单个值的简单字段和多选字段，其中特征链接到可能包含多个值的集合元素。

   在模式中定义特性时，此模式必须具有基于单个字段的主键（未授权复合键）。

* **featureDate（布尔值）**:属性链接到“@feature”特征字段。如果其值为“true”，则允许您查看上次更新该值的时间。
* **filterPath（字符串）**:此属性接收一个Xpath，并允许您在字段上定义过滤器。
* **folderLink(string)**:此属性接收链接的名称，可用于恢复包含实体的文件。
* **folderModel(string)**:定义启用实体存储的文件夹类型。仅当存在“@folderLink”时才定义此属性。
* **folderProcess（字符串）**:定义存储实体模型实例的链接。仅当存在“@folderLink”时才定义此属性。
* **fullLoad（布尔值）**:此属性强制在表单的字段选择期间显示表中的所有记录。
* **img(string)**:接收链接到元素的图像的路径。此属性的值为“命名空间：图像名称”类型。 例如：img=&quot;cus:myImage.jpg&quot;。 实际上，映像必须导入到应用程序服务器。
* **完整性(字符串**):源表对目标表的出现的引用完整性。

   可访问的值有：

   * “定义”：Adobe Campaign不删除通过链接引用的实体
   * “正常”：删除源实例将初始化目标实例（默认模式）上链接的键，此类型的完整性将初始化所有外键
   * “拥有”：删除源事件会触发删除目标事件
   * “owncopy”：类似于“own”（如果删除）或重复事件（如果重复）
   * “中性”：不做任何事

* **label(string**):元素标签。
* **labelSingular(string)**:在界面的某些部分中使用的元素的标签（奇异形式）。
* **length(string**):max为“字符串”类型SQL字段的值授权的字符数。
* **localizable（布尔值）**:如果激活了该属性，则此属性会告知收集工具恢复“@label”属性的值，以用于翻译（内部使用）。
* **name(MNTOKEN)**:与表名称匹配的元素的内部名称。“@name”属性的值必须很短，最好是英文，并且符合链接到XML的命名约束。

   将模式写入数据库时，前缀会通过Adobe Campaign自动添加到字段名称。

   * “i”：“integer”类型的前缀。
   * “d”：“多次”类型的前缀。
   * “s”：字符串类型的前缀。
   * “ts”：前缀。

   要以自治方式定义表的名称，您需要在主模式元素的定义中使用“@sqltable”属性。

* **noDbIndex（布尔值）**:允许您指定元素将不进行索引。
* **ordered(boolean)**:如果激活了属性(ordered=&quot;true&quot;),Adobe Campaign会将元素声明序列保留在XML收集元素中。
* **pkSequence(string)**:接收用于计算自动增量键的序列的名称。仅当在模式的根元素上定义了自动增量键时，才能使用此属性。
* **pkgStatus(string)**:在包导出过程中，值将作为此属性值的函数考虑：

   * “always”：元素将始终存在
   * “never”：元素永远不会存在
   * &quot;default（或nothing）&quot;:除非元素是默认元素，或者它不是内部字段且与其他实例不兼容，否则将导出元素

* **ref(string)**:此属性定义对由多个模式共享的>element>元素的引用（定义因子化）。定义未复制到当前模式。
* **必需(布尔值**):如果激活了此属性(@required=&quot;true&quot;)，则界面中将突出显示该字段。该字段的标签将以红色显示。
* **revAdvanced（布尔值）**:激活后，此属性指定相反的链接为“高级”链接。
* **revCardinality（字符串）**:此属性定义两个表之间链接的基数。它用于“link”类型`<element>`。

   可能的值有：

   * “single”：简单的1-1类型链接
   * “未绑定”：1-N类型集合链接

   默认情况下，如果在创建链接时未指定属性，则基数为1-N。

* **revDesc（字符串）**:此属性接收链接到相反链接的描述。
* **revExternalJoin（布尔值）**:激活后，此属性允许您在相反的链接上强制使用外部连接。
* **revIntegrity（字符串）**:此属性定义目标模式上的完整性。与“@integrity”属性相同的值已授权。 默认情况下，Adobe Campaign会为此属性提供“正常”值。
* **revLabel(字符串**):标签。
* **revLink（字符串）**:反向链接的名称。如果值为“_NONE_”，则不会在目标模式中创建相反的链接。
* **revTarget(字符串**):目标反向链接。
* **sql（布尔值）**:如果激活了此属性(@sql=&quot;true&quot;)，则会强制存储SQL元素，即使元素具有xml=&quot;true&quot;属性也是如此。
* **sqlname(string)**:表创建期间字段的名称。如果未指定“@sqlname”，则默认使用“@name”属性的值。 将模式写入表时，会根据字段类型自动添加前缀。
* **sqltable(string)**:对于模式的主要元素，此属性会超载默认生成的SQL表的名称。如果未指定“@sqltable”，则默认名称将采用如下结构：命名空间（首字母大写），后跟SrcSchema的值“@name”。
* **tableSpace(string)**:此属性允许您为表指定存储表空间的新数据(在根上有 `<element>`效)。
* **tableSpaceIndex(string)**:此属性允许您为表指定新的索引存储表空间(在根上有 `<element>`效)。
* **目标(MNTOKEN)**:在表之间创建链接时接收目标模式的名称。此属性仅对“link”类型元素处于活动状态。
* **模板(字符串**):此属性定义对由多个模式 `<element>` 共享的元素的引用。定义会自动复制到当前模式。
* **translatedDefault(string)**:如果找到“@default”属性，则“@translatedDefault”将允许您重新定义表达式以匹配在@default中定义的属性，并由转换工具收集（内部使用）。
* **translatedExpr(string)**:如果找到“@expr”属性，则“@translatedExpr”属性允许您重新定义与“@expr”中定义的属性匹配的表达式，并由转换工具收集该属性（内部使用）。
* **type(MNTOKEN)**:定义在元素中存储的数据类型。

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

* **未绑定（布尔值）**:如果激活了该属性(unboind=&quot;true&quot;)，则链接将声明为1-N基数的集合元素。
* **userEnum（字符串）**:接收“open”明细列表的内部名称。明细列表值可由用户在界面中定义。
* **xml（布尔值）**:如果激活了此选项，则元素中定义的所有值都存储在TEXT类型“mData”字段的XML中。这意味着这些字段将不进行筛选或排序。
* **xmlChildren(boolean)**:强制存储每个子项(  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
