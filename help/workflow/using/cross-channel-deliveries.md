---
title: 跨渠道交付
seo-title: 跨渠道交付
description: 跨渠道交付
seo-description: null
page-status-flag: never-activated
uuid: 191ff39e-f739-48b3-8865-ad1b641b7499
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 8dda45b4-4b5d-4b4e-a8b4-45d9bc49aaf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fa2b6890d3c9eaf7b4b6521b2edfb494faa4798c

---


# 跨渠道交付{#cross-channel-deliveries}

跨渠道交付在营销活动工作流活动 **[!UICONTROL Deliveries]** 的选项卡中可用。

它们允许您创建特定渠道的分发。 您可以像使用经典交付向导一样，指定要作为分发基础的模板及其内容。

可用的各种渠道包括：

* [电子邮件](../../delivery/using/about-email-channel.md)
* [直邮](../../delivery/using/about-direct-mail-channel.md)
* [移动](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

您可以使用不同的定位活动为工作流上游的交付指定一个目标。

例如，我们将在一周后创建一个工作流，用于向订阅推送通知的用户发送电子邮件或短信，然后发送推送通知。 操作步骤：

1. 创建营销活动。
1. 在营销 **[!UICONTROL Targeting and workflows]** 活动的选项卡中，向工作流 **[!UICONTROL Query]** 中添加一个。
1. 配置查询。 例如，在此我们选择订阅推送通知的收件人作为目标维。

   >[!NOTE]
   >
   >对于推送通知，请记住使用订阅者应用 **程序目标** 维度。

   ![](assets/cross_channel_delivery_1.png)

1. 将筛选条件添加到查询。 在这种情况下，我们将选择具有移动号码或电子邮件地址的收件人。

   ![](assets/cross_channel_delivery_2.png)

1. 在您的工 **[!UICONTROL Split]** 作流中添加活动，以划分具有移动号码的收件人和具有电子邮件地址的收件人。
1. 在选项卡 **[!UICONTROL Delivery]** 中，为每个目标选择分发。

   通过双击工作流中的交付活动，以与经典交付向导相同的方式创建交付。 For more on this, refer to this [page](../../delivery/using/about-email-channel.md).

   ![](assets/cross_channel_delivery_3.png)

1. 添加和配置活 **[!UICONTROL Wait]** 动，以便收件人不会同时接收过多的提交。
1. 添加一 **[!UICONTROL Split]** 个活动以划分iOS或Android移动应用程序的订阅者。

   为每个操作系统选择一项服务。 有关服务创建的详细信息，请参阅此 [页](../../delivery/using/configuring-the-mobile-application.md)。

   ![](assets/cross_channel_delivery_4.png)

1. 为每个操作系统选择和配置移动应用程序交付。

   ![](assets/cross_channel_delivery_5.png)
