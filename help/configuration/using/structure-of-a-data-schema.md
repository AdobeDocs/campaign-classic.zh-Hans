---
product: campaign
title: 数据模式的结构
description: 数据模式的结构
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# 数据模式的结构{#structure-of-a-data-schema}

数据模式的结构以树结构的形式显示。 要在Adobe Campaign客户端控制台中以图形方式查看该模式，请选择目标架构并单击&#x200B;**[!UICONTROL Structure]**&#x200B;子选项卡。

![](assets/d_ncs_integration_schema_arbo.png)

作为标准，将首先显示字段（“活动”、“已激活”等） 按字母顺序排列。 接下来是结构元素（邮政地址、位置），最后是链接（电子邮件信息、文件夹等）。

主键由红色键标识，外键由黄色键标识。

根据链接是否属于表，以图形方式对它们进行区分。 从表开始（即表中具有外键的表），首先显示（电子邮件信息、文件夹、国家/地区）。 “反向”收集链接（订阅、订购等） 显示在末尾。
