---
solution: Campaign Classic
product: campaign
title: 活动模拟
description: 活动模拟
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1243'
ht-degree: 2%

---


# 活动模拟{#campaign-simulations}

## 关于模拟 {#about-simulations}

活动优化允许您使用模拟测试活动计划的效率。 这样，您可以衡量活动的潜在成功：产生的收入、基于所应用目标的类型规则量等。

模拟使您能够监视和比较投放的影响。

>[!NOTE]
>
>在“测试”模式下准备的投放互不影响，例如，在评估分布式营销中的活动时，或者只要投放未在临时日历中计划，就不会受到影响。\
>这意味着压力和容量规则仅应用于模式中的投放 **[!UICONTROL Target estimation and message personalization]** 。 在和 **[!UICONTROL Estimation and approval of the provisional target]** 模式 **[!UICONTROL Target evaluation]** 下的投放不会被考虑。\
>在投放属性的子选 **[!UICONTROL Typology]** 项卡中选择投放模式。

![](assets/simu_campaign_select_delivery_mode.png)

## 设置模拟 {#setting-up-a-simulation}

### 创建模拟 {#creating-a-simulation}

要创建模拟，请应用以下步骤：

1. 转至“ **[!UICONTROL Campaigns]** 宇宙”，单 **[!UICONTROL More]** 击部分中的 **[!UICONTROL Create]** 链接并选择 **[!UICONTROL Simulation]** 选项。

   ![](assets/simu_campaign_opti_01.png)

1. 输入模板和模拟的名称。 单击 **[!UICONTROL Save]** 以创建模拟。

   ![](assets/simu_campaign_opti_02.png)

1. 单击选 **[!UICONTROL Edit]** 项卡进行配置。

   ![](assets/simu_campaign_opti_edit.png)

1. 在选 **[!UICONTROL Scope]** 项卡中，指定要为此模拟考虑的投放。 为此，请单击按 **[!UICONTROL Add]** 钮并指定要考虑的投放选择模式。

   ![](assets/simu_campaign_opti_edit_scope.png)

   您可以逐个选择每个投放，或按活动、项目或计划对它们进行排序。

   >[!NOTE]
   >
   >如果您通过计划、项目或投放选择活动，则Adobe Campaign可以自动刷新投放的列表，以便在启动模拟时考虑其影响。 要执行此操作，请选中 **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** 选项。
   >  
   >如果您不这样做，则不会考虑计划、项目或活动中未提供的任何创建模拟的投放:稍后添加的投放将被忽略。

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. 选择要包含在模拟范围中的元素。 如有必要，请使用SHIFT和CTRL键选择多个元素。

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   Click **[!UICONTROL Finish]** to approve the selection.

   您可以人工合并属于计划、投放或投放的选定项目和活动。

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   如有必要，您可以通过链接使用动态 **[!UICONTROL Edit the dynamic condition...]** 条件。

   单击 **[!UICONTROL Save]** 以批准此配置。

   >[!NOTE]
   >
   >计算投放时，只考虑已计算目标的模拟(状态： **目标就绪** , **或交付就绪**)。

1. 在选 **[!UICONTROL Calculations]** 项卡中，选择分析维，如收件人模式。

   ![](assets/simu_campaign_opti_dimension.png)

1. 然后，您可以添加表达式。

   ![](assets/simu_campaign_opti_dimension_02.png)

### 执行设置 {#execution-settings}

模拟 **[!UICONTROL General]** 的选项卡允许您输入执行设置：

* 该选 **[!UICONTROL Schedule execution for down-time]** 项会根据所选的优先级将模拟启动时间定义为较短的忙时段。 模拟使用大量模拟库资源，这就是为什么非紧急数据库应安排在夜间运行。
* 是 **[!UICONTROL Priority]** 应用于模拟以延迟其触发的级别。
* **[!UICONTROL Save SQL queries in the log]**. SQL日志允许您诊断模拟（如果它以错误结尾）。 它们还可以帮助您找出模拟速度太慢的原因。 这些消息将在模拟卡的子选 **[!UICONTROL SQL logs]** 项卡中的后 **[!UICONTROL Audit]** 显示。

## 执行模拟 {#executing-a-simulation}

### 启动模拟 {#starting-a-simulation}

定义模拟范围后，即可执行它。

为此，请打开模拟仪表板并单击 **[!UICONTROL Start simulation]**。

![](assets/simu_campaign_opti_start.png)

执行完成后，打开模拟并单击选 **[!UICONTROL Results]** 项卡以视图为每个投放计算的目标。

![](assets/simu_campaign_opti_results.png)

1. 子标 **[!UICONTROL Deliveries]** 签将列表模拟考虑的所有投放。 它显示了两个计数：

   * 该 **[!UICONTROL Initial count]** 目标为在投放内估计时计算的。
   * 是 **[!UICONTROL Final count]** 模拟后计数的收件人数。

      初始计数和最终计数之间的差异反映了在模拟之前配置的各种规则或过滤器的应用。

      要进一步了解此计算，请编辑 **[!UICONTROL Exclusions]** 子选项卡。

1. 在 **[!UICONTROL Exclusions]** 子选项卡中可视图排除分组。

   ![](assets/simu_campaign_opti_14.png)

1. 子选 **[!UICONTROL Alerts]** 项卡将模拟期间生成的所有警报消息分组。 在容量过载时(例如，如果目标收件人数超过设置容量)，可以发送警报消息。
1. 在子 **[!UICONTROL Exploration of the exclusions]** 选项卡中可以创建结果分析表。 用户需要在横坐标／纵坐标轴中指示变量。

   有关创建分析表的示例，请参阅“浏览”结 [果的结尾](#exploring-results)。

### 查看结果 {#viewing-results}

#### 审核 {#audit}

使用选 **[!UICONTROL Audit]** 项卡可以监视模拟执行情况。 子选 **[!UICONTROL SQL Logs]** 项卡对专家用户很有用。 它列表SQL格式的执行日志。 仅当在执行模拟之前在 **[!UICONTROL Save SQL queries in the log]** 选项卡中选择了该选 **[!UICONTROL General]** 项时，才显示这些日志。

![](assets/simu_campaign_opti_11.png)

#### 浏览结果 {#exploring-results}

通过 **[!UICONTROL Exploration of the exclusions]** 子选项卡可以分析由模拟生成的数据。

描述性分析详 [细介绍](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

## 模拟结果 {#results-of-a-simulation}

标签和标签中 **[!UICONTROL Log]** 的指 **[!UICONTROL Results]** 示器首先概述了模拟结果。 要获得更详细的结果视图，请打开选 **[!UICONTROL Reports]** 项卡。

### 报告 {#reports}

要分析模拟的结果，请编辑其报告：它们显示排除和原因。

默认情况下提供以下报告：

* **[!UICONTROL Detail of simulation exclusions]** :该报告详细列出了所有相关投放的排除原因。
* **[!UICONTROL Simulation summary]** :此报告显示各个模拟中被排除在投放之外的人口。
* **[!UICONTROL Summary of exclusions linked to the simulation]** :此报告显示由模拟引起的排除的图表以及应用的类型规则，以及一个显示每个规则的排除率的图表。

>[!NOTE]
>
>您可以创建新报告并将其添加到提供的报告。 如需详细信息，请参阅[此部分](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

要访问报告，请通 **[!UICONTROL Reports]** 过模拟的仪表板单击目标的链接。

![](assets/campaign_opt_reporting_edit_from_board.png)

您还可以使用可从模拟仪表板 **[!UICONTROL Reports]** 访问的链接编辑报告。

### 比较模拟 {#comparing-simulations-}

每次执行模拟时，结果将替换以前的任何结果：不能显示结果并将结果从一个执行操作与另一个执行操作进行比较。

要比较结果，您需要使用报告。 事实上，Adobe Campaign允许您保存报表历史记录，以便以后再次视图它。 这段历史在模拟的整个生命周期中得以保存。

**示例:**

1. 创建应用类型学A的 **投放** 的模拟。
1. 在选 **[!UICONTROL Reports]** 项卡中，编辑其中一个可用的报表， **[!UICONTROL Detail of simulation exclusions]** 例如。
1. 在报表的右上角，单击该图标以创建新历史记录。

   ![](assets/campaign_opt_reporting_create_hist.png)

1. 关闭模拟并更改类型学A的 **配置**。
1. 再次执行模拟，并将结果与报告中显示的创建历史记录的结果进行比较。

   ![](assets/campaign_opt_reporting_edit_hist.png)

   可以根据需要保存任意数量的报告历史记录。

### 报告轴 {#reporting-axes}

通过 **[!UICONTROL Calculations]** 选项卡可以在报告上定义目标轴。 这些轴将在结果分析期间使用(请参 [阅浏览结果](#exploring-results))。

>[!NOTE]
>
>我们建议在模拟模板中定义计算轴，而不是为每个模拟单独定义计算轴。\
>模拟模板保存在 **[!UICONTROL Resources > Templates > Simulation templates]** Adobe Campaign树的节点中。

**示例:**

在以下示例中，我们要根据报告的状态(“收件人”、“潜在客户”或“无”)创建额外的轴。

1. 要定义报告轴，请选择包含要在字段中处理的信息的 **[!UICONTROL Analysis dimension]** 表。 此信息是强制性的。
1. 在此，我们要选择收件人表的区段字段。

   ![](assets/simu_campaign_opti_09.png)

1. 可以使用以下选项：

   * **[!UICONTROL Generate target overlap statistics]** 允许您恢复模拟报告中的所有重叠统计信息。 重叠是指在一个收件人内至少两个投放中的目标。

      >[!IMPORTANT]
      >
      >选择此选项会显着增加模拟执行时间。

   * **[!UICONTROL Keep the simulation work table]** 让你留下模拟痕迹。

      >[!IMPORTANT]
      >
      >自动保存这些表需要大量存储容量：确保数据库足够大。

显示模拟结果时，选定表达式的信息将显示在子选 **[!UICONTROL Overlaps]** 项卡中。

投放目标重叠表示一个模拟的至少两投放中的目标收件人。

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>仅当启用了该选项时，才显 **[!UICONTROL Generate target recovery statistics]** 示此子选项卡。

在子标签中创建的排除报告报告中可以处理分析轴 **[!UICONTROL Exploring exclusions]** 上的信息。 For more on this, refer to [Exploring results](#exploring-results).
