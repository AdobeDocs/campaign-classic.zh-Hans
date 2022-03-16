---
product: campaign
title: '架构元素和属性 — 帮助元素 '
description: 帮助元素
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 8%

---

# 帮助元素 {#help--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-6}

help:==EMPTY

## 属性 {#attributes-6}

无

## 父母 {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

## 子项 {#children-6}

无

## 说明 {#description-6}

通过此元素，您可以 `<element>`  或  `<attribute>`   元素。 它只能包含文本，并且以XML形式存储在数据库中。

## 属性描述 {#attribute-description-6}

此元素没有属性。

## 示例 {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
