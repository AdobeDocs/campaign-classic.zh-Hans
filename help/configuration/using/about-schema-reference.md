---
product: campaign
title: 开始使用Adobe Campaign中的架构
description: 了解如何使用架构并扩展Adobe Campaign数据库的概念数据模型
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
TQID: 'https://experienceleague.adobe.com/ikQVjdkvhTM-361S7mcpRYsuhpqjHxX-Y-9wdRCYldg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 3%
---
# 架构入门 {#about-schema-reference}

## 什么是架构 {#what-is-a-schema}

本章介绍如何配置扩展模式以扩展Adobe Campaign数据库的概念数据模型。

要更好地了解Campaign内置表及其交互，请参阅[Campaign Classic数据模型](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/datamodel){target="_blank"}（Campaign v8文档）。

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

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解架构的语法和标识，请参阅[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}
