---
solution: Campaign Classic
product: campaign
title: '在 Adobe Campaign 中配置移动应用程序 '
description: 了解如何开始移动应用程序配置
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 10%

---


# 应用程序配置入门

在本节中，您可以根据销售在线假日套餐的公司找到配置示例。 他的移动应用程序(Neotrips)有两种版本可供客户使用：适用于Android的Neotrips和适用于iOS的Neotrips。

要以Adobe Campaign发送推送通知，您需要：

* 为Neotrips移 **[!UICONTROL Mobile application]** 动应用程序创建类型信息服务。 有关iOS, [请参阅此部分](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service)。 以及 [此部分针对Android](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service)。
* 将应用程序的iOS和Android版本添加到此服务。
* 为iOS和Android创建投放。 [请参阅此页面](../../delivery/using/creating-notifications.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>转到服务 **[!UICONTROL Subscriptions]** 的选项卡，以视图订阅者对服务的列表，即在其移动设备上安装应用程序并同意接收通知的所有用户。

## 安装包 {#installing-package-ios}

作为混合／托管客户，请与Adobe客户关怀团队联系，以访问活动中的推送通知渠道。

作为预置型客户，您需要执行以下安装步骤：

1. 从导入向导客户端控制台 **[!UICONTROL Tools > Advanced > Package import...]** 中访问包Adobe Campaign。

   ![](assets/package_ios.png)

1. 选择 **[!UICONTROL Install a standard package]**。

1. 在显示的列表中，选中 **[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 单 **[!UICONTROL Next]**&#x200B;击，然 **[!UICONTROL Start]** 后开始包安装。

   安装包后，进度栏显示 **100%** ，您可以在安装日志中看到以下消息： **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安装窗口。

完成此步骤后，您可以配置Android和iOS应用程序。
请参阅以下部分：

* [iOS 配置步骤](../../delivery/using/configuring-the-mobile-application.md)

* [Android 配置步骤](../../delivery/using/configuring-the-mobile-application-android.md)
