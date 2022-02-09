---
product: campaign
title: 事务性消息传递入门
description: '了解有关Adobe Campaign Classic事务型消息传递工作原理和关键步骤的更多信息。 '
feature: Transactional Messaging
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 6%

---


# 事务性消息传递入门 {#about-transactional-messaging}

![](../../assets/v7-only.svg)

## 概述 {#overview}

**事务型消息传递** （消息中心）是Campaign模块，用于管理从外部信息系统发送的事件生成的自定义触发器通知。

事务型消息是由提供商（如网站）实时发送的个人通信和唯一通信。 特别需要，因为它包含收件人要检查或确认的重要信息。

事务性消息传递功能旨在支持可扩展性并提供24/7服务。

* **什么时候到？** 由于此消息包含重要信息，因此用户希望该消息能够实时发送。 因此，触发事件与收到消息之间的延迟必须非常短。

* **为什么这很重要？** 通常，事务型消息的打开率很高。 因此，应当仔细设计它，因为它定义客户关系时会对客户行为产生重大影响。

* **例如？** 它可以是创建帐户后的欢迎邮件、订单已发运的确认邮件、发票、确认密码更改的邮件、客户浏览您网站后的通知、产品不可用通信、帐户声明等。

>[!IMPORTANT]
>
>事务型消息传递需要特定的许可证。 请核实您的许可协议。

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 事务型消息传递工作原理 {#transactional-messaging-operating-principle}

Adobe Campaign事务型消息传递模块集成到信息系统中，该信息系统可返回要更改为个性化事务型消息的事件。 这些消息可以单独发送，也可以通过电子邮件、短信或推送通知批量发送。

此功能依赖于特定的架构，其中 **执行实例** 与 **控制实例**. 此分发可确保更高的可用性和更好的负载管理。 有关此内容的更多信息，请参阅 [事务型消息架构](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>要为托管在Adobe Cloud上的消息中心执行实例创建新Adobe，您需要联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). 消息中心用户是需要专用权限才能访问的特定操作员 **[!UICONTROL Real time events (nmsRtEvent)]** 文件夹。

事务型消息传递的整个过程可描述如下：

![](assets/transactional-msg-overview.png)

例如，假设您是一家拥有网站的公司，客户可以在该网站购买产品。

Adobe Campaign允许您向将产品添加到购物车的客户发送通知电子邮件。 如果其中某人离开您的网站但未完成购买（触发促销活动事件的外部事件），则会自动向他们发送购物车放弃电子邮件（事务型消息投放）。

实施该功能的主要步骤详见 [此部分](#key-steps).

>[!NOTE]
>
>Adobe Campaign优先处理事务型消息而不是任何其他投放。

## 关键步骤 {#key-steps}

在Adobe Campaign中创建和管理个性化事务型消息时，主要步骤概述如下。

### 对控制实例执行的步骤

在 **控制实例**，则必须执行以下操作：

1. [创建事件类型](../../message-center/using/creating-event-types.md).
1. [创建和设计消息模板](../../message-center/using/creating-the-message-template.md). 在此步骤中，您必须将事件链接到消息。
1. [测试消息](../../message-center/using/testing-message-templates.md).
1. [发布消息模板](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>上述所有步骤均在 **控制实例**. 在控制实例上发布模板也会在所有上发布它 **执行实例**. 有关事务型消息传递实例的更多信息，请参阅 [事务型消息架构](../../message-center/using/transactional-messaging-architecture.md).

### 执行实例上的事件处理

设计和发布事务型消息模板后，如果触发了相应的事件，则对 **执行实例**:

1. 当事件由外部信息系统生成时，相关数据将通过 **PushEvent** 和 **PushEvents** 方法。 请参阅 [事件集合](../../message-center/using/about-event-processing.md#event-collection).
1. 该事件已链接到相应的消息模板。 请参阅 [模板路由](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. 扩充阶段完成后，将发送投放。 请参阅 [投放执行](../../message-center/using/delivery-execution.md). 每个目标收件人都会收到一个个性化的消息。

## 相关主题 {#related-topics}

* [通信渠道入门](../../delivery/using/communication-channels.md)
* [投放创建关键步骤](../../delivery/using/steps-about-delivery-creation-steps.md)
* [事务性消息传递架构](../../message-center/using/transactional-messaging-architecture.md)
* [访问事务性消息传递报告](../../message-center/using/about-transactional-messaging-reports.md)
