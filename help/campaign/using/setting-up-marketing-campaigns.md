---
title: 设置营销活动
seo-title: 设置营销活动
description: 设置营销活动
seo-description: null
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 设置营销活动{#setting-up-marketing-campaigns}

营销活动包括操作（交付）和流程（导入或提取文件）以及资源（营销文档、交付大纲）。 它们用于营销活动。 营销活动是计划的一部分，并且计划包含在营销活动计划中。

要创建营销活动，请执行以下操作：

1. 创建营销活动：发现营销活动及其特点：标签、类型、开始日期和结束日期、预算、关联资源、经理和参加者。

   请参阅 [创建营销活动](#creating-a-campaign)。

1. 定义目标人群：创建具有定位查询的工作流。

   请参 [阅选择目标人群](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)。

1. 创建提交：选择渠道并定义要发送的内容。

   请参阅 [创建提交](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries)。

1. 批准提交。

   请参阅“ [批准”流程](../../campaign/using/marketing-campaign-approval.md#approval-process)。

1. 监控交付。

   请参阅 [监视](../../campaign/using/marketing-campaign-monitoring.md)。

1. 计划营销活动和关联成本。

   请参阅 [创建服务提供商及其成本结构](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

完成这些步骤后，您可以开始发送(请参阅 [Starting a delivery](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery))，检查与发送相关的数据、流程和信息，并在必要时管理相关文档(请参阅 [Managing associated documents](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents))。 您还可以跟踪营销活动和交付的处理阶段的执行情况(请参阅 [跟踪](../../campaign/using/marketing-campaign-monitoring.md))。

## 创建计划和程序层次结构 {#creating-plan-and-program-hierarchy}

要为营销计划和计划配置文件夹层次结构，请执行以下操作：

1. 单击主 **页上的** “资源管理器”图标。
1. 右键单击要在其中创建计划的文件夹。
1. 选择 **添加新文件夹>营销活动管理>计划**。

   ![](assets/create_plan_1.png)

1. 重命名计划。
1. **右键单击新创建的计划，然后选择**&#x200B;属性…….

   ![](assets/create_plan_2.png)

1. 在“常 **规** ”选项卡中，修改“ **内部名称** ”以避免在包导出过程中出现重复。
1. 单击“ **保存**”。
1. 右键单击新创建的计划，然后选择 **创建新的“程序”文件夹**。
1. 重复上述步骤以重命名新的程序文件夹及其内部名称。

## 创建营销活动 {#creating-a-campaign}

### 添加营销活动 {#adding-a-campaign}

您可以通过营销活动列表创建营销活动。 要显示此视图，请选择功 **[!UICONTROL Campaigns]** 能板中的菜 **[!UICONTROL Campaigns]** 单。

![](assets/s_ncs_user_add_an_op_from_list.png)

该字 **[!UICONTROL Program]** 段允许您选择要将营销活动附加到的计划。 此信息是强制性的。

![](assets/s_ncs_user_new_op_wz_a.png)

还可以通过计划创建营销活动。 为此，请单击相 **[!UICONTROL Add]** 关程序选项卡 **[!UICONTROL Schedule]** 中的按钮。

![](assets/s_ncs_user_add_an_op.png)

当您通过程序选项卡创 **[!UICONTROL Schedule]** 建营销活动时，该营销活动会自动链接到相关的程序。 在这 **[!UICONTROL Program]** 种情况下，该字段是隐藏的。

在营销活动创建窗口中，选择营销活动模板并添加营销活动的名称和说明。 您还可以指定营销活动的开始日期和结束日期。

单击 **[!UICONTROL OK]** 以创建营销活动。 它被添加到计划计划中。

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>要筛选要显示的营销活动，请单击链 **[!UICONTROL Filter]** 接，然后选择要显示的营销活动状态。

![](assets/s_ncs_user_program_planning_filter.png)

### 编辑和配置营销活动 {#editing-and-configuring-a-campaign}

然后，您可以编辑刚刚创建的营销活动并定义其参数。

要打开和配置营销活动，请从计划中选择该营销活动，然后单击 **[!UICONTROL Open]**。

![](assets/s_ncs_user_new_op_edit.png)

此操作将带您进入营销活动仪表板。

## 定期和定期营销活动 {#recurring-and-periodic-campaigns}

循环营销活动是基于特定模板的营销活动，其工作流配置为根据关联的计划执行。 因此，工作流将在营销活动中重复出现。 每次执行时都会重复定位，并跟踪各种进程和目标群体。 还可以通过自动工作流创建期间的覆盖期提前执行未来目标，以便使用目标估计启动模拟。

定期营销活动是根据模板的执行计划自动创建的营销活动。

### 创建循环营销活动 {#creating-a-recurring-campaign}

定期营销活动是从特定模板创建的，该模板定义要执行的工作流模板和执行计划。

#### 为重复营销活动创建模板 {#creating-the-campaign-template}

1. 创建营销 **[!UICONTROL Recurring]** 活动模板。

   >[!NOTE]
   >
   >建议您复制默认模板，而不是创建空模板。

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. 输入模板的名称和营销活动的持续时间。

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. 对于此类型的营销活动，会添 **[!UICONTROL Schedule]** 加一个选项卡以创建模板执行计划。

在此选项卡中，指定基于此模板的营销活动的计划执行日期。

![](assets/s_ncs_user_op_template_recur_planning.png)

您可以使用计划创建向导自动填写所有执行日期。 为此，请单击位于 **[!UICONTROL Complete the execution schedule...]** 表上方的链接。

![](assets/s_ncs_user_op_template_recur_planning_wz.png)

执行调度的配置模式与工作流 **[!UICONTROL Scheduler]** 的对象一致。 如需详细信息，请参阅[此部分](../../workflow/using/executing-a-workflow.md#architecture)。

>[!CAUTION]
>
>必须仔细执行执行执行计划配置，以避免数据库过载。 重复的营销活动会根据指定的计划复制模板的工作流。 过度频繁的工作流创建的实现会阻碍数据库的操作。

1. 在字段中指定 **[!UICONTROL Create in advance for]** 一个值，以便为指示的期间创建相应的工作流。
1. 根据此模板创建要在营销活动中使用的工作流模板，其中包含定位参数和一个或多个通用提交。

   >[!CAUTION]
   >
   >此工作流必须另存为循环工作流模板。 为此，请编辑工作流属性，并在选 **[!UICONTROL Recurring workflow template]** 项卡中选择 **[!UICONTROL Execution]** 选项。

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### 创建重复营销活动 {#create-the-recurring-campaign}

要创建循环营销活动并根据模板中定义的计划执行其工作流，请应用以下过程：

1. 根据循环型营销活动模板创建新营销活动。
1. 填写工作流执行计划。

   ![](assets/s_ncs_user_op_recur_planning.png)

1. 市场活动计划允许您为每个行输入自动创建工作流或执行起始日期。

   对于每行，您可以添加以下附加选项：

   * **[!UICONTROL To be approved]** :允许您在工作流中强制提交批准请求
   * **[!UICONTROL To be started]** :允许您在到达开始日期后启动工作流。
   通过 **[!UICONTROL Create in advance for]** 该字段，您可以创建涵盖所输入期间的所有工作流。

   在执行该工作流 **[!UICONTROL Jobs on campaigns]** 时，将根据在营销活动计划中定义的发生次数创建专用工作流。 因此，将为每个执行日期创建一个工作流。

1. 循环工作流是从营销活动中提供的工作流模板自动创建的。 它们可从营销活动的 **[!UICONTROL Targeting and workflows]** 选项卡中看到。

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   循环工作流实例的标签由其模板标签和工作流编号组成，其中间有#字符。

   从计划创建的工作流会自动关联到选项卡 **[!UICONTROL Workflow]** 的列中的该工 **[!UICONTROL Schedule]** 作流。

   ![](assets/s_ncs_user_op_recur_planning_wfs_1.png)

   每个工作流都可以通过此选项卡进行编辑。

   ![](assets/s_ncs_user_op_recur_planning_wf_edit.png)

   >[!NOTE]
   >
   >与工作流关联的计划行的开始日期可以从工作流的变量中使用以下语法：\
   >`$date(instance/vars/@startPlanningDate)`

### 创建定期营销活动 {#creating-a-periodic-campaign}

定期营销活动是基于特定模板的营销活动，允许您根据执行计划创建营销活动实例。 系列活动实例是根据定期系列活动模板自动创建的，具体取决于模板计划中定义的频率。

#### 创建营销活动模板 {#creating-the-campaign-template-1}

1. 创建营销 **[!UICONTROL Periodic]** 活动模板，最好复制现有的营销活动模板。

   ![](assets/s_ncs_user_op_template_period_create.png)

1. 输入模板的属性。

   >[!CAUTION]
   >
   >分配了模板的操作员需要拥有相应的权限才能在选定计划中创建营销活动。

1. 创建与此模板关联的工作流。 模板创建的每个定期营销活动中都会重复该模板。

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >此工作流是工作流模板。 无法从营销活动模板中执行它。

1. 完成循环营销活动模板的执行计划：单击 **[!UICONTROL Add]** 按钮并定义开始和结束日期，或通过链接填写执行计划。

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!CAUTION]
   >
   >定期营销活动模板会根据上述定义的计划创建新营销活动。 因此，必须仔细完成它，以避免Adobe Campaign数据库过载。

1. 到达执行开始日期后，将自动创建匹配的营销活动。 它具有其模板的所有特性。

   每个营销活动都可以通过模板计划进行编辑。

   ![](assets/s_ncs_user_op_template_period_planning.png)

每个周期性营销活动都包含相同的元素。 创建后，它将作为标准营销活动进行管理。
