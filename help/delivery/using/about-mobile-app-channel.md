---
product: campaign
title: 移动应用程序渠道入门
description: 开始使用Adobe Campaign中的移动应用程序渠道
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
TQID: 'https://experienceleague.adobe.com/hNwtWC-TnFXsSv7CqqzKqr29sk67h2rwMBOTcBTToDs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: a4657621-810c-498b-8a27-7ced9c176dda
    internal-label: Push notifications
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d3cdead0-685a-4489-9250-4bb709942f66
    internal-label: Data collection
source-git-commit: 0fdce84d7da1ff42a406ace8f1a180f6a426646a
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 6%
---
# 移动应用程序渠道入门{#about-mobile-app-channel}

使用Adobe Campaign创建推送通知投放，以向您的移动应用程序用户发送个性化消息。

>[!NOTE]
>
>作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关推送通知渠道的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push){target=_blank}。
>
>[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/push/push){target="_blank"}

以下信息特定于Campaign Classic。

+++ **包安装**

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

完成此步骤后，您可以配置Android和iOS应用程序。 请参阅Campaign v8 [文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html){target="_blank"}。

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
>有关这两个连接器的更多信息，请参阅Campaign v8 [文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"}。

+++
