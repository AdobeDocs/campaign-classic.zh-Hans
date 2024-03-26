---
product: campaign
title: 跨渠道投放
description: 了解关于跨渠道投放的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 9%

---

# 跨渠道投放{#cross-channel-deliveries}



跨渠道投放可在 **[!UICONTROL Deliveries]** 活动工作流活动的选项卡。

可用的各种渠道包括：

* [电子邮件](../../delivery/using/about-email-channel.md)
* [直邮](../../delivery/using/about-direct-mail-channel.md)
* [移动](../../delivery/using/sms-channel.md)
* [X(以前称为Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

选择投放所基于的模板并定义其内容。

您可以使用不同的定向活动，在工作流上游指定投放目标。

在下面的示例中，我们将创建一个工作流，以向推送通知订阅者发送电子邮件或短信，然后在一周后发送推送通知。 操作步骤：

1. 创建营销策划。
1. 在 **[!UICONTROL Targeting and workflows]** 选项卡，添加 **[!UICONTROL Query]** 到您的工作流。
1. 配置查询。 例如，在本例中，我们选择订阅了推送通知的收件人作为目标维度。

   >[!NOTE]
   >
   >对于推送通知，请使用 **订阅者申请** 目标维度。

   ![](assets/cross_channel_delivery_1.png)

1. 将筛选条件添加到查询。 在这种情况下，我们将选择具有手机号码或电子邮件地址的收件人。

   ![](assets/cross_channel_delivery_2.png)

1. 添加 **[!UICONTROL Split]** 活动到您的工作流，以划分具有手机号码的收件人和具有电子邮件地址的收件人。
1. 在 **[!UICONTROL Delivery]** 选项卡，为每个目标选择一个投放。

   通过双击工作流中的投放活动，使用与使用经典投放向导相同的方式创建投放。 有关详细信息，请参见此 [ 页面](../../delivery/using/about-email-channel.md)。

   ![](assets/cross_channel_delivery_3.png)

1. 添加和配置 **[!UICONTROL Wait]** 活动，以便收件人不会一次收到太多投放。
1. 添加 **[!UICONTROL Split]** 此活动用于划分iOS或Android移动应用程序的订阅者。

   为每个操作系统选择服务。 有关创建服务的详细信息，请参阅此 [页面](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. 选择并配置每个操作系统的移动应用程序投放。

   ![](assets/cross_channel_delivery_5.png)
