---
solution: Campaign Classic
product: campaign
title: 关于Adobe Campaign Classic模式参考
description: 了解如何配置扩展模式以扩展Adobe Campaign Classic数据库的概念数据模型。
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 7%

---


# 关于模式参考{#about-schema-reference}

本章介绍如何配置扩展模式以扩展Adobe Campaign库的概念数据模型。

要更好地了解活动内置表及其交互，请参阅 [Campaign Classic数据模型](https://helpx.adobe.com/cn/campaign/kb/acc-datamodel.html)。

应用中所承载数据的物理和逻辑结构以 XML 格式进行描述。It obeys a grammar specific to Adobe Campaign, called a **schema**.

模式是与数据库表关联的XML文档。 它定义数据结构并描述表的SQL定义：

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

模式允许您在数据库中定义实体。 每个实体都有一个模式。

下图显示了模式在Adobe Campaign数据系统中的位置：

![](assets/reference_schema_intro.png)

## 模式语法 {#syntax-of-schemas}

模式的根元素为 **`<srcschema>`**。 它包含 **`<element>`** 和 **`<attribute>`** 子元素。

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
>实体的根元素与模式同名。

![](assets/s_ncs_configuration_schema_and_entity.png)

标 **`<element>`** 记定义实体元素的名称。 **`<attribute>`** 模式的标记定义已链接到的标 **`<element>`** 记中属性的名称。

## 模式 {#identification-of-a-schema}

数据模式由其名称和命名空间标识。

命名空间允许您按兴趣区域对一组模式进行分组。 例如，自定义 **命名空间** （客户）用于特定于客&#x200B;**户的配置**。

>[!IMPORTANT]
>
>作为标准，命名空间的名称必须简洁明了，并且必须只包含符合XML命名规则的授权字符。
>
>标识符不能以数字字符开头。

某些命名空间保留为操作Adobe Campaign应用程序所需的系统实体的说明：

* **xtk**:平台系统数据方面，
* **nl**:涉及申请的整体使用，
* **nms**:投放(收件人、投放、跟踪等),
* **ncm**:内容管理,
* **临时**:为临时模式保留。

模式的标识键是使用命名空间和冒号分隔的名称构建的字符串；例如： **cus:收件人**。
