---
product: campaign
title: 架构元素和属性 — 条件元素
description: 条件元素
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
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
