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
source-wordcount: '43'
ht-degree: 18%

---


# sysfilter元素{#sysfilter--element}

## 内容模型{#content-model-15}

sysFilter:==condition

## 属性{#attributes-15}

无

## 父项{#parents-15}

`<element>`

## 子项{#children-15}

`<condition>`

## 说明{#description-15}

此元素允许您定义筛选器。

## 属性描述{#attribute-description-15}

此元素没有属性。

## 示例{#examples-12}

具有@name属性条件的过滤器的定义：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
