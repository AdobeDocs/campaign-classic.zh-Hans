---
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 18%

---

# sysfilter元素 {#sysfilter--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-15}

sysFilter:==条件

## 属性 {#attributes-15}

无

## 父母 {#parents-15}

`<element>`

## 子项 {#children-15}

`<condition>`

## 说明 {#description-15}

利用此元素，可定义过滤器。

## 属性描述 {#attribute-description-15}

此元素没有属性。

## 示例 {#examples-12}

具有属性条件的过滤器的@name义：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
