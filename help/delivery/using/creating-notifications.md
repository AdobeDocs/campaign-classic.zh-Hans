---
title: 创建推送通知
description: 了解如何创建推送通知
page-status-flag: never-activated
uuid: fb1862df-e616-4147-a642-dc867bc983b5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 345af5c2-c852-4086-8ed0-ff3e7e402e04
translation-type: tm+mt
source-git-commit: fd75f7f75e8e77d7228233ea311dd922d100417c
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 4%

---


# 创建通知{#creating-notifications}

本节详细介绍iOS和Android通知投放特有的元素。 本节介绍有关投放创建的全 [局概念](../../delivery/using/steps-about-delivery-creation-steps.md)。

开始，创建新投放。

![](assets/nmac_delivery_1.png)

## 在iOS上发送通知 {#sending-notifications-on-ios}

1. 选择 **[!UICONTROL Deliver on iOS]** 投放模板。

   ![](assets/nmac_delivery_ios_1.png)

1. 要定义通知的目标，请单击 **[!UICONTROL To]** 链接，然后单击 **[!UICONTROL Add]**。

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >本节介绍了选择目标的投放种群时的详细 [过程](../../delivery/using/steps-defining-the-target-population.md)。
   >
   >有关个性化字段使用的详细信息，请参阅关 [于个性化](../../delivery/using/about-personalization.md)。
   >
   >有关包含种子列表的详细信息，请参 [阅关于种子地址](../../delivery/using/about-seed-addresses.md)。

1. 选 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**&#x200B;择与您的移动应用程序相关的服务（本例中为Neotrips），然后选择iOS版本的应用程序。

   ![](assets/nmac_delivery_ios_3.png)

1. 选择通知类型： **[!UICONTROL Alert]**、 **[!UICONTROL Badge]**&#x200B;或 **[!UICONTROL Alert and badge]** 或 **[!UICONTROL Silent Push]**。

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >iOS **7提供** “静默推送”模式。 这允许向移动应用程序发送“静默”通知。 用户未知道通知到达。 它会直接传输到应用程序。

1. 在字 **[!UICONTROL Title]** 段中，输入要在通知中显示的标题标签。 它将仅显示在通知中心提供的通知列表中。 此字段允许您定义iOS通知有 **效负荷** 的标题参数值。

1. 如果使用HTTP/2连接器，则可添加子标题(iOS通知有 **效负荷** 的子标题参数的值)。 请参阅在Adobe Campaign [中配置移动应用程序](../../delivery/using/configuring-the-mobile-application.md) 。

1. 然后，根据 **[!UICONTROL Message]** 所选 **[!UICONTROL Value of the badge]** 的通知类型输入和。

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** 键入 **[!UICONTROL Alert and badge]** 通知后，您可以修改徽章的值（移动应用程序徽标上方的数字）。 要刷新标记，您只需输入0作为值。 如果字段为空，则标记值不会更改。

1. 单击图 **[!UICONTROL Insert emoticon]** 标将表情图标插入推送通知。 要自定义表情图标列表，请参阅自 [定义表情图标列表](../../delivery/using/customizing-emoticon-list.md)

1. 该 **[!UICONTROL Action button]** 选项允许您为警报通知（有效负荷的action_loc_key字段）上显&#x200B;**示的操作按钮定义标签** 。 如果您的iOS应用程序管理可本地化的字&#x200B;**符串(Localizable.strings**)，请在此字段中输入相应的键。 如果应用程序不管理可本地化的文本，请输入要显示在操作按钮上的标签。 有关可本地化字符串的详细信息，请参 [阅Apple文档](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) 。
1. 在字 **[!UICONTROL Play a sound]** 段中，选择要在收到通知时由移动终端播放的声音。

   >[!NOTE]
   >
   >在创建服务时，音效必须包含在应用程序中并进行定义。 请参阅配 [置iOS外部帐户](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios)。

1. 在字 **[!UICONTROL Application variables]** 段中，输入每个变量的值。 应用程序变量允许您定义通知行为：例如，您可以配置在用户激活通知时显示的特定应用程序屏幕。

   >[!NOTE]
   >
   >应用程序变量必须在手机应用程序的代码中定义并在创建服务时输入。 有关此内容的详细信息，请参阅： [在Adobe Campaign中配置移动应用程序](../../delivery/using/configuring-the-mobile-application.md)。

1. 配置通知后，单击选 **[!UICONTROL Preview]** 项卡以预览通知。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >通知样式（横幅或警报）未在Adobe Campaign中定义。 这取决于用户在其iOS设置中选择的配置。 但是，Adobe Campaign允许您预览每种类型的通知样式。 单击右下角的箭头，从一个样式切换到另一个样式。
   >
   >预览使用iOS 10的外观。

要发送验证和发送最终投放，请使用与电子邮件投放相同的流程。

发送消息后，您可以监视和跟踪投放。 有关更多信息，请参阅一下章节。

* [推送通知隔离](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [监控投放](../../delivery/using/monitoring-a-delivery.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)

## 在Android上发送通知 {#sending-notifications-on-android}

1. 开始，方法是选择 **[!UICONTROL Deliver on Android (android)]** 投放模板。

   ![](assets/nmac_delivery_android_1.png)

1. 要定义通知的目标，请单击 **[!UICONTROL To]** 链接，然后单击 **[!UICONTROL Add]**。

   ![](assets/nmac_delivery_android_2.png)

1. 选 **[!UICONTROL Subscribers of an Android mobile application]**&#x200B;择与您的移动应用程序相关的服务（本例中为Neotrips），然后选择应用程序的Android版本。

   ![](assets/nmac_delivery_android_3.png)

1. 然后输入通知的内容。

   ![](assets/nmac_delivery_android_4.png)

1. 单击图 **[!UICONTROL Insert emoticon]** 标将表情图标插入推送通知。 要自定义表情图标列表，请参阅自 [定义表情图标列表](../../delivery/using/defining-interactive-content.md)

1. 在字 **[!UICONTROL Application variables]** 段中，输入每个变量的值。 应用程序变量允许您定义通知行为：例如，您可以配置在用户激活通知时显示的特定应用程序屏幕。

   >[!NOTE]
   >
   >应用程序变量必须在手机应用程序的代码中定义并在创建服务时输入。 有关此内容的详细信息，请参阅： [在Adobe Campaign中配置移动应用程序](../../delivery/using/configuring-the-mobile-application.md)。

1. 配置通知后，单击选 **[!UICONTROL Preview]** 项卡以预览通知。

   ![](assets/nmac_intro_1.png)

要发送验证和发送最终投放，请使用与电子邮件投放相同的流程。

验证和发送投放时的详细过程将在以下各节中介绍：

* [验证投放](../../delivery/using/steps-validating-the-delivery.md)
* [发送投放](../../delivery/using/steps-sending-the-delivery.md)

发送消息后，您可以监视和跟踪投放。 有关更多信息，请参阅一下章节。

* [推送通知隔离](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [监控投放](../../delivery/using/monitoring-a-delivery.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
