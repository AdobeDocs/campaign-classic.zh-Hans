---
product: campaign
title: 架构元素和属性
description: 明细元素
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 2%

---

# 明细元素 {#enumeration--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-5}

枚举：==（help|值）

## 属性 {#attributes-5}

* @basetype（字符串）
* @default（字符串）
* @desc（字符串）
* @label（字符串）
* @name（字符串）
* @template（字符串）

## 父母 {#parents-5}

`<srcschema>`

## 子项 {#children-5}

* `<help>`
* `<value>`

## 说明 {#description-5}

利用此元素，可定义值枚举。 枚举属于其中定义的架构，但可通过其他架构访问。

## 使用和使用上下文 {#use-and-context-of-use-4}

枚举在架构开始时定义（在定义主元素之前）。

## 属性描述 {#attribute-description-5}

* **basetype（字符串）**:枚举中存储的值的类型。

   可用类型列表：

   * 任意
   * 宾
   * blob
   * 布尔
   * 字节
   * CDATA
   * date
   * datetimetz
   * datetimenotz
   * 日期
   * DOMDocument
   * DOMElement
   * 多次
   * 枚举
   * 浮点
   * html
   * int64
   * 链接
   * long
   * 备忘录
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字符串
   * 时间
   * 时间跨平台
   * uuid

* **默认（字符串）**:默认值。 默认值也可以是枚举中定义的值之一。
* **desc（字符串）**:明细列表描述。
* **标签（字符串）**:枚举标签。
* **名称（字符串）**:枚举的内部名称。
* **模板（字符串）**:此属性定义对 `<enumeration>` 由多个架构共享的元素。 定义会自动复制到当前架构中。

## 示例 {#examples-4}

其值存储在数据库中的枚举值示例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

具有默认值的枚举的定义：

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
