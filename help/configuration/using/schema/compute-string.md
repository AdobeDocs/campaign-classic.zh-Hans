---
solution: Campaign Classic
product: campaign
title: 元素和属性
description: 元素和属性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 9%

---


# `<compute-string>` 元素  {#compute-string--element}

## 内容模型{#content-model-1}

compute-string:==EMPTY

## 属性{#attributes-1}

@expr

## 父项{#parents-1}

`<element>`

## 子项{#children-1}

无

## 说明{#description-1}

`<compute-string>`元素允许您根据XTK表达式生成字符串，以根据多个值在接口中显示“内置”标签。

## 使用和使用上下文{#use-and-context-of-use-1}

如果未定义`<compute-string>`，则默认情况下会输入`<compute-string>`元素，并在模式中输入主键的值。

## 属性描述{#attribute-description-1}

* **expr(string)**:XTK和／或Xpath表达式

## 示例{#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

在收件人上计算的字符串结果：“John Doe(john.doe@aol.com)”:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
