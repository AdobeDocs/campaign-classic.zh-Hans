---
product: campaign
title: 创建营销活动
description: 了解如何创建和执行营销活动
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: a8fce21f-ffe3-4819-87ca-ac0ad9f21e41
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 6%

---

# 营销活动入门{#setting-up-marketing-campaigns}

![](../../assets/common.svg)

活动包括操作（投放）和流程（导入或提取文件）以及资源（营销文档、投放概要）。 它们用于营销活动。活动是项目的一部分，项目包含在活动计划中。

![](assets/do-not-localize/how-to-video.png) 了解如何在视频中创建营销计划、项目和 [营销策划](#video)

要创建营销活动，请执行以下操作：

1. 创建营销活动：发现营销活动及其特征：标签、类型、开始和结束日期、预算、关联的资源、经理和参与者。 [了解详情](#creating-a-campaign)。

1. 定义目标群体：创建包含定向查询的工作流。 [了解详情](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)。

1. 创建投放：选择渠道并定义要发送的内容。 [了解详情](../../campaign/using/marketing-campaign-deliveries.md#creating-deliveries)。

1. 批准投放。 [了解详情](../../campaign/using/marketing-campaign-approval.md)。

1. 监测投放. [了解详情](../../campaign/using/marketing-campaign-monitoring.md)。

1. 计划促销活动和关联成本。 [了解详情](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

完成这些步骤后，您可以开始投放（请参阅[此部分](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)），检查与投放相关的数据、流程和信息，并在必要时管理相关文档（请参阅[此部分](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)）。 您还可以跟踪营销活动和投放处理阶段的执行情况（请参阅[此部分](../../campaign/using/marketing-campaign-monitoring.md)）。

## 创建计划和方案层次结构 {#creating-plan-and-program-hierarchy}

要为营销计划和项目配置文件夹层次结构，请执行以下操作：

1. 单击主页上的&#x200B;**Explorer**&#x200B;图标。
1. 右键单击要在其中创建计划的文件夹。
1. 选择&#x200B;**添加新文件夹>营销活动管理>计划**。

   ![](assets/create_plan_1.png)

1. 重命名计划。
1. 右键单击新创建的计划，然后选择&#x200B;**属性……**。

   ![](assets/create_plan_2.png)

1. 在&#x200B;**General**&#x200B;选项卡中，修改&#x200B;**内部名称**&#x200B;以避免在资源包导出期间出现重复。
1. 单击&#x200B;**保存**。
1. 右键单击新创建的计划，然后选择&#x200B;**新建“程序”文件夹**。
1. 重复上述步骤以重命名新的程序文件夹及其内部名称。

## 创建营销策划 {#creating-a-campaign}

### 添加营销活动 {#adding-a-campaign}

您可以通过营销活动列表创建营销活动。 要显示此视图，请选择&#x200B;**[!UICONTROL Campaigns]**&#x200B;功能板中的&#x200B;**[!UICONTROL Campaigns]**&#x200B;菜单。

![](assets/s_ncs_user_add_an_op_from_list.png)

利用&#x200B;**[!UICONTROL Program]**&#x200B;字段，可选择营销活动要附加到的项目。 此信息是强制性的。

![](assets/s_ncs_user_new_op_wz_a.png)

营销策划也可以通过项目创建。 要执行此操作，请单击相关程序&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Add]**&#x200B;按钮。

![](assets/s_ncs_user_add_an_op.png)

当您通过项目的&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡创建营销活动时，营销活动会自动链接到相关项目。 在这种情况下，**[!UICONTROL Program]**&#x200B;字段处于隐藏状态。

在营销活动创建窗口中，选择营销活动模板并添加营销活动的名称和描述。 您还可以指定营销活动开始和结束日期。

单击&#x200B;**[!UICONTROL OK]**&#x200B;以创建营销活动。 它会添加到项目计划中。

![](assets/s_ncs_user_program_planning_with_op.png)

>[!NOTE]
>
>要过滤要显示的营销活动，请单击&#x200B;**[!UICONTROL Filter]**&#x200B;链接，然后选择要显示的营销活动状态。

![](assets/s_ncs_user_program_planning_filter.png)

### 编辑和配置营销活动 {#editing-and-configuring-a-campaign}

然后，您可以编辑刚刚创建的营销活动并定义其参数。

要打开和配置营销活动，请从计划中选择它，然后单击&#x200B;**[!UICONTROL Open]**。

![](assets/s_ncs_user_new_op_edit.png)

这会将您转到营销活动仪表板。

## 定期和定期促销活动 {#recurring-and-periodic-campaigns}

定期营销活动是基于特定模板的营销活动，其工作流配置为根据关联的计划执行。 因此，工作流将在营销活动中循环使用。 每次执行时都会重复定位，并跟踪各种进程和目标群体。 还可以在自动工作流创建期间通过覆盖期提前执行未来目标，以便使用目标估计启动模拟。

定期营销活动是根据模板的执行计划自动创建的营销活动。

### 创建定期营销活动 {#creating-a-recurring-campaign}

定期营销活动是根据定义要执行的工作流模板和执行计划的特定模板创建的。

#### 为定期促销活动创建模板 {#creating-the-campaign-template}

1. 创建&#x200B;**[!UICONTROL Recurring]**&#x200B;营销活动模板。

   >[!NOTE]
   >
   >建议复制默认模板，而不要创建空模板。

   ![](assets/s_ncs_user_op_template_recur_tab.png)

1. 输入模板的名称和营销活动的持续时间。

   ![](assets/s_ncs_user_op_template_recur_duplicate.png)

1. 对于此类型的营销活动，会添加&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡以创建模板执行计划。

在此选项卡中，根据此模板指定营销活动的计划执行日期。

![](assets/s_ncs_user_op_template_recur_planning.png)

执行计划的配置模式与工作流的&#x200B;**[!UICONTROL Scheduler]**&#x200B;对象一致。 如需详细信息，请参阅[此部分](../../workflow/using/architecture.md)。

>[!IMPORTANT]
>
>必须仔细执行执行计划配置，以避免数据库过载。 定期营销活动会根据指定的计划复制其模板的工作流。 过于频繁的工作流创建的实施会阻碍数据库的操作。

1. 在&#x200B;**[!UICONTROL Create in advance for]**&#x200B;字段中指定一个值，以便为指示的时段创建相应的工作流。
1. 使用定位参数和一个或多个通用投放，创建要在基于此模板的营销活动中使用的工作流模板。

   >[!NOTE]
   >
   >此工作流必须另存为定期工作流模板。 为此，请编辑工作流属性，并在&#x200B;**[!UICONTROL Execution]**&#x200B;选项卡中选择&#x200B;**[!UICONTROL Recurring workflow template]**&#x200B;选项。

   ![](assets/s_ncs_user_op_template_recur_wf_option.png)

#### 创建定期营销活动 {#create-the-recurring-campaign}

要创建定期营销活动并根据模板中定义的计划执行其工作流，请应用以下过程：

1. 根据定期促销活动模板创建新促销活动。
1. 填写工作流执行计划。

   ![](assets/s_ncs_user_op_recur_planning.png)

1. 营销活动计划允许您为每个行输入自动工作流创建或执行开始日期。

   对于每行，您可以添加以下其他选项：

   * **[!UICONTROL To be approved]** :允许您在工作流中强制提交批准请求。
   * **[!UICONTROL To be started]** :允许您在达到开始日期时启动工作流。

   利用&#x200B;**[!UICONTROL Create in advance for]**&#x200B;字段，可创建涵盖所输入时段的所有工作流。

   执行&#x200B;**[!UICONTROL Jobs on campaigns]**&#x200B;工作流时，将根据营销活动计划中定义的发生次数创建专用工作流。 因此，将为每个执行日期创建工作流。

1. 定期工作流是根据营销活动中存在的工作流模板自动创建的。 它们显示在营销活动的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中。

   ![](assets/s_ncs_user_op_recur_planning_wfs.png)

   定期工作流实例的标签由其模板标签和工作流编号组成，其中之间有#字符。

   从计划创建的工作流会自动与其关联到&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡的&#x200B;**[!UICONTROL Workflow]**&#x200B;列中。

   ![](assets/s_ncs_user_op_recur_planning_wfs_1.png)

   可从此选项卡编辑每个工作流。

   ![](assets/s_ncs_user_op_recur_planning_wf_edit.png)

   >[!NOTE]
   >
   >与工作流关联的计划行的开始日期可从工作流变量中使用以下语法：\
   >`$date(instance/vars/@startPlanningDate)`

### 创建定期营销活动 {#creating-a-periodic-campaign}

定期营销活动是基于特定模板的营销活动，允许您根据执行计划创建营销活动实例。 根据模板计划中定义的频率，根据定期促销活动模板自动创建促销活动实例。

#### 创建营销活动模板 {#creating-the-campaign-template-1}

1. 创建&#x200B;**[!UICONTROL Periodic]**&#x200B;营销活动模板，最好复制现有的营销活动模板。

   ![](assets/s_ncs_user_op_template_period_create.png)

1. 输入模板的属性。

   >[!NOTE]
   >
   >分配了模板的操作员需要拥有在选定项目中创建营销策划的适当权限。

1. 创建与此模板关联的工作流。 该模板将在模板创建的每个定期营销活动中重复显示。

   ![](assets/s_ncs_user_op_template_period_wf.png)

   >[!NOTE]
   >
   >此工作流是工作流模板。 无法从营销活动模板执行。

1. 完成其执行计划以作为定期促销活动模板：单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并定义开始和结束日期，或通过链接填写执行计划。

   ![](assets/s_ncs_user_op_template_period_planning_add.png)

   >[!IMPORTANT]
   >
   >定期营销活动模板可根据上面定义的计划创建新营销活动。 因此，必须仔细完成，以避免Adobe Campaign数据库过载。

1. 达到执行开始日期后，将自动创建匹配的营销活动。 它具有模板的所有特性。

   可以通过模板计划编辑每个营销活动。

   ![](assets/s_ncs_user_op_template_period_planning.png)

每个定期营销活动都包含相同的元素。 创建后，即可将其作为标准营销活动进行管理。

## 教程视频 {#video}

此视频演示如何创建营销计划、项目和营销策划。

>[!VIDEO](https://video.tv.adobe.com/v/35132?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign操作方法视频。
