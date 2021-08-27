---
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 8%

---

# 条件元素 {#condition--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-2}

条件：==EMPTY

## 属性 {#attributes-2}

* @boolOperator（字符串）
* @enabledIf（字符串）
* @expr（字符串）

## 父母 {#parents-2}

`<sysfilter>`

## 子项 {#children-2}

无

## 说明 {#description-2}

利用此元素，可定义筛选条件。

## 使用和使用上下文 {#use-and-context-of-use-2}

一个`<sysfiler>`元素可以包含多个筛选条件。

## 属性描述 {#attribute-description-2}

* **boolOperator（字符串）**:如果在同 `<conditions>` 一元素中定义了多  `<sysfilter>` 个元素，则通过此属性可以合并它们。默认情况下，`<condition>`元素之间的逻辑链接为“AND”。 “@boolOperator”属性允许您组合“OR”和“AND”类型链接。
* **enabledIf（字符串）**:条件激活测试。
* **expr（字符串）**:XTK表达式。

## 示例 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
