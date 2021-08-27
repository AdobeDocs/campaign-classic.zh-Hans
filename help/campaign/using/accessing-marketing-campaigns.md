---
product: campaign
title: 访问营销活动
description: 访问营销活动
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 2%

---

# 访问营销活动{#accessing-marketing-campaigns}

![](../../assets/common.svg)

Adobe Campaign允许您创建、配置、执行和分析营销活动。 所有营销活动都可从统一的控制中心进行管理。

## 工作区基础知识 {#workspace-basics}

### 主页 {#home-page}

连接到Adobe Campaign后，您将看到主页。

![](assets/campaign_global_view.png)

单击导航栏中的链接以访问各种功能。

营销活动元素位于&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡中：在这里，您可以看到营销项目和营销策划的概述及其子集。 营销计划由营销策划组成，营销策划由投放、任务、链接的资源等组成。 在使用Campaign进行营销活动管理的背景下，有关投放、预算、审阅人和链接文档的信息可在营销活动中找到。

**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Browsing]**&#x200B;块提供了各种条目，具体取决于实例上安装的模块。 例如，您可以访问：

* **营销活动日历**:计划、营销计划、投放和营销策划的日历。请参阅[营销活动日历](#campaign-calendar)。
* **营销活动**:访问所有营销项目中包含的营销活动。
* **投放**:对链接到营销策划的投放的访问权限。
* **Web应用程序**:访问web应用程序（表单、登陆页面等）。

>[!NOTE]
>
>有关Adobe Campaign整体人机工程学、权限和用户档案管理功能的更多信息，请参阅[此部分](../../platform/using/adobe-campaign-workspace.md)。
>
>[此部分](../../delivery/using/steps-about-delivery-creation-steps.md)中详细描述了与渠道和投放相关的所有功能。

### 营销活动日历 {#campaign-calendar}

每个营销活动都属于一个项目，而该项目又属于一个计划。 可通过&#x200B;**营销活动**&#x200B;选项卡的&#x200B;**[!UICONTROL Campaign calendar]**&#x200B;菜单访问计划、项目和营销活动。

要编辑计划、项目群、营销活动或投放，请在日历中单击其名称，然后单击&#x200B;**[!UICONTROL Open...]**。 随后，它会显示在新选项卡中，如下所示：

![](assets/d_ncs_user_interface_hierar.png)

您可以过滤营销活动日历中显示的信息。 为此，请单击&#x200B;**[!UICONTROL Filter]**&#x200B;链接并选择筛选条件。

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>当您按日期过滤时，所有开始日期晚于指定日期和/或结束日期早于指定日期的营销活动都会显示。 需要使用每个字段右侧的日历选择日期。

您还可以使用&#x200B;**[!UICONTROL Search]**&#x200B;字段过滤显示的项目。

链接到每个项目的图标允许您查看其状态：已完成、正在进行、正在编辑等。

### 在营销计划中浏览 {#browsing-in-a-marketing-program}

Campaign允许您管理由各种营销活动组成的一组项目。 每个营销活动都包含投放以及关联的流程和资源。

#### 浏览程序 {#browsing-a-program}

编辑程序时，请使用下面描述的选项卡浏览并配置该程序。

* **Schedule**&#x200B;选项卡显示某月、某周或某天的节目日历，具体取决于您在日历标题中单击的选项卡。

   如有必要，您可以通过此页面创建营销策划、项目或任务。

   ![](assets/s_ncs_user_interface_campaign02.png)

* 通过&#x200B;**Edit**&#x200B;选项卡，您可以个性化程序：名称、开始和结束日期、预算、链接的文档等。

   ![](assets/s_ncs_user_interface_campaign05.png)

#### 浏览营销活动 {#browsing-campaigns}

营销活动可通过营销活动日历、项目的&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡或营销活动列表访问。

1. 通过营销活动日历，选择要显示的营销活动，然后单击&#x200B;**[!UICONTROL Open]**&#x200B;链接。

   ![](assets/campaign_planning_edit_op.png)

   营销活动在新选项卡中进行编辑，如下所示：

   ![](assets/campaign_op_edit.png)

1. 通过项目的&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡，编辑模式与通过营销活动日历的编辑模式相同。
1. 通过&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Campaigns]**&#x200B;链接，单击要编辑的营销活动名称。

   ![](assets/campaign_edit_from_list.png)

### 控制活动 {#controlling-a-campaign}

#### 功能板 {#dashboard}

对于每个营销活动，作业、资源和投放都集中在单个屏幕（功能板）中，让您能够与他人协作管理营销操作。

营销活动的仪表板用作控制界面。 它直接访问营销活动创建和管理的主要阶段：投放、提取文件、通知、预算等。

![](assets/s_ncs_user_op_board_start_del.png)

借助Adobe Campaign，您可以设置协作流程，以创建和批准营销和沟通活动的各个阶段：预算、目标、内容等的审批

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>[营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)中介绍了营销活动模板的配置。

#### 计划 {#schedule}

营销活动可集中化一组投放。 对于每个营销活动，计划提供所有组件的全局视图：这样，您便可以显示任务和投放，并轻松访问它们。

![](assets/campaign_planning_tab.png)

#### 论坛 {#forum}

对于每个营销活动，运营商都可以通过专用论坛交换消息。

有关更多信息，请参阅[讨论论坛](../../mrm/using/discussion-forums.md)。

#### 报告 {#reports}

**[!UICONTROL Reports]**&#x200B;链接允许您访问营销活动报告。

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>有关报告的详情，请参见[此部分](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

#### 配置 {#configuration}

营销活动通过营销活动模板创建。 您可以配置可重复使用的模板，其中已为其选择某些选项并保存其他设置。 对于每个营销活动，都提供以下功能：

* 文档和资源的引用：您可以将文档与营销活动（简介、报告、图像等）关联。 支持所有文档格式。 请参阅[管理关联文档](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)。
* 定义成本：对于每个营销活动，Adobe Campaign允许您定义可在创建营销活动时使用的成本条目和成本计算结构。 例如：印刷成本、使用外部代理、房租等。 请参阅[定义成本类别](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories)。
* 定义目标：您可以为营销活动定义可量化的目标，例如订阅者数量、业务量等。 此信息稍后会用在营销活动报表中。
* 管理种子地址（有关更多信息，请参阅[此部分](../../delivery/using/about-seed-addresses.md)）和控制组（请参阅[定义控制组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)）。
* 管理批准：您可以选择要批准的处理，并根据需要选择审核运算符或运算符组。 请参阅[检查和批准投放](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

>[!NOTE]
>
>要访问营销活动配置并对其进行更改，请单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Advanced campaign parameters...]**&#x200B;链接。 有关在营销活动级别设置参数以便投放自动继承值的更多信息，请参阅[我们的技术说明](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Setparametersatthecampaignlevelsodeliveriesinheritvaluesautomatically)。

## 使用Web界面 {#using-the-web-interface-}

您可以通过Internet浏览器访问Adobe Campaign控制台屏幕，以查看所有营销活动和投放，以及有关数据库中用户档案的报告和信息。 此访问不启用记录创建。 根据操作员权限，您可以查看和/或对数据库中的数据执行操作。 例如，您可以批准营销活动内容和定位、重新启动或停止投放等。

1. 与往常一样，通过https://`<your instance>:<port>/view/home`登录。
1. 使用菜单访问概述。

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

批准（例如，对目标或投放内容）可以通过Web访问进行。

![](assets/campaign_web_interface_validation.png)

您还可以使用通知消息中包含的链接。 有关更多信息，请参阅[检查和批准投放](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。
