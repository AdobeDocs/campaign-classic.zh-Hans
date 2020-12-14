---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---


# 连接元素{#join--element}

## 内容模型{#content-model-7}

join:==EMPTY

## 属性{#attributes-7}

* @dstFilterExpr（字符串）
* @xpath-dst（字符串）
* @xpath-src（字符串）

## 父项{#parents-7}

`<element>`

## 子项{#children-7}

无

## 说明{#description-7}

允许您定义在SQL表之间创建连接的字段。

## 使用和使用上下文{#use-and-context-of-use-5}

`<join>`元素只能在父`<element>`元素类型为“link”时使用。 这意味着父元素必须声明“@type=link”属性。

无需在`<join>`元素中指定远程表的名称和命名空间。 它们需要在父`<element>`中指定。

根据惯例，链接在模式末尾定义。

如果定义链接类型元素时未指定`<join>`元素，则链接将自动放置在两个表的主键上。

## 属性描述{#attribute-description-7}

* **dstFilterExpr（字符串）**:此属性允许您限制远程表中合格值的数量。
* **xpath-dst（字符串）**:此属性接收Xpath（远程表的@name属性）。
* **xpath-src（字符串）**:此属性接收Xpath(当前模式中的@name属性)。

## 示例{#examples-6}

在当前表的“email”字段与远程表的“@compagny-id”字段之间的链接：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根据必须包含“EN”值的“@country”字段的内容，筛选指向“cus:Country”表的链接：

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
