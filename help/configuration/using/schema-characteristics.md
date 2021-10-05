---
product: campaign
title: 模式特性
description: 模式特性
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# 模式特性{#schema-characteristics}

![](../../assets/v7-only.svg)

引用现有表的模式的特征如下：

* Adobe Campaign不得修改相对于现有表的SQL对象，
* 必须明确指定表和列的名称，
* 必须声明索引。

>[!IMPORTANT]
>
>请勿删除标准收件人表中的字段，即使这些字段无用也是如此。 这可能会导致Adobe Campaign数据库中的行为错误。

## 视图属性 {#the-view-attribute}

源架构接受&#x200B;**srcSchema**&#x200B;根元素的&#x200B;**view**&#x200B;属性。 在自定义表中处理Adobe Campaign时，必须使用该函数。 **view=&quot;true&quot;**&#x200B;属性告知数据库结构更新向导忽略此模式。 因此，禁止应用程序将表、其列及其索引与相应模式同步。

当此属性设置为&#x200B;**true**&#x200B;时，架构仅用于生成SQL查询以访问此表的数据。

## 表和列的名称 {#names-of-tables-and-columns}

当通过表更新向导创建表时，表和列的名称会根据各个架构和属性的名称自动生成。 但是，可以通过输入以下属性来强制使用SQL名称：

* **** 模式主元素内的sqltable，用于指定表，
* **** sqlname，以指定列。

**示例**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

在此示例中，如果未明确指定表和列的名称，则应用程序将使用&#x200B;**CusIndivial**&#x200B;表， **lastName**&#x200B;和&#x200B;**firstName**&#x200B;列。

在架构中，只能填充现有表列的一部分。 未填充的列将不允许用户访问。

## 索引字段 {#indexed-fields}

在客户端控制台中对列表记录进行排序时，对索引字段进行排序可获得更好的性能。 在架构中声明索引时，控制台会在列标签左侧的排序箭头下，以红线显示索引字段，如下所示：

![](assets/s_ncs_integration_mapping_index.png)

在架构中，索引的定义如下：

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

因此，在匹配架构中声明自定义表的现有索引很重要。

为源模式的每个键和链接声明隐式声明索引。 通过指定&#x200B;**noDbIndex=&quot;true&quot;**&#x200B;属性，可以阻止索引声明：

**示例**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
