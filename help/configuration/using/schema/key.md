---
product: campaign
title: 架构元素和属性 — 关键元素
description: 关键元素
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# 关键元素 {#key--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-8}

key：==keyfield

## 属性 {#attributes-8}

* @allowEmptyPart（布尔型）
* @applicableIf（字符串）
* @internal（布尔型）
* @label（字符串）
* @name (MNTOKEN)
* @noDbIndex（布尔型）

## 父项 {#parents-8}

`<element>`

## 子项 {#children-8}

`<keyfield>`

## 说明 {#description-8}

利用此元素，可定义用于标识表中记录的键。

一个表必须至少有一个键。

## 使用和使用上下文 {#use-and-context-of-use-6}

作为规则，键在架构的主元素和索引之后声明。

如果一个键包含多个字段（即多个字段），则该键称为复合 `<keyfield>` 子项)。 请勿使用复合键来定义主键。

如果架构的主元素包含“@autopk=true”属性，则主键是唯一的。 每个架构只能有一个主密钥。

前1000个标识符是保留标识符，因此，如果需要为键定义值范围，请从1000开始。

## 属性描述 {#attribute-description-8}

* **allowEmptyPart（布尔值）**：对于复合键，如果激活此属性，则当其至少一个键不为空时，这些键被视为有效。 如果是这种情况，空概念值为“0”（布尔值或适用于所有类型的数值数据）。 默认情况下，需要输入构成组合键的所有键。
* **applicableIf（字符串）**：通过此属性，可将键设为可选。 它定义应用键定义的条件。 此属性接收XTK表达式。
* **internal（布尔型）**：如果已激活，则此属性可告知Adobe Campaign密钥是主密钥。
* **标签（字符串）**：键的标签。
* **名称(MNTOKEN)**：键的内部名称。
* **noDbIndex（布尔型）**：如果激活(noDbIndex=&quot;true&quot;)，则不会为匹配键的字段编制索引。

## 示例 {#examples-------}

授权“@expr”或“alias”字段为空的复合键的声明：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

中字符串类型的“名称”字段上的主键声明 `<srcschema>`  以及匹配的SQL查询：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
