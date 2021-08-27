---
product: campaign
title: 数据模式
description: 数据模式
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---

# 数据模式{#data-schemas}

![](../../assets/common.svg)

以下是关于在Adobe Campaign中使用数据模式的一些一般原则。

有关在Adobe Campaign中创建和配置数据架构的更多信息，请参阅[此部分](../../configuration/using/about-schema-edition.md)。

## 模式结构 {#schema-structure}

数据架构的XML文档必须包含具有&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;属性的&#x200B;**`<srcschema>`**&#x200B;根元素，以填充架构名称及其命名空间。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

架构的入口点是其主要元素。 很容易识别，因为它与架构同名，并且应该是根元素的子元素。 内容的描述以此元素开头。

在内容管理架构中，主元素由以下行表示：

```
<element name="book" template="ncm:content" xmlChildren="true">
```

通过在主元素中输入的&#x200B;**template**&#x200B;属性，可以将具有通用属性的架构扩展到所有内容定义，如名称、创建日期、作者、关联字符串等。

**ncm:content**&#x200B;架构中对这些属性进行了描述。

>[!NOTE]
>
>存在&#x200B;**xmlChildren**&#x200B;属性表示通过主元素输入的数据结构存储在内容实例的XML文档中。

>[!CAUTION]
>
>创建新架构或在架构扩展期间，您需要为整个架构保留相同的主键序列值(@pkSequence)。

## 数据类型 {#data-types}

以下是内容管理架构的示例，其中填充了以下类型：

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

可以使用各种属性来扩充数据架构的&#x200B;**`<element>`**&#x200B;和&#x200B;**`<attribute>`**&#x200B;元素。

内容管理中使用的主要属性如下：

* **标签**:简短描述，
* **desc**:长描述，
* **默认**:表达式在内容创建时返回默认值，
* **userEnum**:用于存储和显示通过此字段输入的值的自由枚举，
* **枚举**:修复了在预先知道可能值列表时使用的枚举。

以下是我们的示例架构，其中填充了以下属性：

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

集合是具有相同名称和相同层次结构级别的元素列表。

在本例中，**`<chapter>`**&#x200B;和&#x200B;**`<page>`**&#x200B;元素是集合元素。 因此，必须将&#x200B;**unbound**&#x200B;属性添加到这些元素的定义中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>存在&#x200B;**ordered=&quot;true&quot;**&#x200B;属性允许您对插入的集合元素进行排序。

## 元素引用 {#element-referencing}

元素引用在内容架构中非常常用。 它允许您对&#x200B;**`<element>`**&#x200B;元素的定义进行分解，以便可以在具有相同结构的其他元素上引用该元素。

要引用的元素上的&#x200B;**ref**&#x200B;属性必须使用引用元素的路径(XPath)完成。

**示例**:添加与示 **** 例模式元素结构相 **`<chapter>`** 同的Appendixsection。

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

章节结构将移至主元素外部名为“section”的元素。 章节和节引用“section”元素。

## 计算字符串 {#compute-string}

**计算字符串**&#x200B;是XPath表达式，用于构造表示内容实例的字符串。

以下是我们使用其&#x200B;**计算字符串**&#x200B;的示例架构：

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
>**Name**&#x200B;编辑控件允许您输入架构的键，包括名称和命名空间。 架构根元素的&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;属性会在架构的XML编辑字段中自动更新。
