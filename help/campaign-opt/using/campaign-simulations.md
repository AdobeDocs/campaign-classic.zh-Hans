---
product: campaign
title: 活动模拟
description: Campaign模拟入门
role: User, Data Engineer
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Campaigns
exl-id: 709c64a8-34bf-43fa-a820-238295fb26b8
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 2%

---

# 活动模拟{#campaign-simulations}

## 关于模拟 {#about-simulations}

通过活动优化，您可以使用模拟来测试活动计划的效率。 这让您可以衡量营销活动的潜在成功情况：产生的收入、基于应用的分类规则的目标数量等。

通过模拟，您可以监控和比较投放的影响。

>[!NOTE]
>
>在测试模式下准备的投放彼此之间没有影响，例如，在分布式营销中评估活动时，或者只要投放未在临时日程表中计划。\
>这意味着压力和容量规则仅适用于中的投放。 **[!UICONTROL Target estimation and message personalization]** 模式。 投放 **[!UICONTROL Estimation and approval of the provisional target]** 和 **[!UICONTROL Target evaluation]** 模式未被考虑在内。\
>在以下内容中选择交货方式： **[!UICONTROL Typology]** 投放属性的子选项卡。

![](assets/simu_campaign_select_delivery_mode.png)

## 设置模拟 {#setting-up-a-simulation}

### 创建模拟 {#creating-a-simulation}

要创建模拟，请应用以下步骤：

1. 打开 **[!UICONTROL Campaigns]** 选项卡，单击 **[!UICONTROL More]** 内的链接 **[!UICONTROL Create]** 部分，然后选择 **[!UICONTROL Simulation]** 选项。

   ![](assets/simu_campaign_opti_01.png)

1. 输入模板和模拟的名称。 单击 **[!UICONTROL Save]** 创建模拟。

   ![](assets/simu_campaign_opti_02.png)

1. 单击 **[!UICONTROL Edit]** 选项卡进行配置。

   ![](assets/simu_campaign_opti_edit.png)

1. 在 **[!UICONTROL Scope]** 选项卡，指定要为此模拟考虑的投放。 要执行此操作，请单击 **[!UICONTROL Add]** 按钮并指定要考虑的投放选择模式。

   ![](assets/simu_campaign_opti_edit_scope.png)

   您可以逐个选择每个投放，也可以按活动、项目或计划对投放进行排序。

   >[!NOTE]
   >
   >如果您通过计划、项目或营销策划选择投放，Adobe Campaign会自动刷新投放列表，以便在启动模拟时考虑。 要执行此操作，请查看 **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** 选项。
   >  
   >如果不这样做，则在创建模拟时计划、项目或营销策划中不可用的任何投放都不会被考虑：稍后添加的投放将被忽略。

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. 选择要包含在模拟范围内的元素。 如有必要，请使用SHIFT和CTRL键选取多个元素。

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   单击 **[!UICONTROL Finish]** 以批准所选内容。

   您可以手动合并选定投放和属于计划、项目或营销策划的投放。

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   如有必要，您可以通过 **[!UICONTROL Edit the dynamic condition...]** 链接。

   单击 **[!UICONTROL Save]** 以批准此配置。

   >[!NOTE]
   >
   >在计算模拟时，只考虑已计算目标的投放(状态： **目标就绪** 或 **准备投放**)。

1. 在 **[!UICONTROL Calculations]** 选项卡，选择一个分析维度，例如收件人模式。

   ![](assets/simu_campaign_opti_dimension.png)

1. 然后，您可以添加表达式。

   ![](assets/simu_campaign_opti_dimension_02.png)

### 执行设置 {#execution-settings}

此 **[!UICONTROL General]** 通过模拟的选项卡，可以输入执行设置：

* 此 **[!UICONTROL Schedule execution for down-time]** 选项根据所选的优先级将模拟启动延迟到不太繁忙的时间段。 模拟需要使用大量数据库资源，因此，例如非紧急模拟应安排在夜间运行。
* 此 **[!UICONTROL Priority]** 是应用于模拟以延迟其触发的级别。
* **[!UICONTROL Save SQL queries in the log]**. SQL日志允许您诊断模拟是否以错误结束。 它们还可以帮助您了解为什么模拟速度太慢。 在模拟之后，这些消息将出现在中 **[!UICONTROL SQL logs]** 的子选项卡 **[!UICONTROL Audit]** 选项卡。

## 执行模拟 {#executing-a-simulation}

### 开始模拟 {#starting-a-simulation}

一旦定义了模拟范围，您就可以执行它。

为此，请打开模拟仪表板，然后单击 **[!UICONTROL Start simulation]**.

![](assets/simu_campaign_opti_start.png)

执行完成后，打开模拟并单击 **[!UICONTROL Results]** 选项卡，查看为每次投放计算的目标。

![](assets/simu_campaign_opti_results.png)

1. 此 **[!UICONTROL Deliveries]** 子选项卡列出了模拟所考虑的所有投放。 它显示两个计数：

   * 此 **[!UICONTROL Initial count]** 是在投放估计期间计算的目标。
   * 此 **[!UICONTROL Final count]** 是模拟后计数的收件人数量。

     初始计数和最终计数之间的差异反映了模拟之前配置的各种规则或过滤器的应用。

     要了解有关此计算的更多信息，请编辑 **[!UICONTROL Exclusions]** 子选项卡。

1. 此 **[!UICONTROL Exclusions]** 通过子选项卡，可以查看排除项划分信息。

   ![](assets/simu_campaign_opti_14.png)

1. 此 **[!UICONTROL Alerts]** 子选项卡对模拟期间生成的所有警报消息进行分组。 在容量过载时（例如，如果定向的收件人数量超过设置的容量），可以发送警报消息。
1. 此 **[!UICONTROL Exploration of the exclusions]** 子选项卡用于创建结果分析表。 用户需要在横坐标/纵坐标轴中指示变量。

   有关创建分析表的示例，请参见的结尾 [浏览结果](#exploring-results).

### 查看结果 {#viewing-results}

#### 审核 {#audit}

此 **[!UICONTROL Audit]** 选项卡可让您监视模拟的执行。 此 **[!UICONTROL SQL Logs]** 子选项卡对于专家用户很有用。 它以SQL格式列出执行日志。 仅当满足以下条件时，才会显示这些日志 **[!UICONTROL Save SQL queries in the log]** 已选择选项 **[!UICONTROL General]** 选项卡。

![](assets/simu_campaign_opti_11.png)

#### 浏览结果 {#exploring-results}

此 **[!UICONTROL Exploration of the exclusions]** 利用子选项卡，可分析模拟生成的数据。

中详细介绍了描述性分析 [本节](../../reporting/using/about-adobe-campaign-reporting-tools.md).

## 模拟的结果 {#results-of-a-simulation}

中的指示器 **[!UICONTROL Log]** 和 **[!UICONTROL Results]** 选项卡提供模拟结果的第一个概览。 要获得更详细的结果视图，请打开 **[!UICONTROL Reports]** 选项卡。

### 报告 {#reports}

要分析模拟的结果，请编辑其报告：它们显示排除项和原因。

默认情况下，会提供以下报表：

* **[!UICONTROL Detail of simulation exclusions]** ：此报表为所有相关的投放提供了一个详细的排除原因图表。
* **[!UICONTROL Simulation summary]** ：此报表显示各种投放中从模拟中排除的群体。
* **[!UICONTROL Summary of exclusions linked to the simulation]** ：此报表显示由模拟导致的排除图表、应用的分类规则以及显示每个规则的排除率的图表。

>[!NOTE]
>
>您可以创建新报告并将它们添加到提供的报告中。 如需详细信息，请参阅[此部分](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

要访问报表，请单击 **[!UICONTROL Reports]** 目标模拟在其功能板上的链接。

![](assets/campaign_opt_reporting_edit_from_board.png)

您还可以使用编辑报告 **[!UICONTROL Reports]** 可从模拟仪表板访问的链接。

### 比较模拟 {#comparing-simulations-}

每次执行模拟时，结果都会替换之前的任何结果：您无法显示和比较一个执行中的结果。

要比较结果，您需要使用报告。 事实上，Adobe Campaign允许您保存报表历史记录，以便稍后再次查看。 该历史记录将在模拟的生命周期中保存。

**示例:**

1. 创建对投放的模拟，投放采用哪种类型 **A** 应用于。
1. 在 **[!UICONTROL Reports]** 选项卡，编辑其中一个可用报表，例如 **[!UICONTROL Detail of simulation exclusions]** 例如。
1. 在报告的右上角部分，单击图标以创建新历史记录。

   ![](assets/campaign_opt_reporting_create_hist.png)

1. 关闭模拟并更改分类配置 **A**.
1. 再次执行模拟，并将结果与创建历史记录的报告中所显示的结果进行比较。

   ![](assets/campaign_opt_reporting_edit_hist.png)

   您可以根据需要保存任意数量的报告历史记录。

### 报表轴 {#reporting-axes}

此 **[!UICONTROL Calculations]** 选项卡允许您在目标上定义报告轴。 这些轴将在结果分析期间使用(请参阅 [浏览结果](#exploring-results))。

>[!NOTE]
>
>我们建议在模拟模板中定义计算轴，而不是为每个模拟分别定义计算轴。\
>模拟模板保存在中 **[!UICONTROL Resources > Templates > Simulation templates]** Adobe Campaign树的节点。

**示例:**

在下面的示例中，我们要根据收件人的状态（“客户”、“潜在客户”或无）创建一个额外的报表轴。

1. 要定义报表轴，请选择包含要在中处理信息的表 **[!UICONTROL Analysis dimension]** 字段。 此信息是强制性的。
1. 在此，我们要选择收件人表的区段字段。

   ![](assets/simu_campaign_opti_09.png)

1. 可以使用以下选项：

   * **[!UICONTROL Generate target overlap statistics]** 用于恢复模拟报表中的所有重叠统计信息。 重叠是在一个模拟中针对至少两个投放的收件人。

     >[!IMPORTANT]
     >
     >选择此选项可显着增加模拟执行时间。

   * **[!UICONTROL Keep the simulation work table]** 可让您保留模拟跟踪。

     >[!IMPORTANT]
     >
     >自动保存这些表需要很大的存储容量：确保数据库足够大。

显示仿真结果时，所选表达式的信息将显示在 **[!UICONTROL Overlaps]** 子选项卡。

投放目标重叠指示模拟的至少两个投放中的目标收件人。

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>此子选项卡仅在 **[!UICONTROL Generate target recovery statistics]** 选项已启用。

可以在中创建的排除分析报表中处理有关报表轴的信息 **[!UICONTROL Exploring exclusions]** 子选项卡。 有关详细信息，请参见 [浏览结果](#exploring-results).
