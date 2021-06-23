---
product: campaign
title: 在Adobe Campaign中配置Android移动应用程序
description: 了解如何设置适用于Android的移动应用程序
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 3%

---

# Android 配置步骤

安装包后，您可以在Adobe Campaign Classic中定义Android应用程序设置。

>[!NOTE]
>
>要了解如何配置iOS应用程序以及如何创建iOS投放，请参阅此[部分](configuring-the-mobile-application.md)。

关键步骤包括：

1. [配置Android外部帐户](#configuring-external-account-android)
1. [配置Android服务](#configuring-android-service)
1. [在Campaign中创建移动设备应用程序](#creating-android-app)
1. [使用附加数据扩展应用程序模式](#extend-subscription-schema)

然后，您将能够[创建Android富通知](create-notifications-android.md)。

## 配置Android外部帐户 {#configuring-external-account-android}

对于Android，提供了两个连接器：

* V1连接器，允许每个MTA子项有一个连接。
* V2连接器，允许与FCM服务器同时连接以提高吞吐量。

要选择要使用的连接器，请执行以下步骤：

1. 转到&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。
1. 选择&#x200B;**[!UICONTROL Android routing]**&#x200B;外部帐户。
1. 在&#x200B;**[!UICONTROL Connector]**&#x200B;选项卡中，填写&#x200B;**[!UICONTROL JavaScript used in the connector]**&#x200B;字段：

   对于Android V2:https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > 您也可以按照以下方式对其进行配置： https://localhost:8080/nms/jsp/androidPushConnector.js ，但我们建议您使用连接器版本2。

   ![](assets/nmac_connectors3.png)

1. 对于Android V2,Adobe服务器配置文件(serverConf.xml)中还提供了一个额外的参数：

   * **maxGCMConnectPerChild**:每个子服务器启动的对FCM的并行HTTP请求的最大限制（默认为8）。

## 配置Android服务 {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中配置Android服务](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. 转到&#x200B;**[!UICONTROL Profiles and Targets > Services and subscriptions]**&#x200B;节点，然后单击&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定义&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。
1. 转到&#x200B;**[!UICONTROL Type]**&#x200B;字段并选择&#x200B;**[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >默认的&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;目标映射已链接到收件人表。 如果要使用其他目标映射，则需要创建新的目标映射，并在服务的&#x200B;**[!UICONTROL Target mapping]**&#x200B;字段中输入该映射。 有关创建目标映射的更多信息，请参阅[此部分](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 创建Android应用程序。 如需详细信息，请参阅[此部分](configuring-the-mobile-application-android.md#creating-android-app)。

## 创建Android移动应用程序 {#creating-android-app}

创建服务后，您现在需要创建Android应用程序：

1. 在您新创建的服务中，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 选择&#x200B;**[!UICONTROL Create an Android application]**&#x200B;并输入&#x200B;**[!UICONTROL Label]**。

   ![](assets/nmac_android.png)

1. 确保通过SDK在Adobe Campaign和应用程序代码中定义相同的&#x200B;**[!UICONTROL Integration key]**。 如需详细信息，请参阅[此部分](integrating-campaign-sdk-into-the-mobile-application.md)。

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;可通过字符串值完全自定义，但需要与SDK中指定的值完全相同。

1. 选择&#x200B;**[!UICONTROL API version]**:HTTP v1或HTTP（旧版）。 [此部分](#select-api-version)中详细介绍了这些配置

1. 填写&#x200B;**[!UICONTROL Firebase Cloud Messaging the Android connection settings]**&#x200B;字段。

1. 单击 **[!UICONTROL Finish]**，然后单击 **[!UICONTROL Save]**。您的Android应用程序现已准备就绪，可在Campaign Classic中使用。

默认情况下，Adobe Campaign会在&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;表的&#x200B;**[!UICONTROL User identifier]**(@userKey)字段中保存一个键。 利用此键，可将订阅链接到收件人。 要收集其他数据（例如复杂的协调键值），您需要应用以下配置：

### 选择API版本{#select-api-version}

创建服务和新的移动应用程序后，您需要根据所选的API版本配置移动应用程序。

* **HTTP v1** 配置在此部分 [中详述](configuring-the-mobile-application-android.md#android-service-httpv1)。
* **此部分** 中详细介绍了HTTP(旧 [版)](configuring-the-mobile-application-android.md#android-service-http)配置。

#### 配置HTTP v1 API{#android-service-httpv1}

要配置HTTP v1 API版本，请执行以下步骤：

1. 在&#x200B;**[!UICONTROL Mobile application creation wizard]**&#x200B;窗口的&#x200B;**[!UICONTROL API version]**&#x200B;下拉菜单中，选择&#x200B;**[!UICONTROL HTTPV1]**。

1. 单击&#x200B;**[!UICONTROL Load project json file to extract projet details...]**&#x200B;直接加载您的JSON密钥文件。 有关如何提取JSON文件的更多信息，请参阅[此页面](https://firebase.google.com/docs/admin/setup#initialize-sdk)。

   您还可以手动输入以下详细信息：
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. 单击&#x200B;**[!UICONTROL Test the connection]**&#x200B;以检查您的配置是否正确以及营销服务器是否有权访问FCM。

   >[!CAUTION]
   >
   >对于中间源部署， **[!UICONTROL Test connection]**&#x200B;按钮将不检查MID服务器是否有权访问FCM服务器。

   ![](assets/nmac_android_11.png)

1. 作为一种选项，您可以根据需要使用某些&#x200B;**[!UICONTROL Application variables]**&#x200B;扩充推送消息的内容。 这些任务是完全可自定义的，并且是发送到移动设备的消息有效负荷的一部分。

1. 单击 **[!UICONTROL Finish]**，然后单击 **[!UICONTROL Save]**。您的Android应用程序现已准备就绪，可在Campaign Classic中使用。

以下是用于进一步个性化推送通知的FCM有效负载名称：

| 消息类型 | 可配置消息元素（FCM有效负载名称） | 可配置选项（FCM有效负载名称） |
|:-:|:-:|:-:|
| 数据消息 | N/A | validate_only |
| 通知消息 | 标题， body， android channel_id，图标，声音，标记，颜色， click_action，图像， ticker，置顶，可见性， notification_priority， notification_count <br> | validate_only |

<br>
<br>

#### 配置HTTP（旧版）API{#android-service-http}

要配置HTTP（旧版）API版本，请执行以下步骤：

1. 在&#x200B;**[!UICONTROL Mobile application creation wizard]**&#x200B;窗口的&#x200B;**[!UICONTROL API version]**&#x200B;下拉菜单中，选择&#x200B;**[!UICONTROL HTTP (legacy)]**。

1. 输入由移动应用程序开发人员提供的&#x200B;**[!UICONTROL Project key]**。

1. 作为一种选项，您可以根据需要使用某些&#x200B;**[!UICONTROL Application variables]**&#x200B;扩充推送消息的内容。 这些任务是完全可自定义的，并且是发送到移动设备的消息有效负荷的一部分。

   在以下示例中，我们添加&#x200B;**title**、**imageURL**&#x200B;和&#x200B;**iconURL**&#x200B;以创建富推送通知，然后向应用程序提供要在通知中显示的图像、标题和图标。

   ![](assets/nmac_android_2.png)

1. 单击 **[!UICONTROL Finish]**，然后单击 **[!UICONTROL Save]**。您的Android应用程序现已准备就绪，可在Campaign Classic中使用。

以下是用于进一步个性化推送通知的FCM有效负载名称：

| 消息类型 | 可配置消息元素（FCM有效负载名称） | 可配置选项（FCM有效负载名称） |
|:-:|:-:|:-:|
| 数据消息 | 不适用 | dryRun |
| 通知消息 | 标题， body， android_channel_id，图标，声音，标记，颜色， click_action <br> | dryRun |

<br>

## 扩展appsubscriptionRcp模式 {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中扩展appsubscriptionRcp模式](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

您需要扩展&#x200B;**appsubscriptionRcp**&#x200B;以定义新的其他字段，以将应用程序中的参数存储在Campaign数据库中。 例如，这些字段将用于个性化。 操作步骤：

1. 创建&#x200B;**[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**&#x200B;架构的扩展并定义新字段。 在[此页面](../../configuration/using/about-schema-edition.md)中了解有关模式扩展的更多信息

1. 在&#x200B;**[!UICONTROL Subscription parameters]**&#x200B;选项卡中定义映射。

   >[!CAUTION]
   >
   >确保&#x200B;**[!UICONTROL Subscription parameters]**&#x200B;选项卡中的配置名称与移动应用程序代码中的配置名称相同。 请参阅[此小节](integrating-campaign-sdk-into-the-mobile-application.md)。
