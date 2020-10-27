---
title: 建议
seo-title: 建议
description: 建议
seo-description: null
page-status-flag: never-activated
uuid: d898fe6d-7627-405f-b2bc-b17bf1dc9e96
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: a31c5c9f-503f-4b55-8409-34d4addbd581
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 3%

---


# 建议{#recommendations}

Adobe Campaign是高事务性系统（OLTP数据库）。 这意味着基础数据库将经常更新，导致性能随时间的推移而下降。 要避免此类问题，必须定期维护数据库。

>[!IMPORTANT]
>
>只有在定期维护数据库时，数据库才能以最佳方式运行。 某些RDBMS提供的自动维护是不够的，而且不能取代任何关系型数据库事务管理系统的深入维护。
>  
>本文档描述的程序是建议。 维护计划是数据库管理员的责任，在出现问题时，管理员必须是您的第一个联系人。
