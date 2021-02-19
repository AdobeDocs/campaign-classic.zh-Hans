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
source-wordcount: '175'
ht-degree: 6%

---


# param元素{#param--element}

## 内容模型{#content-model-12}

param:==help

## 属性{#attributes-12}

* @_operation(string)
* @desc(string)
* @enum(string)
* @inout(string)
* @label(string)
* @localizable(string)
* @name(MNTOKEN)
* @namespace(MNTOKEN)
* @type(string)

## 父项{#parents-12}

`<parameters>`

## 子项{#children-12}

`<help>`

## 说明{#description-12}

通过此元素，可以定义一个参数以调用SOAP方法。

## 属性描述{#attribute-description-12}

* **desc(string**):与元素相关的 `<param>` 描述。
* **inout(字符串**):此属性定义参数是否位于SOAP调用的输入(in)或输出(out)。如果未指定此属性，则默认参数为输入(&quot;@inout=in&quot;)。
* **label(string**): `<param>` 标签
* **localizable(字符串**)如果激活了该属性，则此属性会告知收集工具恢复“@label”属性的值，以用于翻译（内部使用）。
* **name(MNTOKEN)**:内部名称  `<param>`
* **type(string)**:此属性定义元素的类 `<param>` 型

   列表可用类型：

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

## 示例{#examples-9}

字符串类型“serviceName”入站设置的定义：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
