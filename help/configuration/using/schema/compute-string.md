---
product: campaign
title: 元素和属性
description: 计算字符串元素
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 6%

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

的 `<compute-string>` 元素允许您根据XTK表达式生成字符串，以根据多个值在界面中显示“已构建”标签。

## 使用和使用上下文 {#use-and-context-of-use-1}

否时 `<compute-string>` 定义 `<compute-string>` 默认情况下，元素输入为架构中主键的值。

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
