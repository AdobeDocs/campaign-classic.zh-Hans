---
product: campaign
title: 配置和发送投放
description: 了解如何配置和发送投放
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '1517'
ht-degree: 11%

---

# 配置和发送投放 {#configuring-and-sending-the-delivery}

## 权限{#delivery-permissions}

只有投放所有者才能开始投放。 对于能够开始投放的其他操作员（或操作员组），请在&#x200B;**[!UICONTROL Delivery start:]**&#x200B;字段中添加他们作为审阅人。 [了解详情](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)。

## 投放其他参数 {#delivery-additiona-parameters}

在发送投放之前，您可以通过&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡在投放属性中定义发送参数。

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**：使用此选项可通过设置投放的优先级来更改投放的发送顺序：正常、高或低。

* **[!UICONTROL Message batch quantity]**：使用此选项定义在同一XML传递包中分组的邮件数。 如果参数设置为0，则消息将自动分组。 包大小由计算`<delivery size>/1024`定义，每个包最小为8条，最大为256条消息。

  >[!IMPORTANT]
  >
  >通过复制现有投放创建投放时，此参数会重置。

* **[!UICONTROL Send using multiple waves]**：使用此选项可分批发送消息，而不是一次发送给整个受众。 [了解详情](#sending-using-multiple-waves)。

* **[!UICONTROL Test SMTP delivery]**：使用此选项测试通过SMTP发送的邮件。 处理投放直至连接到 SMTP 服务器，但不发送：对于投放的每个收件人，Campaign 连接到 SMTP 提供商服务器，执行 SMTP RCPT TO 命令，并在执行 SMTP DATA 命令之前关闭连接。

  >[!NOTE]
  >
  >* 不得在中间源中设置此选项。
  >
  >* 在[本节](../../installation/using/configure-delivery-settings.md)中了解有关SMTP服务器配置的更多信息。

* **[!UICONTROL Email BCC]**：使用此选项通过密件抄送在外部系统上存储电子邮件，只需将密件抄送电子邮件地址添加到您的邮件目标即可。 [了解详情](sending-messages.md#archiving-emails)。

## 确认投放 {#confirming-delivery}

配置投放并准备好发送后，执行投放分析。

为此，请单击&#x200B;**[!UICONTROL Send]**，选择所需的操作并单击&#x200B;**[!UICONTROL Analyze]**。 [了解详情](steps-validating-the-delivery.md#analyzing-the-delivery)。

![](assets/s_ncs_user_email_del_send.png)

完成后，单击&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;以启动邮件的投放。

然后，您可以关闭投放助手，并从&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡中跟踪投放的执行情况，可通过此投放的详细信息或投放列表访问该选项卡。

发送消息后，您可以监控和跟踪投放。 有关更多信息，请参阅一下章节。

* [监测投放](about-delivery-monitoring.md)
* [了解投放失败](understanding-delivery-failures.md)
* [关于邮件跟踪](about-message-tracking.md)

## 安排发送投放 {#scheduling-the-delivery-sending}

您可以通过计划投放来延迟消息发送。

1. 单击&#x200B;**[!UICONTROL Send]**&#x200B;按钮并选择&#x200B;**[!UICONTROL Postpone delivery]**&#x200B;选项。

1. 在&#x200B;**[!UICONTROL Contact date]**&#x200B;字段中指定开始日期。

![](assets/dlv_email_del_plan.png)

1. 然后，您可以开始投放分析，然后确认投放发送。 但是，在&#x200B;**[!UICONTROL Contact date]**&#x200B;字段中给定的日期之前，不会开始投放发送。

>[!IMPORTANT]
>
>开始分析后，您定义的联系日期即是固定的。 如果修改此日期，则必须重新启动分析，以便考虑所做的修改。

![](assets/s_ncs_user_email_del_start_delayed.png)

在投放列表中，投放将以&#x200B;**[!UICONTROL Pending]**&#x200B;状态显示。

![](assets/s_ncs_user_email_del_waiting.png)

也可以通过投放的&#x200B;**[!UICONTROL Scheduling]**&#x200B;按钮在上游配置计划。

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

这样，您可以将投放推迟到以后的日期，或将投放保存在临时日程表中。

* **[!UICONTROL Schedule delivery (no automatic execution)]**&#x200B;选项允许您计划投放的临时分析。

  保存此配置后，投放将更改为&#x200B;**[!UICONTROL Targeting pending]**&#x200B;状态。 分析将在指定的日期启动。

* 使用&#x200B;**[!UICONTROL Schedule delivery (automatic execution on planned date)]**&#x200B;选项可以指定交货日期。

  单击&#x200B;**[!UICONTROL Send]**&#x200B;并选择&#x200B;**[!UICONTROL Postpone delivery]**，然后启动分析并确认投放。 分析完成后，投放目标已准备就绪，并在指定日期自动发送消息。

日期和时间以当前运算符的时区表示。 通过位于联系日期输入字段下方的&#x200B;**[!UICONTROL Time zone]**&#x200B;下拉列表，您可以将输入的日期和时间自动转换为所选时区。

例如，如果您安排在伦敦时间8点自动执行投放，则该时间将自动转换为所选时区：

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 使用多批次发送 {#sending-using-multiple-waves}

要平衡负荷，您可以将投放分为多个批。 配置批次数量及其相对于整个投放的比例。

>[!NOTE]
>
>您只能定义两个连续波形之间的大小和延迟。 无法配置每个波次的收件人选择标准。

1. 打开投放属性窗口，然后单击&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡。
1. 选择&#x200B;**[!UICONTROL Send using multiple waves]**&#x200B;选项并单击&#x200B;**[!UICONTROL Define waves...]**&#x200B;链接。

   ![](assets/s_ncs_user_wizard_waves.png)

1. 要配置批次，您可以：

   * 定义每个波次的大小。 例如，如果您在相应字段中输入&#x200B;**[!UICONTROL 30%]**，则每个波次将代表投放中包含的30%的消息，但最后一个波次除外，后者将代表10%的消息。

     在&#x200B;**[!UICONTROL Period]**&#x200B;字段中，指定两个连续批次开始之间的延迟。 例如，如果输入&#x200B;**[!UICONTROL 2d]**，则第一个波段将立即开始，第二个波段将在两天内开始，第三个波段将在四天内开始，依此类推。

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 定义发送每个波次的日历。

     在&#x200B;**[!UICONTROL Start]**&#x200B;列中，指定两个连续批次开始之间的延迟。 在&#x200B;**[!UICONTROL Size]**&#x200B;列中，输入固定数字或百分比。

     在下面的示例中，第一波表示投放中包含的消息总数的25%，将立即启动。 接下来的两个批次将完成投放，并设置为以六小时间隔开始。

     ![](assets/s_ncs_user_wizard_waves_create.png)

   特定分类规则&#x200B;**[!UICONTROL Wave scheduling check]**&#x200B;可确保在上一波次的计划早于投放有效期。 在投放属性的&#x200B;**[!UICONTROL Typology]**&#x200B;选项卡中配置的营销活动类型及其规则显示在具有类型的[验证进程中](steps-validating-the-delivery.md#validation-process-with-typologies)。

   >[!IMPORTANT]
   >
   >确保最后一个批次不超过&#x200B;**[!UICONTROL Validity]**&#x200B;选项卡中定义的投放截止日期。 否则，某些消息可能不会发送。
   >
   >在配置最后批次时，还必须留出足够的时间进行重试。 请参阅[此小节](steps-sending-the-delivery.md#configuring-retries)。

1. 要监控您的发送，请转到投放日志。 请参阅[此页](delivery-dashboard.md#delivery-logs-and-history)。

   您可以看到已在已处理批次中发送的投放（**[!UICONTROL Sent]**&#x200B;状态）以及将在剩余批次中发送的投放（**[!UICONTROL Pending]**&#x200B;状态）。

以下两个示例是使用多个批次的最常见用例。

* **启动过程中**

  使用新平台发送电子邮件时，Internet服务提供商(ISP)会怀疑无法识别的IP地址。 如果突然发送大量电子邮件，ISP通常会将其标记为垃圾邮件。

  要避免被标记为垃圾邮件，您可以逐步增加使用批次发送的数量。 这应该可以确保启动阶段的顺利发展，并帮助您降低地址无效的总比率。

  为此，请使用&#x200B;**[!UICONTROL Schedule waves according to a calendar]**&#x200B;选项。 例如，将第一个波次设置为10%，将第二个波次设置为15%，以此类推。

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **涉及呼叫中心的营销活动**

  通过电话管理忠诚度促销活动时，贵组织处理致电订阅者的能力有限。

  使用批次，您可以将消息数量限制为每天20条，例如，考虑呼叫中心的每日处理能力。

  为此，请选择&#x200B;**[!UICONTROL Schedule multiple waves of the same size]**&#x200B;选项。 输入&#x200B;**[!UICONTROL 20]**&#x200B;作为波次大小，并在&#x200B;**[!UICONTROL Period]**&#x200B;字段中输入&#x200B;**[!UICONTROL 1d]**。

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 配置重试 {#configuring-retries}

由于&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;错误而临时取消传递的邮件将会自动重试。 此[部分](understanding-delivery-failures.md#delivery-failure-types-and-reasons)中介绍了投放失败类型和原因。

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

  您也可以选择指定日期。为此，请选择&#x200B;**[!UICONTROL Explicitly set validity dates]**。 在此情况下，也可以使用投放和有效期限日期指定时间。默认情况下使用当前时间，但您可以直接在输入字段中修改此项。

  >[!IMPORTANT]
  >
  >对于托管或混合安装，如果您已升级到[Enhanced MTA](sending-with-enhanced-mta.md)，则仅当设置为&#x200B;**3.5天或更短时间时**，才会使用Campaign电子邮件投放中的&#x200B;**[!UICONTROL Delivery duration]**&#x200B;设置。 如果定义的值超过3.5天，则不会将其考虑在内。

* **资源的有效性限制**： **[!UICONTROL Validity limit]**&#x200B;字段用于已上传的资源，主要用于镜像页面和图像。 本页上的资源仅在限制时间内有效（以节省磁盘空间）。

  此字段中的值可以用[此节](../../platform/using/adobe-campaign-workspace.md#default-units)中列出的单位表示。
