---
product: campaign
title: 元素和属性 — 计算字符串元素
description: 计算字符串元素
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 5%

---

# 计算字符串元素 {#compute-string--element}

![](../../../assets/v7-only.svg)

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
