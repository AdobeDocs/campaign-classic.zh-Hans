---
solution: Campaign Classic
product: campaign
title: 营销活动模板
description: 营销活动模板
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 0%

---


# 创建和配置活动模板{#campaign-templates}

所有营销活动均基于存储主要特征和功能的模板。 活动模板集中在&#x200B;**[!UICONTROL Resources > Templates > Campaign templates]**&#x200B;节点中。 默认模板将作为标准提供。 它允许您使用所有可用模块(文档、任务、种子地址等)创建新活动，但提供的模块取决于您的权限和Adobe Campaign平台的配置。

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>单击主页上的&#x200B;**[!UICONTROL Explorer]**&#x200B;图标时将显示树。

提供内置模板以创建尚未定义特定配置的活动。 您可以创建和配置活动模板，然后从这些模板创建活动。

![](assets/do-not-localize/how-to-video.png) 有关活动创建的详细信息，请参 [阅此视频](../../campaign/using/marketing-campaign-deliveries.md#create-email-video)。

## 创建活动模板{#creating-or-duplicating-a-campaign-template}

要创建活动模板，请按照以下步骤操作：

1. 打开活动&#x200B;**Explorer**。
1. 在&#x200B;**“资源”>“模板”>“活动模板”**&#x200B;中，单击模板列表上方工具栏中的&#x200B;**“新建”**。

   ![](assets/create_campaign_template_1.png)

1. 输入新活动模板的标签。
1. 单击&#x200B;**保存**&#x200B;并重新打开模板。
1. 在&#x200B;**编辑**&#x200B;选项卡中，根据需要输入&#x200B;**内部名称**&#x200B;和其他值。
1. 选择&#x200B;**高级活动设置**&#x200B;以向活动模板添加工作流。

   ![](assets/create_campaign_template_2.png)

1. 将&#x200B;**定位和工作流**&#x200B;值更改为&#x200B;**是**。

   ![](assets/create_campaign_template_3.png)

1. 在&#x200B;**定位和工作流**&#x200B;选项卡中，单击&#x200B;**添加工作流……**。

   ![](assets/create_campaign_template_4.png)

1. 完成&#x200B;**Label**&#x200B;字段，然后单击&#x200B;**确定**。
1. 根据您的要求创建您的工作流。
1. 单击&#x200B;**保存**。您的模板现已准备好在活动中使用。

您还可以&#x200B;**重复**&#x200B;默认模板以重复使用和调整其配置。

该活动模板的各种选项卡和子选项卡允许您访问其设置，如[常规配置](#general-configuration)中所述。

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 选择模块{#select-modules}

通过&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;链接，可以启用和禁用基于此模板的活动的作业。 选择要在基于此模板创建的活动中启用的功能。

![](assets/s_ncs_user_op_template_tab1.3.png)

如果未选择某个功能，则与该过程相关的元素（菜单、图标、选项、选项卡、子选项卡等） 将不会显示在模板的界面中或基于此模板的活动中。 活动详细信息左侧的选项卡通常与在模板中选择的进程一致。 例如，如果未选择&#x200B;**费用和目标**，则基于此模板的活动中将不显示相应的&#x200B;**[!UICONTROL Budget]**&#x200B;选项卡。

此外，配置窗口的快捷键会添加到活动仪表板。 启用某个功能后，直接链接将允许从活动仪表板访问该功能。

例如，使用以下配置：

![](assets/s_ncs_user_op_template_tab1.4.png)

活动仪表板中显示以下链接（缺少&#x200B;**[!UICONTROL Add a task]**&#x200B;链接）：

![](assets/s_ncs_user_op_template_tab1.3ex.png)

将只显示以下选项卡：

![](assets/s_ncs_user_op_template_tab1.4ex.png)

但是，使用此类配置：

![](assets/s_ncs_user_op_template_tab2.2ex.png)

此时将显示以下链接和选项卡：

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## 模块{#typology-of-enabled-modules}的类型

* **对照组**

   选择此模块后，将在模板的高级设置和基于此模板的活动中添加一个附加选项卡。 配置可通过模板进行定义，也可针对每个活动单独进行定义。 了解有关[本节](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)中对照组的更多信息。

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **种子地址**

   选择此模块后，将在模板的高级设置和基于此模板的活动中添加一个附加选项卡。 配置可通过模板进行定义，也可针对每个活动单独进行定义。 了解有关[本节](../../delivery/using/about-seed-addresses.md)中种子地址的更多信息。

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **文档**

   选择此模块后，将在模板的&#x200B;**[!UICONTROL Edition]**&#x200B;选项卡和基于此模板的活动中添加其他选项卡。 附加的文档可以从模板中添加，也可以为每个活动单独添加。 了解有关[本节](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)中文档的更多信息。

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **大纲**

   选择此模块后，**[!UICONTROL Documents]**&#x200B;选项卡中会添加一个&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子选项卡，以定义活动的投放概要。 了解有关[本节](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)中投放概要的更多信息。

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **定位和工作流**

   当您选择&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;模块时，会添加一个选项卡，以便您基于此模板为活动创建一个或多个工作流。 还可以基于此模板为每个活动单独配置工作流。了解有关[此部分](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)中活动工作流的更多信息。

   ![](assets/s_ncs_user_op_template_activate_5.png)

   启用此模块后，将在活动的高级设置中添加一个选项卡以定义进程执行序列。

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **批准**

   如果选择&#x200B;**[!UICONTROL Approval]**，则可以选择要批准的进程以及负责批准的运算符。 了解有关[本节](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)中批准的更多信息。

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   您可以通过模板高级设置部分的&#x200B;**[!UICONTROL Approvals]**&#x200B;选项卡选择是否启用流程批准。 必须批准已选择批准的作业，才能对邮件投放进行授权。

   必须将审阅人操作员或操作员组关联到每个已启用的批准。

* **费用和目标**

   选择此模块后，将向基于此模板的模板和活动的详细信息中添加&#x200B;**[!UICONTROL Budget]**&#x200B;选项卡，以便选择关联的预算。

   ![](assets/s_ncs_user_op_template_activate_7.png)

## 属性和执行{#general-configuration}

### 模板属性{#template-properties}

![](assets/s_ncs_user_op_new_template.png)

创建活动模板时，需要输入以下信息：

* 输入模板的&#x200B;**标签**:默认情况下，此标签将分配给通过此模板创建的所有活动。
* 从下拉活动中选择列表&#x200B;**nature**。 此列表中可用的值是保存在&#x200B;**[!UICONTROL natureOp]**&#x200B;明细列表中的值。

   >[!NOTE]
   >
   >有关明细列表的详细信息，请参阅[入门](../../platform/using/managing-enumerations.md)部分。

* 选择&#x200B;**类型的活动**:唯一、循环或周期。 默认情况下，活动模板应用于唯一活动。 循环和周期活动详见[本节](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns)。
* 指定活动的持续时间，即活动将发生的天数。 创建基于此模板的活动时，将自动填充活动开始和结束日期。

   如果活动是重复的，则必须直接在模板中指定活动开始和结束日期。

* 指定模板的&#x200B;**相关项目**:基于此模板的活动将链接到所选项目。

### 模板执行参数{#template-execution-parameters}

**[!UICONTROL Advanced campaign settings...]**&#x200B;链接允许您配置模板的高级选项以处理投放目标(对照组、种子地址等) 以及活动测量和工作流执行的配置。

![](assets/s_ncs_user_op_template_tab1.2.png)

## 跟踪活动执行{#campaign-reverse-scheduling}

您可以为活动创建计划并跟踪成绩，例如为特定日期准备事件计划。 活动模板现在允许您根据任务的结束日期计算开始的活动日期。

在“任务配置”框中，转到&#x200B;**[!UICONTROL Implementation schedule]**&#x200B;区域并选中&#x200B;**[!UICONTROL The start date is calculated based on the campaign end date]**&#x200B;框。 (此处，“开始日期”是任务开始日期)。 转到&#x200B;**[!UICONTROL Start]**&#x200B;字段并输入间隔：任务将在活动结束日期之前开始此时间。 如果输入的期间长于活动设置为最后，任务将在活动之前开始。

![](assets/mrm_task_in_template_start_date.png)

使用此模板创建活动时，将自动计算任务开始日期。 但是，您始终可以在以后更改它。
