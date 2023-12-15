---
product: campaign
title: 为Android设备创建推送通知
description: 了解如何为Android创建推送通知
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Push
role: User, Developer, Data Engineer
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 9756f05e3887bc74578bae00138c4d1317a480f8
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 1%

---

# 为Android创建通知{#create-notificaations-android}

使用Adobe Campaign在Android设备上发送推送通知。 中介绍了有关投放创建的全局概念 [本节](steps-about-delivery-creation-steps.md).

首先，创建新投放。

![](assets/nmac_delivery_1.png)

使用Firebase Cloud Messaging，您可以选择两种类型的消息：

* **[!UICONTROL Data message]**，由客户端应用程序处理。
  <br>消息直接发送到移动应用程序，该应用程序将生成并向设备显示Android通知。 数据消息仅包含您的自定义应用程序变量。

* **[!UICONTROL Notification message]**，由FCM SDK自动处理。
  <br> FCM会代表客户端应用程序在用户设备上自动显示消息。 通知消息包含预定义的一组参数和选项，但仍可以使用自定义应用程序变量进一步个性化。

有关Firebase Cloud Messaging消息类型的详细信息，请参阅 [FCM文档](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages){target="_blank"}.


## 创建数据消息 {#creating-data-message}

1. 转到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 单击 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 选择 **[!UICONTROL Deliver on Android (android)]** 在 **[!UICONTROL Delivery template]** 下拉菜单。 添加 **[!UICONTROL Label]** 到您的投放。

1. 单击 **[!UICONTROL To]** 以定义要定位的群体。 默认情况下， **[!UICONTROL Subscriber application]** 目标映射已应用。 单击 **[!UICONTROL Add]** 以选择您的服务。

   ![](assets/nmac_android_7.png)

1. 在 **[!UICONTROL Target type]** 窗口，选择 **[!UICONTROL Subscribers of an Android mobile application]** 并单击 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 下拉列表中，选择您之前创建的服务，然后选择应用程序，并单击 **[!UICONTROL Finish]**.
此 **[!UICONTROL Application variables]** 根据在配置步骤中添加的内容，自动添加。

   ![](assets/nmac_android_6.png)

1. 选择 **[!UICONTROL data message]** 作为 **[!UICONTROL Message Type]**.

1. 编辑富通知。

   ![](assets/nmac_android_5.png)

1. 您可以在之前配置的信息中添加信息 **[!UICONTROL Application variables]** 如果需要。 **[!UICONTROL Application variables]** 需要在Android服务中进行配置，并且是发送到移动设备的消息有效负载的一部分。

1. 单击 **[!UICONTROL Save]** 并发送您的投放。

在订阅者的移动Android设备上接收时，推送通知中应显示图像和网页。

![](assets/nmac_android_4.png)

## 创建通知消息 {#creating-notification-message}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中创建Android推送通知](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html#additional-resources){target="_blank"}.

1. 转到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 单击 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 选择 **[!UICONTROL Deliver on Android (android)]** 在 **[!UICONTROL Delivery template]** 下拉菜单。 添加 **[!UICONTROL Label]** 到您的投放。

1. 单击 **[!UICONTROL To]** 以定义要定位的群体。 默认情况下， **[!UICONTROL Subscriber application]** 目标映射已应用。 单击 **[!UICONTROL Add]** 以选择您的服务。

   ![](assets/nmac_android_7.png)

1. 在 **[!UICONTROL Target type]** 窗口，选择 **[!UICONTROL Subscribers of an Android mobile application]** 并单击 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 下拉列表中，选择您之前创建的服务，然后选择应用程序，并单击 **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. 选择 **[!UICONTROL notification message]** 作为 **[!UICONTROL Message Type]**.

1. 添加标题并编辑消息。 使用以下内容个性化您的推送通知 **[!UICONTROL Notification options]**：

   * **[!UICONTROL Channel ID]**：设置通知的渠道ID。 在收到任何具有此渠道ID的通知之前，应用程序必须创建具有此渠道ID的渠道。
   * **[!UICONTROL Sound]**：设置设备收到通知时播放的声音。
   * **[!UICONTROL Color]**：设置通知的图标颜色。
   * **[!UICONTROL Icon]**：将通知的图标设置为在用户档案的设备上显示。
   * **[!UICONTROL Tag]**：设置用于替换通知抽屉中现有通知的标识符。
   * **[!UICONTROL Click action]**：设置与用户单击您的通知关联的操作。

   欲知详情，请参阅 **[!UICONTROL Notification options]** 以及如何填写这些字段，请参阅 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_8.png)

1. 如果您的应用程序配置了HTTP v1 API协议，则可以使用以下内容进一步将推送通知个性化 **[!UICONTROL HTTPV1 additional options]**：

   * **[!UICONTROL Ticker]**：设置通知的滚动条文本。 仅适用于设置为Android 5.0 Lollipop的设备。
   * **[!UICONTROL Image]**：设置要在通知中显示的图像URL。
   * **[!UICONTROL Notification Count]**：设置直接显示在应用程序图标上的新未读信息数量。
   * **[!UICONTROL Sticky]**：设置为true或false。 如果设置为false，则当用户单击通知时，会自动取消通知。 如果设置为true，则即使用户单击通知，也会显示通知。
   * **[!UICONTROL Notification Priority]**：将通知的优先级设置为“默认”、“最小”、“低”或“高”。 有关详细信息，请参见 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**：将通知的可见性级别设置为public、private或secret。 有关详细信息，请参见 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   欲知详情，请参阅 **[!UICONTROL HTTP v1 additional options]** 以及如何填写这些字段，请参阅 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_9.png)

1. 您可以在之前配置的信息中添加信息 **[!UICONTROL Application variables]** 如果需要。 **[!UICONTROL Application variables]** 需要在Android服务中进行配置，并且是发送到移动设备的消息有效负载的一部分。

1. 单击 **[!UICONTROL Save]** 并发送您的投放。

在订阅者的移动Android设备上接收时，推送通知中应显示图像和网页。
