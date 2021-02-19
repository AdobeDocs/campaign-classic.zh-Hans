---
solution: Campaign Classic
product: campaign
title: 建议
description: 建议
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---


# 建议{#recommendations}

Adobe Campaign是一个高度事务性系统（OLTP数据库）。 这意味着基础数据库将经常更新，导致性能随时间推移而降低。 要避免此类问题，必须定期维护数据库。

>[!IMPORTANT]
>
>只有定期维护数据库，数据库才能以最佳方式运行。 某些RDBMS提供的自动维护不够充分，并不取代任何关系数据库事务管理系统的深入维护。
>  
>本文档中描述的程序是建议。 维护计划是数据库管理员的责任，在出现问题时，管理员必须是您的第一个联系人。
