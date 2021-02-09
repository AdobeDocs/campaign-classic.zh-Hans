---
solution: Campaign Classic
product: campaign
title: 投放执行
description: 投放执行
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: fd6195ca447fa0345189f3153f44ad2f9a067210
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 7%

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
>对于托管或混合安装，如果已升级到[增强的MTA](../../delivery/using/sending-with-enhanced-mta.md)，则还可以使用Adobe Campaign增强的MTA发送所有事务性消息，以改进交付能力、吞吐量和弹回处理。 所有方面都与标准营销消息相同。

## 事务性消息监视{#transactional-message-monitoring}

要监视事务性消息，请检查投放日志。 访问投放日志显示在[此部分](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)中。

通过每小时运行的技术工作流(**[!UICONTROL Message Center execution instance]**)将从执行实例发送的事务投放同步回控制实例。

>[!NOTE]
>
>投放每周根据最新的事件更新(而非在事件创建日期)累计事件。 因此，当从控制实例提取事务消息投放日志时，与每个投放日志ID关联的投放ID可能随着日志的更新而随时间发生变化(例如，当收到事件的入站弹回时)。

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

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