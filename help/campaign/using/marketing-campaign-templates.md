---
product: campaign
title: 营销活动模板
description: 营销活动模板
feature: Campaigns, Templates
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 3%

---

# 创建和配置营销活动模板 {#campaign-templates}

![](../../assets/v7-only.svg)

所有营销活动都基于存储主要特征和功能的模板。 营销活动模板集中在 **[!UICONTROL Resources > Templates > Campaign templates]** 节点。 默认模板将作为标准模板提供。 它允许您使用所有可用模块（文档、任务、种子地址等）创建新营销活动，但提供的模块取决于您的权限和Adobe Campaign平台的配置。

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>在单击 **[!UICONTROL Explorer]** 图标。

提供了内置模板以用于创建尚未定义特定配置的活动。您可以创建和配置活动模板，然后从这些模板创建活动。

![](assets/do-not-localize/how-to-video.png) 有关营销活动创建的更多信息，请参阅 [此视频](../../campaign/using/marketing-campaign-deliveries.md#create-email-video).

## 创建营销活动模板 {#creating-or-duplicating-a-campaign-template}

要创建营销活动模板，请执行以下步骤：

1. 打开营销活动 **资源管理器**.
1. 在 **资源>模板>营销活动模板**，单击 **新建** 在工具栏的模板列表上方。

   ![](assets/create_campaign_template_1.png)

1. 输入新营销活动模板的标签。
1. 单击 **保存** 然后重新打开您的模板。
1. 在 **编辑** ，输入 **内部名称** 和其他值（如果需要）。
1. 选择 **高级营销活动设置** 向营销活动模板添加工作流。

   ![](assets/create_campaign_template_2.png)

1. 更改 **定位和工作流** 值 **是**.

   ![](assets/create_campaign_template_3.png)

1. 在 **定位和工作流** ，单击 **添加工作流……**.

   ![](assets/create_campaign_template_4.png)

1. 完成 **标签** 字段，单击 **确定**.
1. 根据您的要求创建工作流。
1. 单击&#x200B;**保存**。您的模板现已准备就绪，可在营销活动中使用。

您还可以 **重复** 用于重复使用和调整其配置的默认模板。

利用营销活动模板的各种选项卡和子选项卡，可访问其设置，如 [常规配置](#general-configuration).

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 选择模块 {#select-modules}

的 **[!UICONTROL Advanced campaign settings...]** 利用链接，可根据此模板为营销活动启用和禁用作业。 选择要在基于此模板创建的营销活动中启用的功能。

![](assets/s_ncs_user_op_template_tab1.3.png)

如果未选择某项功能，则与该过程相关的元素（菜单、图标、选项、选项卡、子选项卡等） 不会显示在模板的界面中或基于此模板的营销活动中。 营销活动详细信息左侧的选项卡通常与模板中选择的流程一致。 例如，如果 **费用和目标** 未选择，则对应 **[!UICONTROL Budget]** 选项卡不会显示在基于此模板的营销活动中。

此外，配置窗口的快捷方式也添加到营销活动仪表板。 启用功能后，通过直接链接可从营销活动仪表板访问该功能。

例如，使用以下配置：

![](assets/s_ncs_user_op_template_tab1.4.png)

营销活动仪表板( **[!UICONTROL Add a task]** 链接缺失):

![](assets/s_ncs_user_op_template_tab1.3ex.png)

此时将仅显示以下选项卡：

![](assets/s_ncs_user_op_template_tab1.4ex.png)

但是，使用此类配置：

![](assets/s_ncs_user_op_template_tab2.2ex.png)

将显示以下链接和选项卡：

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## 模块类型 {#typology-of-enabled-modules}

* **控制组**

   选择此模块后，会在模板的高级设置和基于此模板的营销活动中添加一个额外的选项卡。 配置可通过模板进行定义，也可单独为每个营销活动定义。 在 [此部分](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

   ![](assets/s_ncs_user_op_template_activate_1.png)

* **种子地址**

   选择此模块后，会在模板的高级设置和基于此模板的营销活动中添加一个额外的选项卡。 配置可通过模板进行定义，也可单独为每个营销活动定义。 详细了解种子地址(位于 [此部分](../../delivery/using/about-seed-addresses.md).

   ![](assets/s_ncs_user_op_template_activate_2.png)

* **文档**

   选择此模块后，会向 **[!UICONTROL Edition]** 选项卡，以及基于此模板的营销活动。 可以从模板添加附加的文档，也可以单独为每个营销活动添加附加的文档。 了解有关 [此部分](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).

   ![](assets/s_ncs_user_op_template_activate_3.png)

* **大纲**

   选择此模块后， **[!UICONTROL Delivery outlines]** 子选项卡 **[!UICONTROL Documents]** 选项卡，以定义营销活动的投放大纲。 了解有关 [此部分](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

   ![](assets/s_ncs_user_op_template_activate_4.png)

* **定位和工作流**

   当您选择 **[!UICONTROL Targeting and workflows]** 模块中，添加了一个选项卡，用于根据此模板为营销活动创建一个或多个工作流。 还可以根据此模板为每个营销活动单独配置工作流。有关 [此部分](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow).

   ![](assets/s_ncs_user_op_template_activate_5.png)

   启用此模块后，会在营销活动的高级设置中添加一个选项卡，以定义流程执行顺序。

   ![](assets/s_ncs_user_op_template_activate_5a.png)

* **批准**

   如果您选择 **[!UICONTROL Approval]**，则可以选择要批准的流程以及负责批准的操作员。 了解有关批准的更多信息，请参阅 [此部分](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

   ![](assets/s_ncs_user_op_template_activate_5b.png)

   您可以选择是否通过 **[!UICONTROL Approvals]** “模板高级设置”部分的选项卡。 必须批准已选择批准的作业才能授权邮件投放。

   必须将审阅人操作员或操作员组关联到每个已启用的批准。

* **费用和目标**

   选择此模块后， **[!UICONTROL Budget]** 选项卡会添加到模板和基于此模板的营销活动的详细信息中，以便选择关联的预算。

   ![](assets/s_ncs_user_op_template_activate_7.png)

## 属性和执行 {#general-configuration}

### 模板属性 {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

创建营销活动模板时，需要输入以下信息：

* 输入 **标签** 模板：默认情况下，此标签将分配给通过此模板创建的所有营销活动。
* 选择营销活动 **自然** 从下拉列表中。 此列表中可用的值是 **[!UICONTROL natureOp]** 枚举。

   >[!NOTE]
   >
   >有关枚举的更多信息，请参阅 [快速入门](../../platform/using/managing-enumerations.md) 中。

* 选择 **营销活动类型**:唯一、循环或定期。 默认情况下，促销活动模板适用于独特的促销活动。 定期和定期营销活动详见 [此部分](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns).
* 指定营销活动的持续时间，即营销活动将发生的天数。 创建基于此模板的营销活动时，将自动填充营销活动开始和结束日期。

   如果营销活动是重复的，则必须直接在模板中指定营销活动开始和结束日期。

* 指定 **相关计划** 模板：基于此模板的营销活动将链接到所选项目。

### 模板执行参数 {#template-execution-parameters}

的 **[!UICONTROL Advanced campaign settings...]** 链接允许您配置模板的高级选项以处理投放目标（控制组、种子地址等） 以及营销活动测量和工作流执行的配置。

![](assets/s_ncs_user_op_template_tab1.2.png)

## 跟踪促销活动执行{#campaign-reverse-scheduling}

您可以为营销活动创建计划并跟踪成绩，例如为特定日期准备事件计划。 营销活动模板现在允许您根据营销活动的结束日期计算任务的开始日期。

在任务配置框中，转到 **[!UICONTROL Implementation schedule]** 区域并检查 **[!UICONTROL The start date is calculated based on the campaign end date]** 框中。 （此处，“开始日期”是任务开始日期）。 转到 **[!UICONTROL Start]** 字段，然后输入间隔：该任务将在营销活动结束日期之前很久开始。 如果输入的时段长于营销活动设置为最后的时段，则任务将在营销活动之前开始。

![](assets/mrm_task_in_template_start_date.png)

使用此模板创建营销活动时，将自动计算任务开始日期。 但是，您随时可以在以后进行更改。
