---
solution: Campaign Classic
product: campaign
title: '在 Adobe Campaign 中配置移动应用程序 '
description: 了解如何开始移动应用程序配置
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 965aee2e310dd7e35d7a65bf9a1bda5dc8eb0959
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 8%

---


# 应用程序配置入门

在本节中，您可以根据销售在线假日套餐的公司找到配置示例。 他的移动应用程序(Neotrips)有两种版本可供客户使用：适用于Android的Neotrips和适用于iOS的Neotrips。

要以Adobe Campaign发送推送通知，您需要：

* 为Neotrips移动应用程序创建&#x200B;**[!UICONTROL Mobile application]**&#x200B;类型信息服务。 有关iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service)，请参阅[此部分。 和[此部分用于Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service)。
* 将应用程序的iOS和Android版本添加到此服务。
* 为iOS和Android创建投放。 [请参见此页面](../../delivery/using/creating-notifications.md)。

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>转到服务的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡，视图列表服务的订户，即在其移动设备上安装应用程序并同意接收通知的所有用户。

## 安装软件包{#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中安装移动应用程序包](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

作为混合／托管客户，请与[Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)团队联系，以访问活动中的推送通知渠道。

作为预置型客户，您需要安装内置软件包。

>[!CAUTION]
>
>了解有关活动内置包、最佳实践和建议的更多信息，请参阅本页](../../installation/using/installing-campaign-standard-packages.md)。[

安装步骤有：

1. 从Adobe Campaign客户端控制台的&#x200B;**[!UICONTROL Tools > Advanced > Package import...]**&#x200B;访问包导入向导。

   ![](assets/package_ios.png)

1. 选择 **[!UICONTROL Install a standard package]**。

1. 在出现的列表中，选中&#x200B;**[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;开始软件包安装。

   安装包后，进度栏显示&#x200B;**100%**，安装日志中显示以下消息：**[!UICONTROL Installation of packages successful]**。

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安装窗口。

完成此步骤后，您可以配置Android和iOS应用程序。
请参阅以下部分：

* [iOS 配置步骤](../../delivery/using/configuring-the-mobile-application.md)

* [Android 配置步骤](../../delivery/using/configuring-the-mobile-application-android.md)
