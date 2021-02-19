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
source-wordcount: '93'
ht-degree: 8%

---


# 条件元素{#condition--element}

## 内容模型{#content-model-2}

condition:==EMPTY

## 属性{#attributes-2}

* @boolOperator(string)
* @enabledIf(string)
* @expr(string)

## 父项{#parents-2}

`<sysfilter>`

## 子项{#children-2}

无

## 说明{#description-2}

此元素允许您定义筛选条件。

## 使用和上下文{#use-and-context-of-use-2}

一个`<sysfiler>`元素可包含多个过滤条件。

## 属性描述{#attribute-description-2}

* **boolOperator(string)**:如果在 `<conditions>` 同一元素中定义  `<sysfilter>` 了多个元素，则此属性允许您组合它们。默认情况下，`<condition>`元素之间的逻辑链接为“AND”。 “@boolOperator”属性允许您组合“OR”和“AND”类型链接。
* **enabledIf（字符串）**:条件激活测试。
* **expr(字符串**):XTK表达式。

## 示例{#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
