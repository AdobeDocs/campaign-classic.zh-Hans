---
title: 验证投放
seo-title: 验证投放
description: 验证投放
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
source-git-commit: 7ffbbe95247f28115f7e46eb0e94f2612fb4ea93
workflow-type: tm+mt
source-wordcount: '1673'
ht-degree: 4%

---


# 验证投放 {#validating-the-delivery}

创建并配置投放后，您必须先验证该目标，然后再将其发送到主。

操作步骤：

1. **分析投放**: 通过此步骤，您可以准备要传送的消息。 请参阅 [分析投放](#analyzing-the-delivery)。

   本节将介绍在分析过程中应 [用的规则](#validation-process-with-typologies) 。 可用校验模式在更改批准 [模式部分中详细](#changing-the-approval-mode) 。

1. **发送验证**: 通过此步骤，您可以批准内容、URL、个性化字段等。 请参阅 [发送验证](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)[和定义特定验证目标](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)。

>[!IMPORTANT]
>
>必须在对消息内容进行每次修改后执行这两个步骤。

## 分析投放 {#analyzing-the-delivery}

分析是计算目标群和准备投放含量的阶段。 投放完成后，即可发送。

### 启动分析 {#launching-the-analysis}

1. 要启动投放分析，请单击 **[!UICONTROL Send]**。
1. 选择 **[!UICONTROL Deliver as soon as possible]**。

   ![](assets/s_ncs_user_email_del_send.png)

1. 单击 **[!UICONTROL Analyze]** 以手动启动分析。

   进度栏显示分析的进度。

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >在分析过程中使用的验证规则在带 [有类型的验证过程中进行](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) 说明。

1. 您可以随时单击以停止分析 **[!UICONTROL Stop]**。

   ![](assets/s_ncs_user_wizard_email01_16.png)

   准备阶段不发送任何消息。 因此，您可以开始或取消分析，而无风险。

   >[!IMPORTANT]
   >
   >运行时，分析冻结投放(或验证)。 对投放(或验证)的任何更改必须在适用前先经过其他分析。

1. 等到分析完成。

   分析完成后，窗口的上半部分将指示投放准备是否完成或是否发生任何错误。 将列出所有验证步骤、警告和错误。 彩色图标显示消息类型：
   * 蓝色图标表示有信息消息。
   * 黄色图标表示出现非关键处理错误。
   * 红色图标指示阻止发送投放的严重错误。

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 单击 **[!UICONTROL Close]** 以更正错误（如果有）。

1. 进行更改后，重新启动分析单击 **[!UICONTROL Analyze]**。

检查分析结果后，您将能够单击以 **[!UICONTROL Confirm delivery]** 将消息发送到指定目标。 通过确认消息可启动投放。

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>如果要 **[!UICONTROL Change the main delivery target]** 发送的消息数与您的配置不匹配，请单击链接。 这样，您就可以更改目标群的定义并重新开始分析。

### 分析参数 {#analysis-parameters}

通过 **[!UICONTROL Analysis]** 投放属性的选项卡，您可以定义一组与分析阶段消息准备相关的信息。

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

此选项卡允许访问以下选项：

* **[!UICONTROL Label and code of the delivery]** : 本节中的选项用于计算投放分析阶段中这些字段的值。 字 **[!UICONTROL Compute the execution folder during the delivery analysis]** 段计算将在投放阶段包含此分析操作的文件夹的名称。
* **[!UICONTROL Approval mode]** : 此字段允许您在完成投放后定义手动或自动分析。 这些校验模式显示在更 [改批准模式部分](#changing-the-approval-mode) 。
* **[!UICONTROL Prepare the delivery parts in the database]** : 此选项使您能够提高投放分析性能。 有关更多信息，请参阅[此章节](#improving-delivery-analysis)。
* **[!UICONTROL Prepare the personalization data with a workflow]** : 此选项允许您在自动工作流程中准备包含在投放中的个性化数据，这可以显着提高执行个性化的性能。 有关此方面的详细信息，请参 [阅优化个性化](../../delivery/using/personalization-fields.md#optimizing-personalization)。
* **[!UICONTROL Start job in a detached process]** : 通过此选项，您可以在单独的流程中开始投放分析。 默认情况下，分析函数使用Adobe Campaign应用程序服务器进程(web nlserver)。 通过选择此选项，即使在应用程序服务器故障事件，您也能确保完成分析。
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** : 此选项会在查询阶段将SQL投放日志添加到分析日志。
* **[!UICONTROL Ignore personalization scripts during sending]** : 通过此选项，可以绕过对HTML内容中的JavaScript指令的解释。 它们将按原样显示在已交付的内容中。 这些指令与&lt;%=标 **签一起引入** 。)

### 提高投放分析性能 {#improving-delivery-analysis}

要加快投放准备，您可以在启 **[!UICONTROL Prepare the delivery parts in the database]** 动分析之前选中该选项。

启用此选项后，将直接在投放库内执行分析准备，这可以显着加快。

当前，只有满足以下条件时，此选项才可用：
* 投放必须是电子邮件。 目前不支持其他渠道。
* 您不得使用中间源或外部路由，只能使用批量投放路由类型。 您可以检查在选项卡中 **[!UICONTROL General]** 使用的路由 **[!UICONTROL Delivery properties]**。
* 不能目标来自外部文件的人群。 对于单个投放，单击 **[!UICONTROL To]** 中的链接 **[!UICONTROL Email parameters]** 并检查选 **[!UICONTROL Defined in the database]** 项是否已选中。 对于在工作流中使用的投放，请检查收件人是否 **[!UICONTROL Specified by the inbound event(s)]** 在选项卡 **[!UICONTROL Delivery]** 中。
* 您必须使用PostgreSQL数据库。

### 配置分析优先级 {#analysis-priority-}

当投放是活动的一部分时，选项卡 **[!UICONTROL Advanced]** 会优惠其他选项。 这样，您就可以在同一活动中组织投放的处理顺序。

在发送之前，将分析每个投放。 分析持续时间取决于投放提取文件。 文件大小越大，分析越长，以下投放等待。

使用的选项，您 **[!UICONTROL Message preparation by the scheduler]** 可以在投放工作流中排定活动分析的优先级。

![](assets/delivery_analysis_priority.png)

如果投放太大，最好为其分配低优先级，以避免降低其他工作流投放的分析。

>[!NOTE]
>
>为确保较大的投放分析不会减慢工作流的进度，您可以通过滴答来计划其执行 **[!UICONTROL Schedule execution for a time of low activity]**。

## 发送校样{#sending-a-proof}

为了检测邮件配置中可能出现的错误，Adobe 强烈建议您设置投放验证周期。尽可能频繁地向测试收件人发送验证内容，确保内容已获得批准。每次进行变更时都应发送验证内容，以批准内容。

>[!NOTE]
>
>* 可用校验模式在更改审 [批模式中详细介绍](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)。
>* 验证目标的配置在定义特 [定验证目标中有说明](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)。

>



要发送验证，请按照以下步骤操作：

1. 确保已按照定义特定验证验证目标中 [的说明配置目标](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)。
1. 单 **[!UICONTROL Send a proof]** 击投放向导顶栏。

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 开始消息分析。 请参 [阅分析投放](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。
1. 您现在可以发送投放(请参 [阅发送投放](../../delivery/using/steps-sending-the-delivery.md))。

   发送投放后，验证将显示在投放列表中，并自动创建和编号。 如果您希望访问其内容和属性，可以编辑该内容。 有关详细信息，请参见此 [ 页面](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard)。

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >如果为投放（HTML和文本）创建了多种格式，则可以选择要发送到窗口下半部分的验证收件人的消息格式。

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

您可能希望修改投放内容，因为接收验证的验证组发表了任何评论。 进行更改后，必须重新启动分析，然后再发送其他验证。 每个新验证编号并登录投放日志。

分析投放后，您可以视图通过日志（选项卡） **[!UICONTROL Proofs]** 的子选项卡发送的各&#x200B;**[!UICONTROL Audit]** 种验证。

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

您必须发送所需数量的验证，直到投放内容最终确定。 之后，您可以将投放发送到主目标并关闭验证周期。

投放 **[!UICONTROL Advanced]** 属性的选项卡允许您定义验证的属性。 根据需要，您可以覆盖收件人排除规则。

![](assets/s_ncs_user_wizard_email01_145.png)

可以使用以下选项：

* 第一个选项允许您保留验证多次。
* 以下两个选项都允许您将阻止列表和地址的收件人保留为隔离。 请参阅自定义排除设置中主目标的这些 [选项说明](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings)。 与投放的目标不同，默认情况下排除这些地址，默认情况下保留这些地址作为验证的目标。
* 通 **[!UICONTROL Keep the delivery code for the proof]** 过该选项，您可以为验证提供与其相关的投放定义的相同的投放代码。 此代码在投放向导的第一步中指定。
* 默认情况下，验证的主题以“验证#”为前缀，其中#是验证的编号。 您可以在字段中更改此前 **[!UICONTROL Label prefix]** 缀。

## 含类型的验证流程 {#validation-process-with-typologies}

在发送任何消息之前，您应分析活动以批准其内容和配置。 The checking rules applied during the analysis phase are defined in a **typology**. 默认情况下，对于电子邮件，分析涵盖以下要点：

* 批准对象
* 批准URL和图像
* 批准URL标签
* 批准退订链接
* 检查验证大小
* 检查有效期
* 检查批次的计划

将在投放参数的选项卡中选择要应 **[!UICONTROL Typologies]** 用于每个投放的类型。

您可以通过节点视图和编辑批准规则、其内容、其执行顺序以及其完整 **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** 说明。

您可以从此节点创建新规则和定义新类型。 但是，这些任务是为了解JavaScript的专家用户保留的。

有关类型规则的详细信息，请参 [阅关于活动类型](../../campaign/using/about-campaign-typologies.md)。

要编辑当前排版，请单 **[!UICONTROL Edit link]** 击字段右侧的图 **[!UICONTROL Typology]** 标。

![](assets/s_ncs_user_email_del_typo_tab.png)

选 **[!UICONTROL Rule]** 项卡提供要应用的类型规则的列表。 选择规则，然后单击 **[!UICONTROL Detail...]** 图标以视图其配置：

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 类型类型在销售压力管理框架内使用。 有关更多信息，请参阅[此章节](../../campaign/using/about-marketing-resource-management.md)。

## 更改审批模式 {#changing-the-approval-mode}

投放 **[!UICONTROL Analysis]** 属性的选项卡允许您选择校验模式。 如果在分析期间生成警告(例如，如果某些字符在投放的主题中突出等)，您可以配置投放以定义是否应仍执行该字符。 默认情况下，用户必须确认在分析阶段结束时发送消息： 这是手 **动验** 证。

从相应字段的下拉列表中选择其他批准模式。

![](assets/s_ncs_user_email_del_validation_mode.png)

可以使用以下批准模式：

* **[!UICONTROL Manual]**: 在分析阶段结束时，用户必须确认投放以发送开始。 为此，请单击 **[!UICONTROL Start]** 按钮以启动投放。
* **[!UICONTROL Semi-automatic]**: 如果分析阶段不生成警告消息，则自动开始发送。
* **[!UICONTROL Automatic]**: 发送在分析阶段结束时自动开始，而不管其结果如何。
