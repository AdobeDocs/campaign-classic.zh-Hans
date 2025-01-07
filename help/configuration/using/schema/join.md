---
product: campaign
title: 架构元素和属性 — 连接元素
description: 连接元素
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# 连接元素 {#join--element}


## 内容模型 {#content-model-7}

join：==EMPTY

## 属性 {#attributes-7}

* @dstFilterExpr（字符串）
* @xpath-dst（字符串）
* @xpath-src（字符串）

## 父项 {#parents-7}

`<element>`

## 子项 {#children-7}

无

## 说明 {#description-7}

用于定义在SQL表之间创建连接的字段。

## 使用和使用环境 {#use-and-context-of-use-5}

仅当父`<element>`元素为“link”类型时，才能使用`<join>`元素。 这意味着父元素必须声明“@type=link”属性。

不必在`<join>`元素中指定远程表的名称和命名空间。 它们需要在父`<element>`中指定。

按照惯例，链接在架构结束时定义。

如果定义链接类型元素时未指定`<join>`元素，则链接将自动置于两个表的主键上。

## 属性说明 {#attribute-description-7}

* **dstFilterExpr （字符串）**：此属性允许您限制远程表中符合条件的值的数量。
* **xpath-dst （字符串）**：此属性接收Xpath(远程表的@name属性)。
* **xpath-src （字符串）**：此属性接收Xpath(当前架构中的@name属性)。

## 示例 {#examples-6}

当前表的“email”字段与远程表的“@compagny-id”字段之间的链接：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根据必须包含“EN”值的“@country”字段的内容，过滤了指向“cus：Country”表的链接：

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
