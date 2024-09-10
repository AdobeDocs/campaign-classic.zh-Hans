---
product: campaign
title: 在Adobe Campaign中配置移动应用程序
description: 了解如何开始使用移动应用程序配置
feature: Push
role: User, Developer
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 5%

---

# 应用程序配置入门



您可以在此部分找到基于销售在线假日包公司的配置示例。 其移动应用程序(Neotrips)有两种版本可供客户使用：Android的Neotrips和iOS的Neotrips。

要在Adobe Campaign中发送推送通知，您需要：

* 为Neotrips移动应用程序创建&#x200B;**[!UICONTROL Mobile application]**&#x200B;类型信息服务。 请参阅iOS](configuring-the-mobile-application.md#configuring-ios-service)的[此部分。 和[Android](configuring-the-mobile-application-android.md#configuring-android-service)的此分区。
* 将应用程序的iOS和Android版本添加到此服务。
* 为[iOS](create-notifications-ios.md)和[Android](create-notifications-android.md)创建投放。

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>转到服务的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡，以查看服务的订阅者列表，即在其移动设备上安装了应用程序并同意接收通知的所有人员。

## 安装包 {#installing-package-ios}

[!BADGE 内部部署和混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"}

![](assets/do-not-localize/how-to-video.png) [在视频中了解如何安装移动应用包](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

作为混合/托管客户，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)团队以访问Campaign中的推送通知渠道。

作为内部部署客户，您需要安装内置软件包。

>[!CAUTION]
>
>在[此页面](../../installation/using/installing-campaign-standard-packages.md)中了解有关Campaign内置包、最佳实践和建议的更多信息。

安装步骤为：

1. 从Adobe Campaign客户端控制台的&#x200B;**[!UICONTROL Tools > Advanced > Import package]**&#x200B;访问包导入助手。

   ![](assets/package_ios.png)

1. 选择 **[!UICONTROL Install a standard package]**。

1. 在显示的列表中，选中&#x200B;**[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;以开始安装包。

   安装包后，进度条显示&#x200B;**100%**，您可以在安装日志中看到以下消息： **[!UICONTROL Installation of packages successful]**。

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]**&#x200B;安装窗口。

完成此步骤后，您可以配置Android和iOS应用程序。
请参阅以下章节：

* [iOS 配置步骤](configuring-the-mobile-application.md)

* [Android 配置步骤](configuring-the-mobile-application-android.md)
