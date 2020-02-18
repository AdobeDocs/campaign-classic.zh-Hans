---
title: 架构特性
seo-title: 架构特性
description: 架构特性
seo-description: null
page-status-flag: never-activated
uuid: ca8eb7af-ef22-403a-8f04-ece5dc903174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 441e80e1-0559-41fd-83e8-afdf94279e75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 架构特性{#schema-characteristics}

引用现有表的架构的特性如下：

* Adobe Campaign不得修改相对于现有表的SQL对象，
* 必须明确指定表和列的名称，
* 必须声明索引。

>[!IMPORTANT]
>
>请勿删除标准收件人表中的字段，即使这些字段没有用处。 这可能会在Adobe Campaign数据库中导致行为错误。

## 视图属性 {#the-view-attribute}

源架构接受 **srcSchema** root元素的 **view属性** 。 在自定义表中处理Adobe Campaign时，必须使用它。 view=&quot; **true&quot;属性告知数据库结构更新向导** ，以忽略此架构。 因此，禁止应用程序将表、其列及其索引与相应的架构同步。

当此属性设置为 **true**&#x200B;时，此架构仅用于生成SQL查询以访问此表的数据。

## 表和列的名称 {#names-of-tables-and-columns}

当表由表更新向导创建时，表和列的名称将基于各个架构和属性的名称自动生成。 但是，可以通过输入以下属性强制使用SQL名称：

* **sqltable** ，用于指定表，
* **sqlname** ，用于指定列。

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

在此示例中，如果未明确指定表和列的名称，则应用程序应该已对表使用 **CusIndividual** ，对列使用 **lastName****和firstName** 。

在架构中，只能填充现有表的部分列。 未填充的列将不可供用户访问。

## 索引字段 {#indexed-fields}

从客户端控制台对列表记录进行排序时，通过对索引字段进行排序可以获得更好的性能。 在架构中声明索引使控制台在列标签左侧的排序顺序箭头下显示索引字段，其中带有红线，如下所示：

![](assets/s_ncs_integration_mapping_index.png)

在架构中，索引定义如下：

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

因此，在匹配架构中声明自定义表的现有索引很重要。

为源架构的每个键和链接声明隐式声明索引。 通过指定noDbIndex=&quot;true&quot;属 **性可以阻止索引声明** :

**示例**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

