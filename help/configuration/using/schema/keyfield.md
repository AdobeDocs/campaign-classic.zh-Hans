---
product: campaign
title: 架构元素和属性 — keyfield元素
description: keyfield元素
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
TQID: 'https://experienceleague.adobe.com/tVWLlgg97dREZZHvUW81FhDVhS-uNvUHlbhH0YBrAdY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 6%
---
# keyfield元素 {#keyfield--element}


## 内容模型 {#content-model-9}

keyfield：==EMPTY

## 属性 {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## 父项 {#parents-9}

`<key>`  ,  `<dbindex />`

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
