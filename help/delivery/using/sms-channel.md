---
product: campaign
title: 短信渠道入门
description: 短信渠道入门
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# 短信渠道入门{#sms-channel}

使用Adobe Campaign向客户在其移动设备上发送短信。 您可以通过短信编辑器以文本格式创建、个性化和预览消息。

请参阅Campaign v8文档以了解与短信投放创建相关的关键步骤：

* [短信渠道概述](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hans){target="_blank"}：了解如何在移动设备上向客户发送短信。
* [创建短信投放](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/create-sms.html?lang=zh-Hans){target="_blank"}：探索创建新短信投放所需的不同步骤。
* [定义内容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-content.html?lang=zh-Hans){target="_blank"}：了解如何个性化短信消息的内容。
* [选择受众](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-audience.html?lang=zh-Hans){target="_blank"}：主目标是从Adobe Campaign数据库提取的，也可以存储在外部文件中。
* [发送短信校样](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs.html?lang=zh-Hans)：设置投放验证周期至关重要。 在将内容发送给受众之前，请确保内容已获批准。
* [发送给受众](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-send.html?lang=zh-Hans)：当您的短信通过验证时，您现在可以将其发送给受众。
* [监控和跟踪SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms-monitor.html?lang=zh-Hans)：监控SMS投放，以确保营销活动有效。

请参阅这些页面以了解有关配置的信息：

* [独立配置](sms-set-up.md)：了解如何在独立实例上配置短信渠道。
* [中间源配置](sms-set-up-mid.md)：了解如何通过中间服务器发送到手机。
* [SMS连接器](sms-protocol.md)：了解SMS连接器协议和设置。
* [其他配置](sms-send.md)：了解高级参数和其他其他配置。
* [疑难解答](troubleshooting-sms.md)：我们列出了一系列潜在问题及其解决方案。

<!--
Use Adobe Campaign to send personalized SMS messages.

Before starting sending SMS:

* Make sure recipient profiles contain at least a mobile phone in their profile.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).

The key steps to send a SMS are as follows:

* [Configure the SMS channel](sms-set-up.md)
* [Create a SMS delivery](sms-create.md)
* [Define the audience](sms-create.md#selecting-the-target-population)
* [Define the SMS content](sms-create.md#defining-the-sms-content)
* [Send, monitor and track SMS](sms-send.md)
* [Troubleshoot](troubleshooting-sms.md)

In addition, you need to be familiar with SMS protocol and settings. Walk through the connection set up between Adobe Campaign and a SMPP provider in [this document](sms-protocol.md)

For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Adobe Campaign also lets you submit notifications on mobile terminals, via its **Adobe Campaign Mobile App Channel (NMAC)** option. 
> 
>For more on this, refer to the [Get started with mobile app channel](about-mobile-app-channel.md) section.
-->