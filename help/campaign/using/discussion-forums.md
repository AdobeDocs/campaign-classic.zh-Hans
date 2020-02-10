---
title: 论坛
seo-title: 论坛
description: 论坛
seo-description: null
page-status-flag: never-activated
uuid: 6253bb32-c71d-45ac-bc03-027131ae95a5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 88eb17b6-5206-4064-9cd9-b4645a85c609
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 论坛{#discussion-forums}

Adobe Campaign运营商可以使用论坛来共享信息。 以下元素各有其论坛：计划、计划、活动、资源、模拟、股票。 每家运营商还设有个人论坛。 所有讨论都是公开的，甚至在个人论坛上。

运营商可订阅论坛，以在每次发布消息时接收通知电子邮件。

## 访问论坛 {#accessing-a-forum}

要访问营销活动、运营商等的论坛，请转到其仪表板，然后单击 **[!UICONTROL Forum]** 右上角的链接。 此链接还为您提供论坛中消息的总数。

![](assets/mrm_forum_access_link.png)

## 使用论坛 {#using-a-forum}

消息及其响应按时间顺序显示（从最新到最旧）。

要显示消息的内容，请单击其标题。

![](assets/mrm_forum_expand_msg.png)

**开始新的讨论**

要开始新的讨论，请单 **[!UICONTROL Add a discussion]** 击右上角的按钮。 出现 **[!UICONTROL Discussion forum]** 此框（见下文）。

![](assets/mrm_forum_new_thread.png)

**向现有讨论发布消息**

要向现有讨论发布消息，请打开要回答的消息，然后单击左 **[!UICONTROL Reply]** 上角的链接。 出现 **[!UICONTROL Discussion forum]** 此框（见下文）。

![](assets/mrm_forum_answer_msg.png)

当您回复消息时，发布原始消息的人将收到通知。

**编写消息**

包装 **[!UICONTROL Discussion forum]** 盒中：

1. 在字段中输入您 **[!UICONTROL Message]** 的文本，在字段中输入讨论 **[!UICONTROL Subject]** 标题。

   ![](assets/mrm_forum_edit_msg.png)

1. 如有必要，请：

   * 如果您希望某人参加未订阅论坛的讨论，请使用该字 **[!UICONTROL Operator to notify]** 段。 运营商将收到此特定消息的通知电子邮件（他们不会订阅论坛）。 要通知多个运算符，请选择一组运算符。
   * 要向邮件中添加附件，请单击 **[!UICONTROL Browse]**。 附件也将包含在通知电子邮件中。 附件只能单独发送：要发送多个文件，您需要将其压缩。

1. 单击 **[!UICONTROL Create the message]** 以将其发布到论坛。

>[!NOTE]
>
>将消息发布到论坛后，便无法再更改或删除该消息。

## 发布到运营商的个人论坛 {#posting-to-the-personal-forum-of-an-operator}

例如，如果您的消息与特定营销活动无关，但您仍希望跟踪Adobe Campaign中的对话，则可以向运营商论坛发布消息。 个人论坛是公开的，所有运营商都会看到您的信息。 每次有人发布到其个人论坛时，运营商都会收到一条消息。

要访问运营商论坛，请执行以下操作：

* 如果您有权访问浏览器的节 **[!UICONTROL Administration > Access management > Operators]** 点，请打开所需操作员的功能板，然后单击右上角 **[!UICONTROL Forum]** 的链接。
* 如果没有，请在Adobe Campaign中查找操作员的姓名（通过此操作员发布到论坛的消息，将一个任务分配给他），然后单击该姓名以访问他们的仪表板。 您还可以要求管理员创建操作员文件夹的视图。

## 订阅论坛 {#subscribing-to-a-forum}

订阅论坛可让您关注讨论。 每次向论坛发布消息时，您都会收到电子邮件通知。 此电子邮件将包含邮件正文和任何附件。 要回答邮件，请单击电子邮件正文，然后登录Adobe Campaign web界面。 订阅论坛时，所有人都可以看到此信息。

* 要订阅论坛，请单击 **[!UICONTROL Follow discussions]** 消息列表上方右上方部分的按钮。

   ![](assets/mrm_forum_subscribe.png)

   此部分为蓝色，显示您订阅了论坛。

* 要取消订阅论坛，请单击该 **[!UICONTROL Unsubscribe]** 按钮。

   ![](assets/mrm_forum_unsubscribe.png)

* 您的个人仪表板会列出您订阅的论坛。 单击链 **[!UICONTROL Subscription to discussion forums]** 接以显示列表，然后单击您感兴趣的项目以访问其论坛。

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   有关个人仪表板的详细信息，请参阅 [此部分](../../platform/using/access-management.md#operators)。

* 要查看订阅论坛的用户，请单击 **[!UICONTROL List of subscribers to this discussion forum]** 消息列表上方的链接。

   ![](assets/mrm_forum_subscribers.png)

## 检查通知传送 {#checking-notification-delivery}

如果订阅论坛的运营商没有按预期接收通知：

* 检查是否在操作员的配置文件中输入了电子邮件地址。
* 转到该节 **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** 点并检查工作 **[!UICONTROL Jobs in discussion forums]** 流是否已启动且没有错误。
* 查看交付日志：

   * 在Adobe Campaign主页上，转到 **[!UICONTROL Campaigns > Navigation > Deliveries]**，然后打开分 **[!UICONTROL Discussion forum notification]** 发。
   * 在资源管理器中，转到， **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**&#x200B;然后单击 **[!UICONTROL Discussion forum notifications]**。
   在该框 **[!UICONTROL Discussion forum notifications]** 中，交付日志位于选项卡中 **[!UICONTROL Edit > Delivery]** 。 您还可以查看 **[!UICONTROL Tracking > Log]** 选项卡和 **[!UICONTROL Exclusion causes]** 选项卡。

