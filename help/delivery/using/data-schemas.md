---
product: campaign
title: 在Campaign中使用数据架构
description: 了解如何在Campaign中使用数据架构
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Data Model
role: User, Developer, Data Engineer
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---

# 在Campaign中使用数据架构{#data-schemas}

以下是有关在Adobe Campaign中使用数据架构的一些一般原则。

有关在Adobe Campaign中创建和配置数据架构的更多信息，请参阅[此部分](../../configuration/using/about-schema-edition.md)。

## 模式结构 {#schema-structure}

数据架构的XML文档必须包含具有&#x200B;**名称**&#x200B;和&#x200B;**命名空间**&#x200B;属性的&#x200B;**`<srcschema>`**&#x200B;根元素，才能填充架构名称及其命名空间。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

架构的入口点是其主元素。 此插件易于识别，因为它与架构具有相同的名称，并且应该是根元素的子项。 内容的描述以此元素开头。

在内容管理架构中，主元素由以下行表示：

```
<element name="book" template="ncm:content" xmlChildren="true">
```

在主元素中输入的&#x200B;**template**&#x200B;属性允许您使用通用属性将架构扩展到所有内容定义，例如名称、创建日期、作者、关联的字符串等。

这些属性在&#x200B;**ncm：content**&#x200B;架构中进行了描述。

>[!NOTE]
>
>**xmlChildren**&#x200B;属性的存在表示通过主元素输入的数据结构存储在内容实例的XML文档中。

>[!CAUTION]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

## 数据类型 {#data-types}

以下是填充了类型的内容管理架构示例：

```
<srcSchema name="book" namespace="cus">
  <element name="book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string"/>
    <attribute name="date" type="date"/>
    <attribute name="language" type="string"/>
    <element name="chapter">
      <attribute name="name" type="string"/>
      <element name="page" type="string>
        <attribute name="number" type="short"/>
      </element>
    </element>
  </element>
</element>
```

## 属性 {#properties}

各种属性可用于扩充数据架构的&#x200B;**`<element>`**&#x200B;和&#x200B;**`<attribute>`**&#x200B;元素。

内容管理使用的主要属性如下：

* **标签**：简短说明，
* **desc**：详细描述，
* **默认值**：表达式在创建内容时返回默认值，
* **userEnum**：可用枚举来存储和显示通过此字段输入的值，
* **枚举**：预先知道可能值的列表时使用的固定枚举。

以下是填充了属性的架构示例：

```
<srcSchema name="book" namespace="cus">
  <enumeration name="language" basetype="string" default="eng">    
    <value name="fra" label="French"/>    
    <value name="eng" label="English"/>   
  </enumeration>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter">
      <attribute name="name" type="string" label="Name" desc="Name of chapter"/>
      <element name="page" type="string" label="Page" desc="Page content">
        <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
      </element>
    </element>
  </element>
</srcSchema>
```

## 收藏集元素 {#collection-elements}

集合是具有相同名称和相同层次级别的元素的列表。

在我们的示例中，**`<chapter>`**&#x200B;和&#x200B;**`<page>`**&#x200B;元素是集合元素。 因此，必须将&#x200B;**未绑定**&#x200B;特性添加到这些元素的定义中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>**ordered=&quot;true&quot;**&#x200B;属性的存在允许您对插入的收藏集元素进行排序。

## 元素引用 {#element-referencing}

元素引用在内容架构中被大量使用。 它可让您分解&#x200B;**`<element>`**&#x200B;元素的定义，以便在具有相同结构的其他元素上引用它。

要引用的元素上的&#x200B;**ref**&#x200B;属性必须使用引用元素的路径(XPath)来填写。

**示例**：添加了结构与我们示例架构的&#x200B;**`<chapter>`**&#x200B;元素相同的&#x200B;**Appendix**&#x200B;节。

```
<srcSchema name="book" namespace="cus">
  <element name="section">
    <attribute name="name" type="string" label="Name" desc="Name"/>
    <element name="page" type="string" label="Page" desc="Content of page">
      <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
    </element>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter" ref="section"/>
    <element name="appendix" label="Appendix" ref="section"/>
  </element>
</srcSchema>
```

章节结构将移至主元素之外名为“section”的元素。 章节和小节引用“section”元素。

## 计算字符串 {#compute-string}

**计算字符串**&#x200B;是用于构造表示内容实例的字符串的XPath表达式。

以下是我们的示例架构，其中包含其&#x200B;**计算字符串**：

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 编辑模式 {#editing-schemas}

编辑字段允许您输入源架构的XML内容：

![](assets/d_ncs_integration_schema_edition.png)

保存源架构后，将自动启动扩展架构生成。

>[!NOTE]
>
>**Name**&#x200B;编辑控件允许您输入架构的键，该键由名称和命名空间组成。 架构根元素的&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;属性在架构的XML编辑字段中自动更新。
