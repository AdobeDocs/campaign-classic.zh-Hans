---
product: campaign
title: 验证
description: 验证
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 验证{#validating}

![](../../assets/common.svg)

验证投放时的全局概念在 [此部分](steps-validating-the-delivery.md).

在投放分析期间生成直邮投放的输出文件。 文件的内容取决于所选的输出列(请参阅 [提取文件](defining-the-direct-mail-content.md#extraction-file))。

>[!NOTE]
>
>分析阶段详见 [分析投放](steps-validating-the-delivery.md#analyzing-the-delivery).

在分析阶段，会生成文件，但不会更新与收件人相关的信息（即投放日志）。 因此，您可以取消此作业，而不会产生任何风险。

在单击之前，请检查分析结果和输出文件的内容 **[!UICONTROL Confirm delivery]**. 确认消息允许您启动投放。

发送确认会开始指定文件中的数据提取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然后，您可以关闭向导，并通过 **[!UICONTROL Delivery]** 选项卡，可通过投放详细信息访问。

您可以从 **[!UICONTROL Analysis]** 选项卡。

有两种模式：

* **[!UICONTROL Messages are considered sent after validation]** （默认模式）：在此功能模式下，当操作员确认发送（其状态从“待决投放”传递到“已发送”）并且投放自动设置为 **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :利用此模式，可通过服务提供商发送的外部文件更新broadlogs。 在这种情况下，需要使用处理此信息的工作流来更新broadlog状态。

   >[!NOTE]
   >
   >在这种情况下，还需要将投放的状态更改为 **[!UICONTROL Finished]** 广播日志更新后，会立即由用户发送消息。
