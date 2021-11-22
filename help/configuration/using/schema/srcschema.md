---
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---

# srschema元素 {#srcschema--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-14}

srcSchema:==(attribute) | createdBy |数据 |元素 |枚举 |帮助 |界面 |方法 | modifiedBy)

## 属性 {#attributes-14}

已创建(datetime)、createdBy-id(long)、desc(string)、entitySchema(string)、extendedSchema(string)、img(string)、实施(string)、标签(string)、labelSingular(string)、lastModified(datetime)、库(boolean)、mappingType(string)、modifiedBy-id(long)、名称(string)、napespace(syRing)、view(booleneyBey(boole)、view(string)、xtkschema(string)、xtkschema(string)

## 父母 {#parents-14}

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

的 `<srcschema>` 是架构的根元素。 它是定义架构的输入点。

## 使用和使用上下文 {#use-and-context-of-use-9}

架构演示可在 [关于模式参考](../../../configuration/using/about-schema-reference.md) 和 [模式结构](../../../configuration/using/schema-structure.md).

## 属性描述 {#attribute-description-14}

* **已创建(datetime)**:此属性提供有关架构创建日期和时间的信息。 它有一个“日期时间”窗体。 显示的值取自服务器。 时间以UTC格式显示。
* **createdBy-id(long)**:是创建架构的运算符的标识符。
* **desc（字符串）**:架构描述
* **entitySchema（字符串）**:语法和批准所基于的基本架构(对于Adobe Campaign，默认为：xtk:srcSchema)。 保存当前架构时，Adobe Campaign将批准其语法，并在@xtkschema属性中声明该架构。
* **extendedSchema（字符串）**:接收当前模式扩展所基于的现成模式的名称。 表单为“namespace:name”。
* **img（字符串）**:链接到架构的图标（可在架构创建向导中定义）。
* **标签（字符串）**:架构标签。
* **labelSingular（字符串）**:标签（单数），用于在界面中显示。
* **lastModified(datetime)**:此属性提供有关上次修改的日期和时间的信息。 它有一个“日期时间”窗体。 显示的值取自服务器。 时间以UTC格式显示。
* **库（布尔）**:将架构用作库，而不是实体。 因此，由于“@ref”和“@template”属性，其他架构可能会引用此架构。
* **mappingType（字符串）**:

   * &quot;sql&quot;:数据库映射
   * &quot;textFile&quot;:文本文件映射
   * &quot;xmlFile&quot;:XML格式文本文件映射
   * &quot;binaryFile&quot;:二进制文件映射

* **modifiedBy-id(long)**:匹配更改架构的运算符的标识符。
* **名称（字符串）**:唯一架构名称。
* **命名空间（字符串）**:架构的命名空间(默认：nms， xtk， nl)。 在为项目创建新架构时，我们建议您使用专用命名空间。
* **useRecycleBin（布尔值）**:在应用程序中激活垃圾桶功能。 在最终删除之前，已删除的记录将被放入垃圾桶中。 此函数仅在“交付”模式下可用。
* **视图（布尔值）**:如果激活了该模式(@view=&quot;true&quot;)，则将该模式用作视图。 数据库结构更新向导将不考虑架构。 此选项主要用于引用外部表。
* **xtkschema（字符串）**:定义模式语法的模式的名称（默认情况下为xtk:srcSchema）。

## 示例 {#examples-11}

`<srcschema>` “nms:delivery”模式的元素

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
