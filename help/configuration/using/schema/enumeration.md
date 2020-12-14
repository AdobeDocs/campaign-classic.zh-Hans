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
source-wordcount: '196'
ht-degree: 5%

---


# 明细列表元素{#enumeration--element}

## 内容模型{#content-model-5}

明细列表:==(help| value)

## 属性{#attributes-5}

* @basetype（字符串）
* @default（字符串）
* @desc（字符串）
* @label(string)
* @name（字符串）
* @template(string)

## 父项{#parents-5}

`<srcschema>`

## 子项{#children-5}

* `<help>`
* `<value>`

## 说明{#description-5}

此元素使我们能够定义值明细列表。 明细列表属于在中定义的模式，但可通过其他模式访问。

## 使用和使用上下文{#use-and-context-of-use-4}

明细列表在模式的开始下定义（在定义主要元素之前）。

## 属性描述{#attribute-description-5}

* **basetype(string)**:存储在明细列表中的值的类型。

   列表可用类型：

   * 任意
   * 宾
   * 斑点
   * 布尔
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datetimenotz
   * 日期
   * DOMDocument
   * DOMElement
   * 多次
   * 枚举
   * 浮
   * html
   * int64
   * 链接
   * 长
   * 备忘录
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字符串
   * 时间
   * 时间平移
   * uuid

* **default(string)**:默认值。默认值也可以是明细列表中定义的值之一。
* **desc(string)**:明细列表描述。
* **label(string)**:明细列表标签。
* **name(string)**:明细列表的内部名称。
* **模板(字符串**):此属性定义对由多个模式 `<enumeration>` 共享的元素的引用。定义会自动复制到当前模式。

## 示例{#examples-4}

其值存储在明细列表库中的值示例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

具有默认值的明细列表的定义：

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
