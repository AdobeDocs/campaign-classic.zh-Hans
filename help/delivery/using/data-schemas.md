---
title: 数据模式
seo-title: 数据模式
description: 数据模式
seo-description: null
page-status-flag: never-activated
uuid: 3327a38c-e44d-4581-a67b-bb60c1604a5f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: aeaa9475-3715-40a4-8864-29d126883272
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 2%

---


# 数据模式{#data-schemas}

以下是关于在Adobe Campaign中使用数据模式的一些一般原则。

有关在Adobe Campaign中创建和配置模式的详细信息，请参 [阅此部分](../../configuration/using/about-schema-edition.md)。

## 模式结构 {#schema-structure}

数据模式的XML文档必须包含 **`<srcschema>`** 根元素，其 **名称****和命名空间属性** 才能填充模式名称及其命名空间。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

模式的入口点是其主要元素。 很容易识别，因为它与模式同名，并且它应该是根元素的子元素。 内容的描述以此元素开头。

在内容管理模式中，主元素由以下行表示：

```
<element name="book" template="ncm:content" xmlChildren="true">
```

在主 **要元素** 中输入的模板属性允许您将具有通用属性的模式扩展到所有内容定义，如名称、创建日期、作者、关联字符串等。

这些属性在ncm:content **模式中有介绍** 。

>[!NOTE]
>
>xmlChildren属性 **的存在** ，表示通过主元素输入的数据结构存储在内容实例的XML文档中。

>[!CAUTION]
>
>创建新模式或在模式扩展期间，您需要为整个模式保留相同的主键序列值(@pkSequence)。

## 数据类型 {#data-types}

以下是已填写类型的内容管理模式的示例：

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

可以使用各种属性来丰富 **`<element>`** 数据 **`<attribute>`** 模式的元素和元素。

在内容管理中使用的主要属性如下：

* **标签**:简短描述，
* **desc**:长描述，
* **默认**:表达式在内容创建时返回默认值，
* **userEnum**:免费明细列表存储和显示通过此字段输入的值，
* **枚举**:修复了预先知道可能值的明细列表时使用的列表。

下面是我们的示例模式，其中填写了属性：

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

集合是具有相同名称和相同分层级别的元素的列表。

在我们的示例中， **`<chapter>`** 和元 **`<page>`** 素是集合元素。 因此 **,** “未绑定”属性必须添加到以下元素的定义中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>存在ordered=&quot; **true&quot;属性允许您** 对插入的集合元素进行排序。

## 元素引用 {#element-referencing}

元素引用在内容模式中使用很多。 它允许您将元素的定义分解 **`<element>`** ，以便在具有相同结构的其他元素上引用它。

要 **引用** 的元素上的ref属性必须使用引用元素的路径(XPath)完成。

**示例**:添加与 **示例** 模式元素结 **`<chapter>`** 构相同的附录部分。

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

章结构将移至主元素外名为“section”的元素。 本章和章节引用“章节”元素。

## 计算字符串 {#compute-string}

计 **算字符串** 是用于构造表示内容实例的字符串的XPath表达式。

下面是我们用其Compute字符串进行 **模式的示例**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 编辑模式 {#editing-schemas}

编辑字段允许您输入源模式的XML内容：

![](assets/d_ncs_integration_schema_edition.png)

保存源模式时，将自动启动扩展模式生成。

>[!NOTE]
>
>通过 **“名** 称编辑”控件，您可以输入模式的键，包括名称和命名空间。 命名空间 **根元** 素的名 **** 称和模式属性会在模式的XML编辑字段中自动更新。
