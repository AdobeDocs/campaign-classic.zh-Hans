---
title: 营销活动模拟
seo-title: 营销活动模拟
description: 营销活动模拟
seo-description: null
page-status-flag: never-activated
uuid: d5a090ef-57e5-46b2-b9ad-6d4d964c8e20
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: e8e7a720-c93d-491d-8768-270e47e9c898
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 营销活动模拟{#campaign-simulations}

## 关于仿真 {#about-simulations}

营销活动优化允许您使用模拟测试营销活动计划的效率。 这使您能够衡量营销活动的潜在成功：生成的收入、基于所应用的类型学规则的目标数量等。

通过模拟，您可以监视和比较交付的影响。

>[!NOTE]
>
>在“测试”模式下准备的交付互不影响，例如在分布式营销中评估营销活动时，或只要临时日历中未计划交付即可。\
>这意味着压力和容量规则只适用于模式下的交付 **[!UICONTROL Target estimation and message personalization]** 。 不考虑在 **[!UICONTROL Estimation and approval of the provisional target]** 模式和 **[!UICONTROL Target evaluation]** 模式下的交付。\
>在交付属性的子标签 **[!UICONTROL Typology]** 中选择交付模式。

![](assets/simu_campaign_select_delivery_mode.png)

## 设置模拟 {#setting-up-a-simulation}

### 创建模拟 {#creating-a-simulation}

要创建模拟，请应用以下步骤：

1. 转到宇宙 **[!UICONTROL Campaigns]** ，单击部分中的 **[!UICONTROL More]** 链接并 **[!UICONTROL Create]** 选择选 **[!UICONTROL Simulation]** 项。

   ![](assets/simu_campaign_opti_01.png)

1. 输入模板和模拟的名称。 单击 **[!UICONTROL Save]** 以创建模拟。

   ![](assets/simu_campaign_opti_02.png)

1. 单击选 **[!UICONTROL Edit]** 项卡进行配置。

   ![](assets/simu_campaign_opti_edit.png)

1. 在选项 **[!UICONTROL Scope]** 卡中，指定要为此模拟考虑的提交。 为此，请单击按 **[!UICONTROL Add]** 钮并指定要考虑的传送选择模式。

   ![](assets/simu_campaign_opti_edit_scope.png)

   您可以逐个选择每个分发，或按营销活动、计划或计划对其排序。

   >[!NOTE]
   >
   >如果您通过计划、计划或营销活动选择分发，则Adobe Campaign可以在模拟启动时自动刷新分发列表以考虑这些分发。 要执行此操作，请选中该 **[!UICONTROL Refresh the selection of deliveries each time the simulation is started]** 选项。
   >  
   >如果不这样做，则创建模拟时计划、计划或营销活动中不可用的任何分发将不会被考虑在内：稍后添加的提交将被忽略。

   ![](assets/simu_campaign_opti_edit_scope_update.png)

1. 选择要包含在模拟范围内的元素。 如有必要，使用SHIFT和CTRL键选择多个元素。

   ![](assets/simu_campaign_opti_edit_scope_select.png)

   单击 **[!UICONTROL Finish]** 以批准选择。

   您可以人工合并属于计划、计划或营销活动的选定提交和提交。

   ![](assets/simu_campaign_opti_edit_scope_save.png)

   如有必要，您可以通过链接使用动态条 **[!UICONTROL Edit the dynamic condition...]** 件

   单击 **[!UICONTROL Save]** 以批准此配置。

   >[!CAUTION]
   >
   >在计算模拟时，只考虑已计算目标的交付(状态：Target ready **** (目标就绪 **)**&#x200B;或Ready to deliver（就绪）。

1. 在选项卡 **[!UICONTROL Calculations]** 中，选择分析维，例如收件人架构。

   ![](assets/simu_campaign_opti_dimension.png)

1. 然后，您可以添加表达式。

   ![](assets/simu_campaign_opti_dimension_02.png)

### 执行设置 {#execution-settings}

在模 **[!UICONTROL General]** 拟的选项卡中，您可以输入执行设置：

* 该选 **[!UICONTROL Schedule execution for down-time]** 项会根据所选的优先级将模拟启动定义为较不繁忙的时间段。 仿真使用大量数据库资源，这就是为什么非紧急仿真应安排在夜间运行的原因。
* 该级 **[!UICONTROL Priority]** 别是应用于模拟以延迟其触发的级别。
* **[!UICONTROL Save SQL queries in the log]**. 使用SQL日志，可以在模拟以错误结尾时进行诊断。 它们还可以帮助您找出模拟过慢的原因。 模拟完成后，这些消息将显示在选 **[!UICONTROL SQL logs]** 项卡的子选项卡中 **[!UICONTROL Audit]** 。

## 执行模拟 {#executing-a-simulation}

### 启动模拟 {#starting-a-simulation}

定义模拟范围后，即可执行它。

为此，请打开模拟控制板并单击 **[!UICONTROL Start simulation]**。

![](assets/simu_campaign_opti_start.png)

执行完成后，打开模拟并单击选项 **[!UICONTROL Results]** 卡以查看为每个交付计算的目标。

![](assets/simu_campaign_opti_results.png)

1. 子选 **[!UICONTROL Deliveries]** 项卡列出模拟所考虑的所有提交。 它显示了两个计数：

   * 该 **[!UICONTROL Initial count]** 目标是在其交付中的估计期间计算的目标。
   * 是 **[!UICONTROL Final count]** 经过模拟计算的收件人数。

      初始计数和最终计数之间的差异反映了在模拟之前配置的各种规则或过滤器的应用。

      要进一步了解此计算，请编辑 **[!UICONTROL Exclusions]** 子选项卡。

1. 通过 **[!UICONTROL Exclusions]** 子选项卡可以查看排除分组信息。

   ![](assets/simu_campaign_opti_14.png)

1. 子选 **[!UICONTROL Alerts]** 项卡将模拟过程中生成的所有警报消息分组。 在容量过载时（例如，如果目标接收者数量超过设定容量），可以发送警报消息。
1. 通过 **[!UICONTROL Exploration of the exclusions]** 子选项卡可创建结果分析表。 用户需要指示横坐标／纵坐标轴中的变量。

   有关创建分析表的示例，请参阅“浏览结果”( [Exploring results)的结尾](#exploring-results)。

### 查看结果 {#viewing-results}

#### 审计 {#audit}

该选 **[!UICONTROL Audit]** 项卡允许您监视模拟执行。 子选 **[!UICONTROL SQL Logs]** 项卡对专家用户很有用。 它列出SQL格式的执行日志。 仅当在模拟执行之前在选 **[!UICONTROL Save SQL queries in the log]** 项卡中选择了该选项时，才 **[!UICONTROL General]** 会显示这些日志。

![](assets/simu_campaign_opti_11.png)

#### 浏览结果 {#exploring-results}

通过 **[!UICONTROL Exploration of the exclusions]** 子选项卡可以分析模拟生成的数据。

本节详细介绍了 [描述性分析](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

## 模拟结果 {#results-of-a-simulation}

选项卡和选项卡中 **[!UICONTROL Log]** 的指 **[!UICONTROL Results]** 示器提供了模拟结果的第一个概述。 有关结果的更详细视图，请打开选项 **[!UICONTROL Reports]** 卡。

### 报告 {#reports}

要分析模拟结果，请编辑其报告：它们显示排他性和原因。

默认情况下提供以下报告：

* **[!UICONTROL Detail of simulation exclusions]** :该报告提供了所有相关交付的排除原因的详细图表。
* **[!UICONTROL Simulation summary]** :此报告显示了各个交付中从模拟中排除的人口。
* **[!UICONTROL Summary of exclusions linked to the simulation]** :此报告显示模拟导致的排除情况图表以及应用的类型规则，以及每个规则的排除率图表。

>[!NOTE]
>
>您可以创建新报告并将其添加到提供的报告中。 如需详细信息，请参阅[此部分](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

要访问报告，请通过 **[!UICONTROL Reports]** 其仪表板单击目标模拟的链接。

![](assets/campaign_opt_reporting_edit_from_board.png)

您还可以使用从模拟功能板访 **[!UICONTROL Reports]** 问的链接编辑报告。

### 比较仿真 {#comparing-simulations-}

每次执行模拟时，结果都会替换以前的任何结果：您无法显示结果并将结果从一个执行操作与另一个执行操作进行比较。

要比较结果，您需要使用报告。 事实上，Adobe Campaign允许您保存报表历史记录，以便日后再次查看它。 在仿真的整个生命周期中都保存了这一历史。

**例如：**

1. 在应用了类型学 **A的交付上** ，创建模拟。
1. 在选 **[!UICONTROL Reports]** 项卡中，编辑其中一个可用的报告， **[!UICONTROL Detail of simulation exclusions]** 例如。
1. 在报表的右上角部分，单击该图标以创建新历史记录。

   ![](assets/campaign_opt_reporting_create_hist.png)

1. 关闭模拟并更改类型 **A的配置**。
1. 再次执行模拟，并将结果与报告中显示的创建历史记录的结果进行比较。

   ![](assets/campaign_opt_reporting_edit_hist.png)

   您可以根据需要保存任意数量的报告历史记录。

### 报告轴 {#reporting-axes}

通过 **[!UICONTROL Calculations]** 该选项卡可以定义目标上的报告轴。 这些轴将在结果分析过程中使用(请参阅 [探索结果](#exploring-results))。

>[!NOTE]
>
>我们建议在模拟模板中定义计算轴，而不是为每个模拟单独定义计算轴。\
>模拟模板保存在Adobe Campaign **[!UICONTROL Resources > Templates > Simulation templates]** 树的节点中。

**例如：**

在以下示例中，我们要根据收件人的状态（“客户”、“潜在客户”或“无”）创建其他报告轴。

1. 要定义报表轴，请选择包含要在字段中处理的信息的表 **[!UICONTROL Analysis dimension]** 格。 此信息是强制性的。
1. 在此，我们要选择收件人表的区段字段。

   ![](assets/simu_campaign_opti_09.png)

1. 可以使用以下选项：

   * **[!UICONTROL Generate target overlap statistics]** 允许您恢复模拟报告中的所有重叠统计信息。 重叠是在一个模拟内至少两个传送中的目标收件人。

      >[!CAUTION]
      >
      >选择此选项会显着增加模拟执行时间。

   * **[!UICONTROL Keep the simulation work table]** 让您保留模拟跟踪。

      >[!CAUTION]
      >
      >自动保存这些表需要大量存储容量：确保数据库足够大。

显示模拟结果时，所选表达式的信息将显示在子选 **[!UICONTROL Overlaps]** 项卡中。

传送目标重叠表示在模拟的至少两个传送中目标接收者。

![](assets/simu_campaign_opti_13.png)

>[!NOTE]
>
>仅当启用了该选项时，才显 **[!UICONTROL Generate target recovery statistics]** 示此子选项卡。

在子标签中创建的排除分析报告中可以处理有关报告轴 **[!UICONTROL Exploring exclusions]** 的信息。 For more on this, refer to [Exploring results](#exploring-results).
