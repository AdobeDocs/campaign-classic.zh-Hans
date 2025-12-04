---
product: campaign
title: 了解隔离管理
description: 了解隔离管理
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# 了解隔离管理{#understanding-quarantine-management}

>[!NOTE]
>
>有关隔离管理的全面指南记录在[Campaign v8隔离管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines)页面中。 此内容适用于Campaign Classic v7和Campaign v8用户，内容包括：
>
>* 隔离与阻止列表概念
>* 为何将地址添加到隔离（硬/软错误）
>* 软错误管理和错误计数器阈值
>* 如何访问和识别隔离的地址
>* 如何从隔离中删除地址（自动、手动、批量）
>* 隔离管理报告
>
>此页面记录了&#x200B;**Campaign Classic v7特定的配置**，用于混合部署和内部部署中的隔离管理。

有关全面的隔离管理指南，请参阅[Campaign v8隔离管理文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}。

## 隔离配置 {#v7-quarantine-config}

以下配置选项可用于&#x200B;**Campaign Classic v7混合/内部部署**&#x200B;以自定义隔离行为。

### 软错误阈值配置 {#soft-error-threshold}

对于使用旧版Campaign MTA的内部部署，您可以修改错误数以及两个错误之间的间隔时间，然后再隔离地址。

要配置这些设置，请执行以下操作：

1. 从&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**&#x200B;访问部署向导
2. 导航到&#x200B;**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. 配置：
   * **错误数**：隔离地址之前的最大软错误数（默认值： 5）
   * **两个重大错误之间的时段**：错误计数的时间范围（以秒为单位）（默认值： 86,400秒= 1天）

当错误计数器达到阈值时，将隔离该地址。 如果最后一次重大错误发生在10天之前，则错误计数器将重新初始化。

有关更多详细信息，请参阅[投放发送](communication-channels.md) > **配置重试**&#x200B;下的&#x200B;**此页面**。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，重试设置和错误阈值由Adobe根据IP性能和域信誉进行管理。 无需配置。

### 数据库清理工作流 {#database-cleanup-workflow}

对于内部部署，**[!UICONTROL Database cleanup]**&#x200B;技术工作流会自动删除符合特定条件的隔离地址。

从&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**&#x200B;访问此工作流。

在以下情况下，工作流会从隔离中删除地址：

* 成功投放后处于&#x200B;**[!UICONTROL With errors]**&#x200B;状态的地址
* 如果最后一次软退回发生在10天之前，则地址处于&#x200B;**[!UICONTROL With errors]**&#x200B;状态
* 30天后出现&#x200B;**[!UICONTROL With errors]**&#x200B;错误的&#x200B;**[!UICONTROL Mailbox full]**&#x200B;状态的地址

确保此工作流定期运行（推荐：每天）以保持隔离列表卫生。

有关数据库清理的详细信息，请参阅[此部分](../../production/using/database-cleanup-workflow.md)。

>[!NOTE]
>
>对于Campaign v8托管云服务用户，数据库清理工作流由Adobe进行监视和管理。

### 推送通知隔离详情 {#push-quarantine-specifics}

对于Campaign Classic v7，推送通知隔离遵循常规隔离机制，但有一些特定于渠道的行为。

对于&#x200B;**iOS**&#x200B;和&#x200B;**Android**&#x200B;推送通知，隔离机制使用设备令牌而不是电子邮件地址。 卸载或重新安装移动应用程序时，将隔离关联的令牌。

有关推送通知隔离方案(iOS和Android错误类型、重试行为等)的详细信息，请参阅[了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}文档，该文档包括全面的推送通知错误类型表。

### SMS隔离详细信息 {#sms-quarantine-specifics}

对于Campaign Classic v7，SMS隔离遵循常规隔离机制，其中某些特定于渠道的行为与电话号码而不是电子邮件地址相关。

SMS隔离机制会因所使用的连接器而异：

* **标准SMPP连接器**： **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;中定义的错误鉴别规则适用于短信投放。

* **扩展通用SMPP连接器**：使用正则表达式（正则表达式）以不同的方式处理错误管理，以解析SMSC提供程序返回的状态报告(SR)消息。

有关SMS隔离方案和错误类型的详细信息，请参阅[了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}文档，该文档包含全面的SMS错误类型表。

## 相关主题

* [隔离管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}（Campaign v8文档）
* [了解投放失败](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}（Campaign v8文档）
* [投放最佳实践](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}（Campaign v8文档）
* [数据库清理工作流](../../production/using/database-cleanup-workflow.md) （v7混合/内部部署）
* [配置投放重试](communication-channels.md) （v7混合/内部部署）
