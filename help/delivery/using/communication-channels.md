---
product: campaign
title: 通信渠道
description: 创建投放，在不同渠道上发送个性化信息
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 14%

---

# 通信渠道{#communication-channels}

借助 Adobe Campaign，您可以发送跨渠道活动内容，包括电子邮件、短信、推送通知和直邮，并使用各种专门的报告衡量其有效性。这些消息通过投放设计和发送，并且可以针对每个收件人进行个性化。

核心功能包括定向、消息定义和个性化、通信执行和相关的运营报告。

作为Campaign v8促销活动的一部分，重组了Campaign Classic文档。 公共功能现在仅在Campaign v8文档集中可用。



>[!BEGINTABS]

>[!TAB 通信渠道文档]

要了解有关通信渠道的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target=_blank}。


[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target=_blank}


>[!TAB 投放内容和受众]

请参阅Campaign v8文档以了解与投放创建、内容和受众相关的关键步骤：

* [创建投放](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#create-the-delivery){target="_blank"}：了解如何创建一次性投放。
* [定义内容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#content-of-the-delivery){target="_blank"}：配置特定于每个渠道的投放内容。
* [指定受众](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#target-population){target="_blank"}：定义几种类型的目标：主受众、验证目标、种子地址和对照组。
* [使用投放模板](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html){target="_blank"}：了解如何定义模板以便于创建投放。





>[!TAB 传递验证和发送]

请参阅这些页面，以在Campaign v8文档中了解投放验证、发送和最佳实践：

* [验证投放](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#validate-the-delivery){target="_blank"}：了解如何在将投放发送到主目标之前验证投放。
* [发送投放](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html#configuring-and-sending-the-delivery){target="_blank"}：配置投放设置并定义发送消息的方式。
* [投放最佳实践](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html){target="_blank"}：查阅与Campaign投放功能相关的最佳实践。

>[!ENDTABS]

以下设置特定于Campaign Classic。 有关其他投放设置，请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target="_blank"}。

+++ **投放分析**

**改进投放分析性能**

要加快投放准备速度，您可以在启动分析之前选中&#x200B;**[!UICONTROL Prepare the delivery parts in the database]**&#x200B;选项。

启用此选项后，将直接在数据库中执行投放准备，这可以显着加快分析。

目前，仅当满足以下条件时，此选项才可用：

* 投放必须是电子邮件。 目前不支持其他渠道。
* 您不得使用中间源或外部路由，只能使用批量投放路由类型。 您可以检查&#x200B;**[!UICONTROL General]**&#x200B;的&#x200B;**[!UICONTROL Delivery properties]**&#x200B;选项卡中使用的路由。
* 无法定位来自外部文件的群体。 对于单个投放，请单击&#x200B;**[!UICONTROL To]**&#x200B;中的&#x200B;**[!UICONTROL Email parameters]**&#x200B;链接，并检查是否选择了&#x200B;**[!UICONTROL Defined in the database]**&#x200B;选项。 对于工作流中使用的投放，检查&#x200B;**[!UICONTROL Specified by the inbound event(s)]**&#x200B;选项卡中的收件人是否为&#x200B;**[!UICONTROL Delivery]**。
* 您必须使用PostgreSQL数据库。

**配置分析优先级**

如果投放属于营销活动，**[!UICONTROL Advanced]**&#x200B;选项卡会提供一个额外的选项。 这样，您就可以在同一营销活动中组织投放的处理顺序。

在发送之前，会分析每个投放。 分析持续时间取决于投放提取文件。 文件大小越大，分析所需的时间就越长，从而会等待以下投放。

**[!UICONTROL Message preparation by the scheduler]**&#x200B;的选项允许您在营销活动工作流中优先考虑投放分析。

![](assets/delivery_analysis_priority.png)

如果投放过大，最好为其分配较低的优先级，以避免减慢对其他工作流投放的分析。

>[!NOTE]
>
>为了确保较大的投放分析不会减慢工作流的进度，您可以通过勾选&#x200B;**[!UICONTROL Schedule execution for a time of low activity]**&#x200B;来计划其执行。

+++

+++ **投放发送**

**配置重试**

由于&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;错误而临时取消传递的邮件将会自动重试。 此[部分](understanding-delivery-failures.md#delivery-failure-types-and-reasons)中介绍了投放失败类型和原因。

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign将不再使用投放中的重试设置。 软退回重试次数以及它们之间的时间长度由Enhanced MTA根据从消息的电子邮件域返回的退回响应的类型和严重性确定。

对于使用旧版Campaign MTA的内部部署安装和托管/混合安装，投放参数&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡的中心部分指示在投放后一天应执行多少次重试，以及重试之间的最小延迟。

![](assets/s_ncs_user_wizard_retry_param.png)

默认情况下，安排在投放的第一天进行五次重试，最小间隔为一小时分布在一天中的24小时内。 每天进行一次重试的程序在此之后并一直到投放截止日期（在&#x200B;**[!UICONTROL Validity]**&#x200B;选项卡中定义）。 请参阅[定义有效期](#defining-validity-period)。

**定义有效期**

启动投放后，可发送消息（以及任何重试），直到投放截止日期为止。 通过&#x200B;**[!UICONTROL Validity]**&#x200B;选项卡在投放属性中指示此情况。

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]**&#x200B;字段允许您输入全局投放重试限制。 这意味着，Adobe Campaign 从开始日期开始发送消息，然后对于仅返回错误的消息，将执行定期、可配置的重试，直至达到有效期限。

  您也可以选择指定日期。为此，请选择&#x200B;**[!UICONTROL Explicitly set validity dates]**。 在此情况下，也可以使用投放和有效期限日期指定时间。默认情况下使用当前时间，但您可以直接在输入字段中修改此项。

  >[!IMPORTANT]
  >
  >对于托管或混合安装，如果您已升级到[Enhanced MTA](sending-with-enhanced-mta.md)，则仅当设置为&#x200B;**[!UICONTROL Delivery duration]** 3.5天或更短时间时&#x200B;**，才会使用Campaign电子邮件投放中的**&#x200B;设置。 如果定义的值超过3.5天，则不会将其考虑在内。

* **资源的有效性限制**： **[!UICONTROL Validity limit]**&#x200B;字段用于已上传的资源，主要用于镜像页面和图像。 本页上的资源仅在限制时间内有效（以节省磁盘空间）。

  此字段中的值可以用[此节](../../platform/using/adobe-campaign-workspace.md#default-units)中列出的单位表示。

+++

<!--

   Learn how to create a one-shot single delivery. You can create other types of deliveries to build your use cases. 

For more information about the different types of deliveries and how to create them, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html){target="_blank"}. 

>[!NOTE]
>
>Adobe Campaign offers a set of tools to monitor your deliverability and optimize email sending. Learn more in [this section](about-deliverability.md).

Delivery sending can be automated by preparing a delivery and/or sending it in the process of a workflow. For more on delivery-type activities in workflows, refer to [this section](../../workflow/using/about-action-activities.md).

Adobe Campaign offers the following delivery channels:

1. **Email channel**: email deliveries let you send personalized emails to the target population. Refer to [About email channel](about-email-channel.md).
1. **Direct mail channel**: direct mail deliveries let you generate an extraction file which contains data on the target population. Refer to [About direct mail channel](about-direct-mail-channel.md).
1. **Mobile channel**: deliveries on mobile channels let you send personalized SMS or LINE messages to the target population. Refer to [SMS channel](sms-channel.md).
1. **Mobile application channel**: mobile app deliveries let you send notifications to iOS and Android systems. Refer to the [Mobile app channel](about-mobile-app-channel.md) chapter.

   Other channels are described on [this section](#other-channels).

   >[!NOTE]
   >
   >The number of available channels depends on your contract. Please check your license agreement.

Deliveries can be carried out **online** (via email, one of the mobile channels and push notifications), and **offline** (direct mail channel).

Depending on the channel, delivery modes can be:

* Direct mass delivery via Adobe Campaign (default mode for email channel).
* External delivery via a specialist operator who is given the output file generated by the delivery assistant (default mode for direct mail channel).

External accounts are configured via the **[!UICONTROL Administration > Platform > External accounts]** node. This configuration should be performed by expert users only.

## Email deliveries {#email-deliveries}

The [Email channel](about-email-channel.md) is one of the core channels in Adobe Campaign, allowing you to schedule and send personalized emails to specific targets.

You can send different types of emails:

* Single-send emails: emails that you can send once to a defined target. They are usually used to promote a specific content that would be prepared and sent only once (newsletter, promotional email, etc.).
* Recurring emails: in a campaign, send the same email regularly and aggregate each send and its reports on a periodic basis. The same email is sent, but usually to a different target, based on the eligible target for the day of the send. A common example is a birthday email. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* Transactional emails: unitary emails that are triggered based on your customers' behavior. Refer to [Transactional messaging](../../message-center/using/about-transactional-messaging.md).

To learn about delivery usage and recommendations, consult Campaign [Delivery best practices](delivery-best-practices.md).

For more on the different types of deliveries, refer to [this section](#types-of-deliveries).

## Mobile deliveries {#mobile-deliveries}

Adobe Campaign allows you to deliver [SMS](sms-channel.md) and [LINE](line-channel.md) messages on mobiles.

For SMS messages, you can create, modify, and personalize messages in text format only. You can also preview your SMS messages before they are sent.

For LINE messages, you can send text or images and links.

To deliver SMS or LINE messages to a mobile phone you need:

* An external account configured on the **[!UICONTROL Mobile (SMS)]** channel or on the **[!UICONTROL LINE]** channel. 
* An SMS or LINE delivery template that is correctly linked to this external account.

## Push notifications {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. Once configuration and integration steps have been performed, iOS and Android deliveries can be created and sent. You can also design rich notifications with images or videos.

## Direct mail {#direct-mail}

[Direct mail](about-direct-mail-channel.md) is an offline channel that allows you to personalize and generate the file required by direct mail providers. It gives you the possibility to mix online and offline channels in your customer journeys.

Online channels allow you to create your messages (email, SMS, mobile app delivery, etc.) and send them to your audience directly from Adobe Campaign. With offline channels, it is different. When you prepare a direct mail delivery, Adobe Campaign generates a file including all the targeted profiles and the chosen contact information (postal address for example). You will then be able to send this file to your direct mail provider who will take care of the actual sending.

## Other channels {#other-channels}

Adobe Campaign offers Telephone delivery template, which is used to create external deliveries. Using this channel implies you set up dedicated methodologies to process output files. Configuration steps are the same as for [Direct mail channel](about-direct-mail-channel.md).

>[!NOTE]
>
>The Telephone channel is not available out-of-the-box. Its implementation requires Adobe Consulting or an Adobe Partner to be engaged. Please reach out to your Adobe representative for more information.

In addition, 'Other' type deliveries use a specific technical template which does not execute a process: this lets them manage marketing actions executed outside of the Adobe Campaign platform.

This channel has no specific mechanism. It is a generic channel that has its own external account routing option, delivery template type and campaign workflow activity, just like any other communication channel available in Adobe Campaign.

This channel is designed for descriptive purposes only, for example to define deliveries for which you want to keep a trace of the target of a campaign performed in a tool other than Adobe Campaign.

## Types of deliveries{#types-of-deliveries}

There are three types of delivery objects in Campaign:

### Single delivery {#single-delivery}

A **delivery** is a standalone delivery object that is executed once. It can be duplicated, prepared again, but as long as it is in its final state (canceled, stopped, finished), it cannot be reused.

Deliveries can be created either from the list of deliveries, or within a workflow via a [Delivery](../../workflow/using/delivery.md) activity.

Workflows also provide specific delivery activities according to the type of channel you want to use. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### Recurring delivery {#recurring-delivery}

A **recurring delivery** lets you create a new delivery each time the activity is executed. This avoids you having to create a new delivery for recurring tasks.

As an example, if you run this type of activity once a month, you will end up with 12 deliveries after a year.

Recurring deliveries are created within workflows via the [Recurring delivery activity](../../workflow/using/recurring-delivery.md). An example of this activity being used is presented in this section: [Creating a recurring delivery in a targeting workflow](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Continuous delivery {#continuous-delivery}

A **continuous delivery** lets you add new recipients to an existing delivery, which avoids having to create a new delivery each time it is executed.

If an information in the delivery changes (content, name, etc.), a new delivery object is created at the delivery execution. If no information was changed, the same delivery object is reused and the delivery and tracking logs are added in the same object.

As an example, if you run this type of activity once a month, you will end up with a single delivery after a year (provided you did not make any change to the delivery).

Continuous deliveries are created within workflows via the [Continuous delivery activity](../../workflow/using/continuous-delivery.md).-->
