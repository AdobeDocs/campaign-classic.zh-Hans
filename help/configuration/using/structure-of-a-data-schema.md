---
title: 数据模式的结构
seo-title: 数据模式的结构
description: 数据模式的结构
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 13%

---


# 数据模式的结构{#structure-of-a-data-schema}

数据模式的结构以树结构的形式显示。 要在视图客户端控制台中以图形方式Adobe Campaign模式，请选择目标，然 **[!UICONTROL Structure]** 后单击子选项卡。

![](assets/d_ncs_integration_schema_arbo.png)

作为标准，字段首先显示（活动、已激活等） 按字母顺序排列。 接下来是结构元素（邮政地址、位置），最后是链接（电子邮件信息、文件夹等）。

主键由红色键标识，外键由黄色键标识。

链接是否属于表，以图形方式进行区分。 来自表的开始（即表中有外键）将首先显示（电子邮件信息、文件夹、国家／地区）。 “颠倒”收集链接(订阅、订单等) 显示。
