---
product: campaign
title: 架构元素和属性 — 参数元素
description: parameters element
feature: Schema Extension
exl-id: 54538c3e-3232-4bf7-a09c-dacf0f072be5
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 12%

---

# parameters element {#parameters--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-13}

parameters：==param

## 属性 {#attributes-13}

无

## 父项 {#parents-13}

`<method>`

## 子项 {#children-13}

`<param>`

## 说明 {#description-13}

此元素定义了一组`<parameter>`元素。

## 使用和使用环境 {#use-and-context-of-use-8}

此元素是必需的，即使对于`<method>`元素的单个`<param>`子元素也是如此。

## 属性说明 {#attribute-description-13}

无

## 示例 {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```
