---
product: campaign
title: 为iOS设备创建推送通知
description: 了解如何为iOS创建推送通知
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 615b56c5f4362b0f47ec5700be7d170c0e108f4c
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 3%

---

# 创建iOS{#create-notifications-ios}通知

本节详细介绍iOS通知交付的特定元素。 有关投放创建的全局概念，请参见[此部分](../../delivery/using/steps-about-delivery-creation-steps.md)。

首先创建新投放。

![](assets/nmac_delivery_1.png)

要为iOS设备创建推送通知，请执行以下步骤：

1. 选择&#x200B;**[!UICONTROL Deliver on iOS]**&#x200B;投放模板。

   ![](assets/nmac_delivery_ios_1.png)

1. 要定义通知的目标，请单击&#x200B;**[!UICONTROL To]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Add]**。

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >选择投放的目标群体时的详细过程，请参见[此部分](steps-defining-the-target-population.md)。
   >
   >有关个性化字段使用的更多信息，请参阅[此部分](about-personalization.md)。
   >
   >有关包含种子列表的更多信息，请参阅[关于种子地址](../../delivery/using/about-seed-addresses.md)。

1. 选择&#x200B;**[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**，选择与移动应用程序相关的服务（在本例中为Neotrips），然后选择应用程序的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 选择通知类型：**[!UICONTROL Alert]**、**[!UICONTROL Badge]**&#x200B;或&#x200B;**[!UICONTROL Alert and badge]**&#x200B;或&#x200B;**[!UICONTROL Silent Push]**。

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >**静默推送**&#x200B;模式允许向移动应用程序发送“静默”通知。 用户未知晓通知的到达。 它将直接转给应用程序。

1. 在&#x200B;**[!UICONTROL Title]**&#x200B;字段中，输入要在通知中显示的标题标签。 它将仅显示在通知中心提供的通知列表中。 利用此字段，可定义iOS通知有效负载的&#x200B;**title**&#x200B;参数的值。

1. 如果使用HTTP/2连接器，则可以添加子标题（iOS通知有效负载的&#x200B;**subtitle**&#x200B;参数的值）。 请参阅[此部分](configuring-the-mobile-application.md)。

1. 然后，根据所选通知类型输入&#x200B;**[!UICONTROL Message]**&#x200B;和&#x200B;**[!UICONTROL Value of the badge]**。

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** 和 **[!UICONTROL Alert and badge]** 类型通知允许您修改徽章的值（移动应用程序徽标上方的数字）。要刷新标记，您只需输入0作为值。 如果字段为空，则标记值不会更改。

1. 单击&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;图标以将表情符号插入推送通知。 要自定义表情符号列表，请参阅[此部分](../../delivery/using/customizing-emoticon-list.md)

1. **[!UICONTROL Action button]**&#x200B;允许您为出现在警报通知（有效负载的&#x200B;**action_loc_key**&#x200B;字段）中的操作按钮定义标签。 如果您的iOS应用程序管理可本地化的字符串(**Localizable.strings**)，请在此字段中输入相应的键。 如果您的应用程序不管理可本地化的文本，请输入要在操作按钮上显示的标签。 有关可本地化字符串的更多信息，请参阅[Apple文档](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) 。
1. 在&#x200B;**[!UICONTROL Play a sound]**&#x200B;字段中，选择要在收到通知时由移动终端播放的声音。

   >[!NOTE]
   >
   >必须在应用程序中包含声音，并在创建服务时定义声音。 请参阅[此小节](configuring-the-mobile-application.md#configuring-external-account-ios)。

1. 在&#x200B;**[!UICONTROL Application variables]**&#x200B;字段中，输入每个变量的值。 应用程序变量允许您定义通知行为：例如，您可以配置在用户激活通知时显示的特定应用程序屏幕。

   >[!NOTE]
   >
   >应用程序变量必须在移动应用程序的代码中定义，并在服务创建期间输入。 如需详细信息，请参阅[此部分](configuring-the-mobile-application.md)。

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
* [监测投放](../../delivery/using/about-delivery-monitoring.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)


## 创建iOS富通知{#creating-ios-delivery}

在iOS 10或更高版本中，可以生成富通知。 Adobe Campaign可以使用允许设备显示丰富通知的变量发送通知。

现在，您需要创建新投放并将其链接到您创建的移动应用程序。

1. 转到&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 单击 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Deliver on iOS (ios)]**。 向投放中添加&#x200B;**[!UICONTROL Label]**。

1. 单击&#x200B;**[!UICONTROL To]**&#x200B;以定义要定位的群体。 默认情况下，将应用&#x200B;**[!UICONTROL Subscriber application]**&#x200B;目标映射。 单击&#x200B;**[!UICONTROL Add]**&#x200B;以选择我们之前创建的服务。

   ![](assets/nmac_ios_9.png)

1. 在&#x200B;**[!UICONTROL Target type]**&#x200B;窗口中，选择&#x200B;**[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**。

1. 在&#x200B;**[!UICONTROL Service]**&#x200B;下拉列表中，选择您之前创建的服务，然后选择要定位的应用程序，然后单击&#x200B;**[!UICONTROL Finish]**。
根据配置步骤中添加的内容，会自动添加**[!UICONTROL Application variables]**。

   ![](assets/nmac_ios_6.png)

1. 编辑您的富通知。

   ![](assets/nmac_ios_7.png)

1. 选中编辑通知窗口中的&#x200B;**[!UICONTROL Mutable content]**&#x200B;框，以允许移动应用程序下载媒体内容。

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;并发送投放。

当在订阅者的移动iOS设备上收到图像和网页时，应在推送通知中显示。

![](assets/nmac_ios_8.png)
