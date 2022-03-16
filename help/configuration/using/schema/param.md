---
product: campaign
title: 架构元素和属性 — 参数元素
description: 参数元素
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 2%

---

# 参数元素 {#param--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-12}

参数：==帮助

## 属性 {#attributes-12}

* @_operation（字符串）
* @desc（字符串）
* @enum（字符串）
* @inout（字符串）
* @label（字符串）
* @localizable（字符串）
* @name(MNTOKEN)
* @namespace(MNTOKEN)
* @type（字符串）

## 父母 {#parents-12}

`<parameters>`

## 子项 {#children-12}

`<help>`

## 说明 {#description-12}

利用此元素，可定义用于调用SOAP方法的参数。

## 属性描述 {#attribute-description-12}

* **desc（字符串）**:与相关的描述 `<param>` 元素。
* **输入（字符串）**:此属性定义参数是否位于SOAP调用的输入（输入）或输出（输出）。 如果未指定此属性，则输入默认参数(&quot;@inout=in&quot;)。
* **标签（字符串）**: `<param>` 标签
* **可本地化（字符串）**:如果激活了该属性，则此属性将告知收集工具恢复“@label”属性的值以进行翻译（内部使用）。
* **name(MNTOKEN)**:内部名称 `<param>`
* **类型（字符串）**:此属性定义 `<param>` 元素

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

## 示例 {#examples-9}

字符串类型的“serviceName”集客设置的定义：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
