---
solution: Campaign Classic
product: campaign
title: 关于事件处理
description: 关于事件处理
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 3%

---


# 关于事件处理{#about-event-processing}

在事务消息的上下文中，由外部信息系统生成事件，并通过&#x200B;**[!UICONTROL PushEvent]**&#x200B;和&#x200B;**[!UICONTROL PushEvents]**&#x200B;方法(参考[事件说明](../../message-center/using/event-description.md))发送到Adobe Campaign。 它包含链接到事件的数据，例如事务性消息的类型（例如，订单确认或在网站上创建帐户）、电子邮件地址或移动号码，以及允许您在投放前丰富和个性化的其他信息。 这可以是客户联系信息、消息语言或电子邮件格式。

事件数据示例：

![](assets/messagecenter_events_request_001.png)

要处理事务消息事件，必须应用以下步骤：

1. 事件集合,
1. 事件传输到消息模板，
1. 事件扩充,
1. 投放执行,
1. 链接投放失败的事件的回收(此步骤可通过Adobe Campaign工作流执行)。

## 事件状态{#event-statuses}

**事件历史记录**&#x200B;位于&#x200B;**[!UICONTROL Message Center]** > **[!UICONTROL Event history]**&#x200B;下，将所有处理的事件分为一个视图。 它们可以按事件类型或&#x200B;**status**&#x200B;分类。 以下状态为：

* **待定**:这意味着事件可能是：

   * 刚刚收集但尚未处理的事件。 **[!UICONTROL Number of errors]**&#x200B;列显示值0。 电子邮件模板尚未链接。
   * 已处理但确认错误的事件。 **[!UICONTROL Number of errors]**&#x200B;列显示的值不是0。 要了解何时将再次处理此事件，请查阅&#x200B;**[!UICONTROL Process requested on]**&#x200B;列。

* **待处理投放**:已处理事件，并且投放模板已链接。电子邮件正在等待投放，并应用经典投放过程。 有关详细信息，您可以打开投放。 请参阅[投放](../../delivery/using/about-message-tracking.md)。
* **Sent**, Ignoredand  **** 投放 **错误**:这些投放状态通过updateEventsStatus工作 **** 流进行恢复。有关更多信息，您可以打开相关投放。
* **事件未涵盖**:消息中心路由阶段失败。例如，Adobe Campaign找不到充当事件模板的电子邮件。
* **事件已过期**:已达到最大发送尝试数。事件被视为null。
