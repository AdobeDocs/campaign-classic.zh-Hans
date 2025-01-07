---
product: campaign
title: 架构元素和属性 — keyfield元素
description: keyfield元素
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# keyfield元素 {#keyfield--element}


## 内容模型 {#content-model-9}

keyfield：==EMPTY

## 属性 {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## 父项 {#parents-9}

`<key>` ， `<dbindex />`

## 子项 {#children-9}

无

## 说明 {#description-9}

此元素定义要集成到索引或键中的字段。

## 属性说明 {#attribute-description-9}

* **xlink (MNTOKEN)**：允许您自动引用关系表（N-N链接）的联接中定义的外键。
* **xpath (MNTOKEN)**： `<attribute>`元素上索引或键的定义。 此属性接收一个Xpath，它定义定义定义键或索引的架构属性的路径。

## 示例 {#examples-}

在索引中选择“sName”字段，其中Xpath位于“@name”上：

```
<keyfield xpath="@name"/>
```
