---
product: campaign
title: 架构元素和属性
description: keyfield元素
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 2%

---

# keyfield元素 {#keyfield--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-9}

keyfield:==EMPTY

## 属性 {#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

## 父母 {#parents-9}

`<key>`  ,  `<dbindex />`

## 子项 {#children-9}

无

## 说明 {#description-9}

此元素定义要集成到索引或键中的字段。

## 属性描述 {#attribute-description-9}

* **xlink(MNTOKEN)**:允许您自动引用在连接中为关系表（N-N链接）定义的外键。
* **xpath(MNTOKEN)**:索引或键的定义 `<attribute>`  元素。 此属性接收一个Xpath，该Xpath定义用于定义键或索引的架构属性的路径。

## 示例 {#examples-}

在索引中选择“sName”字段，并在“@name”上使用Xpath:

```
<keyfield xpath="@name"/>
```
