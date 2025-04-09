---
product: campaign
title: 在Adobe Campaign中配置Android移动应用程序
description: 了解如何为Android设置移动应用程序
feature: Push
role: User, Developer
level: Intermediate, Experienced
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 10%

---

# Android 配置步骤

安装包后，您可以在Adobe Campaign Classic中定义Android应用程序设置。

关键步骤包括：

1. [配置Android外部帐户](#configuring-external-account-android)
1. [配置Android服务](#configuring-android-service)
1. [在Campaign中创建移动应用程序](#creating-android-app)
1. [使用其他数据扩展应用程序架构](#extend-subscription-schema)

然后，您就可以[创建Android富通知](create-notifications-android.md)。

>[!IMPORTANT]
>
>Android Firebase Cloud Messaging (FCM) 服务的一些重要更改将于 2024 年发布，并将影响您的 Adobe Campaign 实施。您可能需要更新 Android 推送消息的订阅服务配置，才能支持此更改。您已经可以检查并执行操作。 在此[Adobe Campaign v8技术说明](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=zh-Hans){target="_blank"}中了解详情。


## 配置Android外部帐户 {#configuring-external-account-android}

对于Android，提供了两个连接器：

* V1连接器，允许每个MTA子级有一个连接。
* V2连接器允许同时连接到FCM服务器以提高吞吐量。

要选择要使用的连接器，请执行以下步骤：

1. 转到&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。
1. 选择&#x200B;**[!UICONTROL Android routing]**&#x200B;外部帐户。
1. 在&#x200B;**[!UICONTROL Connector]**&#x200B;选项卡中，填写&#x200B;**[!UICONTROL JavaScript used in the connector]**&#x200B;字段：

   对于Android V2： https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > 您也可以按照https://localhost:8080/nms/jsp/androidPushConnector.js进行配置，但我们建议您使用连接器版本2。

   ![](assets/nmac_connectors3.png)

1. 对于Android V2，Adobe Server配置文件(serverConf.xml)中还提供了另一个参数：

   * **maxGCMConnectPerChild**：每个子服务器向FCM发出的并行HTTP请求的最大限制（默认为8）。

## 配置Android服务 {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign){target="_blank"}中配置Android服务。

1. 转到&#x200B;**[!UICONTROL Profiles and Targets > Services and subscriptions]**&#x200B;节点并单击&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定义&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。
1. 转到&#x200B;**[!UICONTROL Type]**&#x200B;字段并选择&#x200B;**[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >默认&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;目标映射已链接到收件人表。 如果要使用其他目标映射，则需要创建一个新的目标映射，并在服务的&#x200B;**[!UICONTROL Target mapping]**&#x200B;字段中输入该映射。 有关创建目标映射的详细信息，请参阅[此部分](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 创建您的Android应用程序。 如需详细信息，请参阅[此小节](configuring-the-mobile-application-android.md#creating-android-app)。

## 创建Android移动应用程序 {#creating-android-app}

创建服务后，您现在需要创建Android应用程序：

1. 在新创建的服务中，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 选择&#x200B;**[!UICONTROL Create an Android application]**&#x200B;并输入&#x200B;**[!UICONTROL Label]**。

   ![](assets/nmac_android.png)

1. 确保通过SDK在Adobe Campaign和应用程序代码中定义了相同的&#x200B;**[!UICONTROL Integration key]**。<!--For more on this, refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;可使用字符串值完全自定义，但需要与SDK中指定的值完全相同。

1. 选择&#x200B;**[!UICONTROL API version]**： HTTP v1或HTTP（旧版）。 [此部分](#select-api-version)中详细介绍了这些配置

1. 填写&#x200B;**[!UICONTROL Firebase Cloud Messaging the Android connection settings]**&#x200B;字段。

1. 单击&#x200B;**[!UICONTROL Finish]**，然后单击&#x200B;**[!UICONTROL Save]**。 您的Android应用程序现在可以在Campaign Classic中使用。

默认情况下，Adobe Campaign会在&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;表的&#x200B;**[!UICONTROL User identifier]** (@userKey)字段中保存一个键。 利用此密钥，可将订阅链接到收件人。 要收集其他数据（如复杂的协调密钥），您需要应用以下配置：

### 配置API版本{#select-api-version}

>[!IMPORTANT]
>
>Android Firebase Cloud Messaging (FCM) 服务的一些重要更改将于 2024 年发布，并将影响您的 Adobe Campaign 实施。作为Google不断努力改进其服务的一部分，旧版FCM API将于2024年6月20日&#x200B;**终止**。 在此[Adobe Campaign v8技术说明](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=zh-Hans){target="_blank"}中了解详情。

在创建服务和新的移动应用程序后，您需要配置移动应用程序。 不应选择&#x200B;**HTTP（旧版）** API，因为它已被Google弃用。

要配置HTTP v1 API版本，请执行以下步骤：

1. 在您的&#x200B;**[!UICONTROL Mobile application creation wizard]**&#x200B;窗口中，从&#x200B;**[!UICONTROL API version]**&#x200B;下拉菜单中选择&#x200B;**[!UICONTROL HTTPV1]**。

1. 单击&#x200B;**[!UICONTROL Load project json file to extract project details...]**&#x200B;直接加载您的JSON密钥文件。 有关如何提取JSON文件的详细信息，请参阅[此页面](https://firebase.google.com/docs/admin/setup#initialize-sdk)。

   您还可以手动输入以下详细信息：
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. 单击&#x200B;**[!UICONTROL Test the connection]**&#x200B;以检查您的配置是否正确，以及营销服务器是否有权访问FCM。

   >[!CAUTION]
   >
   >对于中间源部署，**[!UICONTROL Test connection]**&#x200B;按钮将不会检查MID服务器是否有权访问FCM服务器。

   ![](assets/nmac_android_11.png)

1. 作为一个选项，您可以根据需要使用大约&#x200B;**[!UICONTROL Application variables]**&#x200B;扩充推送消息内容。 这些都是完全可自定义的，并且是发送到移动设备的消息有效负载的一部分。

1. 单击&#x200B;**[!UICONTROL Finish]**，然后单击&#x200B;**[!UICONTROL Save]**。 您的Android应用程序现在可以在Campaign Classic中使用。

以下是FCM有效负荷名称，用于进一步个性化您的推送通知：

| 消息类型 | 可配置消息元素（FCM有效负荷名称） | 可配置选项（FCM有效负荷名称） |
|:-:|:-:|:-:|
| 数据消息 | N/A | validate_only |
| 通知消息 | title，正文， android_channel_id，图标，声音，标记，颜色，点击操作，图像，滚动条，粘性，可见性，通知优先级，通知计数<br> | validate_only |

## 扩展appsubscriptionRcp架构 {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中扩展appsubscriptionRcp架构](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html#extending-the-app-subscription-schema-to-personalize-push-notifications)

您需要扩展&#x200B;**appsubscriptionRcp**，以定义新的附加字段来将应用程序中的参数存储在Campaign数据库中。 例如，这些字段用于个性化。 操作步骤：

1. 创建&#x200B;**[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**&#x200B;架构的扩展并定义新字段。 在[此页面](../../configuration/using/about-schema-edition.md)中了解有关架构扩展的更多信息

1. 在&#x200B;**[!UICONTROL Subscription parameters]**&#x200B;选项卡中定义映射。

   >[!CAUTION]
   >
   >确保&#x200B;**[!UICONTROL Subscription parameters]**&#x200B;选项卡中的配置名称与移动应用程序代码中的配置名称相同。<!--Refer to [this section](integrating-campaign-sdk-into-the-mobile-application.md).-->
