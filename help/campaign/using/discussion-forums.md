---
solution: Campaign Classic
product: campaign
title: 论坛
description: 论坛
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# 论坛{#discussion-forums}

Adobe Campaign操作员可以使用论坛来共享信息。 以下元素各有其论坛：计划、项目、活动、资源、模拟、股票。 每家运营商还设有个人论坛。 所有讨论都是公开的，甚至在个人论坛上。

运营商可订阅论坛，以在每次发布消息时接收通知电子邮件。

## 访问论坛{#accessing-a-forum}

要访问活动、操作员等的论坛，请转到其仪表板并单击右上角的&#x200B;**[!UICONTROL Forum]**&#x200B;链接。 此链接还为您提供论坛中消息的总数。

![](assets/mrm_forum_access_link.png)

## 使用论坛{#using-a-forum}

消息及其响应按时间顺序显示（从最新到最旧）。

要显示消息的内容，请单击其标题。

![](assets/mrm_forum_expand_msg.png)

**开始新讨论**

要开始新讨论，请单击右上角的&#x200B;**[!UICONTROL Add a discussion]**&#x200B;按钮。 出现&#x200B;**[!UICONTROL Discussion forum]**&#x200B;框（请参见下文）。

![](assets/mrm_forum_new_thread.png)

**向现有讨论发布消息**

要向现有讨论发布消息，请打开要回答的消息，然后单击左上角的&#x200B;**[!UICONTROL Reply]**&#x200B;链接。 出现&#x200B;**[!UICONTROL Discussion forum]**&#x200B;框（请参见下文）。

![](assets/mrm_forum_answer_msg.png)

当您回复邮件时，发布原始邮件的人将收到通知。

**编写消息**

在&#x200B;**[!UICONTROL Discussion forum]**&#x200B;框中：

1. 在&#x200B;**[!UICONTROL Message]**&#x200B;字段中输入文本，在&#x200B;**[!UICONTROL Subject]**&#x200B;字段中输入讨论标题。

   ![](assets/mrm_forum_edit_msg.png)

1. 如有必要：

   * 如果希望有人参加未订阅论坛的讨论，请使用&#x200B;**[!UICONTROL Operator to notify]**&#x200B;字段。 操作员将收到此特定消息的通知电子邮件（他们将不订阅论坛）。 要通知多个运算符，请选择操作员组。
   * 要向邮件中添加附件，请单击&#x200B;**[!UICONTROL Browse]**。 附件还将包含在通知电子邮件中。 附件只能单独发送：要发送多个文件，您需要将其压缩。

1. 单击&#x200B;**[!UICONTROL Create the message]**&#x200B;将其发布到论坛。

>[!NOTE]
>
>在将消息发布到论坛后，便无法再更改或删除该消息。

## 发布到操作员{#posting-to-the-personal-forum-of-an-operator}的个人论坛

例如，如果您的消息与特定活动无关，但您仍希望跟踪Adobe Campaign中的对话，则可以向操作员的论坛发布消息。 个人论坛是公开的，所有运营商都将看到您的信息。 操作员每次向其个人论坛发帖时都会收到一条消息。

要访问运营商论坛，请执行以下操作：

* 如果您具有访问资源管理器&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;节点的必要权限，请打开所需运算符的仪表板，然后单击右上角的&#x200B;**[!UICONTROL Forum]**&#x200B;链接。
* 如果没有，请在Adobe Campaign中查找操作员的姓名(通过此操作员发布到论坛的消息，将任务分配给他)，然后单击该姓名以访问他们的仪表板。 您还可以要求管理员创建操作员文件夹的视图。

## 订阅论坛{#subscribing-to-a-forum}

订阅论坛可让您关注讨论。 每次向论坛发布消息时，您都会收到电子邮件通知。 此电子邮件将包含邮件正文和任何附件。 要回答邮件，请单击电子邮件正文，然后登录到Adobe CampaignWeb界面。 订阅论坛时，所有人都可以看到此信息。

* 要订阅论坛，请单击消息列表上方右上部的&#x200B;**[!UICONTROL Follow discussions]**&#x200B;按钮。

   ![](assets/mrm_forum_subscribe.png)

   该部分呈蓝色，显示您已订阅论坛。

* 要取消订阅论坛，请单击&#x200B;**[!UICONTROL Unsubscribe]**&#x200B;按钮。

   ![](assets/mrm_forum_unsubscribe.png)

* 您的个人仪表板列表您订阅的论坛。 单击&#x200B;**[!UICONTROL Subscription to discussion forums]**&#x200B;链接以显示列表，然后单击您感兴趣的项目以访问其论坛。

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   有关个人仪表板的详细信息，请参阅[此部分](../../platform/using/access-management.md#operators)。

* 要查看谁订阅了论坛，请单击消息列表上方的&#x200B;**[!UICONTROL List of subscribers to this discussion forum]**&#x200B;链接。

   ![](assets/mrm_forum_subscribers.png)

## 检查通知投放{#checking-notification-delivery}

如果订阅论坛的操作员没有按预期方式接收通知：

* 检查是否在操作员的用户档案中输入电子邮件地址。
* 转到&#x200B;**[!UICONTROL Administration > Production > Technical workflows > Campaign processes]**&#x200B;节点，检查&#x200B;**[!UICONTROL Jobs in discussion forums]**&#x200B;工作流是否已启动且没有错误。
* 视图投放日志:

   * 在Adobe Campaign主页中，转至&#x200B;**[!UICONTROL Campaigns > Navigation > Deliveries]**，然后打开&#x200B;**[!UICONTROL Discussion forum notification]**&#x200B;投放。
   * 在资源管理器中，转至&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**，然后单击&#x200B;**[!UICONTROL Discussion forum notifications]**。

   在&#x200B;**[!UICONTROL Discussion forum notifications]**&#x200B;框中，**[!UICONTROL Edit > Delivery]**&#x200B;选项卡中显示投放日志。 您还可以视图&#x200B;**[!UICONTROL Tracking > Log]**&#x200B;和&#x200B;**[!UICONTROL Exclusion causes]**&#x200B;选项卡。

