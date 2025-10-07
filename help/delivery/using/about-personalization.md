---
product: campaign
title: 个性化入门
description: 了解如何在Campaign中个性化消息和使用条件内容
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 14%

---

# 个性化入门{#about-personalization}

通过 Adobe Campaign 投放的邮件可通过几种不同的方式进行个性化，涉及邮件的内容或外观。根据基于收件人轮廓的特定标准，可以将这些方式结合使用。对于电子邮件投放，您可以从消息的&#x200B;**[!UICONTROL Source]**&#x200B;选项卡直接在JavaScript中定义投放的元素和个性化条件。 一般而言，Adobe Campaign 允许您：

* 个性化邮件的格式。查看[消息内容](defining-the-email-content.md#message-content)。
* 插入动态的个性化字段。查看[个性化字段](personalization-fields.md)。
* 插入预定义的个性化块。 请参阅[个性化块](personalization-blocks.md)。
* 创建条件性内容。请参阅[条件内容](conditional-content.md)部分。

>[!CAUTION]
>
>以下变量是可用于个性化但不得修改的内部变量：**投放**、**消息**、**数据源**、**targetData**、**提供程序**、**优惠券**、**优惠券值**、**建议**。


使用Adobe Campaign，个性化您的投放，以发送与每个收件人的用户档案和兴趣匹配的消息。

Personalization可帮助您使消息更具相关性和吸引力。 您可以使用收件人数据根据条件调整内容、添加动态字段或显示不同信息。 请参阅[Adobe Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}以了解如何在投放中设置和使用个性化功能。

作为Campaign v8促销活动的一部分，重组了Campaign Classic文档。 公共功能现在仅在Campaign v8文档集中可用。

>[!BEGINTABS]

>[!TAB 内容个性化文档]

要了解有关内容个性化的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}。


[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html){target=_blank}


>[!TAB 电子邮件投放创建]

请参阅Campaign v8文档以了解与创建电子邮件投放相关的关键步骤：

* [创建电子邮件投放](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html){target="_blank"}：了解创建电子邮件投放所需的不同步骤。
* [定义电子邮件内容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html){target="_blank"}：定义您的电子邮件将包含的内容：发件人、主题、内容、图像。
* [定义交互式内容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html){target="_blank"}：使用交互式AMP for Email格式发送动态电子邮件。
* [在日语手机上发送电子邮件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html){target="_blank"}：在手机上使用三种特定的日语格式之一发送电子邮件。
* [将文件附加到电子邮件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html){target="_blank"}：了解将一个或多个文件附加到电子邮件的不同方法。


>[!TAB 电子邮件参数]

请参阅Campaign v8文档中的这些页面以了解电子邮件参数：

* [链接到镜像页面](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html){target="_blank"}：配置镜像页面以确保您的客户端始终获得最佳的渲染体验。
* [添加密件抄送地址](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html){target="_blank"}：配置Adobe Campaign以保留从您的平台发送的电子邮件副本。
* [定义其他电子邮件参数](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html){target="_blank"}：了解有关投放属性中可用的选项和参数的更多信息。

另请参阅此[页面](sending-with-enhanced-mta.md)以了解有关增强型MTA的信息。

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->