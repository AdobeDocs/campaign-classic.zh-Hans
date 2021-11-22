---
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 2%

---

# 键元素 {#key--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-8}

键：==keyfield

## 属性 {#attributes-8}

* @allowEmptyPart（布尔）
* @applicableIf（字符串）
* @internal（布尔）
* @label（字符串）
* @name(MNTOKEN)
* @noDbIndex（布尔）

## 父母 {#parents-8}

`<element>`

## 子项 {#children-8}

`<keyfield>`

## 说明 {#description-8}

利用此元素，可定义用于标识表中记录的键。

表必须至少具有一个键。

## 使用和使用上下文 {#use-and-context-of-use-6}

通常，键值会在架构的主元素和索引之后声明。

如果键包含多个字段(即多个 `<keyfield>` 孩子)。 请勿使用复合键来定义主键。

如果架构的主元素包含“@autopk=true”属性，则主键是唯一的。 每个架构只能有一个主键。

前1000个标识符是保留的，因此，如果需要为键定义一系列值，则从1000开始。

## 属性描述 {#attribute-description-8}

* **allowEmptyPart（布尔值）**:对于复合键，如果激活此属性，则当其至少一个键不为空时，它们的键将被视为有效。 如果是这种情况，则空概念值为“0”（布尔值或所有类型的数值数据）。 默认情况下，需要输入构成复合键的所有键。
* **appliableIf（字符串）**:此属性允许您使键为可选项。 它定义了将应用键定义的条件。 此属性接收XTK表达式。
* **内部（布尔）**:如果激活了该键，则此属性会告知Adobe Campaign键是主键。
* **标签（字符串）**:键的标签。
* **name(MNTOKEN)**:密钥的内部名称。
* **noDbIndex（布尔）**:如果激活它(noDbIndex=&quot;true&quot;)，则不会为与键值匹配的字段编入索引。

## 示例 {#examples-------}

复合键的声明，该键授权“@expr”或“alias”字段为空：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

在 `<srcschema>`  和匹配的SQL查询：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
