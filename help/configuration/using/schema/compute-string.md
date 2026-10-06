---
product: campaign
title: 元素和属性 — 计算字符串元素
description: 计算字符串元素
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
TQID: 'https://experienceleague.adobe.com/vLSA9oDdBg-0sElc6QlusY-YviNyRU8Fq6yXRrFrN1g'
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
source-wordcount: '95'
ht-degree: 5%
---
# 计算字符串元素 {#compute-string--element}


## 内容模型 {#content-model-1}

compute-string：==EMPTY

## 属性 {#attributes-1}

@expr

## 父项 {#parents-1}

`<element>`

## 子项 {#children-1}

无

## 说明 {#description-1}

通过`<compute-string>`元素，可生成基于XTK表达式的字符串，以根据多个值在界面中显示“生成”标签。

## 使用和使用环境 {#use-and-context-of-use-1}

如果未定义`<compute-string>`，则默认情况下将输入架构中主键值的`<compute-string>`元素。

## 属性说明 {#attribute-description-1}

* **expr （字符串）**： XTK和/或Xpath表达式

## 示例 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

对收件人计算的字符串结果：“John Doe (john.doe@aol.com)”：

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
