---
product: campaign
title: 访问营销活动
description: 访问营销活动
role: User
feature: Campaigns, Cross Channel Orchestration
exl-id: 1278bda1-f83c-4d38-8042-e6611755cf36
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 2%

---

# 访问营销活动{#accessing-marketing-campaigns}

Adobe Campaign允许您创建、配置、执行和分析营销活动。 所有营销活动都可从统一的控制中心进行管理。

## Workspace基础知识 {#workspace-basics}

### 主页 {#home-page}

连接到Adobe Campaign后，使用导航栏中的链接浏览各种功能。


![](assets/campaign_global_view.png)


在&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡中找到营销活动元素：您可以在此处查看营销项目、营销活动及其子集的概述。 营销策划由活动组成，活动由投放、任务、链接资源等组成。 在使用Campaign进行营销活动管理的情况下，有关投放、预算、审阅人和链接文档的信息可在营销活动中找到。

**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Browsing]**&#x200B;块提供了各种条目，具体取决于实例上安装的模块。 例如，您可以访问：

* **营销活动日历**：计划、营销计划、投放和营销活动的日历。 请参阅[促销活动日历](#campaign-calendar)。
* **营销活动**：访问所有营销计划中包含的营销活动。
* **投放**：访问链接到营销活动的投放。
* **Web应用程序**：访问Web应用程序（表单、登陆页等）。

>[!NOTE]
>
>有关Adobe Campaign整体人机工程学、权限和配置文件管理功能的更多信息，请参阅[此章节](../../platform/using/adobe-campaign-workspace.md)。
>
>[此部分](../../delivery/using/steps-about-delivery-creation-steps.md)中详细介绍了与渠道和投放相关的所有功能。

### 营销活动日历 {#campaign-calendar}

每个营销策划都属于一个项目，而该项目又属于一个计划。 可通过&#x200B;**营销活动**&#x200B;选项卡中的&#x200B;**[!UICONTROL Campaign calendar]**&#x200B;菜单访问计划、项目和营销活动。

要编辑计划、项目、活动或投放，请在日历中单击其名称，然后单击&#x200B;**[!UICONTROL Open...]**。 然后，它将显示在新选项卡中，如下所示：

![](assets/d_ncs_user_interface_hierar.png)

您可以筛选营销活动日历中显示的信息：单击&#x200B;**[!UICONTROL Filter]**&#x200B;链接并选择筛选条件。

![](assets/campaign_planning_filter.png)

>[!NOTE]
>
>在按日期过滤时，将显示开始日期晚于指定日期和/或结束日期早于指定日期的所有营销活动。 使用每个字段右侧的日历选择日期。

您还可以使用&#x200B;**[!UICONTROL Search]**&#x200B;字段筛选显示的项。

链接到每个项目的图标允许您查看其状态：已完成、进行中、正在编辑等。

### 浏览营销项目 {#browsing-in-a-marketing-program}

利用Campaign，可管理由各种营销活动组成的一组项目。 每个营销策划都包含投放以及关联的流程和资源。

#### 浏览程序 {#browsing-a-program}

编辑程序时，请使用下述选项卡浏览和配置程序。

* **计划**&#x200B;选项卡显示月、周或日计划的日历，具体取决于您在日历标题中单击的选项卡。

  如有必要，您可以通过此页面创建营销策划、项目或任务。

  ![](assets/s_ncs_user_interface_campaign02.png)

* 通过&#x200B;**编辑**&#x200B;选项卡，可对项目进行个性化设置：名称、开始和结束日期、预算、链接文档等。

  ![](assets/s_ncs_user_interface_campaign05.png)

#### 浏览营销活动 {#browsing-campaigns}

可以通过营销策划日历、项目的&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡或营销策划列表访问营销策划。

1. 通过营销活动日历，选择要显示的营销活动，然后单击&#x200B;**[!UICONTROL Open]**&#x200B;链接。

   ![](assets/campaign_planning_edit_op.png)

   该营销活动将在新选项卡中进行编辑，如下所示：

   ![](assets/campaign_op_edit.png)

1. 通过项目的&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡，编辑模式与通过营销策划日历的编辑模式相同。
1. 通过&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡的&#x200B;**[!UICONTROL Campaigns]**&#x200B;链接，单击要编辑的营销活动的名称。

   ![](assets/campaign_edit_from_list.png)

### 控制活动 {#controlling-a-campaign}

#### 仪表板 {#dashboard}

对于每个营销活动，任务、资源和投放都集中在一个屏幕中（即功能板），允许您与其他人协作管理营销操作。

营销活动的仪表板用作控制界面。 它直接访问营销活动创建和管理的主要阶段：投放、提取文件、通知、预算等。

![](assets/s_ncs_user_op_board_start_del.png)

借助Adobe Campaign，您可以设置协作流程，以创建和审批营销和通信活动的各个阶段：预算、目标、内容等。

![](assets/s_ncs_user_op_board_validate.png)

>[!NOTE]
>
>[营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)中显示了营销活动模板的配置。

#### 计划 {#schedule}

营销活动集中了一系列投放。 对于每个活动，计划都提供了所有组件的全局视图：您可以显示任务和投放并轻松访问它们。

![](assets/campaign_planning_tab.png)

#### 论坛 {#forum}

对于每个活动，操作员可以通过专用论坛交换消息。

在[论坛](../../mrm/using/discussion-forums.md)中了解详情。

#### 报告 {#reports}

**[!UICONTROL Reports]**&#x200B;链接允许您访问营销活动报告。

![](assets/campaign_reporting_tab.png)

>[!NOTE]
>
>[此部分](../../reporting/using/about-adobe-campaign-reporting-tools.md)中详细介绍了报告。

#### 配置 {#configuration}

营销活动是通过营销活动模板创建的。 您可以配置已选择某些选项且已保存其他设置的可重用模板。 对于每个活动，都提供了以下功能：

* 引用[文档和资源](../../campaign/using/marketing-campaign-deliveries.md#managing-associated-documents)：您可以将文档与营销活动关联（简介、报告、图像等）。 支持所有文档格式。
* 定义成本：对于每个促销活动，Adobe Campaign允许您定义[成本条目和成本计算结构](../../campaign/using/providers-stocks-and-budgets.md#defining-cost-categories)，创建营销活动时可使用该结构。 例如：印刷费、使用外部机构、房间租金。
* 定义目标：您可以定义促销活动的可量化目标，例如订户数、业务量等。 此信息稍后将在营销活动报表中使用。
* 管理[种子地址](../../delivery/using/about-seed-addresses.md)和[对照组](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。
* 管理审批：您可以选择要批准的处理，并根据需要选择审核操作员或操作员组。 [了解详情](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)

>[!NOTE]
>
>要访问Campaign配置并进行更改，请单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中的&#x200B;**[!UICONTROL Advanced campaign parameters...]**&#x200B;链接。

## 使用Web界面 {#using-the-web-interface-}

您可以通过Internet浏览器访问Adobe Campaign控制台屏幕，以查看所有营销活动和投放以及数据库中用户档案的报告和信息。 此访问不会启用记录创建。 根据操作员的权限，您可以查看和/或处理数据库中的数据。 例如，您可以批准活动内容和定位、重新启动或停止投放等。

1. 照常通过https://`<your instance>:<port>/view/home`登录。
1. 使用菜单访问概述。

   ![](assets/s_ncs_user_interface_web_campaign_01.png)

除了在营销策划之间导航和查看这些营销策划之外，您还可以执行以下类型的任务：

* 监测实例上的活动
* 参与验证流程，例如，批准或拒绝投放内容
* 执行其他快速操作，例如，暂停工作流
* 访问所有报告功能
* 参加论坛讨论

此表汇总了您可以从浏览器对营销活动执行的操作：

| 页面  | 操作 |
| --- | --- |
| 活动、投放、优惠等列表。 | 删除列表项 |
| 营销活动 | 取消营销活动 |
| 投放 | 批准投放内容和目标<br/>提交投放内容<br/>确认投放<br/>暂停并停止投放 |
| Web 应用程序 | 创建Web应用程序<br/>编辑应用程序内容和属性<br/>将应用程序内容另存为模板<br/>Publish应用程序 |
| 优惠 | 批准选件内容和资格<br/>禁用联机选件 |
| 任务 | 完成任务<br/>取消任务 |
| 营销资源 | 批准资源<br/>锁定并解锁资源 |
| 营销活动包 | 提交程序包以供审批<br/>批准或拒绝程序包<br/>取消程序包 |
| Campaign 订单 | 创建订单<br/>接受或拒绝订单<!-- Je n'ai pas pu créer de campaign order pour vérifier cela. Peut-on accéder à ces fonctionnalités depuis l'accès web ? --> |
| 库存 | 删除库存行 |
| 优惠模拟 | 启动和停止模拟 |
| 定位工作流 | 启动、暂停和停止工作流 |
| 报告 | 在报告历史记录中保存当前数据 |
| 论坛 | 添加讨论<br/>在讨论中回复邮件<br/>关注讨论并取消订阅 |

### 审批

（例如，目标或投放内容）的批准可通过Web访问进行。

![](assets/campaign_web_interface_validation.png)

您还可以使用通知消息中包含的链接。 有关详细信息，请参阅[检查和批准投放](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。
