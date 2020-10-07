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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 1%

---


# 验证{#validating}

验证投放时的全局概念在本节 [中介绍](../../delivery/using/steps-validating-the-delivery.md)。

在投放分析期间生成直接邮件投放的输出文件。 文件的内容取决于所选的输出列(请参 [阅提取文](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)件)。

>[!NOTE]
>
>分析阶段在分析 [投放中详述](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在分析阶段，生成文件，但不更新有关收件人(即投放日志)的信息。 因此，您可以取消此作业，而不会产生任何风险。

单击前，检查分析结果和输出文件的内容 **[!UICONTROL Confirm delivery]**。 通过确认消息可启动投放。

发送确认开始指定文件中的数据提取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然后，您可以关闭向导并通过选项卡查看投放日志，该 **[!UICONTROL Delivery]** 选项卡可通过投放详细信息访问。

您可以从投放日志属性的选项卡 **[!UICONTROL Analysis]** 中配置投放检索模式。

有两种模式：

* **[!UICONTROL Messages are considered sent after validation]** （默认模式）:在此函数模式中，当操作员确认发送时，所有广播都将更新(其状态从“待定投放”传递到“已发送”)，并且投放自动设置为 **[!UICONTROL Finished]**。
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :此模式允许您通过服务提供商发送的外部文件更新广播。 在这种情况下，需要使用处理此信息的工作流来更新广播状态。

   >[!NOTE]
   >
   >在这种情况下，投放的状态也需要在更新广 **[!UICONTROL Finished]** 播后立即由用户更改为。
