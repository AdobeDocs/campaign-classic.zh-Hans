---
title: 数据架构
seo-title: 数据架构
description: 数据架构
seo-description: null
page-status-flag: never-activated
uuid: 3327a38c-e44d-4581-a67b-bb60c1604a5f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: aeaa9475-3715-40a4-8864-29d126883272
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 数据架构{#data-schemas}

以下是有关在Adobe Campaign中使用数据架构的一些一般原则。

有关在Adobe Campaign中创建和配置数据架构的详细信息，请参阅 [此部分](../../configuration/using/about-schema-edition.md)。

## 架构结构 {#schema-structure}

数据架构的XML文档必须包含根元素，其 **`<srcschema>`** 中包含名称 **和** namespace **属性** ，以填充架构名称及其命名空间。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

架构的入口点是其主要元素。 它易于识别，因为它与架构同名，并且它应该是根元素的子元素。 内容的描述以此元素开头。

在内容管理架构中，主元素由以下行表示：

```
<element name="book" template="ncm:content" xmlChildren="true">
```

在主 **元素中输入的** template属性允许您将具有通用属性的架构扩展到所有内容定义，如名称、创建日期、作者、关联字符串等。

ncm:content架构中介绍了 **这些属性** 。

>[!NOTE]
>
>xmlChildren属性的存 **在表示** ，通过主元素输入的数据结构存储在内容实例的XML文档中。

>[!CAUTION]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

## 数据类型 {#data-types}

以下是已填写类型的内容管理架构的示例：

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

可以使用各种属性来丰富数 **`<element>`** 据架 **`<attribute>`** 构的元素和元素。

内容管理中使用的主要属性如下：

* **label**:简短描述，
* **desc**:长描述，
* **default**:表达式在内容创建时返回默认值，
* **userEnum**:存储和显示通过此字段输入的值的免费枚举，
* **enum**:修复了在事先已知可能值列表时使用的枚举。

下面是我们的示例架构，其中填充了属性：

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

## 集合元素 {#collection-elements}

集合是具有相同名称和相同层次结构的元素列表。

在我们的示例中， **`<chapter>`** 和元 **`<page>`** 素是集合元素。 因此 **，必须将** unboind属性添加到这些元素的定义中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>存在ordered=&quot; **true&quot;属性允许您对插入的集合元素进行排序** 。

## 元素引用 {#element-referencing}

元素引用在内容架构中使用很多。 它允许您将元素的定义分解，以便 **`<element>`** 在具有相同结构的其他元素上引用它。

要 **引用的元素** 上的ref属性必须使用引用元素的路径(XPath)完成。

**示例**:添加与示 **例架构的元素结****`<chapter>`** 构相同的附录部分。

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

章节结构将移至主元素外名为“section”的元素。 本章和章节引用“章节”元素。

## 计算字符串 {#compute-string}

计 **算字符串** 是用于构造表示内容实例的字符串的XPath表达式。

下面是我们的示例架构及其 **Compute字符串**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 编辑架构 {#editing-schemas}

通过编辑字段，您可以输入源架构的XML内容：

![](assets/d_ncs_integration_schema_edition.png)

保存源架构时，将自动启动扩展架构生成。

>[!NOTE]
>
>通过 **“名称** ”编辑控件，您可以输入架构的键，包括名称和命名空间。 架 **构根元** 素的名称和命名空间 **** 属性会在架构的XML编辑字段中自动更新。
