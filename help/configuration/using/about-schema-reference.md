---
title: 关于Adobe Campaign Classic中的架构引用
description: 了解如何配置扩展架构以扩展Adobe Campaign Classic数据库的概念数据模型。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5130802f3723311bcd09e21fc405d298923dd20e

---


# 关于架构引用{#about-schema-reference}

本章介绍如何配置扩展架构以扩展Adobe Campaign数据库的概念数据模型。

要更好地了解Campaign内置表及其交互，请参阅 [Campaign Classic数据模型](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)。

XML描述了应用程序中所承载数据的物理和逻辑结构。 它遵循Adobe Campaign特有的语法（称为架构） ****。

架构是与数据库表关联的XML文档。 它定义了数据结构并描述了表的SQL定义：

* 表的名称
* 字段
* 索引
* 与其他表的链接

还描述了用于存储数据的XML结构：

* 元素和属性
* 元素层次
* 元素和属性类型
* 默认值
* 标签、说明和其他属性。

方案允许您定义数据库中的实体。 每个实体都有一个架构。

下图显示了Adobe Campaign数据系统中架构的位置：

![](assets/reference_schema_intro.png)

## 架构的语法 {#syntax-of-schemas}

架构的根元素为 **`<srcschema>`**。 它包含** **`<element>`** 和 **`<attribute>`** 子元素。

第一个 **`<element>`** 子元素与实体的根重合。

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
>实体的根元素与架构同名。

![](assets/s_ncs_configuration_schema_and_entity.png)

标 **`<element>`** 记定义实体元素的名称。 **`<attribute>`** 架构的标记定义已链接到的标记 **`<element>`** 中的属性名称。

## 架构的标识 {#identification-of-a-schema}

数据架构由其名称及其命名空间标识。

通过命名空间，您可以按感兴趣的区域对一组架构进行分组。 例如，cus命名 **空间用于** 特定于客户的配置(**客户**)。

>[!CAUTION]
>
>作为标准，命名空间的名称必须简明，且必须仅包含符合XML命名规则的授权字符。
>
>标识符不能以数字字符开头。

某些命名空间保留为Adobe Campaign应用程序操作所需的系统实体的说明：

* **xtk**:关于平台系统数据，
* **nl**:关于申请的整体使用，
* **nms**:关于交付（收件人、交付、跟踪等）,
* **ncm**:内容管理方面，
* **temp**:为临时架构保留。

架构的标识密钥是使用命名空间和冒号分隔的名称构建的字符串；例如： **cus:recipient**.
