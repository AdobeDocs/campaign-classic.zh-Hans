---
product: campaign
title: 数据模式的结构
description: 数据模式的结构
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# 数据模式的结构{#structure-of-a-data-schema}

数据模式的结构以树结构的形式显示。 要在Adobe Campaign客户端控制台中以图形方式查看架构，请选择目标架构并单击&#x200B;**[!UICONTROL Structure]**&#x200B;子选项卡。

![](assets/d_ncs_integration_schema_arbo.png)

作为标准，首先显示字段（活动、激活等） 并按字母顺序排列。 结构化元素紧随其后（邮政地址、位置），最后是链接（电子邮件信息、文件夹等）。

主键由红色键标识，外键由黄色键标识。

根据链接是否属于表，以图形方式区分这些链接。 首先显示从表格开始的字段，即在表格中具有外键的字段（电子邮件信息、文件夹、国家/地区）。 “反向”收藏链接（订阅、订单等） 在末尾显示。
