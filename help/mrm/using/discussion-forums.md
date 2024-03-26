---
product: campaign
title: 论坛
description: 了解如何使用Campaign论坛
feature: Resource Management
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 222853c5-c754-4c0b-8ee4-a64b2f8677a4
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 1%

---

# 论坛{#discussion-forums}



Adobe Campaign操作员可以使用论坛来共享信息。 以下每个元素都有自己的论坛：计划、方案、促销活动、资源、模拟、库存。 每个操作员也有一个个人论坛。 所有讨论都是公开的，甚至在个人论坛上也是如此。

操作员可以订阅论坛，以便在每次发布消息时接收通知电子邮件。

## 访问论坛 {#accessing-a-forum}

要访问营销活动、操作员等的论坛，请转到其仪表板并单击 **[!UICONTROL Forum]** 右上角的链接。 此链接还会提供论坛中的邮件总数。

![](assets/mrm_forum_access_link.png)

## 使用论坛 {#using-a-forum}

消息及其响应按时间顺序显示（从最新到最旧）。

要显示消息的内容，请单击其标头。

![](assets/mrm_forum_expand_msg.png)

**开始新的讨论**

要开始新的讨论，请单击 **[!UICONTROL Add a discussion]** 按钮进行标记。 此 **[!UICONTROL Discussion forum]** 框（见下文）。

![](assets/mrm_forum_new_thread.png)

**将消息发布到现有讨论**

要将邮件发布到现有讨论，请打开要应答的邮件，然后单击 **[!UICONTROL Reply]** 左上角的链接。 此 **[!UICONTROL Discussion forum]** 框（见下文）。

![](assets/mrm_forum_answer_msg.png)

当您回复邮件时，发布原始邮件的人员将收到通知。

**编写消息**

在 **[!UICONTROL Discussion forum]** 框：

1. 在 **[!UICONTROL Message]** 字段和讨论标题 **[!UICONTROL Subject]** 字段。

   ![](assets/mrm_forum_edit_msg.png)

1. 如有必要：

   * 如果您希望某个未订阅论坛的用户参与讨论，请使用 **[!UICONTROL Operator to notify]** 字段。 操作员将收到此特定消息的通知电子邮件（他们不会被订阅论坛）。 要通知多个操作员，请选择一组操作员。
   * 若要向邮件添加附件，请单击 **[!UICONTROL Browse]**. 附件也将包含在通知电子邮件中。 附件只能单独发送：要发送多个文件，您需要压缩文件。

1. 单击 **[!UICONTROL Create the message]** 以将其发布到论坛。

>[!NOTE]
>
>消息发布到论坛后，无法再更改或删除。

## 发布到操作员的个人论坛 {#posting-to-the-personal-forum-of-an-operator}

例如，如果您的消息与特定营销活动无关，但仍希望在Adobe Campaign中跟踪对话，则您可以将消息发布到操作员的论坛。 个人论坛是公开的，所有操作员都将看到您的消息。 每次有人在个人论坛中发帖时，操作员都会收到消息。

访问操作员的论坛：

* 如果您拥有访问 **[!UICONTROL Administration > Access management > Operators]** 打开所需运算符的仪表板，然后单击 **[!UICONTROL Forum]** 右上角的链接。
* 如果没有，请在Adobe Campaign中查找操作员的姓名（通过操作员在论坛中发布的消息、分配给他们的任务），然后单击该消息以访问其仪表板。 您还可以要求管理员创建operator文件夹的视图。

## 订阅论坛 {#subscribing-to-a-forum}

通过订阅论坛，可关注讨论。 每次在论坛中发布消息时，您都会收到电子邮件通知。 此电子邮件将包含邮件正文和任何附件。 要回复消息，请单击电子邮件正文，然后登录到Adobe Campaign Web界面。 当您订阅论坛时，此信息对所有人可见。

* 要订阅论坛，请单击 **[!UICONTROL Follow discussions]** 按钮进行标记。

  ![](assets/mrm_forum_subscribe.png)

  部分变为蓝色，并显示您订阅了论坛。

* 要取消订阅论坛，请单击 **[!UICONTROL Unsubscribe]** 按钮。

  ![](assets/mrm_forum_unsubscribe.png)

* 您的个人信息板列出了您订阅的论坛。 单击 **[!UICONTROL Subscription to discussion forums]** 链接以显示列表，然后单击感兴趣的项目以访问其论坛。

  ![](assets/platform_dashboard_operator_subscr_forums.png)

  有关个人仪表板的详细信息，请参阅 [本节](../../platform/using/access-management-operators.md).

* 要查看订阅了论坛的用户，请单击 **[!UICONTROL List of subscribers to this discussion forum]** 消息列表上方的链接。

  ![](assets/mrm_forum_subscribers.png)

## 检查通知投放 {#checking-notification-delivery}

如果订阅论坛的操作员未按预期收到通知：

* 检查操作员的配置文件中是否输入了电子邮件地址。
* 转到 **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** 节点，并检查 **[!UICONTROL Jobs in discussion forums]** 工作流已启动且没有错误。
* 查看投放日志：

   * 在Adobe Campaign主页上，转到 **[!UICONTROL Campaigns > Navigation > Deliveries]**，然后打开 **[!UICONTROL Discussion forum notification]** 投放。
   * 在资源管理器中，转到 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**，然后单击 **[!UICONTROL Discussion forum notifications]**.

  在 **[!UICONTROL Discussion forum notifications]** 框中，投放日志位于 **[!UICONTROL Edit > Delivery]** 选项卡。 您还可以查看 **[!UICONTROL Tracking > Log]** 和 **[!UICONTROL Exclusion causes]** 选项卡。
