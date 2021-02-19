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
source-wordcount: '89'
ht-degree: 8%

---


# compute-string元素{#compute-string--element}

## 内容模型{#content-model-1}

compute-string:==EMPTY

## 属性{#attributes-1}

@expr

## 父项{#parents-1}

`<element>`

## 子项{#children-1}

无

## 说明{#description-1}

`<compute-string>`元素允许您根据XTK表达式生成字符串，以根据多个值在接口中显示“built”标签。

## 使用和上下文{#use-and-context-of-use-1}

如果未定义`<compute-string>`，则默认情况下将输入`<compute-string>`元素，并在模式中输入主键值。

## 属性描述{#attribute-description-1}

* **expr(字符串**):XTK和/或Xpath表达式

## 示例{#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

在收件人上计算的字符串结果：“John Doe(john.doe@aol.com)”：

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
