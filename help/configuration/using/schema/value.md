---
product: campaign
title: 元素和属性 — 值元素
description: 元素和属性
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
TQID: https://experienceleague.adobe.com/rGaA--VHVGxCBHX5SgZUQQ9AwMgOTYWqMYGpYWU4-WY
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 4%

---

# 值元素 {#value--element}


## 内容模型 {#content-model-16}

value：==help

## 属性 {#attributes-16}

* @applicableIf（字符串）
* @desc（字符串）
* @enabledIf（字符串）
* @img（字符串）
* @label（字符串）
* @name（字符串）
* @value（字符串）

## 父项 {#parents-16}

`<enumeration>`

## 子项 {#children-16}

`<help>`

## 说明 {#description-16}

利用此元素，可定义存储在枚举中的值。

## 属性说明 {#attribute-description-16}

* **applicableIf （字符串）**：此属性允许您将枚举值设为可选。 它接收一个XTK表达式。
* **desc （字符串）**：枚举值的说明。
* **enabledIf （字符串）**：激活枚举值的条件。
* **img （字符串）**：链接到“namespace:image_name”表单中枚举的图像。 必须将映像导入应用程序服务器。
* **标签（字符串）**：枚举值的标签。
* **name （字符串）**：枚举值的内部名称。
* **值（字符串）**：枚举值的值。 根据枚举的类型定义值的类型。 如果枚举为字符串类型，则只能包含字符串类型的值。

## 示例 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
