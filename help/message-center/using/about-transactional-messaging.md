---
product: campaign
title: 事务性消息传递快速入门
description: 详细了解Adobe Campaign Classic事务型消息传递的工作原理和关键步骤
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
TQID: 'https://experienceleague.adobe.com/n4w2hZkuzHlD3Axc1tUCGfBQ13D28j3Xpmdh07tVr4g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 8%
---
# 事务性消息传递快速入门 {#about-transactional-messaging}



## 概述 {#overview}

**事务性消息传递** （消息中心）是一个Campaign模块，用于管理从外部信息系统发送的事件生成的自定义触发器通知。

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关事务型消息传递的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}

本节介绍了特定于内部部署和混合部署的事务性消息架构以及控制实例和执行实例的配置。

>[!IMPORTANT]
>
>事务性消息传递需要特定的许可证。 请核实您的许可协议。

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 事务型消息传递工作原理 {#transactional-messaging-operating-principle}

Adobe Campaign事务性消息传递模块集成到一个信息系统中，该信息系统返回要更改为个性化事务性消息的事件。 这些消息可以通过电子邮件、短信或推送通知单独或批量发送。

此功能依赖于特定架构，其中&#x200B;**执行实例**&#x200B;与&#x200B;**控制实例**&#x200B;分开。 此分布可确保更高的可用性和更好的负载管理。 有关详细信息，请参阅[事务性消息架构](../../message-center/using/transactional-messaging-architecture.md)。

>[!NOTE]
>
>要为托管在Adobe Cloud上的消息中心执行实例创建新用户，您需要联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 消息中心用户是特定的操作员，需要专用权限才能访问&#x200B;**[!UICONTROL Real time events (nmsRtEvent)]**&#x200B;文件夹。

>[!NOTE]
>
>Adobe Campaign会优先处理事务型消息，而不是任何其他投放。

## 关键步骤 {#key-steps}

下面概述了在Adobe Campaign中创建和管理个性化事务型消息的主要步骤。

### 在控制实例上执行的步骤

在&#x200B;**控件实例**&#x200B;上，必须执行以下操作：

1. [创建事件类型](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional){target="_blank"}（Campaign v8文档）。
1. [创建并设计消息模板](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"}（Campaign v8文档）。 在此步骤中，必须将事件链接到消息。
1. [测试邮件](../../message-center/using/testing-message-templates.md)。
1. [发布消息模板](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"}（Campaign v8文档）。

>[!NOTE]
>
>上述所有步骤均在&#x200B;**控件实例**&#x200B;上执行。 在控制实例上发布模板也会在所有&#x200B;**执行实例**&#x200B;上发布。 有关事务性消息传递实例的详细信息，请参阅[事务性消息传递体系结构](../../message-center/using/transactional-messaging-architecture.md)。

### 执行实例上的事件处理

设计和发布事务性消息模板后，如果触发了相应的事件，则会对&#x200B;**执行实例**&#x200B;执行以下主要步骤：

1. 当外部信息系统生成事件时，相关数据将通过&#x200B;**PushEvent**&#x200B;和&#x200B;**PushEvents**&#x200B;方法发送到Campaign。 请参阅[事件集合](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-collection){target="_blank"}（Campaign v8文档）。
1. 该事件已链接到相应的消息模板。 请参阅[路由到模板](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-to-template){target="_blank"}（Campaign v8文档）。
1. 扩充阶段完成后，将发送投放。 请参阅[投放执行](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"}（Campaign v8文档）。 每个定向收件人都会收到一条个性化消息。

## 相关主题 {#related-topics}

* [通信渠道入门](../../delivery/using/communication-channels.md)
* [投放创建关键步骤](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hans){target="_blank"}
* [事务性消息传递架构](../../message-center/using/transactional-messaging-architecture.md)
* [访问事务性消息报告](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"}（Campaign v8文档）
