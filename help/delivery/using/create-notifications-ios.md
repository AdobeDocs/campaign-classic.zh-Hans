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

# 为iOS创建通知{#create-notifications-ios}



此部分详细介绍特定于iOS通知投放的元素。 有关投放创建的全局概念，请参阅 [本节](steps-about-delivery-creation-steps.md).

首先创建新投放。

![](assets/nmac_delivery_1.png)

要为iOS设备创建推送通知，请执行以下步骤：

1. 选择 **[!UICONTROL Deliver on iOS]** 投放模板。

   ![](assets/nmac_delivery_ios_1.png)

1. 要定义通知的目标，请单击 **[!UICONTROL To]** 链接，然后单击 **[!UICONTROL Add]**.

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >有关选择投放目标群体的详细过程，请参见 [本节](steps-defining-the-target-population.md).
   >
   >有关个性化字段使用的更多信息，请参阅 [本节](about-personalization.md).
   >
   >有关包含种子列表的详细信息，请参阅 [关于种子地址](about-seed-addresses.md).

1. 选择 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**，选择与您的移动应用程序相关的服务（在本例中为Neotrips），然后选择应用程序的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 选择您的 **[!UICONTROL Notification type]** 介于 **[!UICONTROL General notification (Alert, Sound, Badge)]** 或 **[!UICONTROL Silent notification]**.

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >此 **静默推送** 模式允许向移动应用程序发送“静默”通知。 用户未意识到通知的到达。 它将直接传输到应用程序。

1. 在 **[!UICONTROL Title]** 字段中，输入要显示在通知中心可用通知列表中的标题标签。

   此字段允许您定义 **标题** iOS通知有效负载的参数。

1. 您可以添加 **[!UICONTROL Subtitle]**，iOS通知有效负载的字幕参数的值。 请参阅 [本节](configuring-the-mobile-application.md).

1. 在中输入消息的内容 **[!UICONTROL Message content]** 部分。 有关个性化字段的使用，请参见 [关于个性化](about-personalization.md) 部分。

   ![](assets/nmac_delivery_ios_5.png)

1. 单击 **[!UICONTROL Insert emoticon]** 图标，以将表情符号插入到您的推送通知中。 要自定义表情符号列表，请参阅 [本节](customizing-emoticon-list.md)

1. 从 **[!UICONTROL Sound and Badge]** 选项卡，可以编辑以下选项：

   * **[!UICONTROL Clean Badge]**：启用此选项以刷新标记值。

   * **[!UICONTROL Value]**：设置一个数字，该数字将用于直接在应用程序图标上显示新未读信息的数量。

   * **[!UICONTROL Critical alert mode]**：启用此选项，以便即使用户的手机设置为焦点模式或iPhone处于静音状态，也可以向通知中添加声音。

   * **[!UICONTROL Name]**：在收到通知时，选择移动终端要播放的声音。

   * **[!UICONTROL Volume]**：音量从0到100。
   >[!NOTE]
   >
   >声音必须包含在应用程序中，并在创建服务时定义。 请参阅[此小节](configuring-the-mobile-application.md#configuring-external-account-ios)。

   ![](assets/nmac_delivery_ios_6.png)

1. 从 **[!UICONTROL Application variables]** 选项卡，您的 **[!UICONTROL Application variables]** 都会自动添加。 它们允许您定义通知行为，例如，您可以配置在用户激活通知时显示的特定应用程序屏幕。

   如需详细信息，请参阅[此部分](configuring-the-mobile-application.md)。

1. 从 **[!UICONTROL Advanced]** 选项卡，可以编辑以下常规选项：

   * **[!UICONTROL Mutable content]**：启用此选项可允许移动应用程序下载媒体内容。

   * **[!UICONTROL Thread-id]**：用于将相关通知分组在一起的标识符。

   * **[!UICONTROL Category]**：将显示操作按钮的类别ID的名称。 这些通知为用户提供了一种更快的方式，无需在应用程序中打开或导航即可响应通知执行不同任务。

   ![](assets/nmac_delivery_ios_7.png)

1. 对于时效性通知，您可以指定以下选项：

   * **[!UICONTROL Target content ID]**：用于在打开通知时定位要前转的应用程序窗口的标识符。

   * **[!UICONTROL Launch image]**：要显示的启动图像文件的名称。 如果用户选择启动应用程序，将显示选定的图像而不是应用程序的启动屏幕。

   * **[!UICONTROL Interruption level]**：

      * **[!UICONTROL Active]**：默认情况下，系统会立即显示通知，打开屏幕并播放声音。 通知不会突破焦点模式。

      * **[!UICONTROL Passive]**：系统会将通知添加到通知列表，而不会打开屏幕或播放声音。 通知不会突破焦点模式。

      * **[!UICONTROL Time sensitive]**：系统立即显示通知，打开屏幕，可以播放声音并突破聚焦模式。 此级别不需要Apple的特殊权限。

      * **[!UICONTROL Critical]**：系统立即显示通知，在屏幕上亮起，并绕过静音开关或聚焦模式。 请注意，此级别需要Apple的特殊权限。
   * **[!UICONTROL Relevance score]**：将相关性得分从0设置为100。 系统使用此选项对通知摘要中的通知进行排序。

   ![](assets/nmac_delivery_ios_8.png)

1. 配置通知后，单击 **[!UICONTROL Preview]** 选项卡以预览通知。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >Adobe Campaign中未定义通知样式（横幅或警报）。 这取决于用户在其iOS设置中选择的配置。 但是，Adobe Campaign允许您预览每种类型的通知样式。 单击右下方的箭头可从一个样式切换到另一个样式。
   >
   >预览使用iOS 10外观。

要发送证明并发送最终投放，请使用与电子邮件投放相同的流程。 [了解详情](steps-validating-the-delivery.md)

发送消息后，您可以监控和跟踪投放。 有关更多信息，请参阅一下章节。

* [推送通知隔离](understanding-quarantine-management.md#push-notification-quarantines)
* [监测投放](about-delivery-monitoring.md)
* [了解投放失败](understanding-delivery-failures.md)

## 创建iOS富通知 {#creating-ios-delivery}

使用iOS 10或更高版本，可以生成丰富的通知。 Adobe Campaign可以使用允许设备显示丰富通知的变量发送通知。

现在，您需要创建一个新投放并将其链接到您创建的移动应用程序。

1. 转到 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 单击 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 选择 **[!UICONTROL Deliver on iOS (ios)]** 在 **[!UICONTROL Delivery template]** 下拉菜单。 添加 **[!UICONTROL Label]** 到您的投放。

1. 单击 **[!UICONTROL To]** 以定义要定位的群体。 默认情况下， **[!UICONTROL Subscriber application]** 已应用目标映射。 单击 **[!UICONTROL Add]** 以选择我们之前创建的服务。

   ![](assets/nmac_ios_9.png)

1. 在 **[!UICONTROL Target type]** 窗口，选择 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** 并单击 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 从下拉列表中，选择您之前创建的服务，然后选择要定位的应用程序，然后单击 **[!UICONTROL Finish]**.

   ![](assets/nmac_ios_6.png)

1. 编辑富通知。

   ![](assets/nmac_ios_7.png)

1. 从 **[!UICONTROL Application variables]** 选项卡，您的 **[!UICONTROL Application variables]** 根据在配置步骤中添加的内容，自动添加。

   >[!NOTE]
   >
   >应用程序变量必须在移动应用程序的代码中定义，并在服务创建期间输入。 如需详细信息，请参阅[此部分](configuring-the-mobile-application.md)。

   ![](assets/nmac_ios_10.png)

1. 从 **[!UICONTROL Advanced]** 选项卡，检查 **[!UICONTROL Mutable content]** 框，以允许移动设备应用程序下载媒体内容。

1. 单击 **[!UICONTROL Save]** 并发送您的投放。

在订阅者的iOS移动设备上接收推送通知时，图像和网页应显示在推送通知中。

![](assets/nmac_ios_8.png)




