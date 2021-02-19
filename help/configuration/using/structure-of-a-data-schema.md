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

数据模式的结构以树结构的形式显示。 要在Adobe Campaign客户端控制台中以图形方式视图模式，请选择目标，然后单击&#x200B;**[!UICONTROL Structure]**&#x200B;子选项卡。

![](assets/d_ncs_integration_schema_arbo.png)

作为标准，这些字段首先显示（活动、激活等） 按字母顺序排列。 接下来是结构化元素（邮政地址、位置），最后是链接（电子邮件信息、文件夹等）。

主键由红色键标识，外键由黄色键标识。

链接是否属于表，将以图形方式加以区分。 表中开始的表（即表中包含外键的表）首先显示（电子邮件信息、文件夹、国家/地区）。 “冲销”收集链接(订阅、订单等) 。
