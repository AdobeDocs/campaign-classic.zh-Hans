---
product: campaign
title: 了解Adobe Campaign中的架构结构
description: 架构结构
feature: Custom Resources
role: Developer
audience: configuration
content-type: reference
level: Intermediate, Experienced
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
TQID: 'https://experienceleague.adobe.com/dFZ38qRKX-4vTEYS9GosS5TdW-XhnoIq8ckbjnNEJmo'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 6%
---
# 了解架构结构 {#schema-structure}

本页列出了Adobe Campaign数据类型如何映射到每个数据库管理系统的数据类型。

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关架构结构的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure){target=_blank}

## 映射Adobe Campaign/DBMS数据的类型 {#mapping-the-types-of-adobe-campaign-dbms-data}

下表列出了Adobe Campaign为各种数据库管理系统生成的数据类型的映射。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 字符串<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2 （NVARCHAR2，如果是unicode）<br /> </td> 
  </tr> 
  <tr> 
   <td> 布尔值<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 数字(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 字节<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 数字(3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 短<br /> </td> 
   <td> SMALLINT<br /> </td> 
   <td> 数字(5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 双精度<br /> </td> 
   <td> 双精度<br /> </td> 
   <td> 浮点数<br /> </td> 
  </tr> 
  <tr> 
   <td> 长<br /> </td> 
   <td> 整数<br /> </td> 
   <td> 数字(10)<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> BIGINT<br /> </td> 
   <td> 数字(20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间<br /> </td> 
   <td> 时间<br /> </td> 
   <td> 浮点数<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期时间<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> 日期<br /> </td> 
  </tr> 
  <tr> 
   <td> Datetimenotz<br /> </td> 
   <td> 时间戳<br /> </td> 
   <td> 日期<br /> </td> 
  </tr> 
  <tr> 
   <td> 时间跨度<br /> </td> 
   <td> 双精度<br /> </td> 
   <td> 浮点数<br /> </td> 
  </tr> 
  <tr> 
   <td> 备忘录<br /> </td> 
   <td> 文本<br /> </td> 
   <td> CLOB （Unicode时为NCLOB）<br /> </td> 
  </tr> 
  <tr> 
   <td> Blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 了解详情

浏览以下链接以了解更多信息：

* [架构入门](about-schema-reference.md)
* [数据库映射](database-mapping.md)
* [链接管理](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/developer/schemas-forms/database-links){target="_blank"}（Campaign v8文档）
* [密钥管理](database-keys.md)
