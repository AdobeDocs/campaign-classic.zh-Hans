---
product: campaign
title: 数据库映射
description: 数据库映射
feature: Configuration, Instance Settings
role: Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
TQID: 'https://experienceleague.adobe.com/d3oQ8zJVsjVdj9PZ30rQ8hEuern1l3ZlMAWrbymhnvs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 6%
---
# 数据库映射{#database-mapping}

此页介绍如何在方案的字段中声明索引。

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关架构的SQL映射的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/developer/schemas-forms/database-mapping){target=_blank}

## 索引字段 {#indexed-fields}

通过索引，可以优化应用程序中使用的SQL查询的性能。

从数据架构的主元素声明索引。

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

索引遵循以下规则：

* 索引可以引用表中的一个或多个字段
* 如果&#x200B;**unique**&#x200B;属性包含值“true”，则所有字段中的索引都可以是唯一的（以避免重复）
* 索引的SQL名称由表的SQL名称和索引的名称确定

>[!NOTE]
>
>* 作为标准，索引是从架构的主元素声明的第一个元素。
>
>* 在表映射期间（标准或FDA）自动创建索引。

**示例**：

* 向电子邮件地址和城市添加索引：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* 向“id”名称字段添加唯一索引：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## 了解详情

浏览以下链接以了解更多信息：

* [架构入门](about-schema-reference.md)
* [架构结构](schema-structure.md)
* [密钥管理](database-keys.md)
* [链接管理](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"}（Campaign v8文档）
