---
product: campaign
title: 模式特性
description: 模式特性
feature: Custom Resources
role: Data Engineer, Developer
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 1%

---

# 模式特性{#schema-characteristics}



引用现有表的方案的特性如下：

* Adobe Campaign不得修改相对于现有表的SQL对象，
* 必须显式指定表和列的名称，
* 必须声明索引。

>[!IMPORTANT]
>
>请勿删除内置收件人表中的字段，即使这些字段毫无用处。 这可能会导致Adobe Campaign数据库中的行为错误。

## 视图属性 {#the-view-attribute}

Source架构接受&#x200B;**srcSchema**&#x200B;根元素的&#x200B;**view**&#x200B;属性。 在自定义表中处理Adobe Campaign时，必须使用该字段。 **view=&quot;true&quot;**&#x200B;属性告知数据库结构更新助手忽略此架构。 因此，禁止应用程序将表、其列及其索引与相应的模式同步。

当此属性设置为&#x200B;**true**&#x200B;时，架构仅用于生成SQL查询以访问此表的数据。

## 表和列的名称 {#names-of-tables-and-columns}

当通过表更新助手创建表时，会根据相应架构和属性的名称自动生成表和列的名称。 但是，可以通过输入以下属性来强制使用SQL名称：

* 架构的主元素中的&#x200B;**sqltable**，要指定表，
* 每个属性中的&#x200B;**sqlname**，用于指定列。

**示例**：

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

在此示例中，如果未显式指定表和列的名称，则应用程序会为表使用&#x200B;**CusIndividual**，为列使用&#x200B;**lastName**&#x200B;和&#x200B;**firstName**。

在模式中，可以只填充现有表列的一部分。 用户无法访问未填充的列。

## 索引字段 {#indexed-fields}

从客户端控制台对列表记录进行排序时，通过对索引字段进行排序，可以获得更好的性能。 在架构中声明索引，使控制台在列标签左侧的排序顺序箭头下以红线显示索引字段，如下所示：

![](assets/s_ncs_integration_mapping_index.png)

在架构中，索引的定义如下：

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

因此，在匹配模式中声明自定义表的现有索引很重要。

为源架构的每个键和链接声明隐式声明索引。 可以通过指定&#x200B;**noDbIndex=&quot;true&quot;**&#x200B;属性来阻止索引声明：

**示例**：

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
