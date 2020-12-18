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
source-wordcount: '0'
ht-degree: 0%

---


# 参数元素{#param--element}

## 内容模型{#content-model-12}

param:==帮助

## 属性{#attributes-12}

* @_operation（字符串）
* @desc（字符串）
* @enum（字符串）
* @inout（字符串）
* @label(string)
* @localizable（字符串）
* @name(MNTOKEN)
* @命名空间(MNTOKEN)
* @type（字符串）

## 父项{#parents-12}

`<parameters>`

## 子项{#children-12}

`<help>`

## 说明{#description-12}

此元素允许您定义用于调用SOAP方法的参数。

## 属性描述{#attribute-description-12}

* **desc(string)**:与元素相关的 `<param>` 说明。
* **inout（字符串）**:此属性定义参数是否位于SOAP调用的输入（输入）或输出（输出）。如果未指定此属性，则输入默认参数(&quot;@inout=in&quot;)。
* **label(string)**: `<param>` 标签
* **localizable（字符串）**:如果激活了该属性，则此属性会告知集合工具恢复“@label”属性的值以进行转换（内部使用）。
* **name(MNTOKEN)**:内部名称  `<param>`
* **type(string)**:此属性定义元素的类 `<param>` 型

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

## 示例{#examples-9}

字符串类型“serviceName”入站设置的定义：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
