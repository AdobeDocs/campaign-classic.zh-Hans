---
product: campaign
title: 在Adobe Campaign中配置iOS移动应用程序
description: 了解如何设置适用于iOS的移动应用程序
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 5%

---

# iOS 配置步骤 {#configuring-the-mobile-application-in-adobe-campaign-ios}

![](../../assets/common.svg)

安装包后，您可以在Adobe Campaign Classic中定义iOS应用程序设置。

>[!NOTE]
>
>要了解如何配置Android应用程序以及如何创建Android投放，请参阅此[部分](configuring-the-mobile-application-android.md)。

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
1. 在&#x200B;**[!UICONTROL Connector]**&#x200B;选项卡的&#x200B;**[!UICONTROL Access URL of the connector]**&#x200B;字段中，填写以下URL:```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 单击 **[!UICONTROL Save]**。

您的iOS连接器现已配置完成。 您可以开始创建服务。

## 配置iOS服务 {#configuring-ios-service}

>[!CAUTION]
>
>必须在将应用程序集成到Adobe Campaign SDK之前，为推送操作配置了应用程序。
>
>如果不是这种情况，请参阅[此页面](https://developer.apple.com/documentation/usernotifications)。

1. 转到&#x200B;**[!UICONTROL Profiles and Targets > Services and subscriptions]**&#x200B;节点，然后单击&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定义&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。
1. 转到&#x200B;**[!UICONTROL Type]**&#x200B;字段并选择&#x200B;**[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >默认的&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;目标映射已链接到收件人表。 如果要使用其他目标映射，则需要创建新的目标映射，并在服务的&#x200B;**[!UICONTROL Target mapping]**&#x200B;字段中输入该映射。 有关创建目标映射的更多信息，请参阅[配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 创建iOS开发和生产应用程序。 有关更多信息，请参阅此](configuring-the-mobile-application.md#creating-ios-app)章节[。

## 创建iOS移动设备应用程序 {#creating-ios-app}

创建服务后，在Campaign中创建iOS应用程序。 按照下面的步骤进行操作：

1. 在您新创建的服务中，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 出现以下窗口。 选择&#x200B;**[!UICONTROL Create an iOS application]**，然后输入&#x200B;**[!UICONTROL Label]**&#x200B;开始。

   ![](assets/nmac_ios_2.png)

1. 作为一种选项，您可以根据需要使用某些&#x200B;**[!UICONTROL Application variables]**扩充推送消息的内容。 这些任务是完全可自定义的，并且是发送到移动设备的消息有效负荷的一部分。
在以下示例中，我们添加**mediaURL**&#x200B;和&#x200B;**mediaExt**&#x200B;以创建富推送通知，然后向应用程序提供要在通知中显示的图像。

   ![](assets/nmac_ios_3.png)

1. 利用&#x200B;**[!UICONTROL Subscription parameters]**&#x200B;选项卡，可定义扩展为&#x200B;**[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**&#x200B;架构的映射。

   >[!NOTE]
   >
   >请确保对应用程序的开发版本（沙盒）和生产版本不使用相同的证书。

1. **[!UICONTROL Sounds]**&#x200B;选项卡允许您指定要播放的声音。 单击&#x200B;**[!UICONTROL Add]**&#x200B;并填写&#x200B;**[!UICONTROL Internal name]**&#x200B;字段，该字段必须包含应用程序中嵌入的文件名称或系统声音的名称。

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;以开始配置开发应用程序。

1. 确保通过SDK在Adobe Campaign和应用程序代码中定义相同的&#x200B;**[!UICONTROL Integration key]**。 有关更多信息，请参阅：[将Campaign SDK集成到移动应用程序](integrating-campaign-sdk-into-the-mobile-application.md)。 此集成密钥是特定于每个应用程序的，允许您将移动应用程序关联到Adobe Campaign平台。

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;可通过字符串值完全自定义，但需要与SDK中指定的值完全相同。

1. 从&#x200B;**[!UICONTROL Application icon]**&#x200B;字段中选择一个现成的图标，以个性化您服务中的移动应用程序。

1. 选择 **[!UICONTROL Authentication mode]**。请注意，您随后始终可以在移动应用程序的&#x200B;**[!UICONTROL Certificate]**&#x200B;选项卡中更改身份验证模式。
   * **[!UICONTROL Certificate-based authentication]**:单 **[!UICONTROL Enter the certificate...]**  击，然后选择您的p12密钥，并输入由移动应用程序开发人员提供的密码。
   * **[!UICONTROL Token-based authentication]**:填写连接设置， **[!UICONTROL Key ID]**&#x200B;然 **[!UICONTROL Team ID]** 后 **[!UICONTROL Bundle ID]** 通过单击选择您的p8证书 **[!UICONTROL Enter the private key]**。有关&#x200B;**[!UICONTROL Token-based authentication]**&#x200B;的更多信息，请参阅[Apple文档](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns)。

   >[!NOTE]
   >
   > Adobe建议对iOS配置使用&#x200B;**[!UICONTROL Token-based authentication]**，因为此身份验证模式更安全，不会绑定到证书过期。

   ![](assets/nmac_ios_4.png)

1. 您可以单击&#x200B;**[!UICONTROL Test the connection]**&#x200B;以确保成功。

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;开始配置生产应用程序，并按照与上面所述相同的步骤操作。

   ![](assets/nmac_ios_5.png)

1. 单击 **[!UICONTROL Finish]**。

您的iOS应用程序现已准备就绪，可在Campaign Classic中使用。
