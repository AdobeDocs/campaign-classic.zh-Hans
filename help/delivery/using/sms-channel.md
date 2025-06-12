---
product: campaign
title: 短信渠道入门
description: 短信渠道入门
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
source-git-commit: d3d731c64cb5a430de6adac3aeb326f74134c436
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 短信渠道入门{#sms-channel}

使用Adobe Campaign向客户在其移动设备上发送短信。 您可以通过短信编辑器以文本格式创建、个性化和预览消息。

短信是一个直接、高效的渠道，无论用户身在何处，都可与他们联系。 凭借高打开率和近乎即时的投放方式，短信非常适合用于时效性强的警报、事务性更新和简明的促销消息。 使用短信补充您的跨渠道策略，提供有影响力的实时通信。 请参阅[Adobe Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hans){target=_blank}以了解如何有效配置和使用短信渠道。

作为Campaign v8促销活动的一部分，重组了Campaign Classic文档。 公共功能现在仅在Campaign v8文档集中可用。

>[!BEGINTABS]

>[!TAB 短信渠道文档]

要了解有关短信渠道的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hans){target=_blank}。


[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hans){target=_blank}


>[!TAB 短信投放创建]

请参阅Campaign v8文档以了解与短信投放创建相关的关键步骤：

* [短信渠道概述](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hans){target="_blank"}：了解如何在移动设备上向客户发送短信。
* [创建短信投放](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/create-sms.html?lang=zh-Hans){target="_blank"}：探索创建新短信投放所需的不同步骤。
* [定义内容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-content.html?lang=zh-Hans){target="_blank"}：了解如何个性化短信消息的内容。
* [选择受众](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-audience.html?lang=zh-Hans){target="_blank"}：主目标是从Adobe Campaign数据库提取的，也可以存储在外部文件中。
* [发送短信校样](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs.html?lang=zh-Hans)：设置投放验证周期至关重要。 在将内容发送给受众之前，请确保内容已获批准。
* [发送给受众](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-send.html?lang=zh-Hans)：当您的短信通过验证时，您现在可以将其发送给受众。
* [监控和跟踪SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms-monitor.html?lang=zh-Hans)：监控SMS投放，以确保营销活动有效。


>[!TAB 短信配置]

请参阅这些页面以了解短信配置：

* [独立配置](sms-set-up.md)：了解如何在独立实例上配置短信渠道。
* [中间源配置](sms-set-up-mid.md)：了解如何通过中间服务器发送到手机。
* [SMS连接器](sms-protocol.md)：了解SMS连接器协议和设置。
* [其他配置](sms-send.md)：了解高级参数和其他其他配置。
* [疑难解答](troubleshooting-sms.md)：我们列出了一系列潜在问题及其解决方案。

>[!ENDTABS]



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