---
solution: Campaign Classic
product: campaign
title: 访问营销活动
description: 访问营销活动
audience: campaign
content-type: reference
topic-tags: about-marketing-campaigns
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 1%

---


# 访问营销活动{#accessing-marketing-campaigns}

Adobe Campaign可让您创建、配置、执行和分析营销活动。 所有营销活动都可从统一的控制中心进行管理。

## 工作区基础知识{#workspace-basics}

### 主页{#home-page}

连接到Adobe Campaign后，您将看到主页。

![](assets/campaign_global_view.png)

单击导航栏中的链接可访问各种功能。

活动元素位于&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡中：在此，您可以看到营销项目、活动及其子集的概述。 营销项目由活动组成，这些投放、任务、链接资源等组成。 在使用活动的营销活动管理中，投放、预算、审阅者和链接文档的相关信息可在活动中找到。

**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Browsing]**&#x200B;块会根据实例上安装的模块优惠各种条目。 例如，您可以访问：

* **活动日历**:计划日历、营销项目、投放和活动。请参阅[活动日历](#campaign-calendar)。
* **活动**:访问所有营销项目中包含的活动。
* **投放**:访问链接到投放的活动。
* **Web 应用程序**:访问web应用程序(表单、调查等)。

>[!NOTE]
>
>有关Adobe Campaign的整体人机工程学、权限和用户档案管理功能的详细信息，请参阅[本节](../../platform/using/adobe-campaign-workspace.md)。
>
>与渠道和投放相关的所有功能在[本节](../../delivery/using/steps-about-delivery-creation-steps.md)中有详细说明。

### 活动日历{#campaign-calendar}

每个活动都属于一个项目，而这个又属于一个计划。 计划、项目和活动可通过&#x200B;**活动**&#x200B;选项卡的&#x200B;**[!UICONTROL Campaign calendar]**&#x200B;菜单访问。

要编辑计划、项目、活动或投放，请在日历中单击其名称，然后单击&#x200B;**[!UICONTROL Open...]**。 然后，它会显示在新选项卡中，如下所示：

![](assets/d_ncs_user_interface_hierar.png)

您可以过滤在活动日历中显示的信息。 要执行此操作，请单击&#x200B;**[!UICONTROL Filter]**&#x200B;链接并选择筛选条件。

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>当您对某个日期进行筛选时，所有开始日期晚于指定日期和/或结束日期早于指定日期的活动都会显示。 需要使用每个字段右侧的日历选择日期。

您还可以使用&#x200B;**[!UICONTROL Search]**&#x200B;字段筛选显示的项目。

链接到每个项目的图标可让您视图其状态：完成、进行中、正在编辑等。

### 在营销项目{#browsing-in-a-marketing-program}中浏览

活动允许您管理由各种营销活动组成的一组项目。 每个活动都包含投放以及关联的进程和资源。

#### 浏览项目{#browsing-a-program}

编辑项目时，请使用下面描述的选项卡浏览并配置它。

* **计划**&#x200B;选项卡显示月、周或日的项目日历，具体取决于您在日历标题中单击的选项卡。

   如有必要，您可以通过此页面创建活动、项目或任务。

   ![](assets/s_ncs_user_interface_campaign02.png)

* 通过&#x200B;**编辑**&#x200B;选项卡，您可以个性化项目:名称、开始和结束日期、预算、链接文档等

   ![](assets/s_ncs_user_interface_campaign05.png)

#### 浏览活动{#browsing-campaigns}

活动可以通过活动日历、项目的&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡或活动列表访问。

1. 通过活动日历，选择要显示的活动，然后单击&#x200B;**[!UICONTROL Open]**&#x200B;链接。

   ![](assets/campaign_planning_edit_op.png)

   该活动会在新选项卡中进行编辑，如下所示：

   ![](assets/campaign_op_edit.png)

1. 通过项目的&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡，编辑模式与通过活动日历相同。
1. 通过&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Campaigns]**&#x200B;链接，单击要编辑的活动的名称。

   ![](assets/campaign_edit_from_list.png)

### 控制活动{#controlling-a-campaign}

#### 仪表板{#dashboard}

对于每个活动，作业、资源和投放都集中在一个屏幕中，即仪表板中，它允许您与他人协作管理营销操作。

活动的仪表板用作控制接口。 它直接访问主活动创建和管理阶段：投放、提取文件、通知、预算等。

![](assets/s_ncs_user_op_board_start_del.png)

借助Adobe Campaign，您可以设置协作流程，以创建和批准营销和通信活动的各个阶段：预算、目标、内容等的批准

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>活动模板的配置显示在[活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)中。

#### 计划{#schedule}

活动集中化一组投放。 对于每个活动,计划将优惠所有组件的全局视图:这样，您便可以显示任务和投放并轻松访问它们。

![](assets/campaign_planning_tab.png)

#### 论坛 {#forum}

对于每个活动，运营商都可以通过专用论坛交换消息。

有关详细信息，请参阅[论坛](../../campaign/using/discussion-forums.md)。

#### 报告 {#reports}

**[!UICONTROL Reports]**&#x200B;链接允许您访问活动报告。

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>报告详见[本节](../../reporting/using/about-adobe-campaign-reporting-tools.md)。

#### 配置{#configuration}

活动是通过活动模板创建的。 您可以配置可重用的模板，这些模板已选择某些选项并保存了其他设置。 对于每个活动，提供以下功能：

* 引用文档和资源：您可以将文档与活动（简介、报表、图像等）关联。 支持所有文档格式。 请参阅[管理关联文档](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)。
* 定义成本：对于每个活动，“Adobe Campaign”允许您定义成本分录和成本计算结构，在创建营销活动时可使用这些结构。 例如：印刷成本、使用外部代理、房租等。 请参阅[定义成本类别](../../campaign/using/providers--stocks-and-budgets.md#defining-cost-categories)。
* 定义目标：您可以为活动定义可量化的目标，例如订阅者数量、业务量等。 此信息稍后将用于活动报告。
* 管理种子地址（有关详细信息，请参阅[本节](../../delivery/using/about-seed-addresses.md)）和对照组(请参阅[定义对照组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group))。
* 管理批准：您可以选择要批准的处理，并根据需要选择审核运算符或操作员组。 请参阅[检查和批准投放](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

>[!NOTE]
>
>要访问活动配置并对其进行更改，请单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Advanced campaign parameters...]**&#x200B;链接。 有关在活动级别设置参数以使投放自动继承值的详细信息，请参阅[我们的技术说明](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Setparametersatthecampaignlevelsodeliveriesinheritvaluesautomatically)。

## 使用Web接口{#using-the-web-interface-}

您可以通过Internet浏览器访问Adobe Campaign控制台屏幕，以视图所有活动和投放，以及有关数据库中用户档案的报告和信息。 此访问不启用记录创建。 根据操作员权限，您可以视图和/或对数据库中的数据执行操作。 例如，您可以批准活动内容和定位、重新开始或停止投放等。

1. 通过https://`<your instance>:<port>/view/home`照常登录。
1. 使用菜单访问概述。

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

(例如，目标或投放内容的批准)可以通过Web访问进行。

![](assets/campaign_web_interface_validation.png)

您还可以使用通知消息中包含的链接。 有关详细信息，请参阅[检查和批准投放](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。
