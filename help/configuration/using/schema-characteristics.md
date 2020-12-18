---
solution: Campaign Classic
product: campaign
title: 模式特性
description: 模式特性
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 模式特性{#schema-characteristics}

引用现有表的模式的特性如下：

* Adobe Campaign不得修改相对于现有表的SQL对象，
* 必须显式指定表和列的名称，
* 必须声明索引。

>[!IMPORTANT]
>
>请勿删除标准收件人表中的字段，即使这些字段没有用处也是如此。 这可能导致Adobe Campaign库中的行为错误。

## 视图属性{#the-view-attribute}

源模式接受&#x200B;**srcSchema**&#x200B;根元素的&#x200B;**视图**&#x200B;属性。 在自定义表中处理Adobe Campaign时，必须使用它。 **视图=&quot;true&quot;**&#x200B;属性告知数据库结构更新向导忽略此模式。 因此，禁止应用程序将表、其列和其索引与相应的模式同步。

当此属性设置为&#x200B;**true**&#x200B;时，该模式仅用于生成SQL查询以访问此表的数据。

## 表和列的名称{#names-of-tables-and-columns}

当表更新向导创建表时，将根据各模式和属性的名称自动生成表和列的名称。 但是，可以通过输入以下属性强制使用SQL名称：

* **在** 模式的主元素中指定表，
* **在** 每个属性中指定列。

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

在本示例中，如果未明确指定表和列的名称，则应用程序应使用&#x200B;**CusIndividual**&#x200B;作为表，**lastName**&#x200B;和&#x200B;**firstName**&#x200B;作为列。

在模式中，只能填充现有表的部分列。 未填充的列将不可由用户访问。

## 索引字段{#indexed-fields}

从客户端控制台对列表记录进行排序时，通过对索引字段进行排序可以获得更好的性能。 在模式中声明索引使控制台在列标签左侧的排序顺序箭头下显示索引字段并带有红线，如下所示：

![](assets/s_ncs_integration_mapping_index.png)

在模式中，索引定义如下：

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

因此，在匹配模式中声明自定义表的现有索引很重要。

为源模式的每个密钥和链接声明隐式声明索引。 通过指定&#x200B;**noDbIndex=&quot;true&quot;**&#x200B;属性，可以阻止索引声明：

**示例**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

