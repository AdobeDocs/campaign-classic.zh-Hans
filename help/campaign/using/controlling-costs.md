---
title: 控制成本
seo-title: 控制成本
description: 控制成本
seo-description: null
page-status-flag: never-activated
uuid: 4209ebad-966f-44a6-a33c-bbb398c6f5c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 892b93ed-cb0e-4af5-a1ae-eff0c8b703c6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '2470'
ht-degree: 0%

---


# 控制成本{#controlling-costs}

## 关于成本控制 {#about-cost-control}

Adobe Campaign允许您使用营销资源管理模块控制已计划的、已承诺的和已开具发票的营销成本，并按类别细分这些成本。

为活动的各个流程执行的成本会从市场营销部门预先定义的预算中扣除。 这些金额可以细分为多个类别，以使信息更易读，并提供更详细的营销投资报告。

预算的管理和跟踪集中在Adobe Campaign树的专用节点中。 这样，您就可以监控同一视图和所有预算中分配、保留、承诺和支出的金额。

![](assets/s_ncs_user_budget_node_02.png)

使用MRM实施预算管理时必须应用以下步骤：

1. 定义预算

   有关此问题的详细信息，请 [参阅创建预算](#creating-a-budget)。

1. 定义成本计算方法

   为服务提供商定义成本结构。 请参 [阅创建服务提供商及其成本类别](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

1. 定义活动成本(投放/任务)

   投放和任务所产生的成本是单独或全球为活动模板输入的。 请参 [阅计算成本和库存](../../campaign/using/marketing-campaign-deliveries.md#calculation-of-costs-and-stocks)。

1. 整合

   根据任务、投放和活动的进度状态，将计算费用并转入相应的预算。

   当活动的创建足够提前时，活动预算的进度状态可更改为 **[!UICONTROL Specified]**。 项目的计算成本随后自动输入，其中包括在活动上计算的成本。 请参 [阅成本承诺、计算和收费](#cost-commitment--calculation-and-charging)。

## 创建预算 {#creating-a-budget}

预算通过节点在地图中创 **[!UICONTROL Campaign management > Budgets]** 建。 利用工 **[!UICONTROL New]** 具栏中的按钮，您可以创建预算。

* 添加新预算

   单击图 **[!UICONTROL New]** 标、名称并保存预算。

* 输入初始金额

   在相关字段中指示已分配金额。 其他金额将自动输入。 请参 [阅计算金额](#calculating-amounts)。

* 定义有效期

   指定开始和结束日期。 此信息仅表示。

* 费用

   为活动、任务等创建分配给此预算的成本所在的费用类别。 链接。 请参阅 [费用类别](#expense-categories)。

   ![](assets/s_ncs_user_budget_create_and_save.png)

>[!NOTE]
>
>您可以选择相关预算。
>
>有关此方面的详细信息，请 [参阅将预算关联到其他预算](#linking-a-budget-to-another)。

### 计算金额 {#calculating-amounts}

每个预算都由初始金额定义，初始金额将在计划或执行活动、投放或任务后从与它们相关的各种预算、预算或的成本中减少。 金额的状态（计划、保留、承诺、支出或开票）取决于成本类型和活动、投放或任务中定义的承诺级别。

>[!NOTE]
>
>为类别输入的金额必须与字段中定义的预算信封相 **[!UICONTROL Allocated]** 匹配。

对于活动，根据承诺的程度，可以计划、承诺或预留费用，供将来采取行动。

![](assets/s_user_cost_op_engaged.png)

>[!CAUTION]
>
>创建活动时，必须将进度状 **[!UICONTROL Budget]** 态设置为， **[!UICONTROL Defined]** 以便在执行时考虑成本。 如果状态为 **[!UICONTROL Being edited]**，则不会合并成本。
>   
>该选 **[!UICONTROL Commitment level]** 项指在将成本计入预算前对未来的预测。 根据活动、任务或投放的进度，您可以决定分配更高或更低的承诺级别(1)。 计划，2。 保留，3。 提交)。

例如，Web活动的预计计划成本为45,000欧元。

![](assets/s_user_edit_budget_node_impact_0.png)

对于活动，当预算创建状态设置为 **[!UICONTROL Defined]**&#x200B;时，活动的实际成本（或者，如果没有，计算成本）将转入预算合计。

![](assets/s_user_budget_in_op_a.png)

根据活动预算的承诺级别，金额将输入或字 **[!UICONTROL Planned]**&#x200B;段 **[!UICONTROL Reserved]** 中 **[!UICONTROL Committed]** 。

承诺级别可以修改：

* 在 **活动** 级别的 **[!UICONTROL Budget]** “”选项卡中 **[!UICONTROL Edit]** 找到。 这是配置预算、成本和费用的地方。
* 在 **任务** 级，在窗 **[!UICONTROL Expenses and revenues]** 口中。

![](assets/s_user_op_engagement_level_costs.png)

在预算出现 **[!UICONTROL Reserved]**&#x200B;时，系统会自动为已计费预算执行更新。

![](assets/s_user_edit_budget_node_impact_2.png)

在任务级别，过程相同。

![](assets/s_user_edit_budget_node_impact_task.png)

当支出产生发票并支付发票时，其金额随后将输入字 **[!UICONTROL Invoiced]** 段。

### 费用类别 {#expense-categories}

这些金额可以在多个费用类别中分发，以便更好地阅读数据并更详细地报告营销投资。 费用类别在预算创建过程中通过树 **[!UICONTROL Budgets]** 的节点进行定义。

要添加类别，请 **[!UICONTROL Add]** 单击窗口下半部分的按钮。

![](assets/s_user_budget_category.png)

您可以从现有类别中选择类别，或直接在字段中输入新来定义新。 确认输入后，会显示一条确认消息，允许您将此类别添加到现有类别的列表，并在必要时将其与“自然”关联。 此信息将用于预算报告。

### 将预算关联到另一个 {#linking-a-budget-to-another}

您可以将预算关联到主预算。 为此，请在辅助预算字段 **[!UICONTROL related budget]** 中选择主预算。

![](assets/budget_link.png)

为了显示相关预算的列表，将在主预算中添加附加标签。

![](assets/budget_link_new_tab.png)

此信息将转入预算报告。

## 添加费用行 {#adding-expense-lines}

费用行会自动添加到预算中。 它们是在投放分析和任务完成时创建的。

![](assets/s_ncs_user_budget_line_edit.png)

对于每个活动、投放或任务，生成的成本将分组在预算的支出行中，这些成本将计入预算。 这些费用行是根据相关服务提供商的成本行创建的，并通过相关成本结构计算。

因此，每个费用行都包含以下信息：

* 活动及其相关的投放或任务
* 根据成本结构或估计临时成本计算的金额
* 相关投放或任务的实际成本
* 相应的发票行（仅限MRM）
* 列表按成本类别计算的成本（如果存在成本结构）

在上例中，编辑的费用行包含为Loyalty Spring Pack投放 **的New** cards **活动计算的成本** 。 编辑投放时，标 **[!UICONTROL Direct Mail]** 签会显示如何计算费用行。

此投放的成本计算基于为相关服务提供商选择的成本类别:

![](assets/s_user_edit_del_supplier_costs.png)

根据所选择的成本类别，应用相应的成本结构以计算成本行。 在本例中，对于相关服务提供商，成本结构如下：

![](assets/s_user_edit_node_supplier_costs.png)

>[!NOTE]
>
>成本类别和结构在创建 [服务提供商及其成本类别中显示](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

## 成本承担、计算及收费 {#cost-commitment--calculation-and-charging}

投放和任务可承诺成本。 根据与之相关的过程的进度，更新成本的状态。

### 成本计算过程 {#cost-calculation-process}

成本分为三个类别:

1. 估计临时费用

   估计临时费用是活动进程费用的估计。 只要正在编辑，输入的金额就不会合并。 它必须具有 **[!UICONTROL Specified]** 要在计算中考虑的输入金额的状态。

   此金额是人工输入的，可细分为多个费用类别。 要降低成本，请单击链 **[!UICONTROL Breakdown...]** 接，然后单击 **[!UICONTROL Add]** 按钮以定义新金额。

   ![](assets/s_user_edit_budget_tab_ventil.png)

   您可以将每个成本与类别关联，以便以后可以在相关预算和预算报告中查看按费用类别划分的成本。

1. 计算成本

   计算的成本取决于相关的元素(活动、投放、任务等) 及其状态（正在编辑、进行中、已完成）。 无论如何，如果指定了实际成本，则计算成本将使用此金额。

   如果未提供实际成本，则适用以下规则：

   * 对于正在编辑的活动，计算成本是活动的估计临时成本，或者，如果未定义此成本，则计算成本将是该活动的投放和任务的所有临时成本之和。 如果活动完成，则活动的计算成本将是所有计算成本的总和。
   * 对于尚未分析的投放，计算成本为估计临时成本。 如果分析已经执行，则计算成本将是服务提供成本结构计算的所有成本和目标收件人数之和。
   * 对于在建任务，计算成本采用估计临时成本。 如果任务完成，则计算成本将是从服务提供商成本结构计算的所有成本和完成天数之和。
   * 对于营销计划，对于项目，计算成本是为活动计算的成本总和。 如果这些费用没有具体说明，计算的费用将使用估计的临时费用。

   >[!NOTE]
   >
   >通过 **[!UICONTROL Breakdown]** 链接，您可以视图计算的详细信息和上次成本计算日期。

1. 实际成本

   实际成本是人工输入的，必要时会细分为不同的费用类别。

### 计算和计费 {#calculation-and-charging}

成本按成本结构计算，并在相关活动、投放或任务中选定的预算中扣除。

可以通过预算批准对提交给活动的金额执行检查。 可以在活动中创建其他检查点样式任务，以设置其他批准。 请参 [阅任务类型](../../campaign/using/creating-and-managing-tasks.md#types-of-task)。

### 示例{#example}

我们将创建一个活动:

* 使用投放成本结构的直接邮件服务提供商
* 具有固定成本的任务
* 每日成本的任务

#### 第1步——创建预算 {#step-1---creating-the-budget}

1. 通过节点创建新 **[!UICONTROL Campaign management > Budgets]** 预算。

1. 在该款的字段中定义10,000 **[!UICONTROL Allocated]** 欧元的预 **[!UICONTROL Amounts]** 算。 在窗口的下半部分添加两个费用类别:

![](assets/s_user_cost_mgmt_sample_1.png)

#### 第2步——配置服务提供商和定义成本结构 {#step-2---configuring-the-service-provider-and-defining-the-cost-structures}

1. 从节点创建服务提供商和服务模板及其成本结 **[!UICONTROL Administration > Campaigns]** 构。 有关此内容的详细信息，请 [参阅创建服务提供商及其成本类别](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

   对于直邮投放，请创 **[!UICONTROL Envelopes]** 建成本类别(类型114x229和 **[!UICONTROL Postage]****[!UICONTROL Print]** 162x229)和（类型A3和A4）。 然后创建以下成本结构：

   ![](assets/s_user_cost_mgmt_sample_2.png)

1. 添加固定成本(在成本类别中)，其计算固定且金额为空（在相应的成本结构中），并将为每个投放单独指定。

   ![](assets/s_user_cost_mgmt_sample_5.png)

   对于任务，请创建以下两个成本类别:

   * **[!UICONTROL Room reservation]** （小房间和大房间）, **固定** 成本结构为300和500欧元：

   ![](assets/s_user_cost_mgmt_sample_6.png)

   * **[!UICONTROL Creation]** (**内容模板** )，每日 **成本结** 构为300欧元：

   ![](assets/s_user_cost_mgmt_sample_7.png)

#### 第3步——在活动中计入预算 {#step-3---charging-the-budget-in-the-campaign}

1. 创建活动，然后选择在步骤1中创建的预算。

   >[!NOTE]
   >
   >默认情况下，为项目选择的预算将应用于项目中的所有活动。

   ![](assets/s_user_cost_mgmt_sample_4.png)

1. 指定预计临时成本，细目包括：

   ![](assets/s_user_cost_mgmt_sample_9.png)

1. 单击 **[!UICONTROL Ok]** ，然 **[!UICONTROL Save]** 后确认此信息。 活动的计算成本随后用估计临时成本更新。

#### 第4步——创建直邮投放 {#step-4---creating-the-direct-mail-delivery}

1. 为活动创建工作流并定位查询活动以选择目标(警告，必须指定收件人邮政地址)。

1. 创建直接邮件投放并选择在步骤2中创建的服务提供商:成本类别会自动显示。

1. 改写信封的成本并添加固定成本。 还可以选择类别，考虑这些成本。

   ![](assets/s_user_cost_mgmt_sample_3.png)

   >[!NOTE]
   >
   >如果某个成本类别未使用，则不会产生任何费用。

1. 开始您刚刚创建的用于启动分析和计算成本的工作流。

   ![](assets/s_user_cost_mgmt_sample_10.png)

1. 如果为此活动启用了预算批准，则从仪表板批准预算。 您可以检查成本类别的批准。

   ![](assets/s_user_cost_mgmt_sample_10b.png)

与投放相关的费用行会添加到 **[!UICONTROL Edit > Budget]** 活动的标签中。 编辑它以视图计算的详细信息。

![](assets/s_user_cost_mgmt_sample_11.png)

为投放计算的成本会更新以下信息：

![](assets/s_user_cost_mgmt_sample_12.png)

编辑计算的成本时，您可以检查成本细分以及成本计算的状态和日期。

#### 第5步——创建任务 {#step-5---creating-tasks}

在此活动中，我们将添加两个以前为其创建成本结构的任务(请参 [阅第2步——配置服务提供商和定义成本结构](#step-2---configuring-the-service-provider-and-defining-the-cost-structures))。 为此，请在活动仪表板中单击按 **[!UICONTROL Add a task]** 钮。 命名任务并单击 **[!UICONTROL Save]**。

1. 然后，任务被添加到任务列表。 您必须编辑它才能进行配置。

1. 在标签 **[!UICONTROL Properties]** 中，选择服务和相应的成本类别:

   ![](assets/s_user_cost_mgmt_sample_14.png)

1. 然后，单击任务 **[!UICONTROL Expenses and revenue]** 的图标，并指定估计的临时成本。

   ![](assets/s_user_cost_mgmt_sample_15.png)

   在保存任务后，计算的成本与为估计临时成本输入的值一起指定。

   当任务完成(状态 **[!UICONTROL Finished]** )时，计算的成本将自动更新为大会议室的成本，这是在其成本结构中输入的。 此成本也会显示在细分类别中。

1. 然后，按照同一过程创建第二个任务;计划超过五天，与先前创建的成本结构有关。

   ![](assets/s_user_cost_mgmt_sample_16.png)

   任务完成后，计算成本将使用相关成本结构的值指定，即示例中的1500欧元（5天x 300欧元）:

   ![](assets/s_user_cost_mgmt_sample_17.png)

#### 第6步——更新活动预算状态 {#step-6---update-the-campaign-budget-status}

配置活动后，可将其状态设置为以更新该的状态 **[!UICONTROL Specified]**。 活动的计算成本随后将指明投放的计算成本和活动的任务之和：

![](assets/s_user_cost_mgmt_sample_18.png)

#### 预算批准 {#budget-approval}

激活批准后，您可以通过特殊链接从活动仪表板批准预算。 在启动定位工作流并且需要批准直邮投放时，会显示此链接。

![](assets/s_user_cost_mgmt_sample_19.png)

然后，您可以单击链接以授予或拒绝批准，或者如果已为此活动激活通知，则使用通知电子邮件中的链接。

预算获得批准并完成投放后，成本将通过特殊的技术工作流自动上传。

## 订单和发票 {#orders-and-invoices}

在MRM环境中，您可以保存带有服务提供商的订单并开具发票。 这些订单和发票的整个生命周期都可以通过Adobe Campaign界面进行管理。

### 订单创建 {#order-creation}

要用服务提供商保存新订单，请单 **[!UICONTROL MRM > Orders]** 击树的节点，然后单击按 **[!UICONTROL New]** 钮。

指定订单编号、相关服务提供商和订单总额。

![](assets/s_user_cost_create_order.png)

### 开具和跟踪发票 {#issuing-and-tracking-invoices}

对于每个服务提供商，您可以保存发票并定义其状态和已计费预算。

发票会创建并存储在 **[!UICONTROL MRM > Invoices]** Adobe Campaign树的节点中。

![](assets/s_user_cost_create_invoice.png)

发票由发票行组成，发票行的总额允许自动计算金额。 这些行是从标签中手动创 **[!UICONTROL Invoice lines]** 建的。 它们可以与订单关联，以便将信息上传到订单。

![](assets/s_user_cost_invoice_add_line.png)

每个服务提供商的发票显示在 **[!UICONTROL Invoices]** 用户档案的标签中：

![](assets/s_ncs_user_invoice_from_supplier.png)

在标 **[!UICONTROL Details]** 签中，您可以显示发票的内容。

Click **[!UICONTROL Add]** to create a new invoice.
