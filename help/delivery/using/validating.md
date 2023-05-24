---
product: campaign
title: 验证
description: 验证
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 验证{#validating}



有关验证投放时的全局概念，请参阅 [本节](steps-validating-the-delivery.md).

直邮投放的输出文件在投放分析期间生成。 文件的内容取决于选定的输出列(请参阅 [提取文件](defining-the-direct-mail-content.md#extraction-file))。

>[!NOTE]
>
>有关分析阶段的详情，请参见 [分析投放](steps-validating-the-delivery.md#analyzing-the-delivery).

在分析阶段，会生成文件，但不更新有关收件人的信息（即投放日志）。 因此，您可以取消此作业而不运行任何风险。

在单击之前检查分析结果和输出文件的内容 **[!UICONTROL Confirm delivery]**. 确认消息可让您启动投放。

发送确认会启动指定文件中的数据提取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然后，您可以关闭向导，并通过查看投放日志 **[!UICONTROL Delivery]** 选项卡，可通过投放详细信息访问。

您可以从以下位置配置投放日志检索模式 **[!UICONTROL Analysis]** 选项卡中显示的投放属性。

有两种模式：

* **[!UICONTROL Messages are considered sent after validation]** （默认模式）：在此函数模式下，当操作员确认发送（其状态从“待定投放”传递到“已发送”）并且投放自动设置为 **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** ：利用此模式，可通过服务提供商发送的外部文件更新broadlog。 在这种情况下，需要使用工作流来处理此信息，以更新broadlog状态。

   >[!NOTE]
   >
   >在这种情况下，投放的状态也需要更改为 **[!UICONTROL Finished]** 用户在broadlog更新后立即执行。
