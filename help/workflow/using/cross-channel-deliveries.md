---
solution: Campaign Classic
product: campaign
title: 跨渠道投放
description: 进一步了解跨渠道投放
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 7%

---


# 跨渠道投放{#cross-channel-deliveries}

跨渠道投放位于活动工作流活动的&#x200B;**[!UICONTROL Deliveries]**&#x200B;选项卡中。

它们允许您创建特定投放。 您可以按与经典投放相同的方式指定要基于其的投放向导及其内容。

可用的各种渠道包括：

* [电子邮件](../../delivery/using/about-email-channel.md)
* [直邮](../../delivery/using/about-direct-mail-channel.md)
* [手机](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

您可以使用不同的定位目标为工作流上游的投放指定一个活动。

例如，我们将创建一个工作流，在一周后为推送通知订户发送电子邮件或SMS，然后发送推送通知。 操作步骤：

1. 创建营销策划.
1. 在活动的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中，将&#x200B;**[!UICONTROL Query]**&#x200B;添加到工作流。
1. 配置查询。 例如，在此我们选择订阅推送通知的收件人作为目标维。

   >[!NOTE]
   >
   >对于推送通知，请记住使用&#x200B;**订阅者应用程序**&#x200B;目标维。

   ![](assets/cross_channel_delivery_1.png)

1. 将筛选条件添加到查询。 在这种情况下，我们将选择具有移动号码或电子邮件地址的收件人。

   ![](assets/cross_channel_delivery_2.png)

1. 在您的工作流中添加&#x200B;**[!UICONTROL Split]**&#x200B;活动，将具有移动号码的收件人和具有电子邮件地址的分开。
1. 在&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡中，为每个投放选择一个目标。

   通过在工作流中多次单击投放活动，以与经典投放向导相同的方式创建投放。 有关详细信息，请参见此 [ 页面](../../delivery/using/about-email-channel.md)。

   ![](assets/cross_channel_delivery_3.png)

1. 添加和配置&#x200B;**[!UICONTROL Wait]**&#x200B;活动，以便收件人一次不接收太多投放。
1. 添加&#x200B;**[!UICONTROL Split]**&#x200B;活动以划分iOS或Android移动应用程序的订阅者。

   为每个操作系统选择一项服务。 有关服务创建的详细信息，请参阅此[页面](../../delivery/using/configuring-the-mobile-application.md)。

   ![](assets/cross_channel_delivery_4.png)

1. 为每个操作系统选择并配置移动应用程序投放。

   ![](assets/cross_channel_delivery_5.png)
