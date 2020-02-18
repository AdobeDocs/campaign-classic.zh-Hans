---
title: 配置和发送交付
seo-title: 配置和发送交付
description: 配置和发送交付
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4ac96bf0e54268832b84b17c3cc577af038cc712

---


# 配置和发送交付 {#configuring-and-sending-the-delivery}

>[!NOTE]
>
>只有交付所有者才能开始交付。 为了使其他运算符（或运算符组）能够开始交付，您必须在字段中将其添加为审阅 **[!UICONTROL Delivery start:]** 者。
>
>有关更 [多信息](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers) ，请参阅本节。

## 交付其他参数 {#delivery-additiona-parameters}

在发送传送之前，您可以通过选项卡在传送属性中定义发送参 **[!UICONTROL Delivery]** 数。

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**:此选项允许您通过声明发送的优先级（正常、高或低）来影响发送的顺序。 这样，您就可以优先处理特定、更紧急的交货订单，而不是其他交货。

* **[!UICONTROL Message batch quantity]**:此选项允许您定义在同一XML交付包内分组的消息数。 如果该参数设置为0，则消息将自动分组。 包大小由计算定义， `<delivery size>/1024`每个包最少8条消息，最多256条消息。

   >[!CAUTION]
   >
   >复制交付时，将重置参数。

* **[!UICONTROL Send using multiple waves]**:有关详细信息，请参 [阅使用多波发送](#sending-using-multiple-waves)。

* **[!UICONTROL Test SMTP delivery]**:此选项允许您测试通过SMTP发送。 交付将一直处理到连接到SMTP服务器，但不会发送。

   >[!NOTE]
   >
   >在安装时，使用中间采购时不建议使用此选项，即不调用mta。
   >
   >有关配置SMTP服务器的详细信息，请参阅 [本节](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)。

* **[!UICONTROL Archive emails]**:通过此选项，您只需向邮件目标添加密送电子邮件地址，即可通过密送方式在外部系统上存储电子邮件。 For more on this, refer to [Archiving emails](../../delivery/using/sending-messages.md#archiving-emails).

配置交付并准备发送后，请确保您已运行交付分 [析](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。 完成后，单 **[!UICONTROL Confirm delivery]** 击以启动消息传送。

![](assets/s_ncs_user_email_del_send.png)

然后，您可以关闭传送向导并从选项卡跟踪传送的执行情况，该选项卡可通过此传送的详细信息或传送列表访问 **[!UICONTROL Delivery]** 。

发送消息后，您可以监控和跟踪您的发送。 有关此内容的详细信息，请参阅以下各节：

* [监控投放](../../delivery/using/monitoring-a-delivery.md)
* [了解投放失败](../../delivery/using/understanding-delivery-failures.md)
* [关于消息跟踪](../../delivery/using/about-message-tracking.md)

## 安排交付发送 {#scheduling-the-delivery-sending}

您可以推迟邮件的投放，以便计划内容的投放或管理销售压力并避免过度营销。

1. 单击该 **[!UICONTROL Send]** 按钮并选择该 **[!UICONTROL Postpone delivery]** 选项。

1. 在字段中指定开始日 **[!UICONTROL Contact date]** 期。

![](assets/dlv_email_del_plan.png)

1. 然后，您可以开始分发分析，然后确认分发发送。 但是，在字段中指定的日期之前，交付发送将不会 **[!UICONTROL Contact date]** 开始。

>[!CAUTION]
>
>开始分析后，您定义的联系日期即为固定日期。 如果您修改了此日期，则必须重新开始分析，以便将您的修改考虑在内。

![](assets/s_ncs_user_email_del_start_delayed.png)

在传送列表中，传送将显示为状 **[!UICONTROL Pending]** 态。

![](assets/s_ncs_user_email_del_waiting.png)

还可以通过传送的按钮在上游 **[!UICONTROL Scheduling]** 配置调度。

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

它允许您将交货延迟到以后的日期，或在临时日历中保存交货。

* 通过 **[!UICONTROL Schedule delivery (no automatic execution)]** 此选项，您可以计划对交付的临时分析。

   保存此配置后，传送状态会变 **[!UICONTROL Targeting pending]** 化。 分析将在指定日期启动。

* 通过 **[!UICONTROL Schedule delivery (automatic execution on planned date)]** 此选项可指定交付日期。

   单击 **[!UICONTROL Send]** 并选择 **[!UICONTROL Postpone delivery]** ，然后启动分析并确认提交。 分析完成后，交付目标就绪，消息将在指定日期自动发送。

日期和时间以当前操作员的时区表示。 联系 **[!UICONTROL Time zone]** 人日期输入字段下方的下拉列表允许您将输入的日期和时间自动转换为选定的时区。

例如，如果您计划在伦敦时间8点自动执行交货，则该时间会自动转换为选定的时区：

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 使用多波发送 {#sending-using-multiple-waves}

要平衡负荷，您可以将交货分为多批。 配置批数及其相对于整个交货的比例。

>[!NOTE]
>
>只能定义两个连续波之间的大小和延迟。 无法配置每个波形的收件人选择标准。

1. 打开交付属性窗口，然后单击选 **[!UICONTROL Delivery]** 项卡。
1. 选择选 **[!UICONTROL Send using multiple waves]** 项，然后单击链 **[!UICONTROL Define waves...]** 接。

   ![](assets/s_ncs_user_wizard_waves.png)

1. 要配置波形，您可以：

   * 定义每个波的大小。 例如，如果您在相 **[!UICONTROL 30%]** 应的字段中输入，则每个波形将代表包含在传送中的消息的30%，但最后一个波形除外，后者将代表消息的10%。

      在字段 **[!UICONTROL Period]** 中，指定两个连续波开始之间的延迟。 例如，如果您进 **[!UICONTROL 2d]**&#x200B;入，第一波将立即开始，第二波将在两天后开始，第三波将在四天后开始，依此类推。

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 定义用于发送每个波形的日历。

      在列中， **[!UICONTROL Start]** 指定两个连续波开始之间的延迟。 在列 **[!UICONTROL Size]** 中，输入固定数字或百分比。

      在以下示例中，第一波表示包含在传送中的消息总数的25%，并将立即开始。 接下来的两波将完成传送，并设置为以六小时间隔开始。

      ![](assets/s_ncs_user_wizard_waves_create.png)
   特定的排版规则确 **[!UICONTROL Wave scheduling check]**&#x200B;保在交付有效性限制之前计划好最后一波。 在交付属性的选项卡中配置的系列活 **[!UICONTROL Typology]** 动类型及其规则在验证过程中 [以类型显示](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)。

   >[!CAUTION]
   >
   >确保最后一波不超过交付截止日期(在选项卡中定义 **[!UICONTROL Validity]** )。 否则，可能不会发送某些消息。
   >
   >配置最后一个波形时，还必须允许足够的重试时间。 请参 [阅此部分](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)。

1. 要监控发送，请转到交付日志。 请参 [阅此页](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)。

   您可以看到已在处理波形（状态）中发送的交货，以及将在剩余波形(状&#x200B;**[!UICONTROL Sent]** 态)中发送的&#x200B;**[!UICONTROL Pending]** 交货。

以下两个示例是使用多个波形的最常见用例。

* **在上升过程中**

   使用新平台发送电子邮件时，Internet服务提供商(ISP)会怀疑无法识别的IP地址。 如果突然发送了大量电子邮件，ISP通常会将其标记为垃圾邮件。

   为避免被标记为垃圾邮件，您可以使用波形逐渐增加发送的音量。 这应确保启动阶段的顺利开发，并使您能够降低无效地址的总体速率。

   为此，请使用选 **[!UICONTROL Schedule waves according to a calendar]** 项。 例如，将第一波设置为10%，将第二波设置为15%，依此类推。

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **涉及呼叫中心的营销活动**

   在管理电话忠诚度营销活动时，您的组织处理联系订阅者的呼叫数量的能力有限。

   使用波形，您可以将消息数限制为每天20个，即呼叫中心的日常处理能力。

   为此，请选择选 **[!UICONTROL Schedule multiple waves of the same size]** 项。 在 **[!UICONTROL 20]** 字段中输入波形的大 **[!UICONTROL 1d]** 小和 **[!UICONTROL Period]** 大小。

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 配置重试次数 {#configuring-retries}

由于“软”或“忽略 **”错误** ，暂 **** 时未传送的消息可能会自动重试。 本节介绍了交付失败类型和原 [因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

交付参数选项卡的 **[!UICONTROL Delivery]** 中央部分指示在交付后一天应执行的重试次数和重试之间的最小延迟。

![](assets/s_ncs_user_wizard_retry_param.png)

默认情况下，在交付的第一天将进行五次重试，最小间隔为一小时，分隔一天的24小时。 在此之后，每天一次重试的程序设置为，直到交付截止日期（在选项卡中定义） **[!UICONTROL Validity]** 为止(请参 [阅定义有效期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period))。

>[!NOTE]
>
>对于托管或混合安装，如果您已升级到增强的MTA，则Campaign不再使用交付中的重试设置。 软跳出重试次数和两者之间的时间长度由增强的MTA根据邮件电子邮件域返回的跳出响应的类型和严重性决定。
>
>所有影响在 [Adobe Campaign增强的MTA文档中均有详细介绍](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) 。


## 定义有效期 {#defining-validity-period}

启动交付后，消息（以及任何重试）可发送到交付截止日期。 这通过选项卡在交付属性中指 **[!UICONTROL Validity]** 示。

![](assets/s_ncs_user_email_del_valid_period.png)

* 该字 **[!UICONTROL Delivery duration]** 段允许您输入全局交付重试的限制。 这意味着Adobe Campaign会从开始日期开始发送消息，然后，对于仅返回错误的消息，将执行常规的可配置重试，直到达到有效性限制。

   您还可以选择指定日期。 为此，请选择 **[!UICONTROL Explicitly set validity dates]**。 在这种情况下，交付和有效性限制日期还允许您指定时间。 默认情况下使用当前时间，但您可以直接在输入字段中修改该时间。

* **资源的有效性限制**:该字 **[!UICONTROL Validity limit]** 段用于上传的资源，主要用于镜像页面和图像。 本页上的资源在有限的时间内有效（以节省磁盘空间）。

   此字段中的值可以用本节中列出的单位 [表示](../../platform/using/adobe-campaign-workspace.md#default-units)。

>[!NOTE]
>
>对于托管或混合安装，如果您已升级到增强的MTA，则只有在设置为 **[!UICONTROL Delivery duration]** 3.5天或更少时，才会使用营销活动分发中的 **设置** 。 如果定义的值高于3.5天，则不会将其考虑在内。
>
>所有影响在 [Adobe Campaign增强的MTA文档中均有详细介绍](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) 。
