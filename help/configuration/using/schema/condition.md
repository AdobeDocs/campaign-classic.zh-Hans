---
product: campaign
title: 架构元素和属性 — 条件元素
description: 条件元素
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
TQID: 'https://experienceleague.adobe.com/Jx8bLCt1UEqAZDm0cSuexx25js-e5xTsvkeSMzVCUHw'
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
source-wordcount: '95'
ht-degree: 5%
---
# 条件元素 {#condition--element}


## 内容模型 {#content-model-2}

condition：==EMPTY

## 属性 {#attributes-2}

* @boolOperator（字符串）
* @enabledIf（字符串）
* @expr（字符串）

## 父项 {#parents-2}

`<sysfilter>`

## 子项 {#children-2}

无

## 说明 {#description-2}

利用此元素，可定义筛选条件。

## 使用和使用环境 {#use-and-context-of-use-2}

一个`<sysfiler>`元素可以包含多个筛选条件。

## 属性说明 {#attribute-description-2}

* **boolOperator （字符串）**：如果在同一`<sysfilter>`元素中定义了多个`<conditions>`，则通过此属性可组合它们。 默认情况下，逻辑链接介于`<condition>`个元素之间为“AND”。 “@boolOperator”属性允许您组合“OR”和“AND”类型链接。
* **enabledIf （字符串）**：条件激活测试。
* **expr （字符串）**： XTK表达式。

## 示例 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
