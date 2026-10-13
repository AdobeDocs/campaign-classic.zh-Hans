---
product: campaign
title: 配置和发送投放
description: 了解如何配置和发送投放
feature: Channel Configuration
role: User
hide: true
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
TQID: 'https://experienceleague.adobe.com/-Wh-pHFGE1kTId3t6g7wVJFfSvh2W5ERHi2K5-0Ohdw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b4ecd69f-2adf-4219-bc47-c9cd9a53c118
    internal-label: Channel configuration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 18%
---
# 配置和发送投放 {#configuring-and-sending-the-delivery}

本页介绍特定于Campaign Classic v7的内部部署和混合安装的投放发送设置。

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解有关投放发送设置的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/validate/configure-and-send){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/validate/configure-and-send){target=_blank}

## 投放其他参数 {#delivery-additiona-parameters}

在发送投放之前，您可以通过&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡在投放属性中定义发送参数。

* **[!UICONTROL Test SMTP delivery]**：使用此选项测试通过SMTP发送的邮件。 处理投放直至连接到 SMTP 服务器，但不发送：对于投放的每个收件人，Campaign 连接到 SMTP 提供商服务器，执行 SMTP RCPT TO 命令，并在执行 SMTP DATA 命令之前关闭连接。

  >[!NOTE]
  >
  >* 不得在中间源中设置此选项。
  >
  >* 在[本节](../../installation/using/configure-delivery-settings.md)中了解有关SMTP服务器配置的更多信息。

## 配置重试 {#configuring-retries}

>[!IMPORTANT]
>
>对于托管或混合安装，如果您已升级到[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign将不再使用投放中的重试设置。 软退回重试次数以及它们之间的时间长度由Enhanced MTA根据从消息的电子邮件域返回的退回响应的类型和严重性确定。

对于使用旧版Campaign MTA的内部部署安装和托管/混合安装，投放参数&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡的中心部分指示在投放后一天应执行多少次重试，以及重试之间的最小延迟。

![](assets/s_ncs_user_wizard_retry_param.png)

默认情况下，安排在投放的第一天进行五次重试，最小间隔为一小时分布在一天中的24小时内。 每天进行一次重试的程序在此之后并一直到投放截止日期（在&#x200B;**[!UICONTROL Validity]**&#x200B;选项卡中定义）。 请参阅[定义有效期](#defining-validity-period)。

## 定义有效期 {#defining-validity-period}

启动投放后，可发送消息（以及任何重试），直到投放截止日期为止。 通过&#x200B;**[!UICONTROL Validity]**&#x200B;选项卡在投放属性中指示此情况。

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]**&#x200B;字段允许您输入全局投放重试限制。 这意味着，Adobe Campaign 从开始日期开始发送消息，然后对于仅返回错误的消息，将执行定期、可配置的重试，直至达到有效期限。

  >[!IMPORTANT]
  >
  >对于托管或混合安装，如果您已升级到[Enhanced MTA](sending-with-enhanced-mta.md)，则仅当设置为&#x200B;**3.5天或更短时间时**，才会使用Campaign电子邮件投放中的&#x200B;**[!UICONTROL Delivery duration]**&#x200B;设置。 如果定义的值超过3.5天，则不会将其考虑在内。

* **资源的有效性限制**： **[!UICONTROL Validity limit]**&#x200B;字段用于已上传的资源，主要用于镜像页面和图像。 本页上的资源仅在限制时间内有效（以节省磁盘空间）。

  此字段中的值可以用以下单位表示：**s**&#x200B;表示秒，**m**&#x200B;表示分钟，**h**&#x200B;表示小时，**d**&#x200B;表示天（默认值），**y**&#x200B;表示年。
