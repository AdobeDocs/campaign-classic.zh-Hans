---
title: 验证
seo-title: 验证
description: 验证
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70f51ba3937d0f20d9a488c61b52b7ec4396fa5e

---


# 验证{#validating}

验证交付时的全局概念在本节中 [介绍](../../delivery/using/steps-validating-the-delivery.md)。

在发送分析期间生成直接邮件发送的输出文件。 文件的内容取决于所选的输出列(请参 [阅提取文件](../../delivery/using/defining-the-direct-mail-content.md#extraction-file))。

>[!NOTE]
>
>分析阶段在分析交 [付中详细介绍](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在分析阶段，生成文件，但不更新关于接收者的信息（即交付日志）。 因此，您可以取消此作业，而不会有任何风险。

单击前，请检查分析结果和输出文件的内容 **[!UICONTROL Confirm delivery]**。 通过确认消息，可启动传送。

发送确认会启动指定文件中的数据提取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然后，您可以关闭向导，并通过选项卡查看交付日志，该选项卡可 **[!UICONTROL Delivery]** 以通过交付详细信息访问。

您可以从交付属性的选项卡中配置 **[!UICONTROL Analysis]** 交付日志检索模式。

有两种模式：

* **[!UICONTROL Messages are considered sent after validation]** （默认模式）:在此功能模式中，当操作员确认发送（其状态从“待定交付”传递到“已发送”）并且传送自动设置为时，所有广播都会更新 **[!UICONTROL Finished]**。
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :此模式允许您通过服务提供商发送的外部文件更新广播日志。 在这种情况下，需要使用处理此信息的工作流来更新广播状态。

   >[!NOTE]
   >
   >在这种情况下，在更新广播后，用户还需要将交 **[!UICONTROL Finished]** 付状态更改为。
