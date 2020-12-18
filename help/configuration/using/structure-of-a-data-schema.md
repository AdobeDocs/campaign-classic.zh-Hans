---
solution: Campaign Classic
product: campaign
title: 数据模式的结构
description: 数据模式的结构
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---


# 数据模式的结构{#structure-of-a-data-schema}

数据模式的结构以树结构的形式显示。 要在视图客户端控制台中以图形方式对其进行Adobe Campaign，请选择目标模式，然后单击&#x200B;**[!UICONTROL Structure]**&#x200B;子选项卡。

![](assets/d_ncs_integration_schema_arbo.png)

作为标准，字段首先显示（活动、已激活等） 按字母顺序排列。 接下来是结构元素（邮政地址、位置），最后是链接（电子邮件信息、文件夹等）。

主键由红色键标识，外键由黄色键标识。

链接是否属于表，通过图形方式进行区分。 来自表的开始（即表中有外键）将首先显示（电子邮件信息、文件夹、国家／地区）。 “颠倒”收集链接(订阅、订单等) 显示。
