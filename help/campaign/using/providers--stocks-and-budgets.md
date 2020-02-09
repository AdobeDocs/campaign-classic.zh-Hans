---
title: 供应商、库存和预算
seo-title: 供应商、库存和预算
description: 供应商、库存和预算
seo-description: null
page-status-flag: never-activated
uuid: 6caffaaf-a6a6-40e1-8b17-07c81748382c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: d4627141-cef1-4ddb-ad6a-5dc217b9fa96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 供应商、库存和预算{#providers-stocks-and-budgets}

Adobe Campaign允许您定义将参与营销活动中执行的任务的服务提供商。 有关服务提供商和相关成本结构的信息由Adobe Campaign管理员从主视图定义。 服务提供商从交付中引用，其成本结构允许计算与该交付相关的成本以及管理相关库存。

## 创建服务提供商及其成本结构 {#creating-service-providers-and-their-cost-structures}

每个服务提供商都保存在一个包含联系人详细信息、服务模板和相关作业的文件中。

在树的节点中配置 **[!UICONTROL Administration > Campaign management]** 了服务提供商。

在发送期间执行的任务由服务提供商执行，特别是对于直邮和移动渠道。 例如，这些服务提供商可以参与打印或分发消息。 这些任务涉及每个服务提供商特有的配置和成本。 服务提供商的配置涉及四个阶段：

1. 在Adobe Campaign中创建服务提供商

   请参 [阅添加服务提供商](#adding-a-service-provider)。

1. 定义相关服务模板的成本类别和结构

   请参 [阅定义成本类别](#defining-cost-categories)[和定义成本结构](#defining-the-cost-structure)。

1. 进程配置

   请参 [阅配置与服务关联的进程](#configuring-processes-associated-with-a-service)。

1. 在营销活动级别引用服务提供商

   请参 [阅将服务与营销活动关联](#associating-a-service-with-a-campaign)。

### 创建服务提供商及其成本类别 {#creating-a-service-provider-and-its-cost-categories}

#### 添加服务提供商 {#adding-a-service-provider}

您可以根据需要创建任意数量的服务提供商来进行分发。 添加服务提供商的过程如下：

1. 右键单击服务提供商列表并选择 **[!UICONTROL New]**，或单击服务 **[!UICONTROL New]** 提供商列表上方的按钮。
1. 在窗口的下半部分，指定服务提供商的名称和联系人详细信息。

   ![](assets/s_ncs_user_supplier_node_01.png)

1. 单击该 **[!UICONTROL Save]** 按钮可将服务提供商添加到列表中。

#### 定义成本类别 {#defining-cost-categories}

您必须将服务模板与每个服务提供商相关联。 在这些模板中，您必须首先确定成本类别，并在必要时确定相关库存。 然后，您必须通过成本结构为每个类别创建成本计算规则。

>[!NOTE]
>
>有关详细信息，请参阅定 [义成本结构](#defining-the-cost-structure)。

成本类别是包含一组符合交付类型（电子邮件、直邮等）资格的成本的实体或任务。 成本类别在与服务提供商关联的服务的模板中分组。 每个服务提供商可以引用一个或多个服务模板。

要创建服务模板并定义其内容，请应用以下步骤：

1. 在服务提 **[!UICONTROL Services]** 供商的选项卡中，单击按钮并 **[!UICONTROL Add]** 命名服务模板。

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. 为每种流程类型（通过直邮／电子邮件／等）创建成本类别。 或任务)。 要执行此操作，请单击标 **[!UICONTROL Cost categories]** 签，然后单击按 **[!UICONTROL Add]** 钮，然后输入每个成本类别的参数。

   ![](assets/s_ncs_user_supplier_node_03.png)

   * 为此成本类别输入标签，然后选择相关的流程类型：通过、 **[!UICONTROL Direct mail]**、 **[!UICONTROL E-mail]**、、 **[!UICONTROL Mobile]**&#x200B;或 **[!UICONTROL Telephone]**&#x200B;者交付 **[!UICONTROL Fax]****[!UICONTROL Task]**。
   * 单击按 **[!UICONTROL Add]** 钮可定义与此类别关联的成本类型。
   * 如有必要，将库存线与每种类型的成本相关联，以便使用的数量将自动与现有库存相关联。

      >[!NOTE]
      >
      >库存行在节点中定 **[!UICONTROL Stock management]** 义。\
      >有关详细信息，请参阅 [Stock和订单管理](#stock-and-order-management)。

1. 您可以为此成本类别预选一个值，默认情况下，该值将在服务提供商成本类别中提供（而不是空白）。 为此，请在列中为相关类 **[!UICONTROL Selected]** 型选择相应的选项：

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   在交付级别，默认情况下将选择该值：

   ![](assets/s_ncs_user_supplier_default_cost.png)

### 定义成本结构 {#defining-the-cost-structure}

对于每种类型的成本，成本结构指定要应用的计算规则。

单击标 **[!UICONTROL Cost structure]** 签可配置每个成本类别和类型的成本计算。 单击 **[!UICONTROL Add]** 并输入成本结构。

![](assets/s_ncs_user_supplier_node_04.png)

* 要创建成本结构，请从下拉列表中选择消息类型和相关的成本类别，以及将应用计算规则的成本类型。 这些下拉列表的内容来自通过选项卡输入的信 **[!UICONTROL Cost categories]** 息。

   您必须为成本结构分配标签。 默认情况下，它具有以下交付大纲：成 **本类别——成本类型**。

   但是，您可以重命名它：直接在字段中输入所需的 **[!UICONTROL Label]** 值。

* 成本计算公式在窗口的下部定义。

   此公式可以固定（对于任意数量的消息）或根据消息数计算。

   当它取决于消息的数量时，成本计算结构可以 **[!UICONTROL Linear]**&#x200B;是、 **[!UICONTROL Linear by threshold]**&#x200B;或 **[!UICONTROL Constant by threshold]**。

#### 线性结构 {#linear-structure}

如果消息（或一批消息）的金额始终相同，而与消息总数无关，请选择并输 **[!UICONTROL Linear]** 入每条消息的成本。

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

如果此数量适用于一批消息，则指定字段中相关消息的 **[!UICONTROL for]** 数量。

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### 基于阈值的线性结构 {#linear-structure-by-threshold}

如果金额按每条消息的阈值应用，则必须定义计算 **[!UICONTROL Linear by threshold]** 结构。 在此类费用结构中，每条消息的费用为0.13，例如，如果消息的总数在1到100之间，并且从发送的100到1000条消息的费用为0.12，或者从发送的1000条消息的费用为0.11。

配置将如下：

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

要添加阈值，请单 **[!UICONTROL Add]** 击列表右侧的按钮。

#### 按阈值的恒定结构 {#constant-structure-by-threshold}

最后，您可以根据消息总数配置成本计算。 为此，请选择计算 **[!UICONTROL Constant by threshold]** 结构。 例如，对于1到100条消息，成本将设置为固定金额12.00，对于101到1000条消息，成本将设置为100.00，对于超过1000条消息的任何发送，成本将设置为固定金额500.00，无论总数是多少。

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### 配置与服务关联的进程 {#configuring-processes-associated-with-a-service}

您可以通过选项卡关联与服务关联的进程的相关 **[!UICONTROL Processes]** 信息。

为此，请单击选 **[!UICONTROL Processes]** 项卡，配置向路由器发送信息。

![](assets/s_ncs_user_supplier_node_02.png)

* 此部 **[!UICONTROL File extraction]** 分指示选择此服务时用于交付的导出模板。 您可以在字段中指示输出文件的名 **[!UICONTROL Extraction file]** 称。 通过字段右侧的按钮可插入变量。

   ![](assets/s_ncs_user_supplier_node_02a.png)

* 在该 **[!UICONTROL Notification e-mail]** 部分中，您可以指定在文件发送后通知服务提供商的模板。 选择用于创建警报消息的模板和收件人组。

   默认情况下，通知消息的传送模板会保存在节 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 点中，该节点可从常规视图访问。

* 通过 **[!UICONTROL Post-processing]** 此部分，您可以选择要在分发获得批准后启动的工作流。 如果输入了工作流模板，则会自动创建工作流实例，然后在批准生效后立即启动。 例如，此工作流可以将提取文件发送到外部服务提供商进行处理。

### 将服务与营销活动关联 {#associating-a-service-with-a-campaign}

服务通过交付或任务与营销活动关联。 服务提供商链接到交付模板，以在通过此模板创建的交付中提供其服务。

当选择服务时，与传送类型（直邮、电子邮件等）对应的成本类别中心表中自动指示，以及已定义的处理选项。

>[!NOTE]
>
>如果在选择服务时不显示任何成本类别，则表示未为此类流程定义任何成本类别。 例如，对于电子邮件发送，如果未定义类 **[!UICONTROL E-mail]** 型成本类别，则不显示任何类别，并且选择服务将不起作用。

* 对于直邮递送，您可以从配置窗口中选择服务。

   ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* 对于在移动渠道、传真或电话上传送，则采用相同的选择模式。
* 对于电子邮件传送，该服务会从传送属性 **[!UICONTROL Advanced]** 的选项卡中进行选择，如下例所示：

   ![](assets/s_ncs_user_supplier_email_delivery_select.png)

通过 **[!UICONTROL Amount to surcharge]** 该列，您可以在相关交付或任务的上下文中为此类别添加成本。

在为交货定义成本类别期间，您可以强制选择成本类型。 为此，请选择 **[!UICONTROL A cost type must be selected]**。

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## 库存和订单管理 {#stock-and-order-management}

成本类型可以与库存行关联，以便处理警报、跟踪供应和启动订单。

在Adobe Campaign中设置库存和订单管理以及在供应不足时通知运营商执行交付的步骤如下：

1. 关联服务提供商的Stock创建和引用

   请参 [阅创建库存](#creating-a-stock)。

1. 添加库存行

   请参 [阅添加库存线](#adding-stock-lines)。

1. 在出现警报时通知运营商

   请参 [阅警报操作员](#alerting-operators)。

1. 订单和供应。

   请参阅 [订单](#orders)。

### 库存管理 {#stock-management}

如果库存不足或达到最低阈值，Adobe Campaign可以提醒一组运营商。 通过导航区域的链 **[!UICONTROL Stocks]** 接可以通过 **[!UICONTROL Campaigns]** 宇宙的链 **[!UICONTROL Other choices]** 接访问库存水平。

![](assets/s_ncs_user_stocks_view.png)

#### 创建库存 {#creating-a-stock}

应用以下步骤创建新库存：

1. 单击 **[!UICONTROL Create]** 股票列表上方的按钮。
1. 输入Stock的标签，然后从下拉列表中选择与之关联的服务提供商。

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >有关详细信息，请参阅创 [建服务提供商及其成本结构](#creating-service-providers-and-their-cost-structures)。

#### 添加库存行 {#adding-stock-lines}

一种包括各种股线的股线。 库存行包含交货将消耗的初始资源数量。 每个库存行指示已消耗的数量、库存数量和订购数量。

创建库存时，单击标 **[!UICONTROL Stock lines]** 签以添加新行。

![](assets/s_ncs_user_stocks_display_line.png)

创建库存后，单击它即可进行编辑，并使用其功能板创建和查看库存线。

单击按 **[!UICONTROL Create]** 钮以定义库存参数。

![](assets/s_ncs_user_stocks_new_line.png)

* 在字段中指示最初库存的 **[!UICONTROL Initial stock]** 数量。 系统会 **[!UICONTROL Consumed]** 自动计 **[!UICONTROL In stock]** 算和字段，并会根据营销活动进度更新这些字段。

   ![](assets/s_ncs_user_stocks_create_line.png)

* 指示字段中应提醒操作员订购库存的阈 **[!UICONTROL Alert level]** 值。 达到警报级别后，使用此库存的交货的批准窗口中将显示一条警告消息。

#### 将库存与成本类别关联 {#associating-a-stock-with-cost-categories}

对于给定的服务提供商，在服务中，库存线可以由成本类别之一引用，如下所示：

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### Stock跟踪 {#stock-tracking}

#### 通知运营商 {#alerting-operators}

当交货中引用的库存不足时，将显示警报。 例如，提取文件获得批准时，将显示以下警报：

![](assets/s_ncs_user_stocks_valid_alert.png)

#### 订单 {#orders}

通过 **[!UICONTROL Orders]** 子标签可以查看当前订单并保存新订单。

![](assets/s_ncs_user_stocks_edit_from_board.png)

要保存订单，请编辑目标库存行，单击 **[!UICONTROL Add]** 按钮并指定交货日期和订购数量。

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>到达交货日期后，订购的库存行会自动消失，并在字段中输入的数 **[!UICONTROL Volume on order]** 量会添加到标签 **[!UICONTROL Tracking]** 中。 此数量会自动添加到库存量。

![](assets/s_ncs_user_stocks_node_08.png)

该选 **[!UICONTROL Consumptions]** 项卡包含每个营销活动的消耗量。 此标签中的信息会根据执行的提交自动输入。 单击该 **[!UICONTROL Edit]** 按钮可打开相关的营销活动。

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## 计算预算 {#calculating-budgets}

### 原则 {#principle}

为交付和营销活动管理成本。 根据进度，这些费用将分配至预算。

营销活动的交付成本在营销活动级别进行合并，并且计划的所有营销活动的成本将传递到与之关联的计划。 专用报告可让您跟踪整个平台或每个计划和每个计划的预算。

### 实施 {#implementation}

在营销活动中，选择预算时，必须输入初始金额。 计算的成本将根据所输入金额（支出、预期、保留、承诺）的承诺级别自动更新。 请参 [阅计算金额](../../campaign/using/controlling-costs.md#calculating-amounts)。

>[!NOTE]
>
>创建预算中介绍了创建预 [算的过程](../../campaign/using/controlling-costs.md#creating-a-budget)。

