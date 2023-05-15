---
product: campaign
title: 为iOS设备创建推送通知
description: 了解如何为iOS创建推送通知
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 4520504a-0d9f-4ea7-a5a8-0c07948af4f0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 6%

---

# 创建iOS通知{#create-notifications-ios}



本节详细介绍特定于iOS通知交付的元素。 有关投放创建的全局概念，请参阅 [此部分](steps-about-delivery-creation-steps.md).

首先创建新投放。

![](assets/nmac_delivery_1.png)

要为iOS设备创建推送通知，请执行以下步骤：

1. 选择 **[!UICONTROL Deliver on iOS]** 投放模板。

   ![](assets/nmac_delivery_ios_1.png)

1. 要定义通知的目标，请单击 **[!UICONTROL To]** 链接，然后单击 **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >选择投放的目标群体时的详细过程，请参见 [此部分](steps-defining-the-target-population.md).
   >
   >有关使用个性化字段的更多信息，请参阅 [此部分](about-personalization.md).
   >
   >欲知关于种子清单的详情，请参阅 [关于种子地址](about-seed-addresses.md).

1. 选择 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**，选择与移动应用程序相关的服务（在本例中为Neotrips），然后选择应用程序的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 选择 **[!UICONTROL Notification type]** 介于 **[!UICONTROL General notification (Alert, Sound, Badge)]** 或 **[!UICONTROL Silent notification]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >的 **静默推送** 模式允许向移动应用程序发送“静默”通知。 用户未知晓通知的到达。 它将直接转给应用程序。

1. 在 **[!UICONTROL Title]** 字段，输入要在通知中心提供的通知列表中显示的标题标签。

   利用此字段，可定义 **标题** iOS通知有效负载的参数。

1. 您可以添加 **[!UICONTROL Subtitle]**,iOS通知有效负载的子标题参数的值。 请参阅 [此部分](configuring-the-mobile-application.md).

1. 在 **[!UICONTROL Message content]** 的子菜单。 个性化字段的使用情况请参见 [关于个性化](about-personalization.md) 中。

   ![](assets/nmac_delivery_ios_5.png)

1. 单击 **[!UICONTROL Insert emoticon]** 图标将表情符号插入推送通知。 要自定义表情符号列表，请参阅 [此部分](customizing-emoticon-list.md)

1. 从 **[!UICONTROL Sound and Badge]** 选项卡，您可以编辑以下选项：

   * **[!UICONTROL Clean Badge]**:启用此选项可刷新标记值。

   * **[!UICONTROL Value]**:设置一个数字，该数字将用于直接在应用程序图标上显示新的未读信息数。

   * **[!UICONTROL Critical alert mode]**:启用此选项，即使用户的手机设置为焦点模式或iPhone静音，也可向通知添加声音。

   * **[!UICONTROL Name]**:选择在收到通知时移动终端要播放的声音。

   * **[!UICONTROL Volume]**:音量从0到100。
   >[!NOTE]
   >
   >必须在应用程序中包含声音，并在创建服务时定义声音。 请参阅[此小节](configuring-the-mobile-application.md#configuring-external-account-ios)。

   ![](assets/nmac_delivery_ios_6.png)

1. 从 **[!UICONTROL Application variables]** 选项卡， **[!UICONTROL Application variables]** 会自动添加。 例如，通过它们可定义通知行为，您可以将特定应用程序屏幕配置为在用户激活通知时显示。

   如需详细信息，请参阅[此部分](configuring-the-mobile-application.md)。

1. 从 **[!UICONTROL Advanced]** 选项卡，您可以编辑以下常规选项：

   * **[!UICONTROL Mutable content]**:启用此选项，以允许移动应用程序下载媒体内容。

   * **[!UICONTROL Thread-id]**:用于将相关通知分组在一起的标识符。

   * **[!UICONTROL Category]**:将显示操作按钮的类别ID的名称。 这些通知为用户提供了一种更快的方式，无需在应用程序中打开或导航即可响应通知执行不同任务。

   ![](assets/nmac_delivery_ios_7.png)

1. 对于时间敏感通知，您可以指定以下选项：

   * **[!UICONTROL Target content ID]**:标识符，用于定位在打开通知时要转发的应用程序窗口。

   * **[!UICONTROL Launch image]**:要显示的launch图像文件的名称。 如果用户选择启动您的应用程序，则将显示选定的图像，而不是应用程序的启动屏幕。

   * **[!UICONTROL Interruption level]**:

      * **[!UICONTROL Active]**:默认情况下，系统会立即显示通知、点亮屏幕并播放声音。 通知不会突破“焦点”模式。

      * **[!UICONTROL Passive]**:系统将通知添加到通知列表，而不会点亮屏幕或播放声音。 通知不会突破“焦点”模式。

      * **[!UICONTROL Time sensitive]**:系统会立即显示通知、点亮屏幕、播放声音并打破“聚焦”模式。 此级别不需要Apple的特殊许可。

      * **[!UICONTROL Critical]**:系统立即显示通知，将屏幕点亮，并绕过静音开关或聚焦模式。 请注意，此级别需要获得Apple的特殊许可。
   * **[!UICONTROL Relevance score]**:将相关性得分设置为0到100。 系统将使用它对通知摘要中的通知进行排序。

   ![](assets/nmac_delivery_ios_8.png)

1. 配置通知后，单击 **[!UICONTROL Preview]** 选项卡来预览通知。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >未在Adobe Campaign中定义通知样式（横幅或警报）。 这取决于用户在其iOS设置中选择的配置。 但是，Adobe Campaign允许您预览每种类型的通知样式。 单击右下方的箭头，从一种样式切换到另一种样式。
   >
   >预览使用iOS 10的外观。

要发送校样并发送最终投放，请使用与电子邮件投放相同的流程。 [了解详情](steps-validating-the-delivery.md)

发送消息后，您可以监控和跟踪投放内容。 有关更多信息，请参阅一下章节。

* [推送通知隔离](understanding-quarantine-management.md#push-notification-quarantines)
* [监测投放](about-delivery-monitoring.md)
* [了解投放失败](understanding-delivery-failures.md)

## 创建iOS富通知 {#creating-ios-delivery}

使用iOS 10或更高版本，可以生成富通知。 Adobe Campaign可以使用允许设备显示丰富通知的变量发送通知。

现在，您需要创建新投放并将其链接到您创建的移动应用程序。

1. 转到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 单击 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 选择 **[!UICONTROL Deliver on iOS (ios)]** 在 **[!UICONTROL Delivery template]** 下拉菜单。 添加 **[!UICONTROL Label]** 投放。

1. 单击 **[!UICONTROL To]** 定义要定位的群体。 默认情况下， **[!UICONTROL Subscriber application]** 目标映射。 单击 **[!UICONTROL Add]** 来选择我们之前创建的服务。

   ![](assets/nmac_ios_9.png)

1. 在 **[!UICONTROL Target type]** 窗口，选择 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** 单击 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 下拉列表，选择您之前创建的服务，然后选择要定位的应用程序并单击 **[!UICONTROL Finish]**.

   ![](assets/nmac_ios_6.png)

1. 编辑您的富通知。

   ![](assets/nmac_ios_7.png)

1. 从 **[!UICONTROL Application variables]** 选项卡， **[!UICONTROL Application variables]** 将根据在配置步骤中添加的内容自动添加。

   >[!NOTE]
   >
   >应用程序变量必须在移动应用程序的代码中定义，并在服务创建期间输入。 如需详细信息，请参阅[此部分](configuring-the-mobile-application.md)。

   ![](assets/nmac_ios_10.png)

1. 从 **[!UICONTROL Advanced]** 选项卡，勾选 **[!UICONTROL Mutable content]** 框，以便移动应用程序下载媒体内容。

1. 单击 **[!UICONTROL Save]** 并发送投放内容。

当在订阅者的移动iOS设备上收到图像和网页时，应在推送通知中显示。

![](assets/nmac_ios_8.png)




