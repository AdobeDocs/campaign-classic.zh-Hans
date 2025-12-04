---
product: campaign
title: 投放发送疑难解答
description: 详细了解投放性能以及如何排查与投放监测相关的问题
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# 投放发送疑难解答 {#delivery-troubleshooting}

>[!NOTE]
>
>Campaign v8文档中记录了适用于Campaign Classic v7和Campaign v8用户的有关投放故障排除的综合指南：
>
>* 常见投放失败和解决方案： [了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* 缓慢投放诊断：[在Campaign UI中监视投放](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* 传递最佳实践：[传递最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>本页介绍了针对混合部署和内部部署的特定于&#x200B;**Campaign Classic v7的疑难解答**。

## 故障排除 {#v7-specific}

对于&#x200B;**Campaign Classic v7混合/内部部署**，以下故障排除步骤特定于您管理的基础架构：

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
