---
product: campaign
title: 配置和发送投放
description: 了解如何配置和发送投放
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Channel Configuration
role: User
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 11%

---

# 配置和发送投放 {#configuring-and-sending-the-delivery}

## 权限{#delivery-permissions}

只有投放所有者才能开始投放。 对于能够开始投放的其他操作员（或操作员组），请将其添加为中的审阅人 **[!UICONTROL Delivery start:]** 字段。 [了解详情](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)。

## 投放其他参数 {#delivery-additiona-parameters}

在发送投放之前，您可以在投放属性中定义发送参数，方法是 **[!UICONTROL Delivery]** 选项卡。

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**：使用此选项可通过设置投放的优先级来更改其发送顺序：正常、高或低。

* **[!UICONTROL Message batch quantity]**：使用此选项可定义在同一个XML投放包中分组的消息数。 如果参数设置为0，则消息将自动分组。 程序包大小由计算定义 `<delivery size>/1024`，则每个包最少8条消息，最多256条消息。

  >[!IMPORTANT]
  >
  >通过复制现有投放创建投放时，此参数会重置。

* **[!UICONTROL Send using multiple waves]**：使用此选项可分批发送消息，而不是一次发送给整个受众。 [了解详情](#sending-using-multiple-waves)。

* **[!UICONTROL Test SMTP delivery]**：使用此选项测试通过SMTP进行的发送。 处理投放直至连接到 SMTP 服务器，但不发送：对于投放的每个收件人，Campaign 连接到 SMTP 提供商服务器，执行 SMTP RCPT TO 命令，并在执行 SMTP DATA 命令之前关闭连接。

  >[!NOTE]
  >
  >* 不得在中间源中设置此选项。
  >
  >* 了解有关SMTP服务器配置的更多信息，请参阅 [本节](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL Email BCC]**：使用此选项可以通过密件抄送在外部系统上存储电子邮件，只需将密件抄送电子邮件地址添加到消息目标即可。 [了解详情](sending-messages.md#archiving-emails)。

## 确认投放 {#confirming-delivery}

配置投放并准备好发送后，执行投放分析。

为此，请单击 **[!UICONTROL Send]**，选择所需的操作并单击 **[!UICONTROL Analyze]**. [了解详情](steps-validating-the-delivery.md#analyzing-the-delivery)。

![](assets/s_ncs_user_email_del_send.png)

完成后，单击 **[!UICONTROL Confirm delivery]** 以启动消息的投放。

然后，您可以关闭投放向导，并从以下位置跟踪投放的执行情况 **[!UICONTROL Delivery]** 选项卡，可通过此投放的详细信息或投放列表访问。

发送消息后，您可以监控和跟踪投放。 有关更多信息，请参阅一下章节。

* [监测投放](about-delivery-monitoring.md)
* [了解投放失败](understanding-delivery-failures.md)
* [关于邮件跟踪](about-message-tracking.md)

## 安排发送投放 {#scheduling-the-delivery-sending}

您可以通过计划投放来延迟消息发送。

1. 单击 **[!UICONTROL Send]** 按钮并选择 **[!UICONTROL Postpone delivery]** 选项。

1. 在中指定开始日期 **[!UICONTROL Contact date]** 字段。

![](assets/dlv_email_del_plan.png)

1. 然后，您可以开始投放分析，然后确认投放发送。 但是，直到中给定的日期才会开始投放发送 **[!UICONTROL Contact date]** 字段。

>[!IMPORTANT]
>
>开始分析后，您定义的联系日期即是固定的。 如果修改此日期，则必须重新启动分析，以便考虑所做的修改。

![](assets/s_ncs_user_email_del_start_delayed.png)

在投放列表中，投放将显示为 **[!UICONTROL Pending]** 状态。

![](assets/s_ncs_user_email_del_waiting.png)

您还可以通过在上游配置计划 **[!UICONTROL Scheduling]** 投放的按钮。

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

这样，您可以将投放推迟到以后的日期，或将投放保存在临时日程表中。

* 此 **[!UICONTROL Schedule delivery (no automatic execution)]** 选项允许您计划投放的临时分析。

  保存此配置后，投放将更改为 **[!UICONTROL Targeting pending]** 状态。 分析将在指定的日期启动。

* 此 **[!UICONTROL Schedule delivery (automatic execution on planned date)]** 选项可让您指定提交日期。

  单击 **[!UICONTROL Send]** 并选择 **[!UICONTROL Postpone delivery]** 然后启动分析并确认投放。 分析完成后，投放目标已准备就绪，并在指定日期自动发送消息。

日期和时间以当前运算符的时区表示。 此 **[!UICONTROL Time zone]** 通过位于联系日期输入字段下方的下拉列表，您可以将输入的日期和时间自动转换为所选时区。

例如，如果您安排在伦敦时间8点自动执行投放，则该时间将自动转换为所选时区：

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 使用多批次发送 {#sending-using-multiple-waves}

要平衡负荷，您可以将投放分为多个批。 配置批次数量及其相对于整个投放的比例。

>[!NOTE]
>
>您只能定义两个连续波形之间的大小和延迟。 无法配置每个波次的收件人选择标准。

1. 打开投放属性窗口，然后单击 **[!UICONTROL Delivery]** 选项卡。
1. 选择 **[!UICONTROL Send using multiple waves]** 选项，然后单击 **[!UICONTROL Define waves...]** 链接。

   ![](assets/s_ncs_user_wizard_waves.png)

1. 要配置批次，您可以：

   * 定义每个波次的大小。 例如，如果您输入 **[!UICONTROL 30%]** 在相应的字段中，每个波次将代表投放中所包含报文的30%，但最后一条代表10%的报文。

     在 **[!UICONTROL Period]** 字段，指定两个连续批次开始之间的延迟。 例如，如果您输入 **[!UICONTROL 2d]**，第一波立即开始，第二波在两天内开始，第三波在四天内开始，以此类推。

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 定义发送每个波次的日历。

     在 **[!UICONTROL Start]** 列，指定两个连续批次开始之间的延迟。 在 **[!UICONTROL Size]** 列中，输入固定数字或百分比。

     在下面的示例中，第一波表示投放中包含的消息总数的25%，将立即启动。 接下来的两个批次将完成投放，并设置为以六小时间隔开始。

     ![](assets/s_ncs_user_wizard_waves_create.png)

   特定的分类规则， **[!UICONTROL Wave scheduling check]**，确保最后一个波次的计划时间早于投放有效期限。 营销活动类型及其规则，配置于 **[!UICONTROL Typology]** 的选项卡中显示 [具有类型的验证过程](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >确保最后批次不超过投放截止日期，投放截止日期在中定义 **[!UICONTROL Validity]** 选项卡。 否则，某些消息可能不会发送。
   >
   >在配置最后批次时，还必须留出足够的时间进行重试。 请参阅[此小节](steps-sending-the-delivery.md#configuring-retries)。

1. 要监控您的发送，请转到投放日志。 请参阅[此页](delivery-dashboard.md#delivery-logs-and-history)。

   您可以看到已在已处理批次中发送的投放(**[!UICONTROL Sent]** 状态)和要在剩余批次中发送的投放(**[!UICONTROL Pending]** 状态)。

以下两个示例是使用多个批次的最常见用例。

* **启动过程中**

  使用新平台发送电子邮件时，Internet服务提供商(ISP)会怀疑无法识别的IP地址。 如果突然发送大量电子邮件，ISP通常会将其标记为垃圾邮件。

  要避免被标记为垃圾邮件，您可以逐步增加使用批次发送的数量。 这应该可以确保启动阶段的顺利发展，并帮助您降低地址无效的总比率。

  要执行此操作，请使用 **[!UICONTROL Schedule waves according to a calendar]** 选项。 例如，将第一个波次设置为10%，将第二个波次设置为15%，以此类推。

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **涉及呼叫中心的营销活动**

  在管理电话忠诚度促销活动时，贵组织处理致电订阅者的能力有限。

  使用批次，您可以将每天的消息数量限制为20，这是呼叫中心的每日处理能力。

  要执行此操作，请选择 **[!UICONTROL Schedule multiple waves of the same size]** 选项。 输入 **[!UICONTROL 20]** 因为波浪的大小和 **[!UICONTROL 1d]** 在 **[!UICONTROL Period]** 字段。

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 配置重试 {#configuring-retries}

临时未送达消息的原因为 **柔光** 或 **已忽略** 错误将会自动重试。 此页面中介绍了投放失败类型和原因 [部分](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>对于托管或混合安装，如果已升级到 [增强MTA](sending-with-enhanced-mta.md)，Campaign将不再使用投放中的重试设置。 软退回重试次数以及它们之间的时间长度由Enhanced MTA根据从消息的电子邮件域返回的退回响应的类型和严重性确定。

对于使用旧版Campaign MTA的内部部署和托管/混合安装，的中央部分 **[!UICONTROL Delivery]** 选项卡中的投放参数指示在投放后一天应执行多少次重试，以及重试之间的最小延迟。

![](assets/s_ncs_user_wizard_retry_param.png)

默认情况下，安排在投放的第一天进行五次重试，最小间隔为一小时分布在一天中的24小时内。 之后和到中定义的投放截止日期之前，每天都会安排一次重试 **[!UICONTROL Validity]** 选项卡。 请参阅 [定义有效期](#defining-validity-period).

## 定义有效期 {#defining-validity-period}

启动投放后，可发送消息（以及任何重试），直到投放截止日期为止。 这在投放属性中通过 **[!UICONTROL Validity]** 选项卡。

![](assets/s_ncs_user_email_del_valid_period.png)

* 此 **[!UICONTROL Delivery duration]** 字段可让您输入全局投放重试的限制。 这意味着，Adobe Campaign 从开始日期开始发送消息，然后对于仅返回错误的消息，将执行定期、可配置的重试，直至达到有效期限。

  您也可以选择指定日期。要执行此操作，请选择 **[!UICONTROL Explicitly set validity dates]**. 在此情况下，也可以使用投放和有效期限日期指定时间。默认情况下使用当前时间，但您可以直接在输入字段中修改此项。

  >[!IMPORTANT]
  >
  >对于托管或混合安装，如果已升级到 [增强MTA](sending-with-enhanced-mta.md)， **[!UICONTROL Delivery duration]** 只有将设置为时，才会使用Campaign电子邮件投放中的设置 **3.5天或以下**. 如果定义的值超过3.5天，则不会将其考虑在内。

* **资源的有效期限**：和 **[!UICONTROL Validity limit]** 字段用于已上传的资源，主要用于镜像页面和图像。 本页上的资源仅在限制时间内有效（以节省磁盘空间）。

  此字段中的值可以用中列出的单位表示 [本节](../../platform/using/adobe-campaign-workspace.md#default-units).
