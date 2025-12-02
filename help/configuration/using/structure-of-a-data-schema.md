---
product: campaign
title: 数据架构的结构
description: 数据架构的结构
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# 数据架构的结构{#structure-of-a-data-schema}

数据模式的结构以树结构的形式显示。 要在Adobe Campaign客户端控制台中以图形方式查看架构，请选择目标架构并单击&#x200B;**[!UICONTROL Structure]**&#x200B;子选项卡。

![](assets/d_ncs_integration_schema_arbo.png)

作为标准，这些字段首先显示（活动、已激活等），并按字母顺序显示。 结构化元素紧随其后（邮政地址、位置），最后是链接（电子邮件信息、文件夹等）。

主键由红色键标识，外键由黄色键标识。

根据链接是否属于表，以图形方式区分这些链接。 首先显示从表格开始的字段，即在表格中具有外键的字段（电子邮件信息、文件夹、国家/地区）。 “反向”收藏链接（订阅、订单等）显示在末尾。
