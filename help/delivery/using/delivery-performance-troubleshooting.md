---
product: campaign
title: 投放性能和故障排除
description: 了解如何优化Campaign Classic v7中的投放性能并排查问题
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# 投放性能和故障排除 {#delivery-performance-troubleshooting}

>[!NOTE]
>
>有关投放性能和最佳实践的综合指南记录在[Campaign v8投放最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices)页面中。 此内容适用于Campaign Classic v7和Campaign v8用户。
>
>本页记录了&#x200B;**Campaign Classic v7特定的配置**，用于混合部署和内部部署中的性能优化和故障排除。

有关投放性能、平台优化、隔离管理、数据库维护和计划建议的全面最佳实践，请参阅[Campaign v8投放最佳实践文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}。

## 性能优化 {#performance-optimization}

对于&#x200B;**Campaign Classic v7混合/内部部署**，以下数据库和基础架构优化可以提高投放性能。

### 数据库优化

**索引地址**&#x200B;以优化应用程序中使用的SQL查询的性能。 可以从数据架构的主元素声明索引。 此优化需要直接访问数据库，并在内部部署中自定义架构。

### 基础架构调整

**大型投放配置**：发送给超过100万名收件人的投放在发送队列中需要空间。 对于内部部署，可以将MTA子级配置为处理自定义批次大小。 请与系统管理员联系，以根据基础架构容量调整这些设置。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，基础架构优化和MTA配置由Adobe管理。 请参阅[Campaign v8投放最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}，以了解适用于您的部署的性能建议。

### 数据库维护 {#database-maintenance}

对于&#x200B;**Campaign Classic v7混合/内部部署**，平台和数据库维护会直接影响投放发送性能。

定期维护任务包括：

**数据库清理**：使用数据库清理工作流删除旧的投放日志、跟踪数据和临时表。 较差的数据库维护可能会减慢投放准备和发送的速度。

**数据库性能监视**：监视查询性能、索引碎片和表统计信息。 有关详细指导，请参阅[此页面](../../production/using/database-performances.md)。

**技术工作流监控**：确保所有技术工作流（尤其是清理、跟踪和可投放性更新工作流）都正常运行，并且没有错误。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，数据库维护和技术工作流由Adobe进行监控和管理。 如[Campaign v8监视器投放文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}中所述，专注于特定于投放的监视。

## 投放问题疑难解答 {#troubleshooting}

>[!NOTE]
>
>Campaign v8文档中记录了适用于Campaign Classic v7和Campaign v8用户的有关投放故障排除的综合指南：
>
>* 常见投放失败和解决方案： [了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* 缓慢投放诊断：[在Campaign UI中监视投放](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* 传递最佳实践：[传递最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>此部分记录针对混合部署和内部部署的特定于&#x200B;**Campaign Classic v7的疑难解答**。

对于&#x200B;**Campaign Classic v7混合/内部部署**，以下故障排除步骤特定于您管理的基础架构。

### MX规则配置

如果您遇到特定ISP的限制问题，您可能需要查看和调整MX规则配置。 有关MX规则和配额的详细信息，请参阅[此部分](../../installation/using/email-deliverability.md#about-mx-rules)。

### 针对投放性能的数据库维护

如果您在中间源部署中遇到以下错误：

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

原因与性能问题相关，即营销实例在将数据发送到中间源服务器之前花费过多时间构建数据。

**对于内部部署安装**，请对数据库执行真空和重新索引。 有关数据库维护的详细信息，请参阅[本节](../../production/using/recommendations.md)。

您还应该重新启动所有具有计划活动的工作流，以及所有处于失败状态的工作流。 请参阅[此小节](../../workflow/using/scheduler.md)。

### 技术工作流监测

对于内部部署，请确保与可投放性相关的所有技术工作流均正常运行，并且没有错误：

**可投放性更新工作流**：更新退回邮件鉴别规则和可投放性指示器。

**跟踪工作流**：处理已发送投放的跟踪数据。

**数据库清理工作流**：定期清除旧投放日志和临时表以保持性能。

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;中检查工作流状态。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，技术工作流和基础架构监控由Adobe管理。 如[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}中所述，重点关注投放内容和定位。

## 相关主题

* [了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}（Campaign v8文档）
* [投放最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}（Campaign v8文档）
* [在Campaign UI中监视投放](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}（Campaign v8文档）
* [数据库维护](../../production/using/recommendations.md) （v7混合/内部部署）
* [电子邮件可投放性](../../installation/using/email-deliverability.md)（v7混合/内部部署）
* [数据库性能](../../production/using/database-performances.md) （v7混合/内部部署）

