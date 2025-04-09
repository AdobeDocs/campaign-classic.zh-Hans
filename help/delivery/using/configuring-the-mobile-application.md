---
product: campaign
title: 在Adobe Campaign中配置iOS移动应用程序
description: 了解如何为iOS设置移动应用程序
feature: Push
role: User, Developer
level: Intermediate, Experienced
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 3%

---

# iOS 配置步骤 {#configuring-the-mobile-application-in-adobe-campaign-ios}

安装包后，您可以在Adobe Campaign Classic中定义iOS应用程序设置。

关键步骤包括：

1. [配置iOS外部帐户](#configuring-external-account-ios)
1. [配置iOS服务](#configuring-ios-service)
1. [在Campaign中集成iOS移动应用程序](#creating-ios-app)

然后，您将能够[为iOS设备](create-notifications-ios.md)创建推送通知。

## 配置iOS外部帐户 {#configuring-external-account-ios}

对于iOS，iOS HTTP/2连接器会向HTTP/2 APN发送通知。

要配置此连接器，请执行以下步骤：

1. 转到&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。
1. 选择&#x200B;**[!UICONTROL iOS routing]**&#x200B;外部帐户。
1. 在&#x200B;**[!UICONTROL Connector]**&#x200B;选项卡中，使用以下URL填写&#x200B;**[!UICONTROL Access URL of the connector]**&#x200B;字段： ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 单击 **[!UICONTROL Save]**。

您的iOS连接器现已配置完成。 您可以开始创建服务。

## 配置iOS服务 {#configuring-ios-service}

>[!CAUTION]
>
>在与Adobe SDK进行任何集成之前，必须为推送操作配置应用程序。
>
>如果不是这种情况，请参阅[此页面](https://developer.apple.com/documentation/usernotifications)。

1. 转到&#x200B;**[!UICONTROL Profiles and Targets > Services and subscriptions]**&#x200B;节点并单击&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定义&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。
1. 转到&#x200B;**[!UICONTROL Type]**&#x200B;字段并选择&#x200B;**[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >默认&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;目标映射已链接到收件人表。 如果要使用其他目标映射，则需要创建一个新的目标映射，并在服务的&#x200B;**[!UICONTROL Target mapping]**&#x200B;字段中输入该映射。 有关创建目标映射的详细信息，请参阅[配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 创建iOS开发和生产应用程序。 有关更多信息，请参阅此](configuring-the-mobile-application.md#creating-ios-app)章节[。

## 创建iOS移动应用程序 {#creating-ios-app}

创建服务后，在Campaign中创建您的iOS应用程序。 按照下面的步骤进行操作：

1. 在新创建的服务中，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 出现以下窗口。 选择&#x200B;**[!UICONTROL Create an iOS application]**，并首先输入&#x200B;**[!UICONTROL Label]**。

   ![](assets/nmac_ios_2.png)

1. 作为一个选项，您可以根据需要使用大约&#x200B;**[!UICONTROL Application variables]**扩充推送消息内容。 这些都是完全可自定义的，并且是发送到移动设备的消息有效负载的一部分。
在以下示例中，我们添加**mediaURl**&#x200B;和&#x200B;**mediaExt**&#x200B;以创建富推送通知，然后为应用程序提供要在通知中显示的图像。

   ![](assets/nmac_ios_3.png)

1. **[!UICONTROL Subscription parameters]**&#x200B;选项卡允许您使用&#x200B;**[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**&#x200B;架构的扩展名定义映射。

   >[!NOTE]
   >
   >请确保不要将相同的证书用于应用程序的开发版本（沙盒）和生产版本。

1. **[!UICONTROL Sounds]**&#x200B;选项卡允许您指定要播放的声音。 单击&#x200B;**[!UICONTROL Add]**&#x200B;并填写&#x200B;**[!UICONTROL Internal name]**&#x200B;字段，该字段必须包含嵌入在应用程序中的文件的名称或系统声音的名称。

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;开始配置开发应用程序。

1. 确保通过SDK在Adobe Campaign和应用程序代码中定义相同的&#x200B;**[!UICONTROL Integration key]**。 <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).-->此集成密钥（特定于每个应用程序）允许您将移动应用程序链接到Adobe Campaign平台。

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;可使用字符串值完全自定义，但需要与SDK中指定的值完全相同。

1. 从&#x200B;**[!UICONTROL Application icon]**&#x200B;字段中选择一个现成的图标，以个性化服务中的移动应用程序。

1. 选择 **[!UICONTROL Authentication mode]**。

   ![](assets/nmac_ios_5.png)

   提供了两种模式：

   * （推荐） **[!UICONTROL Token-based authentication]**：填写APNs连接设置&#x200B;**[!UICONTROL Key Id]**、**[!UICONTROL Team Id]**&#x200B;和&#x200B;**[!UICONTROL Bundle Id]**，然后单击&#x200B;**[!UICONTROL Enter the private key...]**&#x200B;选择您的p8证书。 有关&#x200B;**[!UICONTROL Token-based authentication]**&#x200B;的详细信息，请参阅[Apple文档](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}。

   * **[!UICONTROL Certificate-based authentication]**：单击&#x200B;**[!UICONTROL Enter the certificate...]**，然后选择p12密钥并输入移动应用程序开发人员提供的密码。

   >[!NOTE]
   >
   > Adobe建议对您的iOS配置使用&#x200B;**[!UICONTROL Token-based authentication]**，因为P8身份验证密钥更新且更安全。

1. 使用&#x200B;**[!UICONTROL Test the connection]**&#x200B;按钮验证您的配置。

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;开始配置生产应用程序，并遵循上面详述的相同步骤。


1. 单击 **[!UICONTROL Finish]**。

您的iOS应用程序现在可以在Campaign Classic中使用。
