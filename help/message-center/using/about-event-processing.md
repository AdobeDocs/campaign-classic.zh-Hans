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

在事务消息的上下文中，事件由外部信息系统生成，并通过所述和方法被发 **[!UICONTROL PushEvent]** 送 **[!UICONTROL PushEvents]** 给Adobe Campaign(参 [阅事件说明](../../message-center/using/event-description.md))。 它包含链接到事件的数据，如其类型（例如，在网站上订购确认或创建帐户）、电子邮件地址或移动号码，以及其他信息，这些信息允许您在投放前丰富和个性化事务性消息。 这可以是客户联系信息、消息语言或电子邮件格式。

事件数据示例：

![](assets/messagecenter_events_request_001.png)

要处理事务消息事件，必须应用以下步骤：

1. 事件集合,
1. 事件传输到消息模板，
1. 事件扩充,
1. 投放执行,
1. 链接投放失败的事件的回收(此步骤可通过Adobe Campaign工作流执行)。

## 事件状态 {#event-statuses}

事件 **历史记录**(位于 **[!UICONTROL Message Center]** >下)将 **[!UICONTROL Event history]** 所有已处理事件分组为一个视图。 它们可以按事件类型或状态 **分类**。 以下状态为：

* **待定**:即事件可能是：

   * 刚刚收集但尚未处理的事件。 列 **[!UICONTROL Number of errors]** 显示值0。 电子邮件模板尚未链接。
   * 已处理事件，但其确认错误。 列 **[!UICONTROL Number of errors]** 显示的值不是0。 要了解何时将再次处理此事件，请查阅 **[!UICONTROL Process requested on]** 列。

* **待处理投放**:已处理事件并且投放模板已链接。 电子邮件正在挂起投放，且已应用经典投放流程。 有关详细信息，您可以打开投放。 请参阅 [投放](../../delivery/using/about-message-tracking.md)。
* **已发送**、已 **忽略** 和 **投放错误**:这些投放状态通过updateEventsStatus工 **作流进行** 恢复。 有关详细信息，您可以打开相关投放。
* **事件未涵盖**:消息中心路由阶段失败。 例如，Adobe Campaign找不到充当事件模板的电子邮件。
* **事件已过期**:已达到发送尝试的最大数量。 该事件被视为null。
