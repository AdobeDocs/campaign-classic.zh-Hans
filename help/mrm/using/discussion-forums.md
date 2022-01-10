---
product: campaign
title: 论坛
description: 了解如何使用Campaign论坛
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 222853c5-c754-4c0b-8ee4-a64b2f8677a4
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 论坛{#discussion-forums}

![](../../assets/v7-only.svg)

Adobe Campaign运营商可以使用论坛来共享信息。 以下元素各自具有自己的论坛：计划、项目、活动、资源、模拟、库存。 每位运营商还设有个人论坛。 所有讨论都是公开的，甚至在个人论坛上。

操作员可以订阅论坛，以便在每次发布消息时接收通知电子邮件。

## 访问论坛 {#accessing-a-forum}

要访问营销活动的论坛、操作员等，请转到其功能板并单击 **[!UICONTROL Forum]** 链接。 此链接还会显示论坛中的消息总数。

![](assets/mrm_forum_access_link.png)

## 使用论坛 {#using-a-forum}

消息及其响应按时间顺序显示（从最新到最旧）。

要显示消息的内容，请单击其标题。

![](assets/mrm_forum_expand_msg.png)

**开始新讨论**

要开始新讨论，请单击 **[!UICONTROL Add a discussion]** 按钮。 的 **[!UICONTROL Discussion forum]** 框（请参阅下文）。

![](assets/mrm_forum_new_thread.png)

**向现有讨论发送消息**

要将消息发布到现有讨论，请打开要回复的消息，然后单击 **[!UICONTROL Reply]** 链接。 的 **[!UICONTROL Discussion forum]** 框（请参阅下文）。

![](assets/mrm_forum_answer_msg.png)

当您回复消息时，发布原始消息的人将收到通知。

**写消息**

在 **[!UICONTROL Discussion forum]** 框：

1. 在 **[!UICONTROL Message]** 字段和讨论标题 **[!UICONTROL Subject]** 字段。

   ![](assets/mrm_forum_edit_msg.png)

1. 如有必要：

   * 如果您希望某个人参加未订阅论坛的讨论，请使用 **[!UICONTROL Operator to notify]** 字段。 操作员将收到此特定消息的通知电子邮件（他们不会订阅论坛）。 要通知多个运算符，请选择一组运算符。
   * 要向消息中添加附件，请单击 **[!UICONTROL Browse]**. 附件也将包含在通知电子邮件中。 附件只能单独发送：要发送多个文件，您需要压缩这些文件。

1. 单击 **[!UICONTROL Create the message]** 发布到论坛。

>[!NOTE]
>
>将消息发布到论坛后，便无法再更改或删除该消息。

## 帖子到操作员的个人论坛 {#posting-to-the-personal-forum-of-an-operator}

例如，如果您的消息不涉及特定的营销活动，但您仍希望跟踪Adobe Campaign中的对话，则可以将消息发布到操作员的论坛。 个人论坛是公开的，所有运营商都会看到您的信息。 每次有人向其个人论坛发帖时，操作员都会收到一条消息。

要访问操作员论坛，请执行以下操作：

* 如果您拥有访问 **[!UICONTROL Administration > Access management > Operators]** 浏览器的节点，打开所需运算符的仪表板，然后单击 **[!UICONTROL Forum]** 链接。
* 如果没有，请在Adobe Campaign中找到操作员的姓名（通过此操作员向论坛发布的消息，该消息是指派给他们的任务），然后单击该名称以访问其仪表板。 您还可以要求管理员创建操作员文件夹的视图。

## 订阅论坛 {#subscribing-to-a-forum}

订阅论坛可让您关注讨论。 每次向论坛发送消息时，您都会收到电子邮件通知。 此电子邮件将包含邮件正文和任何附件。 要回答消息，请单击电子邮件正文中的，然后登录Adobe Campaign Web界面。 订阅论坛时，所有人都可以看到此信息。

* 要订阅论坛，请单击 **[!UICONTROL Follow discussions]** 按钮。

   ![](assets/mrm_forum_subscribe.png)

   部分显示为蓝色，表示您已订阅论坛。

* 要取消订阅论坛，请单击 **[!UICONTROL Unsubscribe]** 按钮。

   ![](assets/mrm_forum_unsubscribe.png)

* 您的个人仪表板列出了您订阅的论坛。 单击 **[!UICONTROL Subscription to discussion forums]** 链接以显示列表，然后单击您感兴趣的项目以访问其论坛。

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   有关个人功能板的更多信息，请参阅 [此部分](../../platform/using/access-management-operators.md).

* 要查看谁订阅了论坛，请单击 **[!UICONTROL List of subscribers to this discussion forum]** 链接。

   ![](assets/mrm_forum_subscribers.png)

## 检查通知投放 {#checking-notification-delivery}

如果订阅论坛的操作员未按预期收到通知：

* 检查是否在操作员的用户档案中输入了电子邮件地址。
* 转到 **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** 节点并检查 **[!UICONTROL Jobs in discussion forums]** 工作流已启动且没有错误。
* 查看投放日志：

   * 在Adobe Campaign主页上，转到 **[!UICONTROL Campaigns > Navigation > Deliveries]**，然后打开 **[!UICONTROL Discussion forum notification]** 投放。
   * 在资源管理器中，转到 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**，然后单击 **[!UICONTROL Discussion forum notifications]**.
   在 **[!UICONTROL Discussion forum notifications]** 框中，可在 **[!UICONTROL Edit > Delivery]** 选项卡。 您还可以查看 **[!UICONTROL Tracking > Log]** 和 **[!UICONTROL Exclusion causes]** 选项卡。
