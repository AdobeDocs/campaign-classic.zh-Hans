---
product: campaign
title: 投放性能最佳实践
description: 了解有关投放性能和最佳实践的更多信息
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 3%

---

# 投放性能最佳实践 {#delivery-performances}

>[!NOTE]
>
>有关投放性能和最佳实践的综合指南记录在[Campaign v8投放最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices)页面中。 此内容适用于Campaign Classic v7和Campaign v8用户。
>
>本页介绍了针对混合部署和内部部署的特定于&#x200B;**Campaign Classic v7的性能配置**。

有关投放性能、平台优化、隔离管理、数据库维护和计划建议的全面最佳实践，请参阅[Campaign v8投放最佳实践文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}。

## 性能调整 {#best-practices-performance}

对于&#x200B;**Campaign Classic v7混合/内部部署**，以下数据库和基础架构优化可以提高投放性能：

### 数据库优化

**索引地址**&#x200B;以优化应用程序中使用的SQL查询的性能。 可以从数据架构的主元素声明索引。 此优化需要直接访问数据库，并在内部部署中自定义架构。

### 基础架构调整

**大型投放配置**：发送给超过100万名收件人的投放在发送队列中需要空间。 对于内部部署，可以将MTA子级配置为处理自定义批次大小。 请与系统管理员联系，以根据基础架构容量调整这些设置。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，基础架构优化和MTA配置由Adobe管理。 请参阅[Campaign v8投放最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}，以了解适用于您的部署的性能建议。

## 数据库维护 {#performance-issues}

对于&#x200B;**Campaign Classic v7混合/内部部署**，平台和数据库维护会直接影响投放发送性能。

定期维护任务包括：

**数据库清理**：使用数据库清理工作流删除旧的投放日志、跟踪数据和临时表。 较差的数据库维护可能会减慢投放准备和发送的速度。

**数据库性能监视**：监视查询性能、索引碎片和表统计信息。 有关详细指导，请参阅[此页面](../../production/using/database-performances.md)。

**技术工作流监控**：确保所有技术工作流（尤其是清理、跟踪和可投放性更新工作流）都正常运行，并且没有错误。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，数据库维护和技术工作流由Adobe进行监控和管理。 如[Campaign v8监视器投放文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}中所述，专注于特定于投放的监视。

## 相关主题

* [投放最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}（Campaign v8文档）
* [监测您的可投放性](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}（Campaign v8文档）
* [投放故障排除](delivery-troubleshooting.md)
* [数据库性能](../../production/using/database-performances.md) （v7混合/内部部署）
