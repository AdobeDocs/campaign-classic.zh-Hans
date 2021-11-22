---
product: campaign
title: 关于模式版本
description: 模式版本快速入门
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 7%

---

# 关于模式版本{#about-schema-edition}

![](../../assets/v7-only.svg)

Adobe Campaign采用数据模式：

* 定义应用程序内的数据对象如何与底层数据库表的联系起来。
* 定义 Campaign 应用程序中不同数据对象之间的链接。
* 定义并描述每个对象中包含的个别字段。

要更好地了解Campaign内置表及其交互情况，请参阅 [此部分](https://helpx.adobe.com/cn/campaign/kb/acc-datamodel.html).

## 扩展或创建模式 {#extending-or-creating-schemas}

要向Campaign中的一个核心数据模式(例如收件人表(nms:recipient))添加字段、索引或其他元素，您必须扩展该模式。 有关更多信息，请参阅 [扩展模式](../../configuration/using/extending-a-schema.md) 中。

要添加Adobe Campaign中不存在的现成数据类型（例如合同表），您可以直接创建自定义架构。 有关更多信息，请参阅 [数据模式](../../configuration/using/data-schemas.md) 中。

![](assets/schemaextension_getting_started_1.png)

扩展或创建架构以在中使用后，最佳实践是按它们在下面显示的顺序定义其XML内容元素。

## 明细列表 {#enumerations}

首先，在架构的主元素之前定义枚举。 利用这些值，可在列表中显示值，以限制用户对给定字段所做的选择。

示例:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

在定义字段时，您随后可以使用此枚举，如下所示：

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>您还可以使用用户管理的枚举(通常在 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** )以指定给定字段的值。 这些是有效的全局枚举，如果枚举在您正在使用的特定架构之外使用，则最好选择这些枚举。

要进一步了解枚举，请参阅 [枚举](../../configuration/using/schema-structure.md#enumerations) 和 [`<enumeration>` 元素](../../configuration/using/schema/enumeration.md) 中。

## 索引 {#index}

索引是在架构的主元素中声明的第一个元素。

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

的 **xpath** 属性指向您要索引的架构中的字段。

>[!IMPORTANT]
>
>请务必记住，索引提供的SQL查询读取性能增益在写入记录时也会伴随性能点击。 因此，应当使用索引以防范。

有关索引的更多信息，请参阅 [索引字段](../../configuration/using/database-mapping.md#indexed-fields) 中。

## 键 {#keys}

每个表都必须至少具有一个键，并且通常情况下，可使用 **@autopk=true** 属性设置为“true”。

还可以使用 **内部** 属性。

示例:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

在本例中，不要让 **@autopk** 属性会创建一个名为“id”的默认主键，我们将指定自己的“houselId”主键。

>[!IMPORTANT]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

要进一步了解密钥，请参阅 [密钥管理](../../configuration/using/database-mapping.md#management-of-keys) 中。

## 属性（字段） {#attributes--fields-}

利用属性，可定义构成数据对象的字段。 您可以使用 **[!UICONTROL Insert]** 按钮，将空属性模板拖放到XML中光标所在的位置。 有关更多信息，请参阅 [数据模式](../../configuration/using/data-schemas.md) 中。

![](assets/schemaextension_getting_started_2.png)

在 [`<attribute>` 元素](../../configuration/using/schema/attribute.md) 中。 以下是一些最常用的属性：

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

   要查看列出Adobe Campaign为不同数据库管理系统生成的数据类型映射的表，请参阅 [映射Adobe Campaign/DBMS数据类型](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) 中。

有关每个属性的更多信息，请参阅 [属性描述](../../configuration/using/schema/attribute.md) 中。

### 示例 {#examples}

定义默认值的示例：

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

将通用属性用作字段模板的示例也标记为必填：

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

使用隐藏的计算字段的示例 **@advanced** 属性：

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

XML字段的示例也存储在SQL字段中，该字段具有 **@dataPolicy** 属性。

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>尽管大多数属性都根据1-1基数链接到数据库的物理字段，但XML字段或计算字段并非如此。\
>XML字段存储在表的Memo字段(“mData”)中。\
>但是，每次启动查询时都会动态创建计算字段，因此它仅存在于应用层中。

## 链接 {#links}

链接是架构主元素中的最后一些元素。 它们定义实例中所有不同架构如何彼此关联。

链接在包含 **外键** 链接到的表格。

基数有三种类型：1-1、1-N和N-N默认使用的是1-N类型。

### 示例 {#examples-1}

收件人表（即装即用模式）和自定义事务表之间的1-N链接示例：

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

自定义架构“Car”（位于“cus”命名空间中）与收件人表之间的1-1链接示例：

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

收件人表和地址表之间基于电子邮件地址而非主键的外部连接示例：

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

此处，“xpath-dst”对应于目标架构中的主键，而“xpath-src”对应于源架构中的外键。

## 审核跟踪 {#audit-trail}

您希望在架构底部包含的一个有用元素是跟踪元素（审核跟踪）。

使用以下示例可包含与创建日期、创建数据的用户、日期以及表格中所有数据的上次修改作者相关的字段：

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## 更新数据库结构 {#updating-the-database-structure}

完成并保存更改后，任何可能影响SQL结构的更改都需要应用到数据库。 要实现此目的，请使用数据库更新向导。

![](assets/schemaextension_getting_started_3.png)

有关更多信息，请参阅[更新数据库结构](../../configuration/using/updating-the-database-structure.md)。

>[!NOTE]
>
>如果修改不影响数据库结构，您只需重新生成架构即可。 为此，请选择要更新的架构，右键单击并选择 **[!UICONTROL Actions > Regenerate selected schemas...]** . 有关更多信息，请参阅 [重新生成模式](../../configuration/using/regenerating-schemas.md) 中。
