---
solution: Campaign Classic
product: campaign
title: 投放执行
description: 投放执行
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 8%

---


# 投放执行{#delivery-execution}

## 事务性消息发送{#transactional-message-send}

在执行实例上，一旦扩充阶段完成并且投放模板已链接到事件，就会发送投放。

>[!NOTE]
>
>MTA优先处理事务性消息，而不是任何其他投放。

所有投放都分组在&#x200B;**[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**&#x200B;文件夹中。

![](assets/messagecenter_deliveries_execinstances_001.png)

默认情况下，它们按投放月份排序到子文件夹中。 可以在消息模板属性中更改此排序，如下所示。

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>对于托管或混合安装，如果您已升级到增强MTA，则所有事务性消息也可以与Adobe Campaign增强MTA一起发送，以改进交付能力、吞吐量和弹回处理。 所有影响与标准营销消息的影响相同，并在[Adobe Campaign增强MTA](https://helpx.adobe.com/cn/campaign/kb/acc-campaign-enhanced-mta.html)文档中详细介绍。

<!--## Transactional message monitoring {#transactional-message-monitoring}

To monitor your transactional messages, check the delivery logs. Accessing the delivery logs is presented in [this section](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history).

The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->