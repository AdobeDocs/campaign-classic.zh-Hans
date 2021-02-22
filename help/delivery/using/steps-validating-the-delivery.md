---
solution: Campaign Classic
product: campaign
title: 验证投放
description: 验证投放
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 5%

---


# 验证投放 {#validating-the-delivery}

创建和配置投放后，您必须先验证该目标，然后再将其发送到主。

操作步骤：

1. **分析投放**:通过此步骤，您可以准备要传送的消息。请参阅[分析投放](#analyzing-the-delivery)。

   在分析期间应用的规则显示在[本节](#validation-process-with-typologies)中。 [更改批准模式](#changing-the-approval-mode)部分详细介绍了可用校验模式。

1. **发送验证**:通过此步骤，您可以批准内容、URL、个性化字段等。请参阅[发送验证](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)和[定义特定验证目标](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)。

>[!IMPORTANT]
>
>必须在对消息内容进行每次修改后执行这两个步骤。

## 分析投放{#analyzing-the-delivery}

分析是计算目标种群并准备投放内容的阶段。 投放完成后，即可发送。

### 启动分析{#launching-the-analysis}

1. 要启动投放分析，请单击&#x200B;**[!UICONTROL Send]**。
1. 选择 **[!UICONTROL Deliver as soon as possible]**。

   ![](assets/s_ncs_user_email_del_send.png)

1. 单击&#x200B;**[!UICONTROL Analyze]**&#x200B;手动启动分析。

   进度栏显示分析的进度。

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >在[具有类型的验证过程](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)部分中介绍了在分析过程中使用的验证规则。

1. 您可以随时单击&#x200B;**[!UICONTROL Stop]**&#x200B;停止分析。

   ![](assets/s_ncs_user_wizard_email01_16.png)

   在准备阶段不会发送消息。 因此，您可以开始或取消分析，而不会有风险。

   >[!IMPORTANT]
   >
   >运行时，分析将冻结投放(或验证)。 对投放(或验证)的任何更改必须在适用之前先经过其他分析。

1. 等待分析完成。

   分析完成后，窗口的上半部分将指示投放准备是否完成或是否发生任何错误。 将列出所有验证步骤、警告和错误。 彩色图标显示消息类型：
   * 蓝色图标表示有信息性消息。
   * 黄色图标表示出现非关键处理错误。
   * 红色图标指示阻止发送投放的严重错误。

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 单击&#x200B;**[!UICONTROL Close]**&#x200B;以更正错误（如果有）。

1. 进行更改后，重新启动分析，单击&#x200B;**[!UICONTROL Analyze]**。

检查分析结果后，您可以单击&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;将消息发送到指定目标。 通过确认消息可启动投放。

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>如果要发送的消息数与您的配置不匹配，请单击&#x200B;**[!UICONTROL Change the main delivery target]**&#x200B;链接。 这样，您可以更改目标群的定义并重新开始分析。

### 分析参数{#analysis-parameters}

通过投放属性的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡，可以定义一组在分析阶段准备消息的相关信息。

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

此选项卡允许访问以下选项：

* **[!UICONTROL Label and code of the delivery]** :本节中的选项用于计算这些字段在投放分析阶段的值。**[!UICONTROL Compute the execution folder during the delivery analysis]**&#x200B;字段计算在分析阶段将包含此投放操作的文件夹的名称。
* **[!UICONTROL Approval mode]** :此字段允许您在完成投放后定义手动或自动分析。这些校验模式显示在[更改批准模式](#changing-the-approval-mode)部分。
* **[!UICONTROL Prepare the delivery parts in the database]** :通过此选项，可以提高投放分析性能。有关更多信息，请参阅[此章节](#improving-delivery-analysis)。
* **[!UICONTROL Prepare the personalization data with a workflow]** :此选项允许您在自动工作流程中准备包含在投放中的个性化数据，这可以显着提高执行个性化的性能。有关详细信息，请参阅[优化个性化](../../delivery/using/personalization-fields.md#optimizing-personalization)。
* **[!UICONTROL Start job in a detached process]** :通过此选项，您可以在单独的流程中开始投放分析。默认情况下，分析函数使用Adobe Campaign应用程序服务器进程(web nlserver)。 通过选择此选项，您可确保即使在分析服务器出现故障的事件下也能完成该操作。
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** :此选项会在分析阶段将SQL查询日志添加到投放日志。
* **[!UICONTROL Ignore personalization scripts during sending]** :此选项允许您绕过对HTML内容中的JavaScript指令的解释。它们将按原样显示在已交付的内容中。 这些指令与&#x200B;**&lt;%=**&#x200B;标记一起引入。

### 提高投放分析性能{#improving-delivery-analysis}

要加快投放准备，可在启动分析之前检查&#x200B;**[!UICONTROL Prepare the delivery parts in the database]**&#x200B;选项。

启用此选项后，将直接在投放库内执行分析准备，这可以显着加快数据库的准备。

目前，此选项仅在满足以下条件时才可用：
* 投放必须是电子邮件。 目前不支持其他渠道。
* 您不得使用中间源或外部路由，只能使用批量投放路由类型。 您可以检查&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中使用的路由。
* 不能目标来自外部文件的人口。 对于单个投放，单击&#x200B;**[!UICONTROL Email parameters]**&#x200B;中的&#x200B;**[!UICONTROL To]**&#x200B;链接并检查是否选择了&#x200B;**[!UICONTROL Defined in the database]**&#x200B;选项。 对于在工作流中使用的投放，请检查&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡中的收件人是否为&#x200B;**[!UICONTROL Specified by the inbound event(s)]**。
* 您必须使用PostgreSQL数据库。

### 配置分析优先级{#analysis-priority-}

当投放是活动的一部分时，**[!UICONTROL Advanced]**&#x200B;选项卡会优惠其他选项。 这样，您就可以在同一活动中组织投放的处理顺序。

在发送之前，将分析每个投放。 分析持续时间取决于投放提取文件。 文件的大小越大，分析越长，以下投放等待。

**[!UICONTROL Message preparation by the scheduler]**&#x200B;的选项可让您在活动工作流中排定投放分析的优先级。

![](assets/delivery_analysis_priority.png)

如果投放太大，最好为其分配低优先级，以避免降低其他工作流投放的分析。

>[!NOTE]
>
>要确保较大的投放分析不会减慢工作流的进度，您可以通过&#x200B;**[!UICONTROL Schedule execution for a time of low activity]**&#x200B;键入计划其执行。

## 发送校样{#sending-a-proof}

为了检测邮件配置中可能出现的错误，Adobe 强烈建议您设置投放验证周期。尽可能频繁地向测试收件人发送验证内容，确保内容已获得批准。每次进行变更时都应发送验证内容，以批准内容。

>[!NOTE]
>
>* [更改批准模式](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)中详细介绍了可用校验模式。
>* [定义特定验证目标](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)中介绍了验证目标的配置。
>



要发送验证，请按照以下步骤操作：

1. 确保已按照[定义特定验证目标](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)中的说明配置验证目标。
1. 单击投放向导顶栏上的&#x200B;**[!UICONTROL Send a proof]**。

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 开始消息分析。 请参阅[分析投放](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。
1. 您现在可以发送投放(请参阅[发送投放](../../delivery/using/steps-sending-the-delivery.md))。

   发送投放后，验证将显示在投放列表中，并自动创建和编号。 如果您希望访问其内容和属性，可以编辑它。 有关详细信息，请参见此 [ 页面](../../delivery/using/about-delivery-monitoring.md)。

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >如果为投放（HTML和文本）创建了多种格式，则可以选择要发送到窗口下半部分的验证收件人的消息格式。

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

您可能希望修改投放内容，因为接收验证的验证组进行了任何注释。 进行更改后，必须重新启动分析，然后发送其他验证。 每个新验证都会编号并登录到投放日志。

分析投放后，您可以视图通过日志的&#x200B;**[!UICONTROL Proofs]**&#x200B;子选项卡（**[!UICONTROL Audit]**&#x200B;选项卡）发送的各种验证。

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

在验证内容定稿之前，必须发送所需数量的投放。 之后，您可以将投放发送到主目标并关闭验证周期。

通过投放属性的&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡，可以定义验证的属性。 如果需要，您可以覆盖收件人排除规则。

![](assets/s_ncs_user_wizard_email01_145.png)

可以使用以下选项：

* 第一个选项可让您保留验证多次。
* 以下两个选项都允许保持收件人和地阻止列表址处于隔离。 有关[自定义排除设置](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings)中主目标的这些选项的说明。 与投放的目标不同，默认情况下，这些地址被排除，但默认情况下，它们会保留在验证的目标中。
* 通过&#x200B;**[!UICONTROL Keep the delivery code for the proof]**&#x200B;选项，可以为验证提供与其相关的投放所定义的相同的投放代码。 此代码在投放向导的第一步中指定。
* 默认情况下，验证主题以“验证#”为前缀，其中#是验证的编号。 可以在&#x200B;**[!UICONTROL Label prefix]**&#x200B;字段中更改此前缀。

## 类型的验证过程{#validation-process-with-typologies}

在发送任何消息之前，您应分析活动以批准其内容和配置。 在分析阶段应用的检查规则在&#x200B;**类型**&#x200B;中定义。 默认情况下，对于电子邮件，分析涵盖以下几点：

* 批准对象
* 批准URL和图像
* 批准URL标签
* 批准退订链接
* 检查验证大小
* 检查有效期
* 检查批次的计划

将在投放参数的&#x200B;**[!UICONTROL Typologies]**&#x200B;选项卡中选择要应用于每个投放的类型。

您可以通过&#x200B;**[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]**&#x200B;节点视图和编辑批准规则、其内容、其执行顺序以及其完整说明。

您可以从此节点创建新规则和定义新类型。 但是，这些任务是为了解JavaScript的专家用户保留的。

有关类型规则的详细信息，请参阅[关于活动类型](../../campaign/using/about-campaign-typologies.md)。

要编辑当前类型，请单击&#x200B;**[!UICONTROL Typology]**&#x200B;字段右侧的&#x200B;**[!UICONTROL Edit link]**&#x200B;图标。

![](assets/s_ncs_user_email_del_typo_tab.png)

**[!UICONTROL Rule]**&#x200B;选项卡提供要应用的类型规则的列表。 选择一个规则，然后单击&#x200B;**[!UICONTROL Detail...]**&#x200B;图标以视图其配置：

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 类型类型在销售压力管理框架中使用。如需详细信息，请参阅[此部分](../../campaign/using/about-marketing-resource-management.md)。

## 更改批准模式{#changing-the-approval-mode}

使用投放属性的&#x200B;**[!UICONTROL Analysis]**&#x200B;选项卡可以选择校验模式。 如果在分析期间生成警告(例如，如果某些字符在投放主题中突出显示等)，则可以配置投放以定义是否应仍执行该字符。 默认情况下，用户必须确认在分析阶段结束时发送消息：这是&#x200B;**manual**&#x200B;验证。

从相应字段的下拉列表中选择其他批准模式。

![](assets/s_ncs_user_email_del_validation_mode.png)

提供以下批准模式：

* **[!UICONTROL Manual]**:在分析阶段结束时，用户必须确认开始发送的投放。要执行此操作，请单击&#x200B;**[!UICONTROL Start]**&#x200B;按钮以启动投放。
* **[!UICONTROL Semi-automatic]**:如果分析阶段不生成警告消息，则自动开始发送。
* **[!UICONTROL Automatic]**:发送在分析阶段结束时自动开始，而不管其结果如何。
