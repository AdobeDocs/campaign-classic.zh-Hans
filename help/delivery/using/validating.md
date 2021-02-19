---
solution: Campaign Classic
product: campaign
title: 验证
description: 验证
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---


# 验证{#validating}

验证投放时的全局概念在[此部分](../../delivery/using/steps-validating-the-delivery.md)中介绍。

在投放分析期间生成直接邮件投放的输出文件。 文件的内容取决于所选的输出列(请参阅[提取文件](../../delivery/using/defining-the-direct-mail-content.md#extraction-file))。

>[!NOTE]
>
>[分析分析](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)中详细介绍了投放阶段。

在分析阶段，生成文件，但不更新有关收件人(即投放日志)的信息。 因此，您可以取消此作业，而不会产生任何风险。

单击&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;前，请检查分析结果和输出文件的内容。 通过确认消息可启动投放。

发送确认开始指定文件中的数据提取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然后，您可以关闭向导并通过&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡查看投放日志，可通过投放详细信息访问该选项卡。

您可以从投放日志属性的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡中配置投放检索模式。

有两种模式：

* **[!UICONTROL Messages are considered sent after validation]** （默认模式）：在此函数模式中，当操作员确认发送时，所有广播将更新(其状态从“待定投放”传递到“已发送”)，并且投放自动设置为 **[!UICONTROL Finished]**。
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :此模式允许您通过服务提供商发送的外部文件更新广播。在这种情况下，需要使用处理此信息的工作流来更新广播状态。

   >[!NOTE]
   >
   >在这种情况下，用户还需要在更新广播后立即将投放的状态更改为&#x200B;**[!UICONTROL Finished]**。
