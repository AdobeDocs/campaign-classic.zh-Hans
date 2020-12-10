---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 5%

---


# `<value>` 元素  {#value--element}

## 内容模型{#content-model-16}

value:==帮助

## 属性{#attributes-16}

* @applicableIf（字符串）
* @desc（字符串）
* @enabledIf（字符串）
* @img（字符串）
* @label(string)
* @name（字符串）
* @value(string)

## 父项{#parents-16}

`<enumeration>`

## 子项{#children-16}

`<help>`

## 说明{#description-16}

此元素允许您定义存储在明细列表中的值。

## 属性描述{#attribute-description-16}

* **applicableIf(string)**:此属性允许您使明细列表值成为可选值。它接收XTK表达式。
* **desc(string)**:明细列表值的描述。
* **enabledIf（字符串）**:激活明细列表值的条件。
* **img(string)**:链接到“明细列表:image_name”表单中的命名空间的图像。映像必须导入到应用程序服务器上。
* **label(string)**:明细列表值的标签。
* **name(string)**:明细列表值的内部名称。
* **value(string)**:明细列表值的值。值类型根据明细列表类型定义。 如果明细列表为字符串类型，则只能包含字符串类型值。

## 示例{#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
