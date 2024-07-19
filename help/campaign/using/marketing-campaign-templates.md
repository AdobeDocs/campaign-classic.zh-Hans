---
product: campaign
title: 营销活动模板
description: 营销活动模板
role: User
feature: Campaigns, Templates
exl-id: d272d4b9-f1b2-4fb2-9ed9-91a4aea7eca3
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 3%

---

# 创建和配置营销活动模板 {#campaign-templates}

所有营销活动都基于存储主要特性和功能的模板。 营销活动模板集中存储在&#x200B;**[!UICONTROL Resources > Templates > Campaign templates]**&#x200B;节点中。 默认模板作为标准模板提供。 虽然您可以使用所有可用模块（文档、任务、种子地址等）创建新营销活动，但提供的模块取决于您的权限和Adobe Campaign平台的配置。

![](assets/s_ncs_user_campaign_op_template_node.png)

>[!NOTE]
>
>单击主页上的&#x200B;**[!UICONTROL Explorer]**&#x200B;图标时，将显示树。

提供了内置模板以用于创建尚未定义特定配置的活动。您可以创建和配置活动模板，然后从这些模板创建活动。

![](assets/do-not-localize/how-to-video.png)有关营销活动创建的更多信息，请参阅[此视频](../../campaign/using/marketing-campaign-deliveries.md#create-email-video)。

## 创建活动模板 {#creating-or-duplicating-a-campaign-template}

要创建营销活动模板，请执行以下步骤：

1. 打开Campaign **资源管理器**。
1. 在&#x200B;**资源>模板>营销活动模板**&#x200B;中，单击模板列表上方工具栏中的&#x200B;**新建**。

   ![](assets/create_campaign_template_1.png)

1. 输入新活动模板的标签。
1. 单击&#x200B;**保存**&#x200B;并重新打开模板。
1. 在&#x200B;**编辑**&#x200B;选项卡中，根据需要输入&#x200B;**内部名称**&#x200B;和其他值。
1. 选择&#x200B;**高级营销活动设置**&#x200B;以向营销活动模板添加工作流。

   ![](assets/create_campaign_template_2.png)

1. 将&#x200B;**定位和工作流**&#x200B;值更改为&#x200B;**是**。

   ![](assets/create_campaign_template_3.png)

1. 在&#x200B;**定位和工作流**&#x200B;选项卡中，单击&#x200B;**添加工作流……**。

   ![](assets/create_campaign_template_4.png)

1. 完成&#x200B;**标签**&#x200B;字段并单击&#x200B;**确定**。
1. 根据您的要求创建工作流。
1. 单击&#x200B;**保存**。 您的模板现在已准备好在营销活动中使用。

您还可以&#x200B;**复制**&#x200B;默认模板以重复使用并调整其配置。

营销活动模板的各种选项卡和子选项卡允许您访问其设置，如[常规配置](#general-configuration)中所述。

![](assets/s_ncs_user_new_op_template_duplicate.png)

## 选择模块 {#select-modules}

通过&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;链接，您可以基于此模板为营销活动启用和禁用作业。 选择要在基于此模板创建的营销活动中启用的功能。

![](assets/s_ncs_user_op_template_tab1.3.png)

如果未选择某个功能，则将与流程相关的元素（菜单、图标、选项、选项卡、子选项卡等） 将不会显示在模板的界面中或基于此模板的营销活动中。 营销活动详细信息左侧的选项卡通常与模板中选择的流程一致。 例如，如果未选择&#x200B;**费用和目标**，则相应的&#x200B;**[!UICONTROL Budget]**&#x200B;选项卡将不会显示在基于此模板的营销活动中。

此外，配置窗口的快捷方式已添加到营销活动仪表板。 启用某个功能后，可通过直接链接从Campaign仪表板访问该功能。

例如，使用以下配置：

![](assets/s_ncs_user_op_template_tab1.4.png)

营销活动仪表板中显示以下链接（缺少&#x200B;**[!UICONTROL Add a task]**&#x200B;链接）：

![](assets/s_ncs_user_op_template_tab1.3ex.png)

并且只显示以下选项卡：

![](assets/s_ncs_user_op_template_tab1.4ex.png)

但是，对于此类配置：

![](assets/s_ncs_user_op_template_tab2.2ex.png)

将显示以下链接和选项卡：

![](assets/s_ncs_user_op_template_tab2.3ex.png)

## 模块类型 {#typology-of-enabled-modules}

* **对照组**

  选择此模块后，模板的高级设置以及基于此模板的营销活动会添加一个附加选项卡。 可以通过模板定义配置，也可以单独为每个营销活动定义配置。 在[本节](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)中了解有关控制组的更多信息。

  ![](assets/s_ncs_user_op_template_activate_1.png)

* **种子地址**

  选择此模块后，模板的高级设置以及基于此模板的营销活动会添加一个附加选项卡。 可以通过模板定义配置，也可以单独为每个营销活动定义配置。 在[本节](../../delivery/using/about-seed-addresses.md)中了解有关种子地址的更多信息。

  ![](assets/s_ncs_user_op_template_activate_2.png)

* **文档**

  选择此模块后，模板的&#x200B;**[!UICONTROL Edition]**&#x200B;选项卡中会添加一个附加选项卡，以及基于此模板的营销活动。 可从模板添加附加文档，或单独为每个营销活动添加附加文档。 在[本节](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)中了解关于文档的更多信息。

  ![](assets/s_ncs_user_op_template_activate_3.png)

* **大纲**

  选择此模块后，将在&#x200B;**[!UICONTROL Documents]**&#x200B;选项卡中添加一个&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子选项卡，以定义营销活动的投放大纲。 在[本节](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)中了解有关投放概要的更多信息。

  ![](assets/s_ncs_user_op_template_activate_4.png)

* **定位和工作流**

  选择&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;模块后，将添加一个选项卡，允许您基于此模板为营销活动创建一个或多个工作流。 还可以基于此模板为每个营销活动单独配置工作流。请参阅[本节](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)以了解有关营销活动工作流的详细信息。

  ![](assets/s_ncs_user_op_template_activate_5.png)

  启用此模块后，将向营销活动的高级设置添加一个选项卡，以定义流程执行顺序。

  ![](assets/s_ncs_user_op_template_activate_5a.png)

* **批准**

  如果选择&#x200B;**[!UICONTROL Approval]**，则可以选择要批准的进程以及负责批准的操作员。 在[此部分](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)中了解有关审批的更多信息。

  ![](assets/s_ncs_user_op_template_activate_5b.png)

  您可以选择是否通过模板高级设置部分的&#x200B;**[!UICONTROL Approvals]**&#x200B;选项卡启用流程审批。 对于选择批准的作业，邮件投放必须获得批准才能获得授权。

  必须将审阅人操作员或操作员组与每个启用的审批关联。

* **费用和目标**

  选择此模块后，模板和基于此模板的营销活动的详细信息中将添加&#x200B;**[!UICONTROL Budget]**&#x200B;选项卡，以便选择关联的预算。

  ![](assets/s_ncs_user_op_template_activate_7.png)

## 属性和执行 {#general-configuration}

### 模板属性 {#template-properties}

![](assets/s_ncs_user_op_new_template.png)

创建活动模板时，需要输入以下信息：

* 输入模板的&#x200B;**标签**：默认情况下，此标签将分配给通过此模板创建的所有营销活动。
* 从下拉列表中选择营销活动&#x200B;**性质**。 此列表中的可用值是保存在&#x200B;**[!UICONTROL natureOp]**&#x200B;枚举中的值。

  >[!NOTE]
  >
  >有关枚举的详细信息，请参阅[快速入门](../../platform/using/managing-enumerations.md)部分。

* 选择&#x200B;**类型的营销活动**：唯一、定期或定期。 默认情况下，营销活动模板适用于独特营销活动。 [此部分](../../campaign/using/setting-up-marketing-campaigns.md#recurring-and-periodic-campaigns)中详细介绍了循环和定期营销活动。
* 指定营销活动的持续时间，即营销活动将发生的天数。 基于此模板创建营销活动时，将自动填充营销活动开始和结束日期。

  如果促销活动是重复性的，则必须直接在模板中指定促销活动的开始和结束日期。

* 指定模板的&#x200B;**相关项目**：基于此模板的营销活动将链接到所选项目。

### 模板执行参数 {#template-execution-parameters}

通过&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;链接，可配置用于处理投放目标（控制组、种子地址等）的模板的高级选项 以及活动测量和工作流执行的配置。

![](assets/s_ncs_user_op_template_tab1.2.png)

## 跟踪活动执行{#campaign-reverse-scheduling}

您可以为营销活动创建计划并跟踪成绩，例如，为特定日期准备事件计划。 现在，您可以通过营销活动模板根据营销活动的结束日期计算任务的开始日期。

在任务配置框中，转到&#x200B;**[!UICONTROL Implementation schedule]**&#x200B;区域并选中&#x200B;**[!UICONTROL The start date is calculated based on the campaign end date]**&#x200B;框。 （在此，“开始日期”是任务开始日期）。 转到&#x200B;**[!UICONTROL Start]**&#x200B;字段并输入时间间隔：任务将在营销活动结束日期之前很长时间开始。 如果输入的时段长于将营销活动设置为最后的时段，则任务将在营销活动之前开始。

![](assets/mrm_task_in_template_start_date.png)

使用此模板创建营销活动时，将自动计算任务开始日期。 但是，您以后始终可以对其进行更改。
