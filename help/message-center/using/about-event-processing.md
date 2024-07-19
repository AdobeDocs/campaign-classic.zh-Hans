---
product: campaign
title: 事件处理
description: 了解如何在Adobe Campaign Classic中处理事务性消息传递事件
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 2%

---

# 事件处理 {#about-event-processing}



在事务性消息的上下文中，事件由外部信息系统生成，并通过&#x200B;**[!UICONTROL PushEvent]**&#x200B;和&#x200B;**[!UICONTROL PushEvents]**&#x200B;方法发送到Adobe Campaign（请参阅[事件描述](../../message-center/using/event-description.md)）。

此事件包含链接到事件的数据，如其[类型](../../message-center/using/creating-event-types.md)（订单确认、在网站上创建帐户等）、电子邮件地址或手机号码以及其他允许您在投放前扩充和个性化事务型消息的信息（客户联系信息、消息语言、电子邮件格式等）。

事件数据示例：

![](assets/messagecenter_events_request_001.png)

## 事件处理步骤 {#event-processing}

要处理事务性消息事件，需对执行实例应用以下步骤：

1. [事件集合](#event-collection)
1. [事件传输到消息模板](#routing-towards-a-template)
1. 使用个性化数据扩充事件
1. [投放执行](../../message-center/using/delivery-execution.md)
1. [回收链接投放失败的事件](#event-recycling)(通过Adobe Campaign工作流)

一旦通过执行实例执行上述所有步骤后，每个目标收件人都会收到个性化消息。

>[!NOTE]
>
>有关事务性消息传递实例的详细信息，请参阅[事务性消息传递体系结构](../../message-center/using/transactional-messaging-architecture.md)。


## 事件集合 {#event-collection}

信息系统生成的事件可以使用两种模式收集：

* 通过调用SOAP方法，您可以在Adobe Campaign中推送事件：通过PushEvent方法，您可以一次发送一个事件；通过PushEvents方法，您可以一次发送多个事件。 有关详细信息，请参阅[事件描述](../../message-center/using/event-description.md)。

* 通过创建工作流，您可以通过导入文件或通过SQL网关（使用[联合数据访问](../../installation/using/about-fda.md)选项）恢复事件。

收集事件后，在等待链接到消息模板时，将按照技术工作流在执行实例的实时队列和批处理队列之间划分事件。

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>在执行实例上，**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;文件夹不能设置为视图，因为这会导致访问权限问题。 有关将文件夹设置为视图的详细信息，请参阅[此部分](../../platform/using/access-management-folders.md)。

## 模板路由 {#routing-towards-a-template}

在执行实例上发布消息模板后，将自动生成两个模板：一个链接到实时事件，另一个链接到批处理事件。

传送步骤包括将事件链接到相应的消息模板，具体基于：

* 在事件本身的属性中指定的事件类型：

  ![](assets/messagecenter_event_type_001.png)

* 在消息模板属性中指定的事件类型：

  ![](assets/messagecenter_event_type_002.png)

默认情况下，路由依赖以下信息：

* 事件类型
* 要使用的渠道（默认为：电子邮件）
* 基于发布日期的最新投放模板

## 事件状态 {#event-statuses}

在&#x200B;**[!UICONTROL Message Center]** > **[!UICONTROL Event history]**&#x200B;下的&#x200B;**事件历史记录**&#x200B;将所有已处理的事件分组到一个视图中。 它们可以按事件类型或&#x200B;**状态**&#x200B;分类。 这些状态为：

* **挂起**：事件可以是：

   * 刚刚收集且尚未处理的事件。 **[!UICONTROL Number of errors]**&#x200B;列显示值0。 尚未链接电子邮件模板。
   * 事件已处理，但其确认有误。 **[!UICONTROL Number of errors]**&#x200B;列显示的值不是0。 要了解何时再次处理此事件，请参阅&#x200B;**[!UICONTROL Process requested on]**&#x200B;列。

* **待处理投放**：事件已处理，并且投放模板已链接。 电子邮件正在等待投放，并且已应用经典投放流程。 有关详细信息，您可以打开投放。
* **已发送**、**已忽略**&#x200B;和&#x200B;**传递错误**：这些传递状态是通过&#x200B;**updateEventsStatus**&#x200B;工作流恢复的。 有关详细信息，您可以打开相关的投放。
* **事件未覆盖**：事务性消息传递路由阶段失败。 例如，Adobe Campaign未找到用作事件模板的电子邮件。
* **事件已过期**：已达到最大发送尝试次数。 该事件被视为null。

## 事件回收 {#event-recycling}

如果特定渠道上的消息投放失败，Adobe Campaign可以使用其他渠道重新发送消息。 例如，如果短信渠道投放失败，则使用电子邮件渠道重新发送消息。

为此，您需要配置一个工作流，该工作流会重新创建具有&#x200B;**投放错误**&#x200B;状态的所有事件，并为它们分配不同的渠道。

>[!CAUTION]
>
>此步骤只能使用工作流执行，因此仅供专家用户使用。 有关更多信息，请与您的Adobe客户经理联系。