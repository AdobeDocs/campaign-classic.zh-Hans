---
product: campaign
title: 元素和属性 — 值元素
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 3%

---

# 值元素 {#value--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-16}

value:==help

## 属性 {#attributes-16}

* @applicableIf（字符串）
* @desc（字符串）
* @enabledIf（字符串）
* @img（字符串）
* @label（字符串）
* @name（字符串）
* @value（字符串）

## 父母 {#parents-16}

`<enumeration>`

## 子项 {#children-16}

`<help>`

## 说明 {#description-16}

利用此元素，可定义枚举中存储的值。

## 属性描述 {#attribute-description-16}

* **appliableIf（字符串）**:此属性允许您使枚举值为可选值。 它接收XTK表达式。
* **desc（字符串）**:枚举值的描述。
* **enabledIf（字符串）**:用于激活枚举值的条件。
* **img（字符串）**:链接到“namespace:image_name”表单中枚举的图像。 必须将映像导入到应用程序服务器。
* **标签（字符串）**:枚举值的标签。
* **名称（字符串）**:枚举值的内部名称。
* **值（字符串）**:枚举值的值。 根据枚举类型定义值类型。 如果枚举为字符串类型，则可能只包含字符串类型值。

## 示例 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
