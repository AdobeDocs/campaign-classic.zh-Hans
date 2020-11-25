---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign中配置Android移动应用程序
description: 了解如何设置适用于Android的移动应用程序
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 2%

---


# Android 配置步骤

安装该包后，您可以在Adobe Campaign Classic定义Android应用程序设置。

>[!NOTE]
>
>要了解如何为iOS配置应用程序以及如何为iOS创建投放，请参阅此 [部分](../../delivery/using/configuring-the-mobile-application.md)。

关键步骤包括：

1. [配置Android外部帐户](#configuring-external-account-android)
1. [配置Android服务](#configuring-android-service)
1. [在活动中创建移动应用程序](#creating-android-app)
1. [使用其他数据扩展应用程序模式](#extend-subscription-schema)

然后，您将能够创 [建Android富通知](#creating-android-delivery)。

## 配置Android外部帐户 {#configuring-external-account-android}

对于Android，有两个连接器可用：

* V1连接器，允许每个MTA子项连接一个。
* V2连接器允许与FCM服务器同时连接以提高吞吐量。

要选择要使用的连接器，请执行以下步骤：

1. 转到 **[!UICONTROL Administration > Platform > External accounts]**。
1. Select the **[!UICONTROL Android routing]** external account.
1. 在选项卡 **[!UICONTROL Connector]** 中，填写以下字 **[!UICONTROL JavaScript used in the connector]** 段：

   对于Android V2:https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > 您也可以按照以下方式配置它：https://localhost:8080/nms/jsp/androidPushConnector.js，但我们建议您使用连接器的版本2。

   ![](assets/nmac_connectors3.png)

1. 对于Android V2,Adobe服务器配置文件(serverConf.xml)中还提供一个附加参数：

   * **maxGCMConnectPerChild**:每个子服务器启动的对FCM的并行HTTP请求的最大限制（默认为8）。

## 配置Android服务 {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中配置Android服务](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. 转到节 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 点并单击 **[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. Define a **[!UICONTROL Label]** and an **[!UICONTROL Internal name]**.
1. 转到字段 **[!UICONTROL Type]** 并选择 **[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >默认 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目标映射链接到收件人表。 如果要使用其他目标映射，您需要创建新目标映射并在服务 **[!UICONTROL Target mapping]** 字段中输入它。 有关创建目标映射的详细信息，请参阅 [配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然后，单击 **[!UICONTROL Add]** 按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 创建Android应用程序。 有关更多信息，请参阅此](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app)章节[。

## 创建Android移动应用程序 {#creating-android-app}

创建服务后，您现在需要创建Android应用程序：

1. 在新创建的服务中，单击 **[!UICONTROL Add]** 按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 选 **[!UICONTROL Create an Android application]** 择并输入 **[!UICONTROL Label]**。

   ![](assets/nmac_android.png)

1. 确保通过SDK **[!UICONTROL Integration key]** 在Adobe Campaign和应用程序代码中定义相同的内容。 有关此内容的详细信息，请参阅： [将活动SDK集成到移动应用程序中](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。

   >[!NOTE]
   >
   > 它 **[!UICONTROL Integration key]** 可以使用字符串值完全自定义，但必须与SDK中指定的值完全相同。

1. 选择 **[!UICONTROL API version]**:HTTP v1或HTTP（传统）。 本节详细介绍了 [这些配置](#select-api-version)

1. Fill in the **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** fields.

1. 单击 **[!UICONTROL Finish]**，然后单击 **[!UICONTROL Save]**。您的Android应用程序现已准备好用于Campaign Classic。

默认情况下，Adobe Campaign在表的( **[!UICONTROL User identifier]** @userKey)字段中保存一 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 个键。 此键允许您将订阅链接到收件人。 要收集其他合并关键项（如复杂数据），您需要应用以下配置：

### 选择API版本{#select-api-version}

创建服务和新的移动应用程序后，您需要根据所选的API版本配置移动应用程序。

* **HTTP v1配置** 在本节中有详细 [介绍](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1)。
* **HTTP(旧版** )配置详见本 [节](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http)。

#### 配置HTTP v1 API{#android-service-httpv1}

要配置HTTP v1 API版本，请执行以下步骤：

1. 在窗 **[!UICONTROL Mobile application creation wizard]** 口中， **[!UICONTROL HTTPV1]** 从下 **[!UICONTROL API version]** 拉菜单中选择。

1. 单击 **[!UICONTROL Load project json file to extract projet details...]** 以直接加载您的JSON密钥文件。 有关如何提取JSON文件的详细信息，请参阅本 [页](https://firebase.google.com/docs/admin/setup#initialize-sdk)。

   您还可以人工输入以下详细信息：
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. 单 **[!UICONTROL Test the connection]** 击以检查配置是否正确以及营销服务器是否有权访问FCM。

   >[!CAUTION]
   >
   >对于中间源部署， **[!UICONTROL Test connection]** 该按钮将不检查MID服务器是否有权访问FCM服务器。

   ![](assets/nmac_android_11.png)

1. 作为一种选项，您可以根据需要添加一些内容来丰富 **[!UICONTROL Application variables]** 推送消息内容。 这些是完全可自定义的，并且是发送到移动设备的消息有效负荷的一部分。

1. 单击 **[!UICONTROL Finish]**，然后单击 **[!UICONTROL Save]**。您的Android应用程序现已准备好用于Campaign Classic。

以下是FCM有效负荷名称，以进一步个性化您的推送通知：

| 消息类型 | 可配置消息元素（FCM有效负荷名称） | 可配置选项（FCM有效负荷名称） |
|:-:|:-:|:-:|
| 数据消息 | N/A | validate_only |
| 通知消息 | title, body, android_渠道id，图标，声音，标记，颜色，click_action，图像，ticker，粘性，可见性，notification_priority,notification_count <br> | validate_only |

<br>
<br>

#### 配置HTTP（传统）API{#android-service-http}

要配置HTTP（旧版）API版本，请执行以下步骤：

1. 在窗 **[!UICONTROL Mobile application creation wizard]** 口中， **[!UICONTROL HTTP (legacy)]** 从下 **[!UICONTROL API version]** 拉菜单中选择。

1. 输入 **[!UICONTROL Project key]** 由移动应用程序开发人员提供的内容。

1. 作为一种选项，您可以根据需要添加一些内容来丰富 **[!UICONTROL Application variables]** 推送消息内容。 这些是完全可自定义的，并且是发送到移动设备的消息有效负荷的一部分。

   在以下示例中，我们添 **加标题**、 **imageURL** 和 **** iconURL以创建富推送通知，然后为应用程序提供要在通知中显示的图像、标题和图标。

   ![](assets/nmac_android_2.png)

1. 单击 **[!UICONTROL Finish]**，然后单击 **[!UICONTROL Save]**。您的Android应用程序现已准备好用于Campaign Classic。

以下是FCM有效负荷名称，以进一步个性化您的推送通知：

| 消息类型 | 可配置消息元素（FCM有效负荷名称） | 可配置选项（FCM有效负荷名称） |
|:-:|:-:|:-:|
| 数据消息 | N/A | dryRun |
| 通知消息 | title, body, android_渠道id，图标，声音，标记，颜色， click_action <br> | dryRun |

<br>

## 扩展appsubscriptionRcp模式 {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中扩展appsubscriptionRcp模式](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

您需要扩展 **appsubscriptionRcp** ，以定义新的附加字段，以将应用程序的参数存储在活动库中。 例如，这些字段将用于个性化。 操作步骤：

1. 创建模式的扩 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 展并定义新字段。 在本页中进一步了解模式 [扩展](../../configuration/using/about-schema-edition.md)

1. 在选项卡中定义 **[!UICONTROL Subscription parameters]** 映射。

   >[!CAUTION]
   >
   >确保选项卡中的配 **[!UICONTROL Subscription parameters]** 置名称与手机应用程序代码中的配置名称相同。 请参阅将 [活动SDK集成到移动应用程序部](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) 分。

## 创建Android富通知 {#creating-android-delivery}

通过Firebase Cloud Messaging，您可以选择两种类型的消息：

* **[!UICONTROL Data message]**，由客户端应用程序处理。
   <br>消息会直接发送到手机应用程序，该应用程序将生成android通知并显示到设备。 数据消息只包含自定义应用程序变量。

* **[!UICONTROL Notification message]**，由FCM SDK自动处理。
   <br> FCM会代表客户端应用程序在用户设备上自动显示消息。 通知消息包含预定义的参数和选项集，但仍然可以通过自定义应用程序变量进一步个性化。

有关Firebase Cloud消息消息类型的详细信息，请参阅 [FCM文档](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages)。

### 创建数据消息 {#creating-data-message}

1. 转到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 单击 **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. 在 **[!UICONTROL Deliver on Android (android)]** 下拉 **[!UICONTROL Delivery template]** 框中选择。 添加 **[!UICONTROL Label]** 投放。

1. 单击 **[!UICONTROL To]** 以定义要目标的人口。 默认情况下， **[!UICONTROL Subscriber application]** 应用目标映射。 单击 **[!UICONTROL Add]** 以选择您的服务。

   ![](assets/nmac_android_7.png)

1. 在窗口 **[!UICONTROL Target type]** 中，选择 **[!UICONTROL Subscribers of an Android mobile application]** 并单击 **[!UICONTROL Next]**。

1. 在下拉 **[!UICONTROL Service]** 列表中，选择您之前创建的服务，然后选择应用程序并单击 **[!UICONTROL Finish]**。
根据 **[!UICONTROL Application variables]** 在配置步骤中添加的内容，系统会自动添加。

   ![](assets/nmac_android_6.png)

1. 选择 **[!UICONTROL data message]** 为 **[!UICONTROL Message Type]**。

1. 编辑您的丰富通知。

   ![](assets/nmac_android_5.png)

1. 您可以根据需要在之前配置的内容 **[!UICONTROL Application variables]** 中添加信息。 **[!UICONTROL Application variables]** 需要在Android服务中进行配置，并且是发送到移动设备的消息有效负荷的一部分。

1. 单击 **[!UICONTROL Save]** 并发送投放。

当在用户的移动Android设备上收到图像和网页时，应在推送通知中显示。

![](assets/nmac_android_4.png)

### 创建通知消息 {#creating-notification-message}

>[!NOTE]
>
>通知消息的其他选项仅在HTTP v1 API配置中可用。 有关更多信息，请参阅此](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1)章节[。

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中创建Android推送通知](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. 转到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 单击 **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. 在 **[!UICONTROL Deliver on Android (android)]** 下拉 **[!UICONTROL Delivery template]** 框中选择。 添加 **[!UICONTROL Label]** 投放。

1. 单击 **[!UICONTROL To]** 以定义要目标的人口。 默认情况下， **[!UICONTROL Subscriber application]** 应用目标映射。 单击 **[!UICONTROL Add]** 以选择您的服务。

   ![](assets/nmac_android_7.png)

1. 在窗口 **[!UICONTROL Target type]** 中，选择 **[!UICONTROL Subscribers of an Android mobile application]** 并单击 **[!UICONTROL Next]**。

1. 在下拉 **[!UICONTROL Service]** 列表中，选择您之前创建的服务，然后选择应用程序并单击 **[!UICONTROL Finish]**。

   ![](assets/nmac_android_6.png)

1. 选择 **[!UICONTROL notification message]** 为 **[!UICONTROL Message Type]**。

1. 添加标题并编辑邮件。 通过以下方式个性化您的推送通 **[!UICONTROL Notification options]**&#x200B;知：

   * **[!UICONTROL Channel ID]**:设置通知的渠道ID。 在收到任何具有此渠道ID的通知之前，应用程序必须创建具有此渠道ID的渠道。
   * **[!UICONTROL Sound]**:设置设备收到通知时要播放的声音。
   * **[!UICONTROL Color]**:设置通知的图标颜色。
   * **[!UICONTROL Icon]**:将通知的图标设置为在用户档案设备上显示。
   * **[!UICONTROL Tag]**:设置用于在通知抽屉中替换现有通知的标识符。
   * **[!UICONTROL Click action]**:设置与用户关联的操作，单击您的通知。

   有关如何填写这 **[!UICONTROL Notification options]** 些字段的详细信息，请参阅 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)。

   ![](assets/nmac_android_8.png)

1. 如果您的应用程序已配置HTTP v1 API协议，则可以使用以下内容进一步个性化推送通知 **[!UICONTROL HTTPV1 additional options]**:

   * **[!UICONTROL Ticker]**:设置通知的滚动文本。 仅适用于设置为Android 5.0 Lollipop的设备。
   * **[!UICONTROL Image]**:设置要在通知中显示的图像URL。
   * **[!UICONTROL Notification Count]**:设置要直接在应用程序图标上显示的新未读信息数。
   * **[!UICONTROL Sticky]**:设置为true或false。 如果设置为false，则当用户单击通知时，通知将自动消失。 如果设置为true，则即使用户单击通知也仍会显示通知。
   * **[!UICONTROL Notification Priority]**:将通知的优先级设置为默认、最小、低或高。 For more on this, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**:将通知的可见性级别设置为公共、私有或机密。 For more on this, refer to [FCM documentation](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   有关如何填写这 **[!UICONTROL HTTP v1 additional options]** 些字段的详细信息，请参阅 [FCM文档](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)。

   ![](assets/nmac_android_9.png)

1. 您可以根据需要在之前配置的内容 **[!UICONTROL Application variables]** 中添加信息。 **[!UICONTROL Application variables]** 需要在Android服务中进行配置，并且是发送到移动设备的消息有效负荷的一部分。

1. 单击 **[!UICONTROL Save]** 并发送投放。

当在用户的移动Android设备上收到图像和网页时，应在推送通知中显示。
