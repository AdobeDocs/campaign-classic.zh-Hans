---
product: campaign
title: 架构元素和属性 — 枚举元素
description: 枚举元素
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
TQID: https://experienceleague.adobe.com/w8b-2HEtYRMOd9yHFLtvS0vS2tdLDzuIakLfrqImsGo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 198
ht-degree: 11%

---

# 枚举元素 {#enumeration--element}


## 内容模型 {#content-model-5}

枚举：==（help|值）

## 属性 {#attributes-5}

* @basetype（字符串）
* @default（字符串）
* @desc（字符串）
* @label（字符串）
* @name（字符串）
* @template（字符串）

## 父项 {#parents-5}

`<srcschema>`

## 子项 {#children-5}

* `<help>`
* `<value>`

## 说明 {#description-5}

此元素允许我们定义值枚举。 枚举属于在其中定义它的模式，但它可以通过另一个模式访问。

## 使用和使用环境 {#use-and-context-of-use-4}

枚举是在架构的开头定义的（在定义主元素之前）。

## 属性说明 {#attribute-description-5}

* **basetype （字符串）**：枚举中存储的值的类型。

  可用类型列表：

   * 任何
   * 纸盒
   * blob
   * 布尔值
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * 时间戳
   * 日期
   * DOMDocument
   * 圆顶元素
   * double
   * 枚举
   * float
   * html
   * int64
   * 链接
   * 长
   * 备忘录
   * MNTOKEN
   * 百分比
   * 主密钥
   * 短
   * 字符串
   * time
   * timespan
   * uuid

* **默认值（字符串）**：默认值。 默认值也可以是枚举中定义的值之一。
* **desc （字符串）**：枚举描述。
* **标签（字符串）**：枚举标签。
* **name （字符串）**：枚举的内部名称。
* **模板（字符串）**：此属性定义对由多个架构共享的`<enumeration>`元素的引用。 该定义会自动复制到当前架构中。

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
