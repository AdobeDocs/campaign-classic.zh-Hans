---
product: campaign
title: 推荐做法
description: 推荐做法
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 9%

---

# 推荐做法{#recommendations}



Adobe Campaign是一个高度事务性的系统（OLTP数据库）。 这意味着基础数据库将经常更新，导致性能随时间推移而降低。 为了避免此类问题，需要定期维护数据库。

>[!IMPORTANT]
>
>只有在定期维护数据库的情况下，该数据库的性能才会达到最佳。 某些RDBMS提供的自动维护不够充分，不能像任何关系型数据库事务管理系统那样代替深度维护。
>  
>本文档中描述的步骤是建议。 维护计划由数据库管理员负责，在发生问题时，管理员必须是您的第一个联系人。
