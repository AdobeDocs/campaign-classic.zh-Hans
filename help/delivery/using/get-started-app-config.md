---
product: campaign
title: 在Adobe Campaign中配置移动应用程序
description: 了解如何开始使用移动应用程序配置
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 10%

---

# 应用程序配置入门



您可以在此部分找到基于销售在线假日软件包的公司进行配置的示例。 其移动应用程序(Neotrips)有两种版本可供客户使用：Neotrips for Android和Neotrips for iOS。

要在Adobe Campaign中发送推送通知，您需要：

* 创建 **[!UICONTROL Mobile application]** 键入Neotrips移动应用程序的信息服务。 请参阅 [适用于iOS的此部分](configuring-the-mobile-application.md#configuring-ios-service). 和 [此部分适用于Android](configuring-the-mobile-application-android.md#configuring-android-service).
* 将应用程序的iOS和Android版本添加到此服务。
* 创建投放 [iOS](create-notifications-ios.md) 和 [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>转到 **[!UICONTROL Subscriptions]** 选项卡以查看服务的订阅者列表，即在其移动设备上安装了应用程序并同意接收通知的所有人员。

## 安装包 {#installing-package-ios}

[!BADGE 内部部署和混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"}

![](assets/do-not-localize/how-to-video.png) [在视频中了解如何安装移动应用程序包](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

作为混合/托管客户，请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 团队访问Campaign中的推送通知渠道。

作为内部部署客户，您需要安装内置软件包。

>[!CAUTION]
>
>在中详细了解Campaign内置包、最佳实践和建议 [此页面](../../installation/using/installing-campaign-standard-packages.md).

安装步骤包括：

1. 从访问资源包导入向导 **[!UICONTROL Tools > Advanced > Import package]** 在Adobe Campaign客户端控制台中。

   ![](assets/package_ios.png)

1. 选择 **[!UICONTROL Install a standard package]**。

1. 在显示的列表中，选中 **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. 单击 **[!UICONTROL Next]**，则 **[!UICONTROL Start]** 以开始软件包安装。

   安装包后，进度条将显示 **100%** 并且您可以在安装日志中看到以下消息： **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安装窗口。

完成此步骤后，您可以配置Android和iOS应用程序。
请参阅以下章节：

* [iOS 配置步骤](configuring-the-mobile-application.md)

* [Android 配置步骤](configuring-the-mobile-application-android.md)
