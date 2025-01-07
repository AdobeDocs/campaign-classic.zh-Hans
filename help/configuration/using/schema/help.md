---
product: campaign
title: 架构元素和属性 — 帮助元素
description: 帮助元素
feature: Schema Extension
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 12%

---

# 帮助元素 {#help--element}


## 内容模型 {#content-model-6}

help：==EMPTY

## 属性 {#attributes-6}

无

## 父项 {#parents-6}

`<srcschema>` ， `<element>`   ，   `<attribute>`    ，    `<enumeration>`     ，     `<value>`      ，     `<param />`，      `<method />`

## 子项 {#children-6}

无

## 说明 {#description-6}

此元素允许您描述`<element>`或`<attribute>`   元素。 它只能包含文本，并以XML形式存储在数据库中。

## 属性说明 {#attribute-description-6}

此元素没有属性。

## 示例 {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
