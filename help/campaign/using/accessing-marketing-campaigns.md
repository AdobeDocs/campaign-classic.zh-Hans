---
product: campaign
title: 访问营销活动
description: 访问营销活动
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1247'
ht-degree: 3%

---

# 访问营销活动{#accessing-marketing-campaigns}

![](../../assets/v7-only.svg)

Adobe Campaign允许您创建、配置、执行和分析营销活动。 所有营销活动都可从统一的控制中心进行管理。

## 工作区基础知识 {#workspace-basics}

### 主页 {#home-page}

连接到Adobe Campaign后，您将看到主页。

![](assets/campaign_global_view.png)

单击导航栏中的链接可访问各种功能。

促销活动元素位于 **[!UICONTROL Campaigns]** 选项卡：在这里，您可以看到营销项目和营销活动及其子集的概述。 营销计划由营销活动组成，营销活动由投放、任务、链接资源等组成。 在使用Campaign进行营销活动管理的情况下，有关投放、预算、审阅者和链接文档的信息可在营销活动中找到。

此 **[!UICONTROL Browsing]** 块 **[!UICONTROL Campaigns]** 选项卡提供了各种条目，具体取决于实例上安装的模块。 例如，您可以访问：

* **营销活动日历**：计划、营销策划、投放和营销活动的日历。 请参阅 [营销活动日历](#campaign-calendar).
* **营销活动**：访问所有营销策划中包含的营销活动。
* **投放**：访问链接到营销活动的投放。
* **Web应用程序**：对Web应用程序（表单、登陆页面等）的访问权限。

>[!NOTE]
>
>有关Adobe Campaign整体人机工程学、权限和配置文件管理功能的更多信息，请参阅 [本节](../../platform/using/adobe-campaign-workspace.md).
>
>与渠道和投放相关的所有功能详情，请参见 [本节](../../delivery/using/steps-about-delivery-creation-steps.md).

### 营销活动日历 {#campaign-calendar}

每个营销策划都属于一个项目，而该项目又属于一个计划。 计划、项目和营销策划可通过 **[!UICONTROL Campaign calendar]** 中的菜单 **营销活动** 选项卡。

要编辑计划、项目、营销策划或投放，请在日历中单击其名称，然后单击 **[!UICONTROL Open...]**. 然后，它将显示在新选项卡中，如下所示：

![](assets/d_ncs_user_interface_hierar.png)

您可以筛选营销活动日历中显示的信息。 要执行此操作，请单击 **[!UICONTROL Filter]** 链接并选择筛选条件。

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>在按日期过滤时，将显示开始日期晚于指定日期和/或结束日期早于指定日期的所有营销活动。 需要使用每个字段右侧的日历选择日期。

您还可以使用 **[!UICONTROL Search]** 用于筛选显示项的字段。

链接到每个项目的图标允许您查看其状态：已完成、进行中、正在编辑等。

### 浏览营销计划 {#browsing-in-a-marketing-program}

利用Campaign，可管理由各种营销活动组成的一组项目。 每个营销活动都包含投放以及关联的流程和资源。

#### 浏览程序 {#browsing-a-program}

编辑程序时，请使用下面描述的选项卡浏览和配置程序。

* 此 **计划** 选项卡显示某月、周或日的项目日历，具体取决于您在日历标题中单击的选项卡。

   如有必要，您可以通过此页面创建营销策划、项目或任务。

   ![](assets/s_ncs_user_interface_campaign02.png)

* 此 **编辑** 选项卡允许您个性化项目：名称、开始日期和结束日期、预算、链接文档等。

   ![](assets/s_ncs_user_interface_campaign05.png)

#### 浏览营销活动 {#browsing-campaigns}

可以通过活动日历、 **[!UICONTROL Schedule]** 选项卡，或营销策划列表。

1. 通过促销活动日历，选择要显示的促销活动，然后单击 **[!UICONTROL Open]** 链接。

   ![](assets/campaign_planning_edit_op.png)

   营销活动会在新选项卡中进行编辑，如下所示：

   ![](assets/campaign_op_edit.png)

1. 通过 **[!UICONTROL Schedule]** 选项卡上，编辑模式与通过营销策划日历的编辑模式相同。
1. 通过 **[!UICONTROL Campaigns]** 链接 **[!UICONTROL Campaigns]** 选项卡，单击要编辑的营销活动的名称。

   ![](assets/campaign_edit_from_list.png)

### 控制活动 {#controlling-a-campaign}

#### 仪表板 {#dashboard}

对于每个营销活动，作业、资源和投放都集中在一个屏幕中（即功能板），您可以通过该屏幕与其他人协作管理营销操作。

营销活动的仪表板用作控制界面。 它直接访问营销活动的主要创建和管理阶段：投放、提取文件、通知、预算等。

![](assets/s_ncs_user_op_board_start_del.png)

借助Adobe Campaign，您可以设置协作流程，用于创建和审批营销和通信活动的各个阶段：审批预算、目标、内容等。

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>有关营销活动模板的配置，请参见 [营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

#### 计划 {#schedule}

营销活动可集中处理一组投放。 对于每个活动，计划都会提供所有组件的全局视图：这使您能够显示任务和投放并轻松访问它们。

![](assets/campaign_planning_tab.png)

#### 论坛 {#forum}

对于每项活动，操作员可通过专用论坛交换消息。

有关更多信息，请参阅 [论坛](../../mrm/using/discussion-forums.md).

#### 报告 {#reports}

此 **[!UICONTROL Reports]** 链接可让您访问促销活动报表。

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>有关报告的详情，请参阅 [本节](../../reporting/using/about-adobe-campaign-reporting-tools.md).

#### 配置 {#configuration}

营销活动是通过营销活动模板创建的。 您可以配置已选择某些选项并已保存其他设置的可重用模板。 对于每个营销活动，都提供了以下功能：

* 引用文档和资源：您可以将文档与营销活动关联（简介、报告、图像等）。 支持所有文档格式。 参见 [管理关联文档](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents).
* 定义成本：对于每个促销活动，Adobe Campaign允许您定义成本录入和成本计算结构，以便在创建市场营销活动时使用。 例如：印刷费、使用外部机构、房租等。 参见 [定义成本类别](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories).
* 定义目标：您可以定义促销活动的可量化目标，例如订户数、业务量等。 此信息稍后会在营销活动报表中使用。
* 管理种子地址(有关更多信息，请参阅 [本节](../../delivery/using/about-seed-addresses.md))和控制组(请参阅 [定义控制组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group))。
* 管理审批：您可以选择要批准的处理，并根据需要选择审核操作员或操作员组。 参见 [检查和批准投放](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

>[!NOTE]
>
>要访问Campaign配置并对其进行更改，请单击 **[!UICONTROL Advanced campaign parameters...]** 中的链接 **[!UICONTROL Edit]** 选项卡。

## 使用Web界面 {#using-the-web-interface-}

您可以通过Internet浏览器访问Adobe Campaign控制台屏幕，以查看所有营销活动和投放以及数据库中用户档案的报告和信息。 此访问不会启用记录创建。 根据操作员的权限，您可以查看和/或处理数据库中的数据。 例如，您可以批准活动内容和定位、重新启动或停止投放等。

1. 照常通过https://登录`<your instance>:<port>/view/home`.
1. 使用菜单访问概述。

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

除了在营销策划之间导航和查看这些营销策划之外，您还可以执行以下类型的任务：

* 监测实例上的活动
* 参与验证过程，例如，批准或拒绝投放内容
* 执行其他快速操作，例如，暂停工作流
* 访问所有报告功能
* 参加论坛讨论

此表汇总了您可以从浏览器对营销活动执行的操作：

| 页面  | 操作 |
| --- | --- |
| 营销活动、投放、优惠等列表。 | 删除列表项 |
| 营销活动 | 取消营销活动 |
| 投放 | 批准投放内容和目标<br/>提交投放内容<br/>确认投放<br/>暂停和停止投放 |
| Web 应用程序 | 创建Web应用程序<br/>编辑应用程序内容和属性<br/>将应用程序内容另存为模板<br/>发布应用程序 |
| 优惠 | 批准优惠内容和资格<br/>禁用联机选件 |
| 任务 | 完成任务<br/>取消任务 |
| 营销资源 | 批准资源<br/>锁定和解锁资源 |
| Campaign 包 | 提交程序包以供审批<br/>批准或拒绝程序包<br/>取消包 |
| Campaign 订单 | 创建订单<br/>接受或拒绝订单 <!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| 库存 | 删除库存行 |
| 优惠模拟 | 启动和停止模拟 |
| 定位工作流 | 启动、暂停和停止工作流 |
| 报告 | 在报告历史记录中保存当前数据 |
| 论坛 | 添加讨论<br/>在讨论中回复消息<br/>关注讨论并取消订阅 |

### 审批

（例如，目标或投放内容）的批准可通过Web访问进行。

![](assets/campaign_web_interface_validation.png)

您还可以使用通知消息中包含的链接。 有关更多信息，请参阅 [检查和批准投放](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).
