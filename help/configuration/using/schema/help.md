---
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 17%

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
