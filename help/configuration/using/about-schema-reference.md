---
product: campaign
title: 关于Adobe Campaign Classic中的模式引用
description: 了解如何配置扩展模式以扩展Adobe Campaign Classic数据库的概念数据模型
feature: Schema Extension
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 7%

---

# 关于模式参考{#about-schema-reference}

![](../../assets/v7-only.svg)

本章介绍如何配置扩展模式以扩展Adobe Campaign数据库的概念数据模型。

要更好地了解Campaign内置表及其交互情况，请参阅 [Campaign Classic数据模型](https://helpx.adobe.com/cn/campaign/kb/acc-datamodel.html).

应用中所承载数据的物理和逻辑结构以 XML 格式进行描述。它遵循Adobe Campaign特有的语法，称为 **模式**.

模式是与数据库表关联的XML文档。 它定义了数据结构并描述了表的SQL定义：

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

通过架构，您可以定义数据库中的实体。 每个实体都有一个架构。

下图显示了架构在Adobe Campaign数据系统中的位置：

![](assets/reference_schema_intro.png)

## 架构的语法 {#syntax-of-schemas}

架构的根元素为 **`<srcschema>`**. 它包含 **`<element>`** 和 **`<attribute>`** 子元素。

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

的 **`<element>`** 标记定义实体元素的名称。 **`<attribute>`** 架构的标记定义 **`<element>`** 标记。

## 模式的标识 {#identification-of-a-schema}

数据架构通过其名称及其命名空间进行标识。

命名空间允许您按关注区域对一组架构进行分组。 例如， **木槿** 命名空间用于客户特定的配置(**客户**)。

架构的标识键是使用命名空间和名称以冒号分隔的字符串；例如： **cus:recipient**.

>[!IMPORTANT]
>
>命名空间的名称必须简洁明了，且必须仅包含符合XML命名规则的授权字符。
>
>标识符不得以数字字符开头。
>
>以下命名空间是保留的，用于描述操作Adobe Campaign应用程序所需的系统实体，但不得使用： **xtk**, **nl**, **nms**, **ncm**, **临时**, **ncl**, **crm**, **xxl**.

