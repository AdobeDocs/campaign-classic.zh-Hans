---
solution: Campaign Classic
product: campaign
title: 创建推送通知
description: 了解如何创建推送通知
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 4%

---


# 创建通知{#creating-notifications}

本节详细介绍特定于iOS和Android通知投放的元素。 [本节](../../delivery/using/steps-about-delivery-creation-steps.md)介绍了有关创建投放的全局概念。

开始。

![](assets/nmac_delivery_1.png)

## 在iOS {#sending-notifications-on-ios}上发送通知

1. 选择&#x200B;**[!UICONTROL Deliver on iOS]**&#x200B;投放模板。

   ![](assets/nmac_delivery_ios_1.png)

1. 要定义通知的目标，请单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >在[本节](../../delivery/using/steps-defining-the-target-population.md)中显示了选择投放的目标种群的详细过程。
   >
   >有关使用个性化字段的详细信息，请参阅[关于个性化](../../delivery/using/about-personalization.md)。
   >
   >有关包含种子列表的详细信息，请参阅[关于种子地址](../../delivery/using/about-seed-addresses.md)。

1. 选择&#x200B;**[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**，选择与您的移动应用程序相关的服务（本例中为Neotrips），然后选择应用程序的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 选择通知类型：**[!UICONTROL Alert]**、**[!UICONTROL Badge]**&#x200B;或&#x200B;**[!UICONTROL Alert and badge]**&#x200B;或&#x200B;**[!UICONTROL Silent Push]**。

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >从iOS 7中可以使用&#x200B;**无提示推送**&#x200B;模式。 这允许向移动应用程序发送“静默”通知。 用户未知道通知的到达。 它会直接转让给应用程序。

1. 在&#x200B;**[!UICONTROL Title]**&#x200B;字段中，输入要在通知中显示的标题标签。 它将仅显示在通知中心提供的通知列表中。 此字段允许您定义iOS通知有效负荷的&#x200B;**title**&#x200B;参数的值。

1. 如果您使用HTTP/2连接器，则可以添加子标题（iOS通知有效负荷的&#x200B;**subtitle**&#x200B;参数的值）。 请参阅[在Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md)中配置移动应用程序部分。

1. 然后根据所选通知类型输入&#x200B;**[!UICONTROL Message]**&#x200B;和&#x200B;**[!UICONTROL Value of the badge]**。

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** 键 **[!UICONTROL Alert and badge]** 入通知后，您可以修改徽章的值（移动应用程序徽标上方的数字）。要刷新此徽章，您只需输入0作为值。 如果字段为空，则徽章值不会更改。

1. 单击&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;图标将表情图标插入推送通知。 要自定义表情列表，请参阅自定义表情列表](../../delivery/using/customizing-emoticon-list.md)[

1. **[!UICONTROL Action button]**&#x200B;允许您为警报通知（负荷的&#x200B;**action_loc_key**&#x200B;字段）上显示的操作按钮定义标签。 如果您的iOS应用程序管理可本地化的字符串(**Localizable.strings**)，请在此字段中输入相应的键。 如果应用程序不管理可本地化的文本，请输入要在操作按钮上显示的标签。 有关可本地化的字符串的详细信息，请参阅[Apple文档](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1)。
1. 在&#x200B;**[!UICONTROL Play a sound]**&#x200B;字段中，选择接收通知时由移动终端播放的声音。

   >[!NOTE]
   >
   >声音必须包含在应用程序中，并在创建服务时进行定义。 请参阅[配置iOS外部帐户](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios)。

1. 在&#x200B;**[!UICONTROL Application variables]**&#x200B;字段中，输入每个变量的值。 应用程序变量允许您定义通知行为：例如，您可以配置在用户激活通知时显示的特定应用程序屏幕。

   >[!NOTE]
   >
   >应用程序变量必须在手机应用程序的代码中定义，并在创建服务时输入。 有关详细信息，请参阅：[在Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md)中配置移动应用程序。

1. 配置通知后，单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以预览通知。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >通知样式（横幅或警报）未在Adobe Campaign中定义。 这取决于用户在其iOS设置中选择的配置。 但是，Adobe Campaign允许您预览每种类型的通知样式。 单击右下角的箭头，从一种样式切换到另一种样式。
   >
   >预览使用iOS 10的外观。

要发送验证并发送最终投放，请使用与电子邮件投放相同的流程。

发送消息后，您可以监视和跟踪投放。 有关更多信息，请参阅一下章节。

* [推送通知隔离](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [监控投放](../../delivery/using/about-delivery-monitoring.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)

## 在Android {#sending-notifications-on-android}上发送通知

1. 开始，选择&#x200B;**[!UICONTROL Deliver on Android (android)]**&#x200B;投放模板。

   ![](assets/nmac_delivery_android_1.png)

1. 要定义通知的目标，请单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/nmac_delivery_android_2.png)

1. 选择&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**，选择与您的移动应用程序相关的服务（本例中为Neotrips），然后选择应用程序的Android版本。

   ![](assets/nmac_delivery_android_3.png)

1. 然后输入通知的内容。

   ![](assets/nmac_delivery_android_4.png)

1. 单击&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;图标将表情图标插入推送通知。 要自定义表情列表，请参阅自定义表情列表](../../delivery/using/defining-interactive-content.md)[

1. 在&#x200B;**[!UICONTROL Application variables]**&#x200B;字段中，输入每个变量的值。 应用程序变量允许您定义通知行为：例如，您可以配置在用户激活通知时显示的特定应用程序屏幕。

   >[!NOTE]
   >
   >应用程序变量必须在手机应用程序的代码中定义，并在创建服务时输入。 有关详细信息，请参阅：[在Adobe Campaign](../../delivery/using/configuring-the-mobile-application.md)中配置移动应用程序。

1. 配置通知后，单击&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡以预览通知。

   ![](assets/nmac_intro_1.png)

要发送验证并发送最终投放，请使用与电子邮件投放相同的流程。

验证和发送投放时的详细过程将在以下各节中介绍：

* [验证投放](../../delivery/using/steps-validating-the-delivery.md)
* [发送投放](../../delivery/using/steps-sending-the-delivery.md)

发送消息后，您可以监视和跟踪投放。 有关更多信息，请参阅一下章节。

* [推送通知隔离](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [监控投放](../../delivery/using/about-delivery-monitoring.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
