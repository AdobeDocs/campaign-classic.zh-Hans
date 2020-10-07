---
title: 关于模式版本
seo-title: 关于模式版本
description: 关于模式版本
seo-description: null
page-status-flag: never-activated
uuid: edb4d47d-b507-4d86-9873-ebd5f6acefc6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: d5b08e4e-060c-4185-9dac-af270918e2b9
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 7%

---


# 关于模式版本{#about-schema-edition}

Adobe Campaign使用数据模式来：

* 定义应用程序内的数据对象如何与底层数据库表的联系起来。
* 定义 Campaign 应用程序中不同数据对象之间的链接。
* 定义并描述每个对象中包含的个别字段。

要更好地了解活动内置表及其交互，请参阅 [Campaign Classic数据模型](https://helpx.adobe.com/cn/campaign/kb/acc-datamodel.html)。

## 扩展或创建模式 {#extending-or-creating-schemas}

要在活动中向核心模式(如收件人表(nms:收件人))之一添加字段、索引或其他元素，您必须扩展该模式。 For more on this, refer to the [Extending a schema](../../configuration/using/extending-a-schema.md) section.

要添加Adobe Campaign中不存在的全新数据类型（例如合同表），您可以直接创建自定义模式。 For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_1.png)

扩展或创建模式后，最佳实践是按照其XML内容元素在下方的显示顺序定义其XML内容元素。

## 明细列表 {#enumerations}

明细列表在模式的主元素之前先定义。 它们允许您在列表中显示值，以限制用户对给定字段的选择。

示例:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

在定义字段时，您随后可以按如下方式使用此明细列表:

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>您还可以使用用户管理的明细列表(通 **[!UICONTROL Administration]** 常在 **[!UICONTROL Platform]** >下)指定给定字段的值。 这些明细列表实际上是全局明细列表，如果您的可能在您所处的特定模式之外使用，则还是更好的选择。

要进一步了解明细列表，请参阅 [明细列表](../../configuration/using/schema-structure.md#enumerations)[`<enumeration>` 和元素](../../configuration/using/elements-and-attributes.md#enumeration--element) 。

## 索引 {#index}

索引是在模式的主元素中声明的第一个元素。

它们可以是唯一的，也可以是不唯一的，并引用一个或多个字段。

示例:

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

xpath **属性** 指向要索引的模式中的字段。

>[!IMPORTANT]
>
>请务必记住，索引提供的SQL查询读取性能提高也会对写入记录产生性能影响。 因此，应谨慎使用这些索引。

有关索引的详细信息，请参 [阅索引字段](../../configuration/using/database-mapping.md#indexed-fields) 。

## 按键 {#keys}

每个表都必须至少有一个键，通常，它会使用设置为“true”的@autopk= **true** 属性在模式的主元素中自动建立。

主键也可以使用内部属性进 **行定** 义。

示例:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

在此示例中，我们将指 **定自己的** “householdId”主键，而不是让@autopk属性创建名为“id”的默认主键。

>[!IMPORTANT]
>
>创建新模式或在模式扩展期间，您需要为整个模式保留相同的主键序列值(@pkSequence)。

要进一步了解密钥，请参阅“密钥 [管理”部分](../../configuration/using/database-mapping.md#management-of-keys) 。

## 属性（字段） {#attributes--fields-}

属性允许您定义构成数据对象的字段。 您可以使用模式 **[!UICONTROL Insert]** 版工具栏中的按钮将空属性模板拖放到光标所在的XML中。 For more on this, refer to the [Data schemas](../../configuration/using/data-schemas.md) section.

![](assets/schemaextension_getting_started_2.png)

属性的完整列表在元素部 [`<attribute>` 分中](../../configuration/using/elements-and-attributes.md#attribute--element) 。 以下是一些最常用的属性：

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
* **@必填**
* **@ref**
* **@xml**
* **@type**

   要视图一个表，其中列出了Adobe Campaign为不同数据库管理系统生成的数据类型的映射，请参 [阅映射Adobe Campaign/DBMS数据的类型](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) 。

有关每个属性的详细信息，请参阅“属 [性说明](../../configuration/using/elements-and-attributes.md#attribute-description) ”部分。

### 示例{#examples}

定义默认值的示例：

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

将公用属性用作字段模板的示例也标记为必填：

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

使用@advanced属性隐藏的计算字 **段的示** 例：

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

XML字段的示例也存储在SQL字段中，该字段具有 **@dataPolicy** 属性。

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>尽管大多数属性都根据1-1基数链接到数据库的物理字段，但XML字段或计算字段并不是如此。\
>XML字段存储在表的备注字段(“mData”)中。\
>但是，每次启动查询时都动态地创建计算字段，因此它仅存在于应用层中。

## 链接 {#links}

链接是模式主元素中最后的一些元素。 它们定义实例中所有不同模式彼此的关联方式。

链接在模式中声明，该 **包含链接** 到的表的外键。

基数有三种类型：1-1、1-N和N-N它是默认使用的1-N类型。

### 示例{#examples-1}

收件人表(现成模式)和自定义事务表之间的1-N链接示例：

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

自定义模式“Car”(在“cus”命名空间中)与收件人表之间的1-1链接示例：

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

收件人表和地址表之间基于电子邮件地址而不是主键的外部连接示例：

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

此处“xpath-dst”对应于目标模式中的主键，而“xpath-src”对应于源模式中的外键。

## 审核跟踪 {#audit-trail}

您可能希望在模式底部包含的一个有用元素是跟踪元素（审计跟踪）。

请使用以下示例包含与创建日期、创建数据的用户、日期以及表格中所有数据的上次修改的作者相关的字段：

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## 更新数据库结构 {#updating-the-database-structure}

完成并保存更改后，任何可能影响SQL结构的更改都需要应用到数据库。 为此，请使用数据库更新向导。

![](assets/schemaextension_getting_started_3.png)

有关更多信息，请参阅[更新数据库结构](../../configuration/using/updating-the-database-structure.md)。

>[!NOTE]
>
>当修改不影响模式库结构时，您只需重新生成数据。 为此，请选择要更新的模式，右键单击并选择 **[!UICONTROL Actions > Regenerate selected schemas...]** 。 For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

