---
product: campaign
title: 跨渠道投放
description: 了解关于跨渠道投放的更多信息
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 7%

---

# 跨渠道投放{#cross-channel-deliveries}



可在营销活动工作流活动的&#x200B;**[!UICONTROL Deliveries]**&#x200B;选项卡中使用跨渠道投放。

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
1. 在营销活动的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中，向工作流添加&#x200B;**[!UICONTROL Query]**。
1. 配置查询。 例如，在本例中，我们选择订阅了推送通知的收件人作为目标维度。

   >[!NOTE]
   >
   >对于推送通知，请使用&#x200B;**订阅者应用程序**&#x200B;目标维度。

   ![](assets/cross_channel_delivery_1.png)

1. 将筛选条件添加到查询。 在这种情况下，我们将选择具有手机号码或电子邮件地址的收件人。

   ![](assets/cross_channel_delivery_2.png)

1. 将&#x200B;**[!UICONTROL Split]**&#x200B;活动添加到您的工作流中，以划分具有手机号码的收件人和具有电子邮件地址的收件人。
1. 在&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡中，为每个目标选择一个投放。

   通过双击工作流中的投放活动，以与使用经典投放助手相同的方式创建投放。 有关详细信息，请参见此 [ 页面](../../delivery/using/about-email-channel.md)。

   ![](assets/cross_channel_delivery_3.png)

1. 添加并配置&#x200B;**[!UICONTROL Wait]**&#x200B;活动，以便收件人不会一次收到太多投放。
1. 添加&#x200B;**[!UICONTROL Split]**&#x200B;活动以划分iOS或Android移动应用程序的订阅者。

   为每个操作系统选择服务。 有关创建服务的详细信息，请参阅此[页面](../../delivery/using/configuring-the-mobile-application.md)。

   ![](assets/cross_channel_delivery_4.png)

1. 选择并配置每个操作系统的移动应用程序投放。

   ![](assets/cross_channel_delivery_5.png)
