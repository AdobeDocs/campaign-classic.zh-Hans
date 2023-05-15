---
product: campaign
title: 跨渠道投放
description: 了解有关跨渠道投放的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 8%

---

# 跨渠道投放{#cross-channel-deliveries}



在 **[!UICONTROL Deliveries]** 营销活动工作流活动的选项卡。

可用的各种渠道包括：

* [电子邮件](../../delivery/using/about-email-channel.md)
* [直邮](../../delivery/using/about-direct-mail-channel.md)
* [手机](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

选择要作为投放基础的模板并定义其内容。

您可以使用不同的定位活动为工作流上游的投放指定定位。

在以下示例中，我们将创建一个工作流，在一周后为推送通知订阅者发送电子邮件或短信，然后发送推送通知。 操作步骤：

1. 创建营销策划.
1. 在 **[!UICONTROL Targeting and workflows]** 的 **[!UICONTROL Query]** 到您的工作流。
1. 配置查询。 例如，在此，我们选择订阅推送通知的收件人作为目标维度。

   >[!NOTE]
   >
   >对于推送通知，请使用 **订户应用程序** 目标维度。

   ![](assets/cross_channel_delivery_1.png)

1. 将筛选条件添加到查询。 在这种情况下，我们将选择具有手机号码或电子邮件地址的收件人。

   ![](assets/cross_channel_delivery_2.png)

1. 添加 **[!UICONTROL Split]** 活动，以划分具有移动号码的收件人和具有电子邮件地址的收件人。
1. 在 **[!UICONTROL Delivery]** 选项卡，为每个目标选择投放。

   通过双击工作流中的投放活动，以与经典投放向导相同的方式创建投放。 有关详细信息，请参见此 [ 页面](../../delivery/using/about-email-channel.md)。

   ![](assets/cross_channel_delivery_3.png)

1. 添加和配置 **[!UICONTROL Wait]** 活动，以便收件人一次不会收到过多投放。
1. 添加 **[!UICONTROL Split]** 活动来划分iOS或Android移动设备应用程序的订阅者。

   为每个操作系统选择一项服务。 有关服务创建的更多信息，请参阅此 [页面](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. 为每个操作系统选择和配置移动应用程序交付。

   ![](assets/cross_channel_delivery_5.png)
