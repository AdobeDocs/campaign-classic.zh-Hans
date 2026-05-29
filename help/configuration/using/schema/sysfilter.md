---
product: campaign
title: 元素和属性 — sysfilter元素
description: 元素和属性
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
TQID: https://experienceleague.adobe.com/hjsD-JSGBPnwyj1IsLDo-tUy-63apy0-6kT9vngaaQk
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 45
ht-degree: 17%

---

# sysfilter元素 {#sysfilter--element}


## 内容模型 {#content-model-15}

sysFilter：==condition

## 属性 {#attributes-15}

无

## 父项 {#parents-15}

`<element>`

## 子项 {#children-15}

`<condition>`

## 说明 {#description-15}

利用此元素，可定义过滤器。

## 属性说明 {#attribute-description-15}

此元素没有属性。

## 示例 {#examples-12}

在@name属性上具有条件的筛选器的定义：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
