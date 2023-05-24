---
product: campaign
title: 推荐
description: 推荐
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# 推荐{#recommendations}



Adobe Campaign是一个高度事务性的系统（OLTP数据库）。 这意味着基础数据库将经常更新，导致性能随时间推移而降低。 为了避免此类问题，需要定期维护数据库。

>[!IMPORTANT]
>
>只有在定期维护数据库的情况下，该数据库的性能才会达到最佳。 与任何关系型数据库事务管理系统一样，某些RDBMS提供的自动维护是不够的，不能代替深度维护。
>  
>本文档中描述的步骤是建议。 维护计划由数据库管理员负责，在发生问题时，管理员必须是您的第一个联系人。
