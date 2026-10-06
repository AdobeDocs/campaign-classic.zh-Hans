---
product: campaign
title: 数据架构的结构
description: 数据架构的结构
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: 'https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%
---
# 数据架构的结构{#structure-of-a-data-schema}

数据模式的结构以树结构的形式显示。 要在Adobe Campaign客户端控制台中以图形方式查看架构，请选择目标架构并单击&#x200B;**[!UICONTROL Structure]**&#x200B;子选项卡。

![](assets/d_ncs_integration_schema_arbo.png)

作为标准，首先显示字段（活动、激活等） 并按字母顺序排列。 结构化元素紧随其后（邮政地址、位置），最后是链接（电子邮件信息、文件夹等）。

主键由红色键标识，外键由黄色键标识。

根据链接是否属于表，以图形方式区分这些链接。 首先显示从表格开始的字段，即在表格中具有外键的字段（电子邮件信息、文件夹、国家/地区）。 “反向”收藏链接（订阅、订单等） 在末尾显示。
