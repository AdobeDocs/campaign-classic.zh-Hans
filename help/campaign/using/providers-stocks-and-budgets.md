---
product: campaign
title: 供应商、库存和预算
description: 供应商、库存和预算
role: User
feature: Budget Management, Campaigns
hide: true
hidefromtoc: true
exl-id: c60c4f86-a957-4c44-a0fe-39b6e3f0e5d6
source-git-commit: 4f809011a8b4cb3803c4e8151e358e5fd73634e4
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 0%

---

# 供应商、库存和预算{#providers-stocks-and-budgets}

Adobe Campaign允许您定义将参与在营销活动中执行的作业的服务提供商。 Adobe Campaign管理员从主视图中定义有关服务提供商和相关成本结构的信息。 服务提供商从交付中引用，其成本结构允许计算与此交付相关的成本以及相关库存的管理。

## 创建服务提供商及其成本结构 {#creating-service-providers-and-their-cost-structures}

每个服务提供商都保存在包含联系人详细信息、服务模板和相关作业的文件中。

在树的&#x200B;**[!UICONTROL Administration > Campaign management]**&#x200B;节点中配置了服务提供程序。

在投放期间执行的作业由服务提供商执行，特别是对于直邮和移动渠道。 例如，这些服务提供商可以参与打印或分发消息。 这些作业涉及特定于每个服务提供商的配置和成本。 服务提供商的配置涉及四个阶段：

1. 在Adobe Campaign中创建服务提供商

   请参阅[添加服务提供程序](#adding-a-service-provider)。

1. 定义关联服务模板的成本类别和结构

   请参阅[定义成本类别](#defining-cost-categories)和[定义成本结构](#defining-the-cost-structure)。

1. 配置进程

   请参阅[配置与服务关联的进程](#configuring-processes-associated-with-a-service)。

1. 在营销活动级别引用服务提供商

   请参阅[将服务与营销活动关联](#associating-a-service-with-a-campaign)。

### 创建服务提供商及其成本类别 {#creating-a-service-provider-and-its-cost-categories}

#### 添加服务提供商 {#adding-a-service-provider}

您可以根据投放需要创建任意数量的服务提供商。 添加服务提供商的过程如下：

1. 右键单击服务提供商列表并选择&#x200B;**[!UICONTROL New]**，或单击服务提供商列表上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮。
1. 在窗口的下半部分，指定服务提供商的名称和联系详细信息。

   ![](assets/s_ncs_user_supplier_node_01.png)

1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;按钮以将服务提供商添加到列表。

#### 定义成本类别 {#defining-cost-categories}

必须将服务模板与每个服务提供商关联。 在这些模板中，您必须首先确定成本类别以及相关的库存（如有必要）。 然后，您必须通过成本结构为每个类别创建成本计算规则。

>[!NOTE]
>
>有关详情，请参阅[定义成本结构](#defining-the-cost-structure)。

成本类别是一个实体，其中包含一组符合投放类型（电子邮件、直邮等）或任务条件的成本。 成本类别在与服务提供者相关联的服务的模板中分组。 每个服务提供商可以引用一个或多个服务模板。

要创建服务模板并定义其内容，请应用以下步骤：

1. 在服务提供程序的&#x200B;**[!UICONTROL Services]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并命名服务模板。

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. 为每种流程类型（通过直邮/电子邮件/等传递）创建成本类别。 或任务)。 为此，请单击&#x200B;**[!UICONTROL Cost categories]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后输入每个成本类别的参数。

   ![](assets/s_ncs_user_supplier_node_03.png)

   * 输入此成本类别的标签并选择相关的进程类型：由&#x200B;**[!UICONTROL Direct mail]**、**[!UICONTROL Email]**、**[!UICONTROL Mobile]**、**[!UICONTROL Telephone]**&#x200B;或&#x200B;**[!UICONTROL Task]**&#x200B;投放。
   * 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以定义与此类别关联的成本类型。
   * 如有必要，将库存行与每种成本类型相关联，以便使用的数量将自动与现有库存相关联。

     >[!NOTE]
     >
     >在&#x200B;**[!UICONTROL Stock management]**&#x200B;节点中定义了Stock线。\
     >有关详情，请参阅[库存和订单管理](#stock-and-order-management)。

1. 您可以为此成本类别预先选择一个值，默认情况下，服务提供商成本类别中会提供该值（而不是空白值）。 为此，请在&#x200B;**[!UICONTROL Selected]**&#x200B;列中为相关类别类型选择选项：

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   在投放级别，默认情况下将选中值：

   ![](assets/s_ncs_user_supplier_default_cost.png)

### 定义成本结构 {#defining-the-cost-structure}

对于每种类型的成本，成本结构会指定要应用的计算规则。

单击&#x200B;**[!UICONTROL Cost structure]**&#x200B;选项卡为每个成本类别和类型配置成本计算。 单击&#x200B;**[!UICONTROL Add]**&#x200B;并输入成本结构。

![](assets/s_ncs_user_supplier_node_04.png)

* 要创建成本结构，请从下拉列表中选择消息类型和相关的成本类别，以及计算规则将应用的成本类型。 这些下拉列表的内容来自通过&#x200B;**[!UICONTROL Cost categories]**&#x200B;选项卡输入的信息。

  您必须为成本结构分配标签。 默认情况下，它具有以下投放概要：**成本类别 — 成本类型**。

  但是，您可以对其进行重命名：直接在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入所需的值。

* 成本计算公式在窗口的下半部分定义。

  此公式可以固定（适用于任意数量的消息），也可以根据消息数量进行计算。

  当它取决于消息数时，成本计算结构可以是&#x200B;**[!UICONTROL Linear]**、**[!UICONTROL Linear by threshold]**&#x200B;或&#x200B;**[!UICONTROL Constant by threshold]**。

#### 线性结构 {#linear-structure}

如果无论消息总数如何，一条消息（或一批消息）的金额始终相同，请选择&#x200B;**[!UICONTROL Linear]**&#x200B;并输入每条消息的成本。

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

如果此金额适用于一批邮件，请在&#x200B;**[!UICONTROL for]**&#x200B;字段中指定相关邮件数。

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### 阈值线性结构 {#linear-structure-by-threshold}

如果金额按阈值应用于每封邮件，则必须定义&#x200B;**[!UICONTROL Linear by threshold]**&#x200B;计算结构。 在此类型的成本结构中，每条报文的费用为0.13，例如，如果报文总数在1到100条之间，每条报文的费用为0.12，如果发送了100到1000条报文，每条报文的费用为0.11，如果发送了1000条报文，每条报文的费用为0.11。

配置将如下所示：

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

要添加阈值，请单击列表右侧的&#x200B;**[!UICONTROL Add]**&#x200B;按钮。

#### 阈值常量结构 {#constant-structure-by-threshold}

最后，您可以根据报文总数配置成本计算。 为此，请选择&#x200B;**[!UICONTROL Constant by threshold]**&#x200B;计算结构。 例如，对于1到100条报文，成本将设置为12.00的固定金额；对于101到1000条报文的投放，成本将设置为100.00；对于超过1000条报文的任何投放，成本都将设置为500.00，无论总数如何。

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### 配置与服务关联的进程 {#configuring-processes-associated-with-a-service}

您可以通过&#x200B;**[!UICONTROL Processes]**&#x200B;选项卡关联与服务关联的进程信息。

为此，请单击&#x200B;**[!UICONTROL Processes]**&#x200B;选项卡以配置向路由器发送信息。

![](assets/s_ncs_user_supplier_node_02.png)

* **[!UICONTROL File extraction]**&#x200B;部分指示选择此服务时用于投放的导出模板。 您可以在&#x200B;**[!UICONTROL Extraction file]**&#x200B;字段中指明输出文件的名称。 利用字段右侧的按钮，可插入变量。

  ![](assets/s_ncs_user_supplier_node_02a.png)

* **[!UICONTROL Notification email]**&#x200B;部分允许您指定发送文件后通知服务提供商的模板。 选择用于创建警报消息和收件人组的模板。

  默认情况下，通知消息的投放模板保存在可从常规视图访问的&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;节点中。

* 通过&#x200B;**[!UICONTROL Post-processing]**&#x200B;部分，可选择在批准投放后启动的工作流。 如果输入了工作流模板，则会自动创建工作流实例，并在批准生效后立即启动。 例如，此工作流可以将提取文件发送到外部服务提供商进行处理。

### 将服务与活动关联 {#associating-a-service-with-a-campaign}

服务通过投放或任务与活动关联。 服务提供商将链接到投放模板，以在通过此模板创建的投放中提供其服务。

选择服务后，与投放类型（直邮、电子邮件等）对应的成本类别以及已定义的处理选项会自动在中心表中指示。

>[!NOTE]
>
>如果在选择服务时没有显示成本类别，则意味着没有为此类型的流程定义成本类别。 例如，对于电子邮件投放，如果未定义&#x200B;**[!UICONTROL Email]**&#x200B;类型成本类别，则不会显示任何类别，并且选择服务将不会产生任何效果。

* 对于直邮投放，您可以从配置窗口中选择服务。

  ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* 对于通过移动渠道或电话投放，将应用相同的选择模式。
* 对于电子邮件投放，从投放属性的&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中选择服务，如以下示例所示：

  ![](assets/s_ncs_user_supplier_email_delivery_select.png)

**[!UICONTROL Amount to surcharge]**&#x200B;列允许您在相关投放或任务的上下文中为此类别添加成本。

您可以在定义交货的成本类别时，强制强制选择成本类型。 为此，请选择&#x200B;**[!UICONTROL A cost type must be selected]**。

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## 库存和订单管理 {#stock-and-order-management}

成本类型可与库存行关联，以便处理预警、跟踪供应和启动订单。

在Adobe Campaign建立库存和订单管理流程，并在要交付的供应不足时提醒操作员，具体流程如下：

1. 股票创建和引用关联的服务提供商

   请参阅[创建库存](#creating-a-stock)。

1. 添加坯件线

   请参阅[添加库存行](#adding-stock-lines)。

1. 在出现警报时通知操作员

   请参阅[警报运算符](#alerting-operators)。

1. 订单和供应。

   请参阅[订单](#orders)。

### 库存管理 {#stock-management}

如果库存耗尽或达到最小阈值，Adobe Campaign可以提醒一组操作员。 库存水平可通过导航区域的&#x200B;**[!UICONTROL Other choices]**&#x200B;链接通过&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Stocks]**&#x200B;链接访问。

![](assets/s_ncs_user_stocks_view.png)

#### 创建库存 {#creating-a-stock}

应用以下步骤创建新库存：

1. 单击股票列表上方的&#x200B;**[!UICONTROL Create]**&#x200B;按钮。
1. 输入库存的标签，然后从下拉列表中选择与其关联的服务提供商。

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >有关详情，请参阅[创建服务提供商及其成本结构](#creating-service-providers-and-their-cost-structures)。

#### 添加坯件线 {#adding-stock-lines}

一种坯件包括各种坯件线。 库存行包含交货将消耗的初始资源数量。 每个库存行指示消耗数量、库存数量和订购数量。

创建图库时，单击&#x200B;**[!UICONTROL Stock lines]**&#x200B;选项卡以添加新行。

![](assets/s_ncs_user_stocks_display_line.png)

创建坯件后，单击它以进行编辑，并使用其操控板创建和查看坯件线。

单击&#x200B;**[!UICONTROL Create]**&#x200B;按钮以定义毛坯参数。

![](assets/s_ncs_user_stocks_new_line.png)

* 在&#x200B;**[!UICONTROL Initial stock]**&#x200B;字段中指示初始库存数量。 **[!UICONTROL Consumed]**&#x200B;和&#x200B;**[!UICONTROL In stock]**&#x200B;字段会自动计算并随营销活动进度更新。

  ![](assets/s_ncs_user_stocks_create_line.png)

* 在&#x200B;**[!UICONTROL Alert level]**&#x200B;字段中指明应向操作员发出订购库存警报的阈值。 达到警报级别后，使用此库存的交货的审批窗口中将显示警告消息。

#### 将库存与成本类别关联 {#associating-a-stock-with-cost-categories}

对于给定的服务提供商，在服务中，库存行可以由成本类别之一引用，如下所示：

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### 库存跟踪 {#stock-tracking}

#### 警报运算符 {#alerting-operators}

当投放中引用的库存不足时，会显示警报。 例如，在批准提取文件时，将显示以下警报：

![](assets/s_ncs_user_stocks_valid_alert.png)

#### 顺序 {#orders}

**[!UICONTROL Orders]**&#x200B;子选项卡允许您查看当前订单并保存新订单。

![](assets/s_ncs_user_stocks_edit_from_board.png)

要保存订单，请编辑目标库存行，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮并指定交货日期和订购数量。

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>到达交货日期后，订购的库存行会自动消失，并且在&#x200B;**[!UICONTROL Volume on order]**&#x200B;字段中输入的数量将添加到&#x200B;**[!UICONTROL Tracking]**&#x200B;选项卡中。 此数量将自动添加到库存体积中。

![](assets/s_ncs_user_stocks_node_08.png)

**[!UICONTROL Consumptions]**&#x200B;选项卡包含每个营销活动使用的卷。 此选项卡中的信息会根据执行的投放自动输入。 单击&#x200B;**[!UICONTROL Edit]**&#x200B;按钮以打开相关营销策划。

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## 正在计算预算 {#calculating-budgets}

### 原则 {#principle}

管理投放和营销活动的成本。 根据进度，该等成本分配至预算。

营销活动的投放成本在营销活动级别进行合并，项目的所有营销活动的成本都会传递到与其关联的项目。 通过专用报告，您可以跟踪整个平台或每个计划和每个项目的预算。

### 实现 {#implementation}

在市场活动中，当您选择预算时，必须输入初始金额。 计算成本将根据所输入金额（已产生、预期、已保留、已承诺）之承担水平自动更新。 请参阅[计算金额](../../mrm/using/controlling-costs.md#calculating-amounts)。

>[!NOTE]
>
>[创建预算](../../mrm/using/controlling-costs.md#creating-a-budget)中介绍了创建预算的过程。
