---
product: campaign
title: 架构元素和属性 — 参数元素
description: parameters element
feature: Schema Extension
exl-id: 54538c3e-3232-4bf7-a09c-dacf0f072be5
TQID: 'https://experienceleague.adobe.com/tZyI-rIbEifWdgcO80ni6lSHinH0IEeM8UrHFAUpnFs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '48'
ht-degree: 12%
---
# parameters element {#parameters--element}


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
