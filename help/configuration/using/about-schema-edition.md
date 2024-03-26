---
product: campaign
title: 关于模式版本
description: 架构版本入门
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 7%

---

# 关于模式版本{#about-schema-edition}

Adobe Campaign使用数据架构来：

* 定义应用程序内的数据对象如何与底层数据库表的联系起来。
* 定义 Campaign 应用程序中不同数据对象之间的链接。
* 定义并描述每个对象中包含的个别字段。

要更好地了解Campaign内置表及其交互，请参阅 [本节](https://helpx.adobe.com/cn/campaign/kb/acc-datamodel.html).

## 扩展或创建模式 {#extending-or-creating-schemas}

要将字段或索引或其他元素添加到Campaign中的某个核心数据架构(如收件人表(nms：recipient))，您必须扩展该架构。 有关详细信息，请参见 [扩展模式](../../configuration/using/extending-a-schema.md) 部分。

要添加在Adobe Campaign中现成不存在的全新类型数据（例如合同表），您可以直接创建自定义架构。 有关详细信息，请参见 [数据架构](../../configuration/using/data-schemas.md) 部分。

![](assets/schemaextension_getting_started_1.png)

扩展或创建要在其中工作的架构后，最佳实践是按照下面显示的XML内容元素顺序来定义其XML内容元素。

## 明细列表 {#enumerations}

枚举先于架构的主元素之前定义。 它们允许您在列表中显示值，以限制用户对给定字段的选择。

例如：

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

在定义字段时，您可以使用此枚举，如下所示：

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>您还可以使用用户管理的枚举(通常位于 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** )，指定给定字段的值。 这些实际上是全局枚举，如果您可以在所使用的特定架构之外使用枚举，则最好选择它们。

要了解有关明细列表的详细信息，请参阅 [明细列表](../../configuration/using/schema-structure.md#enumerations) 和 [`<enumeration>` 元素](../../configuration/using/schema/enumeration.md) 部分。

## 索引 {#index}

索引是在架构的主元素中声明的第一个元素。

它们可以唯一也可以不唯一，并引用一个或多个字段。

示例：

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

此 **xpath** 属性指向架构中要编制索引的字段。

>[!IMPORTANT]
>
>请务必记住，索引提供的SQL查询读取性能提高也会在写入记录时带来性能下降。 因此，应谨慎使用索引。

有关索引的更多信息，请参阅 [索引字段](../../configuration/using/database-mapping.md#indexed-fields) 部分。

## 键 {#keys}

每个表必须至少有一个键，通常使用在架构的主元素中自动建立它 **@autopk=true** 属性设置为“true”。

也可使用定义主键 **内部** 属性。

例如：

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

在此示例中，不要让 **@autopk** 属性创建一个名为“id”的默认主键，我们将指定自己的“householdId”主键。

>[!IMPORTANT]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

要了解有关密钥的更多信息，请参阅 [密钥管理](../../configuration/using/database-mapping.md#management-of-keys) 部分。

## 属性（字段） {#attributes--fields-}

属性允许您定义组成数据对象的字段。 您可以使用 **[!UICONTROL Insert]** 模式版工具栏中的按钮，将空属性模板拖放到光标所在的XML中。 有关详细信息，请参见 [数据架构](../../configuration/using/data-schemas.md) 部分。

![](assets/schemaextension_getting_started_2.png)

完整的属性列表可在 [`<attribute>` 元素](../../configuration/using/schema/attribute.md) 部分。 以下是一些更常用的属性：

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@type**

  要查看一个表，其中列出了Adobe Campaign为各种数据库管理系统生成的数据类型的映射，请参阅 [映射Adobe Campaign/DBMS数据的类型](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) 部分。

有关每个属性的详细信息，请参阅 [属性说明](../../configuration/using/schema/attribute.md) 部分。

### 示例 {#examples}

定义默认值的示例：

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

将公共属性用作标记为必填字段的模板的示例：

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

使用隐藏的计算字段示例 **@advanced** 属性：

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

XML字段的示例也存储在SQL字段中，该字段具有 **@dataPolicy** 属性。

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>尽管大多数属性根据1-1基数与数据库的物理字段相关联，但XML字段或计算字段并非如此。\
>XML字段存储在表的备注字段(“mData”)中。\
>但是，计算字段是在每次启动查询时动态创建的，因此它仅存在于应用层中。

## 链接 {#links}

链接是架构主元素的最后几个元素之一。 它们定义实例中所有不同的架构如何相互关联。

在包含 **外键** 所链接到的表的URL值。

基数有三种类型：1-1、1-N和N-N。默认使用1-N类型。

### 示例 {#examples-1}

收件人表（现成模式）和自定义事务表之间的1-N链接示例：

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

自定义模式“Car”（位于“cus”命名空间中）和收件人表之间的1-1链接示例：

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

收件人表和地址表之间的外部联接示例，该表基于电子邮件地址而不是主键：

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

此处，“xpath-dst”对应于目标架构中的主键，“xpath-src”对应于源架构中的外键。

## 审核跟踪 {#audit-trail}

架构底部可能想要包含一个有用元素，即跟踪元素（审核跟踪）。

使用下面的示例包含与创建日期、创建数据的用户、日期和表格中所有数据的上次修改的作者相关的字段：

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## 更新数据库结构 {#updating-the-database-structure}

完成并保存更改后，任何可能影响SQL结构的更改都需要应用到数据库。 要执行此操作，请使用数据库更新向导。

![](assets/schemaextension_getting_started_3.png)

有关更多信息，请参阅[更新数据库结构](../../configuration/using/updating-the-database-structure.md)。

>[!NOTE]
>
>当修改不会影响数据库结构时，只需重新生成模式即可。 要执行此操作，请选择要更新的架构，右键单击并选择 **[!UICONTROL Actions > Regenerate selected schemas...]** . 有关详细信息，请参见 [重新生成模式](../../configuration/using/regenerating-schemas.md) 部分。
