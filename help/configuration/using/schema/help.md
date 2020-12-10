---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '46'
ht-degree: 17%

---


# `<help>` 元素  {#help--element}

## 内容模型{#content-model-6}

help:==EMPTY

## 属性{#attributes-6}

无

## 父项{#parents-6}

`<srcschema>`  ,   `<element>`   ,   `<attribute>`         `<enumeration>`     ,      `<value>`      ,      `<param />`       `<method />`

## 子项{#children-6}

无

## 说明{#description-6}

此元素用于描述`<element>`或`<attribute>`   元素。 它只能包含文本，并以XML格式存储在数据库中。

## 属性描述{#attribute-description-6}

此元素没有属性。

## 示例{#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
