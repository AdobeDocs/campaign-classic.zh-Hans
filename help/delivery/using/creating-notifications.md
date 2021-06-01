---
product: campaign
title: 创建推送通知
description: 了解如何创建推送通知
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 4%

---

# 创建通知{#creating-notifications}

本节详细介绍特定于iOS和Android通知交付的元素。 有关投放创建的全局概念，请参见[此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

首先创建新投放。

![](assets/nmac_delivery_1.png)

## 在iOS {#sending-notifications-on-ios}上发送通知

1. 选择&#x200B;**[!UICONTROL Deliver on iOS]**&#x200B;投放模板。

   ![](assets/nmac_delivery_ios_1.png)

1. 要定义通知的目标，请单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >选择投放的目标群体时的详细过程，请参见[此部分](../../delivery/using/steps-defining-the-target-population.md)。
   >
   >有关个性化字段使用的更多信息，请参阅[关于个性化](../../delivery/using/about-personalization.md)。
   >
   >有关包含种子列表的更多信息，请参阅[关于种子地址](../../delivery/using/about-seed-addresses.md)。

1. 选择&#x200B;**[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**，选择与移动应用程序相关的服务（在本例中为Neotrips），然后选择应用程序的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 选择通知类型：**[!UICONTROL Alert]**、**[!UICONTROL Badge]**&#x200B;或&#x200B;**[!UICONTROL Alert and badge]**&#x200B;或&#x200B;**[!UICONTROL Silent Push]**。

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >在iOS 7中，提供了&#x200B;**静默推送**&#x200B;模式。 这允许向移动应用程序发送“静默”通知。 用户未知晓通知的到达。 它将直接转给应用程序。

1. 在&#x200B;**[!UICONTROL Title]**&#x200B;字段中，输入要在通知中显示的标题标签。 它将仅显示在通知中心提供的通知列表中。 利用此字段，可定义iOS通知有效负载的&#x200B;**title**&#x200B;参数的值。

1. 如果使用HTTP/2连接器，则可以添加子标题（iOS通知有效负载的&#x200B;**subtitle**&#x200B;参数的值）。 请参阅[在Adobe Campaign中配置移动应用程序](../../delivery/using/configuring-the-mobile-application.md)一节。

1. 然后，根据所选通知类型输入&#x200B;**[!UICONTROL Message]**&#x200B;和&#x200B;**[!UICONTROL Value of the badge]**。

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** 和 **[!UICONTROL Alert and badge]** 类型通知允许您修改徽章的值（移动应用程序徽标上方的数字）。要刷新标记，您只需输入0作为值。 如果字段为空，则标记值不会更改。

1. 单击&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;图标以将表情符号插入推送通知。 要自定义表情符号列表，请参阅[自定义表情符号列表](../../delivery/using/customizing-emoticon-list.md)

1. **[!UICONTROL Action button]**&#x200B;允许您为出现在警报通知（有效负载的&#x200B;**action_loc_key**&#x200B;字段）中的操作按钮定义标签。 如果您的iOS应用程序管理可本地化的字符串(**Localizable.strings**)，请在此字段中输入相应的键。 如果您的应用程序不管理可本地化的文本，请输入要在操作按钮上显示的标签。 有关可本地化字符串的更多信息，请参阅[Apple文档](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) 。
1. 在&#x200B;**[!UICONTROL Play a sound]**&#x200B;字段中，选择要在收到通知时由移动终端播放的声音。

   >[!NOTE]
   >
   >必须在应用程序中包含声音，并在创建服务时定义声音。 请参阅[配置iOS外部帐户](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios)。

1. 在&#x200B;**[!UICONTROL Application variables]**&#x200B;字段中，输入每个变量的值。 应用程序变量允许您定义通知行为：例如，您可以配置在用户激活通知时显示的特定应用程序屏幕。

   >[!NOTE]
   >
   >应用程序变量必须在移动应用程序的代码中定义，并在服务创建期间输入。 有关更多信息，请参阅：[在Adobe Campaign中配置移动应用程序](../../delivery/using/configuring-the-mobile-application.md)。

1. 配置通知后，单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以预览通知。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >未在Adobe Campaign中定义通知样式（横幅或警报）。 这取决于用户在其iOS设置中选择的配置。 但是，Adobe Campaign允许您预览每种类型的通知样式。 单击右下方的箭头，从一种样式切换到另一种样式。
   >
   >预览使用iOS 10的外观。

要发送校样并发送最终投放，请使用与电子邮件投放相同的流程。

发送消息后，您可以监控和跟踪投放内容。 有关更多信息，请参阅一下章节。

* [推送通知隔离](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [监控投放](../../delivery/using/about-delivery-monitoring.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)

## 在Android {#sending-notifications-on-android}上发送通知

1. 首先选择&#x200B;**[!UICONTROL Deliver on Android (android)]**&#x200B;投放模板。

   ![](assets/nmac_delivery_android_1.png)

1. 要定义通知的目标，请单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/nmac_delivery_android_2.png)

1. 选择&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**，选择与移动应用程序相关的服务（在本例中为Neotrips），然后选择应用程序的Android版本。

   ![](assets/nmac_delivery_android_3.png)

1. 然后输入通知的内容。

   ![](assets/nmac_delivery_android_4.png)

1. 单击&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;图标以将表情符号插入推送通知。 要自定义表情符号列表，请参阅[自定义表情符号列表](../../delivery/using/defining-interactive-content.md)

1. 在&#x200B;**[!UICONTROL Application variables]**&#x200B;字段中，输入每个变量的值。 应用程序变量允许您定义通知行为：例如，您可以配置在用户激活通知时显示的特定应用程序屏幕。

   >[!NOTE]
   >
   >应用程序变量必须在移动应用程序的代码中定义，并在服务创建期间输入。 有关更多信息，请参阅：[在Adobe Campaign中配置移动应用程序](../../delivery/using/configuring-the-mobile-application.md)。

1. 配置通知后，单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以预览通知。

   ![](assets/nmac_intro_1.png)

要发送校样并发送最终投放，请使用与电子邮件投放相同的流程。

有关验证和发送投放的详细过程，请参阅以下章节：

* [验证投放](../../delivery/using/steps-validating-the-delivery.md)
* [发送投放](../../delivery/using/steps-sending-the-delivery.md)

发送消息后，您可以监控和跟踪投放内容。 有关更多信息，请参阅一下章节。

* [推送通知隔离](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [监控投放](../../delivery/using/about-delivery-monitoring.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
