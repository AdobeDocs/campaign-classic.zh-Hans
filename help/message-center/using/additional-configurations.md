---
product: campaign
title: 其他配置
description: 了解如何在Adobe Campaign Classic中为事务性消息设置其他配置
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
TQID: 'https://experienceleague.adobe.com/TJ5R6T1pu5JQU5SaGoWRgZLG2m29TWWPVB8nniorRUg'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: cce1f22c34cbd13d063850a7ca636a3b0dfc62f6
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 4%
---
# 其他配置 {#mc-additional-configurations}

本页介绍Campaign Classic v7上事务性消息传递的其他配置。

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关事务性消息事件清除和技术工作流的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/settings/transactional-msg-settings){target=_blank}

## 监测阈值 {#monitoring-thresholds}

您可以配置在&#x200B;**消息中心服务级别**&#x200B;和&#x200B;**消息中心处理时间**&#x200B;报告中出现的指示器的警告阈值（橙色）和警报阈值（红色）(请参阅[访问事务性消息报告](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"}（Campaign v8文档）)。

为此请执行以下操作步骤：

1. 在&#x200B;**执行实例**&#x200B;上打开部署向导。

1. 转到&#x200B;**[!UICONTROL Message Center]**&#x200B;页面。

1. 使用箭头可更改阈值。

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>队列中待处理的事件数显示在Adobe Campaign进程监视页面的[系统指示器](../../production/using/monitoring-processes.md#system-indicators)部分中。 有关部署向导的详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md#deployment-assistant)。

## 技术工作流 {#technical-workflows}

您必须确保在部署任何事务性消息模板之前确实已创建并启动控制实例上的技术工作流和不同的执行实例。

### 存档工作流计划

避免修改在控制实例上运行的&#x200B;**存档工作流**&#x200B;计划。 否则，从执行实例中拉取的某些跟踪数据可能会丢失。

如果您确实修改了存档工作流计划，则还必须更改执行实例上的&#x200B;**跟踪工作流**&#x200B;计划，以匹配控制实例上的存档工作流计划。

## 配置多品牌策略 {#configuring-multibranding}

本节介绍一个解决方案，用于在Adobe Campaign中为每个品牌配置事务性消息的跟踪和镜像页面URL。

### 兼容性说明 {#compatibility-note}

此旧版品牌策略配置与Campaign v8中引入的新[集中式品牌策略](https://experienceleague.adobe.com/docs/campaign-web/v8/conf/branding/branding-gs.html){target="_blank"}模型不兼容。

如果您的现有环境使用此旧版配置，则无法将其直接迁移到新的集中式品牌推广模型。 要采用新系统，必须全面重新实施品牌设置。

### 先决条件 {#prerequisites}

* 所有主机都必须添加到实例(`config-<instance>.xml`)的配置文件中。
* 必须为每个品牌分配一个子域。
* 如果在HTTPS页面上完成Web跟踪，则您必须拥有适用于所有品牌的HTTPS证书。

要配置多品牌策略，您需要配置执行实例和控制实例。

### 执行实例 {#execution-instance}

在执行实例上，执行以下步骤：

1. 为每个品牌创建一个外部帐户。

   >[!NOTE]
   >
   >在[此部分](../../message-center/using/configuring-instances.md#control-instance)中了解如何创建执行实例类型外部帐户。

1. 扩展nms:extAccount架构以添加跟踪URL：

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >在[扩展架构](../../configuration/using/extending-a-schema.md)部分中了解如何扩展现有架构。

1. 修改nms:extAccount表单：

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. 修改NmsTracking_OpenFormula和NmsTracking_ClickFormula选项以使用外部帐户，而不是全局选项。

   为此，请替换：

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   替换为：

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >升级时，这些更改可能会导致冲突。 您可能需要手动将这些公式与其新版本合并。

### 控制实例 {#control-instance}

在控制实例上，您需要关联投放模板和外部帐户。

为此请执行以下操作步骤：

1. 为每个品牌创建一个与[执行实例](#execution-instance)上定义的内部名称相同的外部帐户（步骤1）。

1. 为每个品牌创建投放模板。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html){target="_blank"}。

1. 在投放模板的&#x200B;**[!UICONTROL Properties]**&#x200B;中，将路由设置为品牌的外部帐户。
