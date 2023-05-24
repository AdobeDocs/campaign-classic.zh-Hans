---
product: campaign
title: 架构元素和属性 — 参数元素
description: 参数元素
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 7%

---

# 参数元素 {#param--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-12}

param：==help

## 属性 {#attributes-12}

* @_operation（字符串）
* @desc（字符串）
* @enum（字符串）
* @inout（字符串）
* @label（字符串）
* @localizable（字符串）
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type（字符串）

## 父项 {#parents-12}

`<parameters>`

## 子项 {#children-12}

`<help>`

## 说明 {#description-12}

利用此元素，可定义用于调用SOAP方法的参数。

## 属性描述 {#attribute-description-12}

* **desc（字符串）**：与有关的描述 `<param>` 元素。
* **inout（字符串）**：此属性定义参数是否在SOAP调用的输入(in)或输出(out)。 如果未指定此属性，则默认参数为输入(&quot;@inout=in&quot;)。
* **标签（字符串）**： `<param>` 标签
* **可本地化（字符串）**：如果激活，此属性会告知收集工具恢复“@label”属性的值以进行翻译（内部使用）。
* **名称(MNTOKEN)**：的内部名称 `<param>`
* **类型（字符串）**：此属性定义 `<param>` 元素

   可用类型列表：

   * 任何
   * 纸盒
   * blob
   * 布尔值
   * 字节
   * CDATA
   * datetime
   * datetimetz
   * datemenotz
   * date
   * DOMDocument
   * DOMElement
   * 多次
   * 枚举
   * 浮点数
   * html
   * int64
   * 链接
   * 长
   * 备忘录
   * MNTOKEN
   * percent
   * 主密钥
   * 短
   * 字符串
   * 时间
   * 时间跨度
   * uuid

## 示例 {#examples-9}

字符串类型的“serviceName”入站设置的定义：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
