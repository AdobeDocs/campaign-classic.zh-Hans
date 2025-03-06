---
product: campaign
title: 构建工作流
description: 了解如何构建工作流
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 8ba20ccd-b03f-4c4f-87c1-a21e80d8e4be
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 4%

---

# 构建工作流 {#building-a-workflow}



此部分详细介绍在Campaign中构建工作流的主要原则和最佳实践。

* 创建工作流，请参阅[创建新工作流](#creating-a-new-workflow)
* 设计工作流图，请参阅[添加和链接活动](#adding-and-linking-activities)
* 访问活动的参数和属性，请参阅[配置活动](#configuring-activities)
* 设计定位工作流，请参阅[定位工作流](#targeting-workflows)
* 使用工作流执行活动，请参阅[活动工作流](#campaign-workflows)
* 访问和创建技术工作流，请参阅[技术工作流](#technical-workflows)
* 使用模板创建工作流，请参阅[工作流模板](#workflow-templates)

## 创建新工作流 {#creating-a-new-workflow}

从&#x200B;**[!UICONTROL Explorer]**&#x200B;访问工作流文件夹。 默认情况下，您可以使用&#x200B;**[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**。

单击位于工作流列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮。

![](assets/create_a_wf_icon.png)

或者，您也可以使用工作流概述（**[!UICONTROL Monitoring]** > **[!UICONTROL Workflow]**&#x200B;链接）中的&#x200B;**[!UICONTROL Create]**&#x200B;按钮。

![](assets/create_a_wf.png)

输入标签并单击&#x200B;**[!UICONTROL Save]**。

>[!NOTE]
>
>修改工作流活动的内部名称或工作流本身时，请确保在关闭工作流之前先保存该工作流，以便正确考虑新的内部名称。

## 添加和链接活动 {#adding-and-linking-activities}

您现在必须定义各种活动，并在图表中将它们链接在一起。 在配置的此阶段，我们可以看到图标签和工作流状态（正在编辑）。 窗口的下部仅用于编辑图。 它包含一个工具栏、活动面板（位于左侧）以及图表本身（位于右侧）。

![](assets/new-workflow-2.png)

>[!NOTE]
>
>如果未显示面板，请单击工具栏上的第一个按钮以显示面板。

活动按类别分组到了面板的不同选项卡中。 可用选项卡和活动会因工作流类型（技术、定位或活动工作流）而异。

* 第一个选项卡包含定位和数据操作活动。 [定位活动](about-targeting-activities.md)中详细介绍了这些活动。
* 第二个选项卡包含计划活动，主要用于协调其他活动。 在[流控制活动](about-flow-control-activities.md)中详细介绍了这些活动。
* 第三个选项卡包含可在工作流中使用的工具和操作。 [操作活动](about-action-activities.md)中详细介绍了这些活动。
* 第四个选项卡包含依赖于给定事件的活动，如接收电子邮件或文件到达服务器。 [事件活动](about-event-activities.md)中详细介绍了这些活动。

创建图

1. 通过在面板中选择某个活动并使用拖放操作将其移至图表中来添加该活动。

   在关系图上添加&#x200B;**开始**&#x200B;活动，然后添加&#x200B;**投放**&#x200B;活动。

   ![](assets/new-workflow-3.png)

1. 通过将&#x200B;**开始**&#x200B;活动过渡拖放到&#x200B;**投放**&#x200B;活动上，将两个活动链接在一起。

   ![](assets/new-workflow-4.png)

   通过将新活动放在过渡的末尾，您可以自动将活动链接到上一个活动。

1. 添加所需的活动并将它们链接在一起，如下图所示。

   ![](assets/new-workflow-5.png)

>[!CAUTION]
>
>您可以在同一工作流中复制并粘贴活动。 但是，我们不建议跨不同的工作流复制并粘贴活动。 某些附加到活动（如投放和计划程序）的设置可能会导致执行目标工作流时出现冲突和错误。 为此，我们建议您&#x200B;**复制**&#x200B;工作流。 有关详细信息，请参阅[重复的工作流](#duplicating-workflows)。

您可以使用以下元素更改图表的显示和布局：

* **使用工具栏**

  通过图编辑工具栏，您可以访问工作流的布局和执行功能。

  ![](assets/s_user_segmentation_wizard_10.png)

  这使您可以调整编辑工具的布局：面板的显示以及图形对象的概述、大小和对齐方式。

  ![](assets/s_user_segmentation_toolbar.png)

  以下各节详细介绍了与进度和日志显示相关的图标：

   * [显示进度](../../workflow/using/monitoring-workflow-execution.md#displaying-progress)
   * [显示日志](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)

* **对象对齐方式**

  要对齐图标，请选择图标并单击&#x200B;**[!UICONTROL Align vertically]**&#x200B;或&#x200B;**[!UICONTROL Align horizontally]**&#x200B;图标。

  使用&#x200B;**CTRL**&#x200B;键选择多个分散的活动，或取消选择一个或多个活动。 单击图表背景取消选择所有内容。

* **映像管理**

  您可以自定义图表的背景图像以及与各种活动相关的图像。 请参阅[更改活动图像](managing-activity-images.md)。

## 配置活动 {#configuring-activities}

双击活动以进行配置，或右键单击并选择&#x200B;**[!UICONTROL Open...]**。

>[!NOTE]
>
>[此部分](about-activities.md)中详细介绍了活动工作流活动。

第一个选项卡包含基本配置。 **[!UICONTROL Advanced]**&#x200B;选项卡包含其他参数，这些参数特别用于定义遇到错误时的行为、指定活动的执行持续时间以及输入初始化脚本。

为了更好地了解活动并提高工作流的清晰度，您可以在活动中输入注释：当操作员滚动到活动上时，会自动显示这些注释。

![](assets/example1-comment.png)

## 定位工作流 {#targeting-workflows}

定向工作流使您能够构建多个投放目标。 您可以通过工作流活动创建查询、根据特定标准定义联合或排除项、添加计划。 此定位的结果可自动传输到充当投放操作目标的列表中

除了这些活动之外，数据管理选项还允许您处理数据和访问高级功能，以满足复杂的定位问题。 有关详细信息，请参阅[数据管理](targeting-data.md#data-management)。

所有这些活动都可以在第一个工作流选项卡中找到。

>[!NOTE]
>
>[此部分](about-activities.md)中详细介绍了定位活动。

可以通过Adobe Campaign树的&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]**&#x200B;节点或主页的&#x200B;**[!UICONTROL Profiles and Targets > Targeting workflows]**&#x200B;菜单创建和编辑定位工作流。

![](assets/target_wf.png)

营销活动框架中的定位工作流存储在所有营销活动工作流中。

### 创建定位工作流程的关键步骤 {#implementation-steps-}

以下各节详细介绍了创建定位工作流的步骤：

1. **识别数据库中的**&#x200B;数据 — 请参阅[创建查询](targeting-data.md#creating-queries)
1. **准备**&#x200B;数据以满足交付需求 — 请参阅[扩充和修改数据](targeting-data.md#enriching-and-modifying-data)
1. **使用**&#x200B;数据执行更新或在传递中更新 — 请参阅[更新数据库](how-to-use-workflow-data.md#updating-the-database)

定位期间执行的所有扩充和所有处理的结果在个性化字段中存储和访问，尤其是在创建个性化消息时使用。 有关详细信息，请参阅[目标数据](data-life-cycle.md#target-data)

### 定位和筛选维度 {#targeting-and-filtering-dimensions}

在数据分段操作过程中，定位键将映射到筛选维度。定位维度可让您定义操作的目标人群：收件人、合同受益人、操作人员、订阅者等。筛选维度可让您根据特定标准选择人群：合同持有人、时事通讯订阅者等。

例如，要选择投保人超过5年的客户，请选择以下定向维度：**客户**&#x200B;和以下筛选维度：**合同持有人**。 然后，您可以在查询活动中定义筛选条件

在定位维度选择阶段，界面中仅提供兼容的筛选维度。

这两个维度必须相关。 因此，**[!UICONTROL Filtering dimension]**&#x200B;列表的内容取决于第一个字段中指定的定向维度。

例如，对于收件人（**收件人**），可以使用以下筛选维度：

![](assets/query_filter_target_dimensions_1.png)

对于&#x200B;**Web应用程序**，列表将包含以下筛选维度：

![](assets/query_filter_target_dimensions_2.png)

## 活动工作流 {#campaign-workflows}

对于每个营销活动，您可以创建要从&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡执行的工作流。 这些工作流特定于营销活动。

![](assets/wf-in-op-edit-delivery-tab.png)

此选项卡包含与所有工作流相同的活动。 [了解详情](#implementation-steps-)

除了定位活动之外，通过活动工作流还可完全为所有可用渠道创建和配置投放。 在工作流中创建后，即可从营销策划的仪表板中访问这些投放。 [了解详情](../../campaign/using/marketing-campaign-deliveries.md)

所有营销活动工作流都集中在&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Campaign workflows]**&#x200B;节点下。

![](assets/campaigns_wf.png)

[此页面](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)中详细介绍了活动工作流和实施示例。

## 技术工作流 {#technical-workflows}

Adobe Campaign中提供了现成的技术工作流。 它们是计划在服务器上定期执行的操作或作业。 它们允许您对数据库进行维护，转发有关投放的跟踪信息，以及设置投放的临时流程。 技术工作流是通过&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;节点配置的。

![](assets/navtree.png)

本机模板可用于创建技术工作流。 它们可以根据您的需求进行配置。

**[!UICONTROL Campaign process]**&#x200B;子文件夹集中了在营销活动中执行流程所需的工作流：任务通知、库存管理、成本计算等。

>[!NOTE]
>
>与每个模块一起安装的技术工作流的列表可在[专用部分](about-technical-workflows.md)中找到。

您可以在树结构的&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;节点中创建其他技术工作流。 但是，此过程是为专家用户保留的。

提供的活动与定位工作流相同。 [了解详情](#implementation-steps-)

## 工作流模板 {#workflow-templates}

工作流模板包含属性的整体配置，还可能包含图表中连接的一系列活动。 此配置可重复用于创建包含一定数量预配置元素的新工作流

您可以基于现有模板创建新工作流模板，或直接将工作流更改为模板。

工作流模板存储在Adobe Campaign树的&#x200B;**[!UICONTROL Resources > Templates > Workflow templates]**&#x200B;节点中。

![](assets/s_advuser_wf_template_tree.png)

除了常规工作流属性之外，模板属性还允许您为基于此模板创建的工作流指定执行文件。

![](assets/s_advuser_wf_template_properties.png)

## 复制工作流 {#duplicating-workflows}

您可以复制不同类型的工作流。 复制后，对工作流的修改不会转移到工作流的副本中。

>[!CAUTION]
>
>工作流中提供了复制粘贴功能，但我们建议您使用&#x200B;**复制**。 复制活动后，将保留其整个配置。 对于投放活动（电子邮件、短信、推送通知……），还会复制附加到活动的投放对象，这可能会导致崩溃。

1. 右键单击工作流。
1. 单击&#x200B;**复制**。

   ![](assets/duplicate-workflows.png)

1. 在工作流窗口中，更改工作流标签。
1. 单击&#x200B;**保存**。

复制功能无法直接在营销活动视图中可用。

但是，您可以创建一个视图以显示实例上的所有工作流。 在此视图中，您可以使用&#x200B;**复制到**&#x200B;来复制工作流。

**创建视图**

1. 在&#x200B;**资源管理器**&#x200B;中，转到在其中创建视图所需的文件夹。
1. 右键单击并转到&#x200B;**添加新文件夹** > **进程**，选择&#x200B;**工作流**。

   ![](assets/add-new-folder-workflows.png)

已创建新文件夹&#x200B;**工作流**。

1. 右键单击并选择&#x200B;**属性**。
1. 在&#x200B;**限制**&#x200B;中，检查&#x200B;**文件夹是否为视图**，然后单击&#x200B;**保存**。

   ![](assets/folder-is-a-view.png)

该文件夹现在已填充了实例的所有工作流。

**复制营销活动工作流**

1. 在工作流视图中选择营销活动工作流。
1. 右键单击&#x200B;**复制到**。
   ![](assets/duplicate-to-right-click.png)
1. 更改其标签。
1. 单击&#x200B;**保存**。

您可以在工作流视图中查看重复的工作流。
