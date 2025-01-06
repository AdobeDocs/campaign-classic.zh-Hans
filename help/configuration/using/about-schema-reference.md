---
product: campaign
title: 开始使用Adobe Campaign中的架构
description: 了解如何使用架构并扩展Adobe Campaign数据库的概念数据模型
feature: Schema Extension
role: Data Engineer, Developer
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 44c40bbd8bff16cbe220d3af3a7bb2847762f58b
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 1%

---

# 模式入门 {#about-schema-reference}

## 什么是架构 {#what-is-a-schema}

本章介绍如何配置扩展模式以扩展Adobe Campaign数据库的概念数据模型。

要更好地了解Campaign内置表及其交互，请参阅[Campaign Classic数据模型](about-data-model.md)。

在Adobe Campaign中，应用程序中所承载数据的物理和逻辑结构以XML形式进行描述。 **架构**&#x200B;是与数据库表关联的XML文档。 它定义数据结构并描述表的SQL定义：

* 表的名称
* 字段
* 索引
* 与其他表的链接

它还描述了用于存储数据的XML结构：

* 元素和属性
* 元素层次结构
* 元素和属性类型
* 默认值
* 标签、描述和其他属性。

使用架构可在数据库中定义实体。 每个实体都有一个架构。

下图显示了架构在Adobe Campaign数据系统中的位置：

![](assets/reference_schema_intro.png)

## 架构的语法 {#syntax-of-schemas}

架构的根元素为&#x200B;**`<srcschema>`**。 它包含&#x200B;**`<element>`**&#x200B;和&#x200B;**`<attribute>`**&#x200B;子元素。

第一个&#x200B;**`<element>`**&#x200B;子元素与实体的根一致。

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>实体的根元素与架构具有相同的名称。

![](assets/s_ncs_configuration_schema_and_entity.png)

**`<element>`**&#x200B;标记定义实体元素的名称。 架构的&#x200B;**`<attribute>`**&#x200B;标记定义&#x200B;**`<element>`**&#x200B;标记中已链接到的属性的名称。

## 架构的标识 {#identification-of-a-schema}

数据架构由其名称和命名空间来标识。

命名空间允许您按感兴趣的区域对一组架构进行分组。 例如，**cus**&#x200B;命名空间用于特定于客户的配置（**客户**）。

架构的标识键是使用命名空间和用冒号分隔的名称构建的字符串；例如： **cus：recipient**。

>[!IMPORTANT]
>
>* 命名空间的名称必须简洁，并且根据XML命名规则只能包含授权字符。
>
>* 标识符不能以数字字符开头。
>
>* 以下命名空间是为Adobe Campaign应用程序操作所需的系统实体描述而保留的，不得使用： **xtk**、**nl**、**nms**、**ncm**、**temp**、**ncl**、**crm**、**xxl**。
>
