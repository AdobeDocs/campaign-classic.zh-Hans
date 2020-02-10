---
title: 访问营销活动
seo-title: 访问营销活动
description: 访问营销活动
seo-description: null
page-status-flag: never-activated
uuid: a482be37-61bb-4588-9dfb-f9c3ee5a1930
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
discoiquuid: 8e7eb53c-bbe2-4bd4-8581-c2a63a3dc84e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 访问营销活动{#accessing-marketing-campaigns}

Adobe Campaign可让您创建、配置、执行和分析营销活动。 所有营销活动都可以从统一的控制中心进行管理。

## 工作区基础知识 {#workspace-basics}

### 主页 {#home-page}

连接到Adobe Campaign后，您将看到主页。

![](assets/campaign_global_view.png)

单击导航栏中的链接可访问各个宇宙。

营销活动元素存在于世 **[!UICONTROL Campaigns]** 界中：您可以在此处查看营销计划和营销活动及其子集的概述。 营销计划由营销活动组成，这些活动由交付、任务、链接资源等组成。 在使用营销活动进行营销活动管理的上下文中，有关分发、预算、审阅者和链接文档的信息可在营销活动中找到。

宇宙的导航块提 **[!UICONTROL Campaigns]** 供各种条目，具体取决于实例上安装的模块。 例如，您可以访问：

* **营销活动日历**:计划、营销计划、交付和营销活动的日历。 请参阅 [Campaign日历](#campaign-calendar)。
* **营销活动**:访问所有营销计划中包含的营销活动。
* **交付**:访问链接到营销活动的分发。
* **Web应用程序**:访问Web应用程序（表单、调查等）。

>[!NOTE]
>
>有关Adobe Campaign整体人机工程学、权限和配置文件管理功能的更多信息，请参 [阅此部分](../../platform/using/adobe-campaign-workspace.md)。
>
>与渠道和交付相关的所有功能在本节中 [有详细说明](../../delivery/using/communication-channels.md)。

### 营销活动日历 {#campaign-calendar}

每个营销活动都属于一个计划，而该计划又属于一个计划。 计划、计划和营销活动可通过“营销活动” **[!UICONTROL Campaign calendar]** 范围中的菜单 **访问** 。

要编辑计划、计划、营销活动或分发，请在日历中单击其名称，然后单击 **[!UICONTROL Open...]**。 然后，它会显示在新选项卡中，如下所示：

![](assets/d_ncs_user_interface_hierar.png)

您可以过滤营销活动日历中显示的信息。 要执行此操作，请单击链 **[!UICONTROL Filter]** 接并选择筛选条件。

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>当您按日期进行筛选时，将显示所有开始日期晚于指定日期和／或结束日期早于指定日期的营销活动。 需要使用每个字段右侧的日历选择日期。

您还可以使用字 **[!UICONTROL Search]** 段过滤显示的项目。

链接到每个项目的图标可让您查看其状态：完成、进行中、正在编辑等。

### 在营销计划中浏览 {#browsing-in-a-marketing-program}

Campaign允许您管理由各种营销活动组成的一组计划。 每个营销活动都包含分发以及关联的流程和资源。

#### 浏览程序 {#browsing-a-program}

编辑程序时，请使用下面介绍的选项卡浏览并配置它。

* “ **计划** ”选项卡显示月、周或日的程序日历，具体取决于您在日历标题中单击的选项卡。

   如有必要，您可以通过此页面创建营销活动、计划或任务。

   ![](assets/s_ncs_user_interface_campaign02.png)

* 通过“ **编辑** ”选项卡，您可以个性化程序：名称、开始日期和结束日期、预算、链接的文档等。

   ![](assets/s_ncs_user_interface_campaign05.png)

#### 浏览营销活动 {#browsing-campaigns}

可通过营销活动日历、计划的选 **[!UICONTROL Schedule]** 项卡或营销活动列表访问营销活动。

1. 通过系列活动日历，选择要显示的系列活动，然后单击链 **[!UICONTROL Open]** 接。

   ![](assets/campaign_planning_edit_op.png)

   营销活动会在新选项卡中进行编辑，如下所示：

   ![](assets/campaign_op_edit.png)

1. 通过程 **[!UICONTROL Schedule]** 序的选项卡，编辑模式与通过系列活动日历的编辑模式相同。
1. 通过 **[!UICONTROL Campaigns]** 范围链接， **[!UICONTROL Campaigns]** 单击要编辑的营销活动的名称。

   ![](assets/campaign_edit_from_list.png)

### 控制营销活动 {#controlling-a-campaign}

#### 功能板 {#dashboard}

对于每个营销活动，任务、资源和交付都集中在一个屏幕（仪表板）中，通过该屏幕，您可以与其他人协作管理营销操作。

营销活动的仪表板用作控制界面。 它直接访问主营销活动创建和管理阶段：交付、提取文件、通知、预算等。

![](assets/s_ncs_user_op_board_start_del.png)

通过Adobe Campaign，您可以设置协作流程，以便创建和批准营销和通信营销活动的各个阶段：预算、目标、内容等的批准。

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>系列活动模板的配置显示在系列活动 [模板中](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

#### 计划 {#schedule}

营销活动集中化一组分发。 对于每个营销活动，计划提供所有组件的全局视图：这样，您便可以显示任务和交付，并轻松访问它们。

![](assets/campaign_planning_tab.png)

#### 论坛 {#forum}

对于每个营销活动，运营商都可以通过专用论坛交换消息。

For more on this, refer to [Discussion forums](../../campaign/using/discussion-forums.md).

#### 报告 {#reports}

通过 **[!UICONTROL Reports]** 链接可访问系列活动报告。

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>本节详细介绍 [了报告](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

#### 配置 {#configuration}

营销活动是通过营销活动模板创建的。 您可以配置可重用的模板，其中已选择某些选项并保存其他设置。 对于每个营销活动，都提供以下功能：

* 文档和资源的引用：您可以将文档与营销活动（简介、报告、图像等）关联。 支持所有文档格式。 请参阅 [管理关联的文档](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)。
* 定义成本：对于每个营销活动，Adobe Campaign允许您定义成本条目和成本计算结构，这些内容可用于创建营销活动。 例如：印刷成本、使用外部代理、房间租赁等。 请参阅 [定义成本类别](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories)。
* 定义目标：您可以为营销活动定义可量化的目标，例如订阅者数量、业务量等。 此信息稍后将用于营销活动报告。
* 管理种子地址(有关详细信息，请参 [阅本节](../../delivery/using/about-seed-addresses.md))和控制组(请参阅 [定义控制组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group))。
* 管理批准：您可以选择要批准的处理，并根据需要选择审核操作符或操作符组。 请参 [阅检查和批准交货](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

>[!NOTE]
>
>要访问营销活动配置并对其进行更改，请单击选 **[!UICONTROL Advanced campaign parameters...]** 项卡中的链 **[!UICONTROL Edit]** 接。 有关在营销活动级别设置参数以自动继承值的详细信息，请参阅我们 [的技术说明](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Setparametersatthecampaignlevelsodeliveriesinheritvaluesautomatically)。

## 使用Web界面 {#using-the-web-interface-}

您可以通过Internet浏览器访问Adobe Campaign控制台屏幕，以查看所有营销活动和分发以及数据库中配置文件的报告和信息。 此访问不启用记录创建。 根据运营商权限，您可以查看和／或对数据库中的数据执行操作。 例如，您可以批准营销活动内容和定位、重新启动或停止分发等。

1. 通过https://照常登录`<your instance>:<port>/view/home`。
1. 使用菜单访问概述。

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

可以通过Web访问进行批准（例如，目标或交付内容）。

![](assets/campaign_web_interface_validation.png)

您还可以使用通知消息中包含的链接。 有关详细信息，请参 [阅检查和批准交货](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。
