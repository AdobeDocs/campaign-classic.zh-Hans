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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 控制成本{#controlling-costs}

## 关于成本控制 {#about-cost-control}

Adobe Campaign允许您使用营销资源管理模块控制已计划的、已承诺的和已开具发票的营销成本，并按类别细分这些成本。

营销活动各个流程中承诺的成本将从营销部门预先定义的预算中扣除。 这些金额可分为几个类别，以使信息更易读，并提供更详细的营销投资报告。

预算管理和跟踪集中在Adobe Campaign树的专用节点中。 这样，您就可以监控同一视图中分配、保留、承诺和支出的金额以及所有预算。

![](assets/s_ncs_user_budget_node_02.png)

使用MRM实施预算管理时必须应用以下步骤：

1. 定义预算

   有关此问题的详细信息，请参 [阅创建预算](#creating-a-budget)。

1. 定义成本计算方法

   为服务提供商定义成本结构。 请参 [阅创建服务提供商及其成本类别](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

1. 定义营销活动成本（提交／任务）

   交货和任务产生的成本将单独或全局输入营销活动模板。 请参 [阅计算成本和库存](../../campaign/using/marketing-campaign-deliveries.md#calculation-of-costs-and-stocks)。

1. 整合

   根据任务、交货和营销活动的进度状态，将计算成本，并将其传递到相应的预算。

   当营销活动的创建足够高级时，可以将营销活动预算的进度状态更改为 **[!UICONTROL Specified]**。 然后，系统会自动输入计划的计算成本以及营销活动计算的成本。 请参 [阅成本承诺、计算和收费](#cost-commitment--calculation-and-charging)。

## 创建预算 {#creating-a-budget}

预算通过节点在地图中创 **[!UICONTROL Campaign management > Budgets]** 建。 通过 **[!UICONTROL New]** 工具栏中的按钮可创建预算。

* 添加新预算

   单击图 **[!UICONTROL New]** 标、名称并保存预算。

* 输入初始金额

   在相关字段中指示分配金额。 其他金额会自动输入。 请参 [阅计算金额](#calculating-amounts)。

* 定义有效期

   指定开始日期和结束日期。 此信息仅表示。

* 费用

   为营销活动、任务等创建分配给此预算的成本所属的费用类别。 链接。 请参阅 [费用类别](#expense-categories)。

   ![](assets/s_ncs_user_budget_create_and_save.png)

>[!NOTE]
>
>您可以选择相关预算。
>
>有关详细信息，请参阅将 [预算关联到其他预算](#linking-a-budget-to-another)。

### 计算金额 {#calculating-amounts}

每个预算都由初始金额定义，该金额将从计划或执行各种营销活动、交货或与它们相关的任务的成本中减少。 金额的状态（已计划、保留、已承诺、已用或已开具发票）取决于成本类型和营销活动、交付或任务中定义的承付款级别。

>[!NOTE]
>
>为类别输入的金额必须与字段中定义的预算封套相 **[!UICONTROL Allocated]** 匹配。

对于营销活动，根据承诺级别，可以计划、提交或预留成本以备将来采取行动。

![](assets/s_user_cost_op_engaged.png)

>[!CAUTION]
>
>创建营销活动后，必须将中的进 **[!UICONTROL Budget]** 度状态设置为， **[!UICONTROL Defined]** 以便在执行时考虑成本。 如果状态为 **[!UICONTROL Being edited]**，则不会合并成本。
>   
>该选 **[!UICONTROL Commitment level]** 项指在将成本计入预算前对未来的预测。 根据营销活动、任务或交付的进度，您可以决定分配更高或更低的承诺级别(1)。 计划2. 保留，3. 提交)。

例如，Web营销活动的预计计划费用为45,000欧元。

![](assets/s_user_edit_budget_node_impact_0.png)

对于营销活动，当预算创建状态设置为时 **[!UICONTROL Defined]**，营销活动的实际成本（或者，如果没有，则计算成本）将转入预算总额。

![](assets/s_user_budget_in_op_a.png)

根据营销活动预算的承诺级别，金额将输入或字 **[!UICONTROL Planned]**&#x200B;段 **[!UICONTROL Reserved]** 中 **[!UICONTROL Committed]** 。

承诺级别可以修改：

* 在系 **列活动** ，在窗口 **[!UICONTROL Budget]** 的选项卡中找到 **[!UICONTROL Edit]** 。 这是配置预算、成本和费用的地方。
* 在任 **务级** ，在窗口 **[!UICONTROL Expenses and revenues]** 中。

![](assets/s_user_op_engagement_level_costs.png)

在预算中， **[!UICONTROL Reserved]**&#x200B;系统会自动为已计费预算执行更新。

![](assets/s_user_edit_budget_node_impact_2.png)

在任务级别上，该过程是相同的。

![](assets/s_user_edit_budget_node_impact_task.png)

当支出产生发票并支付发票时，其金额随后将输入字 **[!UICONTROL Invoiced]** 段。

### 费用类别 {#expense-categories}

这些金额可以分为若干费用类别，以便更好地阅读数据并更详细地报告营销投资。 在预算创建过程中，通过树的节点定 **[!UICONTROL Budgets]** 义费用类别。

要添加类别，请单 **[!UICONTROL Add]** 击窗口下部的按钮。

![](assets/s_user_budget_category.png)

您可以从现有类别中选择一个类别，或直接在字段中输入新类别来定义新类别。 确认输入后，将显示一条确认消息，让您将此类别添加到现有类别列表中，并在必要时将其与“性质”关联。 此信息将用于预算报告。

### 将预算关联到另一个 {#linking-a-budget-to-another}

您可以将预算关联到主预算。 为此，请在辅助预算字段中 **[!UICONTROL related budget]** 选择主预算。

![](assets/budget_link.png)

为了显示相关预算的列表，将向主预算添加一个附加标签。

![](assets/budget_link_new_tab.png)

这些资料将转交预算报告。

## 添加费用行 {#adding-expense-lines}

费用行会自动添加到预算中。 在交付分析期间和任务完成时创建这些组件。

![](assets/s_ncs_user_budget_line_edit.png)

对于每个营销活动、交付或任务，生成的成本将分组在向其收取费用的预算的费用行中。 这些费用行是根据相关服务提供商的成本行创建的，并通过相关的成本结构计算。

因此，每个费用行包含以下信息：

* 营销活动及其相关的分发或任务
* 根据成本结构或估计临时成本计算之金额
* 交付或相关任务的实际成本
* 相应的发票行（仅限MRM）
* 按成本类别计算的成本列表（如果存在成本结构）

在上例中，编辑的费用行包含为Loyalty Spring Pack营销活动的 **New cards** delivery **计算的成本** 。 编辑交货后，您可以在标 **[!UICONTROL Direct Mail]** 签中查看如何计算费用行。

此交付的成本计算基于为相关服务提供商选择的成本类别：

![](assets/s_user_edit_del_supplier_costs.png)

根据所选择的成本类别，应用相应的成本结构以计算成本行。 在本例中，对于相关的服务提供商，成本结构如下：

![](assets/s_user_edit_node_supplier_costs.png)

>[!NOTE]
>
>成本类别和结构在创建服 [务提供商及其成本类别中介绍](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

## 成本承担、计算及收费 {#cost-commitment--calculation-and-charging}

可以提交交货和任务的成本。 根据与之相关的过程的进度，更新成本的状态。

### 成本计算过程 {#cost-calculation-process}

成本分为三类：

1. 估计临时费用

   估计临时费用是对活动进程费用的估计。 只要正在编辑，输入的金额就不会合并。 它必须具 **[!UICONTROL Specified]** 有状态，才能在计算中考虑输入的金额。

   此金额是人工输入的，可分为若干费用类别。 要降低成本，请单击链 **[!UICONTROL Breakdown...]** 接，然后单击按 **[!UICONTROL Add]** 钮以定义新金额。

   ![](assets/s_user_edit_budget_tab_ventil.png)

   您可以将每个成本与一个类别关联，以便以后可以在相关预算和预算报告中查看按费用类别划分的成本细分。

1. 计算成本

   计算的成本取决于相关要素（营销活动、交付、任务等）及其状态（正在编辑、进行中、已完成）。 无论如何，如果指定了实际成本，则计算成本将使用此金额。

   如果未提供实际成本，则适用以下规则：

   * 对于正在编辑的营销活动，计算的成本是营销活动的估计临时成本；如果未定义此成本，则计算的成本将是营销活动的交付和任务的所有临时成本的总和。 如果营销活动完成，则营销活动的计算成本将是所有计算成本的总和。
   * 对于尚未分析的交付，计算成本为估计临时成本。 如果已经执行分析，则计算的成本将是从服务提供成本结构计算的所有成本和目标接收者人数的总和。
   * 对于进行中的任务，计算的成本使用估计的临时成本。 如果任务完成，则计算的成本将是从服务提供商成本结构计算的所有成本和完成的天数的总和。
   * 对于营销计划，对于计划，计算的成本是为营销活动计算的成本总和。 如果这些费用没有具体说明，计算的费用将使用估计的临时费用。
   >[!NOTE]
   >
   >通过 **[!UICONTROL Breakdown]** 该链接可以查看计算的详细信息以及上次的成本计算日期。

1. 实际成本

   实际成本是手动输入的，如有必要，将其分为不同的费用类别。

### 计算和计费 {#calculation-and-charging}

成本通过成本结构计算，并计入在营销活动、交货或相关任务中选择的预算。

可以通过预算批准对提交到营销活动的金额执行检查。 可以在营销活动中创建其他检查点样式的任务，以设置其他批准。 请参 [阅任务类型](../../campaign/using/creating-and-managing-tasks.md#types-of-task)。

### Example {#example}

我们将创建营销活动，包括：

* 使用服务提供商的成本结构的直邮递送
* 具有固定成本的任务
* 每日成本的任务

#### 第1步——创建预算 {#step-1---creating-the-budget}

通过节点创建新预 **[!UICONTROL Campaign management > Budgets]** 算。

在该款的字段中定义10,000 **[!UICONTROL Allocated]** 欧元的预 **[!UICONTROL Amounts]** 算。 在窗口的下半部分添加两个费用类别：

![](assets/s_user_cost_mgmt_sample_1.png)

#### 第2步——配置服务提供商和定义成本结构 {#step-2---configuring-the-service-provider-and-defining-the-cost-structures}

从节点创建服务提供商和服务模板及其成本结 **[!UICONTROL Administration > Campaigns]** 构。

有关详细信息，请参 [阅创建服务提供商及其成本类别](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

* 对于直接邮寄，请创建 **[!UICONTROL Envelopes]** 费用类别（类型114x229和162x229） **[!UICONTROL Postage]****[!UICONTROL Print]** 和（类型A3和A4）。 然后创建以下成本结构：

   ![](assets/s_user_cost_mgmt_sample_2.png)

   添加固定成本（在成本类别中），其计算固定且其金额为空（在相应的成本结构中），并且将为每个交货单独指定。

   ![](assets/s_user_cost_mgmt_sample_5.png)

* 对于任务，请创建以下两个成本类别：

   1. **[!UICONTROL Room reservation]** （小房间和大房间）, **固定** ，费用结构为300和500欧元：

      ![](assets/s_user_cost_mgmt_sample_6.png)

   1. **[!UICONTROL Creation]** (**内容模板** )，每日 **成本结** 构为300欧元：

      ![](assets/s_user_cost_mgmt_sample_7.png)

#### 第3步——在营销活动中计入预算 {#step-3---charging-the-budget-in-the-campaign}

创建营销活动，然后选择在步骤1中创建的预算。

>[!NOTE]
>
>默认情况下，为计划选择的预算将应用于计划中的所有营销活动。

![](assets/s_user_cost_mgmt_sample_4.png)

指定预计临时费用，细目如下：

![](assets/s_user_cost_mgmt_sample_9.png)

单击， **[!UICONTROL Ok]** 然后确 **[!UICONTROL Save]** 认此信息。 营销活动的计算成本随后用估计临时成本进行更新。

#### 第4步——创建直邮递送 {#step-4---creating-the-direct-mail-delivery}

为营销活动创建工作流并定位查询活动以选择目标（警告，必须指定收件人邮政地址）。

创建直邮递送，然后选择在步骤2中创建的服务提供商：系统会自动显示成本类别。

改写信封的成本并添加固定成本。 还可以选择这些费用所关注的类别。

![](assets/s_user_cost_mgmt_sample_3.png)

>[!NOTE]
>
>如果未使用某个成本类别，则不会生成任何费用。

启动您刚刚创建的工作流，以启动分析并计算成本。

![](assets/s_user_cost_mgmt_sample_10.png)

如果为此营销活动启用了预算批准，请从功能板中批准预算。 您可以检查成本类别的批准。

![](assets/s_user_cost_mgmt_sample_10b.png)

与交货相关的费用行会添加到营销活 **[!UICONTROL Edit > Budget]** 动的选项卡中。 编辑它以查看计算的详细信息。

![](assets/s_user_cost_mgmt_sample_11.png)

为交货计算的成本会更新，其信息如下：

![](assets/s_user_cost_mgmt_sample_12.png)

在编辑计算的成本时，您可以检查成本细分以及成本计算的状态和日期。

#### 第5步——创建任务 {#step-5---creating-tasks}

对于此营销活动，我们将添加两个以前为其创建成本结构的任务(请参阅第2步——配置服务提供商和定义成本结构 [](#step-2---configuring-the-service-provider-and-defining-the-cost-structures))。 为此，请在营销活动功能板中单击按 **[!UICONTROL Add a task]** 钮。 命名任务并单击 **[!UICONTROL Save]**。

然后，该任务会添加到任务列表。 您必须编辑它才能进行配置。

在标签 **[!UICONTROL Properties]** 中，选择服务和相应的成本类别：

![](assets/s_user_cost_mgmt_sample_14.png)

然后，单击任 **[!UICONTROL Expenses and revenue]** 务的图标，并指定估计的临时费用。

![](assets/s_user_cost_mgmt_sample_15.png)

在保存任务后，计算的成本与为估计临时成本输入的值一起指定。

当任务完成(状态 **[!UICONTROL Finished]** )时，计算的成本会自动更新为在其成本结构中输入的大会议室的成本。 此费用也会显示在细目的此类别中。

接下来，按照相同的过程再创建一个任务；计划超过五天，并且与先前创建的成本结构有关。

![](assets/s_user_cost_mgmt_sample_16.png)

任务完成后，将使用相关成本结构的值来指定计算成本，即在我们的示例中为1500欧元（5天x 300欧元）:

![](assets/s_user_cost_mgmt_sample_17.png)

#### 第6步——更新营销活动预算状态 {#step-6---update-the-campaign-budget-status}

配置营销活动后，可以将其设置为以更新其状态 **[!UICONTROL Specified]**。 然后，营销活动的计算成本将指示交付的计算成本和营销活动任务的总和：

![](assets/s_user_cost_mgmt_sample_18.png)

#### 预算批准 {#budget-approval}

激活批准后，可通过特殊链接从营销活动仪表板批准预算。 在启动定位工作流并且需要批准直接邮寄时，会显示此链接。

![](assets/s_user_cost_mgmt_sample_19.png)

然后，您可以单击链接以授予或拒绝批准，或者如果已为此营销活动激活通知，则使用通知电子邮件中的链接。

在预算获得批准且交付完成后，成本会通过特殊的技术工作流自动上传。

## 订单和发票 {#orders-and-invoices}

在MRM环境中，您可以向服务提供商保存订单并开具发票。 这些订单和发票的整个生命周期都可以通过Adobe Campaign界面进行管理。

### 订单创建 {#order-creation}

要与服务提供商一起保存新订单，请单击 **[!UICONTROL MRM > Orders]** 树的节点，然后单击按 **[!UICONTROL New]** 钮。

指定订单编号、相关服务提供商以及订单的总金额。

![](assets/s_user_cost_create_order.png)

### 开具和跟踪发票 {#issuing-and-tracking-invoices}

对于每个服务提供商，您可以保存发票并定义其状态和已支付的预算。

发票将创建并存储在Adobe Campaign **[!UICONTROL MRM > Invoices]** 树的节点中。

![](assets/s_user_cost_create_invoice.png)

发票由发票行组成，发票行的总数允许自动计算金额。 这些行是从选项卡中手动创建 **[!UICONTROL Invoice lines]** 的。 它们可以与订单关联，以便将信息上传到订单。

![](assets/s_user_cost_invoice_add_line.png)

每个服务提供商的发票显示在配置文件 **[!UICONTROL Invoices]** 的标签中：

![](assets/s_ncs_user_invoice_from_supplier.png)

在标 **[!UICONTROL Details]** 签中可显示发票的内容。

单 **[!UICONTROL Add]** 击以创建新发票。
