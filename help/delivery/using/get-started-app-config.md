---
product: campaign
title: '在 Adobe Campaign 中配置移动应用程序 '
description: 了解如何从移动应用程序配置开始
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 11%

---

# 应用程序配置入门

在此部分中，您可以找到基于销售在线假日套餐的公司的配置示例。 其移动应用程序(Neotrips)有两个版本可供客户使用：Android版Neotrips和iOS版Neotrips。

要在Adobe Campaign中发送推送通知，您需要：

* 为Neotrips移动应用程序创建&#x200B;**[!UICONTROL Mobile application]**&#x200B;类型的信息服务。 有关iOS](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service)，请参阅[此部分。 和[此部分适用于Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service)。
* 将应用程序的iOS和Android版本添加到此服务。
* 为iOS和Android创建投放。 [请参见此页面](../../delivery/using/creating-notifications.md)。

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>转到服务的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;选项卡，查看服务的订阅者列表，即在其移动设备上安装了应用程序并同意接收通知的所有用户。

## 安装软件包{#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [了解如何在视频中安装移动应用程序包](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

作为混合/托管客户，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)团队以访问Campaign中的推送通知渠道。

作为内部部署客户，您需要安装内置包。

>[!CAUTION]
>
>在[此页面](../../installation/using/installing-campaign-standard-packages.md)中了解有关Campaign内置软件包、最佳实践和建议的更多信息。

安装步骤包括：

1. 从Adobe Campaign客户端控制台的&#x200B;**[!UICONTROL Tools > Advanced > Package import...]**&#x200B;访问包导入向导。

   ![](assets/package_ios.png)

1. 选择 **[!UICONTROL Install a standard package]**。

1. 在显示的列表中，选中&#x200B;**[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;以开始安装软件包。

   安装包后，进度栏显示&#x200B;**100%**，您可以在安装日志中看到以下消息：**[!UICONTROL Installation of packages successful]**。

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安装窗口。

完成此步骤后，您可以配置Android和iOS应用程序。
请参阅以下章节：

* [iOS 配置步骤](../../delivery/using/configuring-the-mobile-application.md)

* [Android 配置步骤](../../delivery/using/configuring-the-mobile-application-android.md)
