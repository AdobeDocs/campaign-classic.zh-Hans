---
product: campaign
title: 在Adobe Campaign中配置iOS移动应用程序
description: 了解如何为iOS设置移动应用程序
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 3b8d685642fc74d918a0e312c66d5e4f7b424192
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 6%

---

# iOS 配置步骤 {#configuring-the-mobile-application-in-adobe-campaign-ios}

![](../../assets/common.svg)

安装包后，您可以在Adobe Campaign Classic中定义iOS应用程序设置。

>[!NOTE]
>
>要了解如何配置Android应用程序以及如何创建Android投放，请参阅此 [部分](configuring-the-mobile-application-android.md).

关键步骤包括：

1. [配置iOS外部帐户](#configuring-external-account-ios)
1. [配置iOS服务](#configuring-ios-service)
1. [在Campaign中集成iOS移动应用程序](#creating-ios-app)

然后，您将能够 [为iOS设备创建推送通知](create-notifications-ios.md).


## 配置iOS外部帐户 {#configuring-external-account-ios}

对于iOS,iOS HTTP/2连接器会向HTTP/2 APN发送通知。

要配置此连接器，请执行以下步骤：

1. 转到 **[!UICONTROL Administration > Platform > External accounts]**.
1. 选择 **[!UICONTROL iOS routing]** 外部帐户。
1. 在 **[!UICONTROL Connector]** ，填写 **[!UICONTROL Access URL of the connector]** 字段，其URL如下： ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 单击 **[!UICONTROL Save]**。

您的iOS连接器现已配置完成。 您可以开始创建服务。

## 配置iOS服务 {#configuring-ios-service}

>[!CAUTION]
>
>必须在将应用程序集成到Adobe Campaign SDK之前，为推送操作配置了应用程序。
>
>如果情况并非如此，请参阅 [本页](https://developer.apple.com/documentation/usernotifications).

1. 转到 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 节点，单击 **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. 定义 **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]**.
1. 转到 **[!UICONTROL Type]** 字段和选择 **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >默认 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目标映射已链接到收件人表。 如果要使用其他目标映射，则需要创建新的目标映射，并在 **[!UICONTROL Target mapping]** 字段。 有关创建目标映射的更多信息，请参阅 [配置指南](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. 然后，单击 **[!UICONTROL Add]** 按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 创建iOS开发和生产应用程序。 有关更多信息，请参阅此](configuring-the-mobile-application.md#creating-ios-app)章节[。

## 创建iOS移动应用程序 {#creating-ios-app}

创建服务后，在Campaign中创建iOS应用程序。 按照下面的步骤进行操作：

1. 在新创建的服务中，单击 **[!UICONTROL Add]** 按钮以选择应用程序类型。

   ![](assets/nmac_service_2.png)

1. 出现以下窗口。 选择 **[!UICONTROL Create an iOS application]** 从输入 **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. 作为一个选项，您可以使用 **[!UICONTROL Application variables]** （如果需要）。 这些任务是完全可自定义的，并且是发送到移动设备的消息有效负荷的一部分。
在以下示例中，我们添加 **mediaURL** 和 **mediaExt** 创建富推送通知，然后向应用程序提供要在通知中显示的图像。

   ![](assets/nmac_ios_3.png)

1. 的 **[!UICONTROL Subscription parameters]** 选项卡，用于定义具有 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 架构。

   >[!NOTE]
   >
   >请确保对应用程序的开发版本（沙盒）和生产版本不使用相同的证书。

1. 的 **[!UICONTROL Sounds]** 选项卡，可指定要播放的声音。 单击 **[!UICONTROL Add]** 填充 **[!UICONTROL Internal name]** 字段，其中必须包含应用程序中嵌入的文件名称或系统声音的名称。

1. 单击 **[!UICONTROL Next]** 以开始配置开发应用程序。

1. 确保相同 **[!UICONTROL Integration key]** 在Adobe Campaign中和通过SDK在应用程序代码中定义。 有关详细信息，请参见[此页面](integrating-campaign-sdk-into-the-mobile-application.md)。此集成密钥是特定于每个应用程序的，允许您将移动应用程序关联到Adobe Campaign平台。

   >[!NOTE]
   >
   > 的 **[!UICONTROL Integration key]** 可通过字符串值完全自定义，但必须与SDK中指定的值完全相同。

1. 从 **[!UICONTROL Application icon]** 字段来个性化服务中的移动应用程序。

1. 选择 **[!UICONTROL Authentication mode]**。请注意，您随后始终可以在 **[!UICONTROL Certificate]** 选项卡。
   * **[!UICONTROL Certificate-based authentication]**:单击 **[!UICONTROL Enter the certificate...]**  然后，选择p12密钥并输入由移动应用程序开发人员提供的密码。
   * **[!UICONTROL Token-based authentication]**:填写连接设置 **[!UICONTROL Key ID]**, **[!UICONTROL Team ID]** 和 **[!UICONTROL Bundle ID]** 然后，单击 **[!UICONTROL Enter the private key]**. 更多信息 **[!UICONTROL Token-based authentication]**，请参阅 [Apple文档](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe建议使用 **[!UICONTROL Token-based authentication]** 的iOS配置，因为此身份验证模式更加安全，不会绑定到证书过期。

   ![](assets/nmac_ios_4.png)

1. 您可以单击 **[!UICONTROL Test the connection]** 以确保成功。

1. 单击 **[!UICONTROL Next]** 要开始配置生产应用程序，请按照与上面所述相同的步骤操作。

   ![](assets/nmac_ios_5.png)

1. 单击 **[!UICONTROL Finish]**。

您的iOS应用程序现已准备就绪，可在Campaign Classic中使用。
