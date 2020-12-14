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
source-wordcount: '101'
ht-degree: 7%

---


# 密钥字段元素{#keyfield--element}

## 内容模型{#content-model-9}

keyfield:==EMPTY

## 属性{#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

## 父项{#parents-9}

`<key>`  ,  `<dbindex />`

## 子项{#children-9}

无

## 说明{#description-9}

此元素定义要集成到索引或键中的字段。

## 属性描述{#attribute-description-9}

* **xlink(MNTOKEN)**:允许您自动引用在关系表（N-N链接）的连接中定义的外键。
* **xpath(MNTOKEN)**:对元素的索引或键的定 `<attribute>`  义。此属性接收一个Xpath，它定义模式属性的路径，该属性定义键或索引。

## 示例{#examples-}

在索引中选择“sName”字段，该索引的Xpath位于“@name”上：

```
<keyfield xpath="@name"/>
```
