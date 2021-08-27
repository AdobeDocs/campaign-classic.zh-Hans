---
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

---

# 计算字符串元素 {#compute-string--element}

![](../../../assets/v7-only.svg)

## 内容模型 {#content-model-1}

compute-string:==EMPTY

## 属性 {#attributes-1}

@expr

## 父母 {#parents-1}

`<element>`

## 子项 {#children-1}

无

## 说明 {#description-1}

`<compute-string>`元素允许您根据XTK表达式生成字符串，以根据多个值在界面中显示“已构建”标签。

## 使用和使用上下文 {#use-and-context-of-use-1}

未定义`<compute-string>`时，默认情况下会输入`<compute-string>`元素，并在其中输入主键的值。

## 属性描述 {#attribute-description-1}

* **expr（字符串）**:XTK和/或Xpath表达式

## 示例 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

对收件人计算的字符串的结果：“John Doe(john.doe@aol.com)”：

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
