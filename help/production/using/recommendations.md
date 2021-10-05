---
product: campaign
title: 推荐
description: 推荐
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# 推荐{#recommendations}

![](../../assets/v7-only.svg)

Adobe Campaign是一个高事务性系统（OLTP数据库）。 这意味着基础数据库将经常更新，导致性能随时间的推移而下降。 为避免出现此类问题，需要定期维护数据库。

>[!IMPORTANT]
>
>只有定期维护数据库，数据库才能发挥最佳性能。 某些RDBMS提供的自动维护是不够的，而且不能取代任何关系数据库事务管理系统的深入维护。
>  
>本文件中描述的程序是建议。 维护计划由数据库管理员负责，在出现问题时，必须由管理员提供第一个联系人。
