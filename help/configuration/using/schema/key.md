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
source-wordcount: '317'
ht-degree: 2%

---


# 键元素{#key--element}

## 内容模型{#content-model-8}

key:==keyfield

## 属性{#attributes-8}

* @allowEmptyPart（布尔值）
* @applicableIf(string)
* @internal（布尔值）
* @label(string)
* @name(MNTOKEN)
* @noDbIndex（布尔值）

## 父项{#parents-8}

`<element>`

## 子项{#children-8}

`<keyfield>`

## 说明{#description-8}

此元素允许您定义用于标识表中记录的键。

表必须至少具有一个键。

## 使用和上下文{#use-and-context-of-use-6}

通常，键在模式的主要元素和索引之后声明。

如果密钥包含多个字段（即多个`<keyfield>`子项），则称为复合键。 请勿使用复合键定义主键。

如果模式的主元素包含“@autopk=true”属性，则主键是唯一的。 每个模式只能有一个主键。

保留前1000个标识符，因此如果需要为键定义值范围，开始为1000。

## 属性描述{#attribute-description-8}

* **allowEmptyPart(boolean)**:对于复合键，如果激活了此属性，则如果其至少一个键不为空，则这些键被视为有效。如果是，则空概念值为“0”（布尔值或所有类型的数值数据）。 默认情况下，组成复合键的所有键都需要输入。
* **applicableIf(string)**:此属性允许您使键成为可选项。它定义将应用键定义的条件。 此属性接收XTK表达式。
* **internal(boolean)**:如果激活了该属性，则此属性会让Adobe Campaign知道该键是主键。
* **label(string**):键的标签。
* **name(MNTOKEN)**:密钥的内部名称。
* **noDbIndex（布尔值）**:如果激活(noDbIndex=&quot;true&quot;)，则将不索引与键匹配的字段。

## 示例{#examples-------}

授权“@expr”或“alias”字段为空的复合键的声明：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

在`<srcschema>`中STRING类型的“Name”字段和匹配的SQL查询中声明主键：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
