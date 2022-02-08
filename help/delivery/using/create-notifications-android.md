---
product: campaign
title: 为Android设备创建推送通知
description: 了解如何为Android创建推送通知
feature: Push
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 1%

---

# 创建Android通知{#create-notificaations-android}

![](../../assets/common.svg)

使用Adobe Campaign在Android设备上发送推送通知。 有关投放创建的全局概念，请参阅 [此部分](steps-about-delivery-creation-steps.md).

首先创建新投放。

![](assets/nmac_delivery_1.png)

使用Firebase Cloud Messaging，您可以选择两种类型的消息：

* **[!UICONTROL Data message]**，由客户端应用程序处理。
   <br>消息将直接发送到移动应用程序，该应用程序将生成Android通知并将通知显示到设备。 数据消息仅包含您的自定义应用程序变量。

* **[!UICONTROL Notification message]**，由FCM SDK自动处理。
   <br> FCM会代表客户端应用程序在用户设备上自动显示消息。 Notification messages contain a predefined set of parameters and options but can still be further personalized with custom application variables.

For more information on Firebase Cloud Messaging messages types, refer to [FCM documentation](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages).

## Create a data message {#creating-data-message}

1. 转到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 单击 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 选择 **[!UICONTROL Deliver on Android (android)]** 在 **[!UICONTROL Delivery template]** 下拉菜单。 添加 **[!UICONTROL Label]** 投放。

1. 单击 **[!UICONTROL To]** 定义要定位的群体。 默认情况下， **[!UICONTROL Subscriber application]** 目标映射。 单击 **[!UICONTROL Add]** 来选择您的服务。

   ![](assets/nmac_android_7.png)

1. 在 **[!UICONTROL Target type]** 窗口，选择 **[!UICONTROL Subscribers of an Android mobile application]** 单击 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 下拉列表中，选择您之前创建的服务，然后选择应用程序并单击 **[!UICONTROL Finish]**.
的 **[!UICONTROL Application variables]** 将根据在配置步骤中添加的内容自动添加。

   ![](assets/nmac_android_6.png)

1. 选择 **[!UICONTROL data message]** as **[!UICONTROL Message Type]**.

1. 编辑您的富通知。

   ![](assets/nmac_android_5.png)

1. 您可以在之前配置的 **[!UICONTROL Application variables]** （如果需要）。 **[!UICONTROL Application variables]** 需要在Android服务中进行配置，并且是发送到移动设备的消息有效负荷的一部分。

1. 单击 **[!UICONTROL Save]** 并发送投放内容。

当在订阅者的Android移动设备上收到图像和网页时，应在推送通知中显示。

![](assets/nmac_android_4.png)

## 创建通知消息 {#creating-notification-message}

>[!NOTE]
>
>通知消息的其他选项仅在HTTP v1 API配置中可用。 有关更多信息，请参阅此](configuring-the-mobile-application-android.md#android-service-httpv1)章节[。

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中创建Android推送通知](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. 转到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 单击 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. Select **[!UICONTROL Deliver on Android (android)]** in the **[!UICONTROL Delivery template]** drop-down. 添加 **[!UICONTROL Label]** 投放。

1. Click **[!UICONTROL To]** to define the population to target. 默认情况下， **[!UICONTROL Subscriber application]** 目标映射。 单击 **[!UICONTROL Add]** 来选择您的服务。

   ![](assets/nmac_android_7.png)

1. 在 **[!UICONTROL Target type]** 窗口，选择 **[!UICONTROL Subscribers of an Android mobile application]** 单击 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 下拉列表中，选择您之前创建的服务，然后选择应用程序并单击 **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. 选择 **[!UICONTROL notification message]** as **[!UICONTROL Message Type]**.

1. Add a title and edit your message. 使用个性化的推送通知 **[!UICONTROL Notification options]**:

   * **[!UICONTROL Channel ID]**:设置通知的渠道ID。 The app must create a channel with this channel ID before any notification with this channel ID is received.
   * **[!UICONTROL Sound]**:设置设备收到通知时要播放的声音。
   * **[!UICONTROL Color]**:设置通知的图标颜色。
   * **[!UICONTROL Icon]**:将通知的图标设置为在用户档案的设备上显示。
   * **[!UICONTROL Tag]**:设置用于替换通知抽屉中现有通知的标识符。
   * **[!UICONTROL Click action]**:设置与用户单击您的通知关联的操作。

   有关 **[!UICONTROL Notification options]** 以及如何填写这些字段，请参阅 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_8.png)

1. If your application is configured with HTTP v1 API protocol, you can further personalize your push notification with the following **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**:设置通知的滚动条文本。 仅适用于设置为Android 5.0 Lollipop的设备。
   * **[!UICONTROL Image]**: Set the image&#39;s URL to be displayed in your notification.
   * **[!UICONTROL Notification Count]**: Set the number of new unread information to display directly on the application icon.
   * **[!UICONTROL Sticky]**:设置为true或false。 如果设置为false，则当用户单击通知时，该通知将自动被取消。 如果设置为true，则即使用户单击通知，也仍会显示通知。
   * **[!UICONTROL Notification Priority]**:将通知的优先级设置为默认、最小、低或高。 有关更多信息，请参阅 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**:将通知的可见性级别设置为公共、私有或机密。 有关更多信息，请参阅 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   有关 **[!UICONTROL HTTP v1 additional options]** 以及如何填写这些字段，请参阅 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification).

   ![](assets/nmac_android_9.png)

1. 您可以在之前配置的 **[!UICONTROL Application variables]** （如果需要）。 **[!UICONTROL Application variables]** 需要在Android服务中进行配置，并且是发送到移动设备的消息有效负荷的一部分。

1. 单击 **[!UICONTROL Save]** 并发送投放内容。

当在订阅者的Android移动设备上收到图像和网页时，应在推送通知中显示。
