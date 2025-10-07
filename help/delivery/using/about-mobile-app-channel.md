---
product: campaign
title: 移动应用程序渠道入门
description: 开始使用Adobe Campaign中的移动应用程序渠道
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 2%

---

# 移动应用程序渠道入门{#about-mobile-app-channel}

使用Adobe Campaign创建推送通知投放，以向您的移动应用程序用户发送个性化消息。

推送通知允许您实时吸引iOS和Android上的用户。 无论发送更新、公告还是促销活动，您都可以控制内容、时间和定位。 请参阅[Adobe Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/emails/email){target=_blank}以了解如何设置和使用推送渠道、管理订阅、与APN和FCM集成以及个性化消息。

作为Campaign v8促销活动的一部分，重组了Campaign Classic文档。 公共功能现在仅在Campaign v8文档集中可用。

>[!BEGINTABS]

>[!TAB 推送渠道文档]

要了解有关推送通知渠道的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hans){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hans){target=_blank}


>[!TAB 推送投放创建]

请参阅Campaign v8文档以了解与推送投放创建相关的关键步骤：

* [创建推送通知](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hans#push-create){target="_blank"}：了解创建推送投放所需的不同步骤。
* [发送并监视推送通知](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hans#push-test){target="_blank"}：了解如何验证、发送和跟踪您的投放。
* [设计Android富推送投放](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html?lang=zh-Hans){target="_blank"}：了解如何为Android设备创建和配置富推送通知。
* [设计iOS富推送投放](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html?lang=zh-Hans){target="_blank"}：了解如何在Adobe Campaign v8中为iOS设备设计和配置富推送通知。


>[!TAB 推送参数]

请参阅Campaign v8文档中的这些页面以了解推送参数：

* [配置先决条件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hans#before-starting){target="_blank"}：了解如何设置权限并配置您的应用程序。
* [配置Launch属性](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hans#launch-property){target="_blank"}：了解如何在Adobe Experience Platform数据收集中设置移动标记属性以启用推送通知。
* [配置推送服务Mobile Services](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hans#push-service){target="_blank"}：在Adobe中设置iOS和Android推送服务，以便为移动设备应用程序用户启用有针对性的推送通知。
* [在移动资产中配置扩展](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hans#configure-extension){target="_blank"}：将Campaign扩展集成到移动资产中，以启用推送通知并有效管理用户交互。

>[!ENDTABS]


以下信息特定于Campaign Classic。

+++ **包安装**

![](assets/do-not-localize/how-to-video.png) [在视频中了解如何安装移动应用包](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=zh-Hans#sending-messages)

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

完成此步骤后，您可以配置Android和iOS应用程序。 请参阅Campaign v8 [文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hans){target="_blank"}。

+++

+++ **故障排除**

如果移动设备已连接到Wi-Fi并且未收到通知，请检查防火墙是否未阻止FCM/APNs端口。

**Android**：移动设备连接到端口5228到5230上的FCM服务器。 因此，必须配置防火墙以授权与FCM的连接。 要打开的端口为：5228（最常用）、5229和5230。

**iOS**：

HTTP/2连接器：必须允许与以下服务器之间的通信：

* api.push.apple.com：端口443
* api.development.push.apple.com：端口443

>[!NOTE]
>
>有关这两个连接器的更多信息，请参阅Campaign v8 [文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hans){target="_blank"}。

+++
