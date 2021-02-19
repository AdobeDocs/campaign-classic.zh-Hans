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
source-wordcount: '454'
ht-degree: 1%

---


# srcschema元素{#srcschema--element}

## 内容模型{#content-model-14}

srcSchema:==(attribute |创建者 |数据 |元素 |明细列表 |帮助 |界面 |方法 | modifiedBy)

## 属性{#attributes-14}

created(datetime)、createdBy-id(long)、desc(string)、entitySchema(string)、extendedSchema(string)、img(string)、implements(string)、labelSingular(string)、lastModified(datetime)、库(string)、mappingType(string)、modifiedBy-id(l、name(string)、string(string)、name(string)、string、string、命名空间(string)、)、useRecycleBin（布尔）、视图（布尔）、xtkschema（字符串）

## 父项{#parents-14}

无

## 子项{#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## 说明{#description-14}

`<srcschema>`是模式的根元素。 它是定义模式的输入点。

## 使用和上下文{#use-and-context-of-use-9}

模式演示在[关于模式引用](../../../configuration/using/about-schema-reference.md)和[模式结构](../../../configuration/using/schema-structure.md)中可用。

## 属性描述{#attribute-description-14}

* **created(datetime)**:此属性提供有关创建模式的日期和时间的信息。它有一个“日期时间”表单。 显示的值取自服务器。 时间以UTC格式显示。
* **createdBy-id(long)**:是创建模式的运算符的标识符。
* **desc(string**):模式描述
* **entitySchema(string)**:基本模式(默认情况下，Adobe Campaign:xtk:srcSchema)。保存当前模式时，Adobe Campaign将使用在@xtkschema属性中声明的模式批准其语法。
* **extendedSchema(string)**:接收当前模式扩展所基于的现成模式的名称。表单为“命名空间：名称”。
* **img(string)**:链接到模式的图标(可在模式创建向导中定义)。
* **label(string**):模式标签。
* **labelSingular(string)**:标签（单数），用于在界面中显示。
* **lastModified(datetime)**:此属性提供有关上次修改的日期和时间的信息。它有一个“日期时间”表单。 显示的值取自服务器。 时间以UTC格式显示。
* **库（布尔值）**:将模式用作库而非实体。因此，由于“@ref”和“@template”属性，其他模式可能会引用此模式。
* **mappingType(string)**:

   * &quot;sql&quot;:数据库映射
   * &quot;textFile&quot;:文本文件映射
   * &quot;xmlFile&quot;:XML格式文本文件映射
   * &quot;binaryFile&quot;:二进制文件映射

* **modifiedBy-id(long)**:匹配更改模式的运算符的标识符。
* **name(string)**:唯一模式名称。
* **命名空间（字符串）**:命名空间模式(默认：nms， xtk， nl)。为项目创建新模式时，建议您使用专用命名空间。
* **useRecycleBin（布尔值）**:在应用程序中激活垃圾桶功能。删除的记录将放在垃圾桶中，最后删除。 此函数仅在“投放”模式下可用。
* **视图（布尔值）**:如果激活了该模式(@view=&quot;true&quot;)，则该视图将用作模式库结构更新向导将不考虑数据。 此选项主要用于引用外部表。
* **xtkschema(字符串**:定义模式语法的模式的名称（默认情况下为xtk:srcSchema）。

## 示例{#examples-11}

`<srcschema>` “nms:投放”的元素开箱即用模式

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
