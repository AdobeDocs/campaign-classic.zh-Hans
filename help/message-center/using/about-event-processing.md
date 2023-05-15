---
product: campaign
title: 事件处理
description: 了解如何在Adobe Campaign Classic中处理事务型消息传递事件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 2%

---

# 事件处理 {#about-event-processing}



在事务型消息传递的上下文中，事件由外部信息系统生成，并通过 **[!UICONTROL PushEvent]** 和 **[!UICONTROL PushEvents]** 方法(请参阅 [事件描述](../../message-center/using/event-description.md))。

此事件包含链接到事件的数据，如 [type](../../message-center/using/creating-event-types.md) （订单确认、在网站上创建帐户等）、电子邮件地址或移动电话号码，以及其他信息，可让您在投放前扩充和个性化事务型消息（客户联系信息、消息语言、电子邮件格式等）。

事件数据示例：

![](assets/messagecenter_events_request_001.png)

## 事件处理步骤 {#event-processing}

要处理事务型消息传递事件，请对执行实例应用以下步骤：

1. [事件集合](#event-collection)
1. [事件传输到消息模板](#routing-towards-a-template)
1. 使用个性化数据扩充事件
1. [投放执行](../../message-center/using/delivery-execution.md)
1. [事件的回收](#event-recycling) 链接投放失败(通过Adobe Campaign工作流)

在通过执行实例执行上述所有步骤后，每个目标收件人都会收到个性化消息。

>[!NOTE]
>
>有关事务型消息传递实例的更多信息，请参阅 [事务型消息架构](../../message-center/using/transactional-messaging-architecture.md).


## 事件集合 {#event-collection}

可以使用两种模式收集由信息系统生成的事件：

* 通过调用SOAP方法，您可以在Adobe Campaign中推送事件：pushEvent方法允许您一次发送一个事件，而pushEvents方法允许您一次发送多个事件。 有关此内容的更多信息，请参阅 [事件描述](../../message-center/using/event-description.md).

* 创建工作流允许您通过导入文件或通过SQL网关(使用 [联合数据访问](../../installation/using/about-fda.md) 选项)。

收集事件后，会按照执行实例的实时队列和批处理队列之间的技术工作流对事件进行划分，同时等待链接到消息模板。

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>在执行实例中， **[!UICONTROL Real time events]** 或 **[!UICONTROL Batch events]** 文件夹不能设置为视图，因为这可能会导致访问权限问题。 有关将文件夹设置为视图的更多信息，请参阅 [此部分](../../platform/using/access-management-folders.md).

## 模板路由 {#routing-towards-a-template}

在执行实例上发布消息模板后，将自动生成两个模板：一个要链接到实时事件，另一个要链接到批处理事件。

路由步骤包括：将事件关联到相应的消息模板；

* 在事件本身的属性中指定的事件类型：

   ![](assets/messagecenter_event_type_001.png)

* 在消息模板属性中指定的事件类型：

   ![](assets/messagecenter_event_type_002.png)

默认情况下，路由取决于以下信息：

* 事件类型
* 要使用的渠道(默认情况下：email)
* 基于发布日期的最近投放模板

## 事件状态 {#event-statuses}

的 **事件历史记录**，在 **[!UICONTROL Message Center]** > **[!UICONTROL Event history]** ，将所有已处理的事件分组到一个视图中。 它们可以按事件类型或按 **状态**. 这些状态包括：

* **待定**:事件可以是：

   * 刚刚收集但尚未处理的事件。 的 **[!UICONTROL Number of errors]** 列显示值0。 电子邮件模板尚未关联。
   * 已处理但确认错误的事件。 的 **[!UICONTROL Number of errors]** 列显示的值不为0。 要了解此事件何时将再次处理，请查阅 **[!UICONTROL Process requested on]** 列。

* **待定投放**:已处理事件并关联投放模板。 电子邮件处于待投放状态，且已应用经典投放流程。 有关更多信息，您可以打开投放。
* **已发送**, **已忽略** 和 **投放错误**:这些投放状态可通过 **updateEventsStatus** 工作流。 有关更多信息，您可以打开相关投放。
* **未涵盖的事件**:事务型消息传递路由阶段失败。 例如，Adobe Campaign未找到充当事件模板的电子邮件。
* **事件过期**:已达到最大发送尝试次数。 该事件被视为null。

## 事件回收 {#event-recycling}

如果在特定渠道上投放消息失败，Adobe Campaign可以使用其他渠道重新发送消息。 例如，如果短信渠道上的投放失败，则会使用电子邮件渠道重新发送消息。

为此，您需要配置一个工作流，该工作流使用 **投放错误** 状态，并为其分配不同的渠道。

>[!CAUTION]
>
>此步骤只能使用工作流执行，因此保留给专家用户。 有关更多信息，请联系您的Adobe客户经理。