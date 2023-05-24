---
product: campaign
title: 元素和属性 — srcschema元素
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# srcschema元素 {#srcschema--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-14}

srcSchema：==(属性 |创建者 |数据 |元素 |明细列表 |帮助 |界面 |方法 |修改者)

## 属性 {#attributes-14}

created (datetime)、createdBy-id (long)、desc (string)、entitySchema (string)、extendedSchema (string)、img (string)、implements (string)、label (string)、labelSingular (string)、lastModified (datetime)、library (boolean)、mappingType (string)、modifiedBy-id (long)、name (string)、namespace (string)、useRecycleBin (booleg)、view (boolean)、view (boolean)、xtkschema (string (string)

## 父项 {#parents-14}

无

## 子项 {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## 说明 {#description-14}

此 `<srcschema>` 是架构的根元素。 它是定义架构的输入点。

## 使用和使用上下文 {#use-and-context-of-use-9}

架构演示文稿在以下位置提供： [关于模式参考](../../../configuration/using/about-schema-reference.md) 和 [模式结构](../../../configuration/using/schema-structure.md).

## 属性描述 {#attribute-description-14}

* **已创建(datetime)**：此属性提供有关架构创建日期和时间的信息。 它具有“日期时间”表单。 显示的值取自服务器。 时间以UTC格式显示。
* **createdBy-id (long)**：创建架构的操作员的标识符。
* **desc（字符串）**：架构描述
* **entitySchema（字符串）**：语法和审批所基于的基本架构(对于Adobe Campaign，默认为：xtk：srcSchema)。 保存当前架构时，Adobe Campaign将批准其语法，并在@xtkschema属性中声明架构。
* **extendedSchema（字符串）**：接收当前架构扩展所基于的现成架构的名称。 格式为“namespace：name”。
* **img（字符串）**：链接到架构的图标（可以在架构创建向导中定义）。
* **标签（字符串）**：架构标签。
* **labelSingular（字符串）**：在界面中显示的标签（单数）。
* **lastModified (datetime)**：此属性提供有关上次修改的日期和时间的信息。 它具有“日期时间”表单。 显示的值取自服务器。 时间以UTC格式显示。
* **库（布尔型）**：将架构用作库而不是实体。 因此，由于“@ref”和“@template”属性，其他架构可能会引用此架构。
* **mappingType（字符串）**：

   * &quot;sql&quot;：数据库映射
   * &quot;textFile&quot;：文本文件映射
   * “xmlFile”： XML格式文本文件映射
   * &quot;binaryFile&quot;：二进制文件映射

* **modifiedBy-id (long)**：匹配更改了架构的运算符的标识符。
* **名称（字符串）**：唯一的架构名称。
* **命名空间（字符串）**：架构的命名空间（默认：nms、xtk、nl）。 为项目创建新架构时，我们建议您使用专用命名空间。
* **useRecycleBin（布尔值）**：在应用程序中激活垃圾桶功能。 删除的记录将在最终删除之前放入垃圾桶中。 此函数仅在“交付”模式下可用。
* **视图（布尔值）**：如果激活(@view=&quot;true&quot;)，则架构将用作视图。 数据库结构更新向导不会将架构考虑在内。 此选项主要用于引用外部表。
* **xtkschema（字符串）**：定义架构语法的架构的名称（默认为xtk：srcSchema）。

## 示例 {#examples-11}

`<srcschema>` “nms：delivery”现成架构的元素

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
