---
title: 关于事件处理
seo-title: 关于事件处理
description: 关于事件处理
seo-description: null
page-status-flag: never-activated
uuid: 6c3e02b3-0d4d-4661-952a-e4915ca9ef92
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: a78c9986-7c49-47db-99a0-9f0949c4dee7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c2c53041d8a19a491b8ec4da12a8a0ced25cf9a

---


# 关于事件处理{#about-event-processing}

在事务消息传递的上下文中，事件由外部信息系统生成，并通过和方法发送到Adobe Campaign(请参 **[!UICONTROL PushEvent]** 阅 **[!UICONTROL PushEvents]** 活动 [说明](../../message-center/using/event-description.md))。 它包含与活动链接的数据，如活动类型（例如，订单确认或网站上的帐户创建）、电子邮件地址或移动号码，以及允许您在发送前丰富和个性化交易消息的其他信息。 这可以是客户联系信息、消息语言或电子邮件格式。

事件数据示例：

![](assets/messagecenter_events_request_001.png)

要处理事务性消息传递事件，必须应用以下步骤：

1. 活动集合、
1. 在将活动扩充传输到消息模板之前（如果您获得了可用于Campaign事务消息模块的扩充选项）,
1. 将活动传输到消息模板，
1. 通过个性化数据丰富活动内容，
1. 交付执行、
1. 链接分发失败的事件的循环使用（此步骤可通过Adobe Campaign工作流执行）。

## 活动状态 {#event-statuses}

事件 **历史记录**，在 **[!UICONTROL Message Center]****[!UICONTROL Event history]** >下，将所有已处理的事件分组到一个视图中。 可以按事件类型或状态对它们进行 **分类**。 这些状态包括：

* **待定**:这意味着活动可能是：

   * 刚刚收集但尚未处理的事件。 该 **[!UICONTROL Number of errors]** 列显示值0。 电子邮件模板尚未链接。
   * 已处理但其确认错误的事件。 该 **[!UICONTROL Number of errors]** 列显示的值不是0。 要了解此事件何时将再次处理，请查阅 **[!UICONTROL Process requested on]** 列。

* **待交付**:已处理该事件，并且已链接交付模板。 电子邮件正在等待发送，且会应用经典的发送过程。 有关详细信息，您可以打开分发。 请参阅 [交付](../../delivery/using/about-message-tracking.md)。
* **发送**、忽 **略** 和交 **付错误**:这些传送状态通过updateEventsStatus工作 **流进行恢复** 。 有关详细信息，您可以打开相关的交付。
* **未涵盖的活动**:消息中心路由阶段失败。 例如，Adobe Campaign未找到充当活动模板的电子邮件。
* **活动已过期**:已达到发送尝试的最大数量。 该事件被视为null。
