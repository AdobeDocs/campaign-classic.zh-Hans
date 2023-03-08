---
product: campaign
title: 营销活动目标受众
description: 了解如何定义营销活动的受众
feature: Campaigns, Audiences
exl-id: 04daa67c-4057-42a7-b993-a6eddf2b883d
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 2%

---

# 选择营销活动受众 {#marketing-campaign-deliveries}

![](../../assets/v7-only.svg)

在营销活动中，您可以为每个投放定义：

* 受众 — 在中了解详情 [在工作流中构建受众](#building-the-main-target-in-a-workflow) 和 [选择目标群体](#selecting-the-target-population).
* 控制组 — 了解详情 [本节](#defining-a-control-group).
* 种子地址 — 了解详情，请参阅 [本节](../../delivery/using/about-seed-addresses.md).

其中一些信息可以从 [活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

要构建投放目标，您可以在数据库中定义收件人的筛选条件。 此收件人选择模式在中显示 [本节](../../delivery/using/steps-defining-the-target-population.md).

## 发送到组

您可以将群体导入列表，然后在投放中定位此列表。 为此请执行以下操作步骤：

1. 编辑相关投放，然后单击 **[!UICONTROL To]** 用于更改目标群体的链接。

1. 在 **[!UICONTROL Main target]** 选项卡，选择 **[!UICONTROL Defined via the database]** 选项并单击 **[!UICONTROL Add]** 以选择收件人。

![](assets/s_user_target_group_add.png)

1. 选择 **[!UICONTROL A list of recipients]** 并单击 **[!UICONTROL Next]** 以选择它。

![](assets/s_user_target_group_next.png)

## 在营销活动工作流中构建受众 {#building-the-main-target-in-a-workflow}

投放的主要目标也可以在营销活动工作流中定义：利用此图形环境，您可以使用查询、测试和运算符构建目标：合并、重复数据删除、共享等。

>[!IMPORTANT]
>
>在营销策划中添加的工作流不能超过28个。 超过此限制，其他工作流在界面中不可见，并且可能会生成错误。

### 创建工作流 {#creating-a-targeting-workflow}

定位可以通过工作流中按图形顺序显示的筛选条件组合来创建。 您可以创建群体和子群体，并根据您的要求定位这些群体。 要显示工作流编辑器，请单击 **[!UICONTROL Targeting and workflows]** 选项卡。

![](assets/s_ncs_user_edit_op_wf_link.png)

通过放置在工作流中的一个或多个查询，从Adobe Campaign数据库中提取目标群体。 要了解如何构建查询，请参阅 [本节](../../workflow/using/query.md).

您可以通过并集、交集、共享、排除等框启动查询和共享群体。

从工作区左侧的列表中选择对象并将其链接以构建目标。

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

在图中，链接图表中目标构建所需的定位和计划查询。 您可以在构建过程中执行定位，以检查从数据库中提取的群体。

>[!NOTE]
>
>有关定义查询的示例和过程，请参见 [本节](../../workflow/using/query.md).

编辑器的左侧部分包含一个表示活动的图形对象库。 第一个选项卡包含定向活动，第二个选项卡包含流量控制活动，这些活动有时用于协调定向活动。

定位工作流执行和格式设置功能可通过图编辑器工具栏访问。

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>有关可用于构建图表的活动以及所有显示和布局功能的详情，请参见 [使用工作流实现自动化](../../workflow/using/architecture.md) 指南。

您可以为单个营销策划创建多个定位工作流。 要添加工作流，请执行以下操作：

1. 转到工作流创建区域的左上角部分，右键单击并选择 **[!UICONTROL Add]**. 您还可以使用 **[!UICONTROL New]** 按钮的位置。

   ![](assets/s_ncs_user_add_a_wf.png)

1. 选择 **[!UICONTROL New workflow]** 模板并命名此工作流。
1. 单击 **[!UICONTROL OK]** 以确认创建工作流，然后为此工作流创建图。

### 执行工作流 {#executing-a-workflow}

可以通过手动启动定位工作流 **[!UICONTROL Start]** 按钮时（如果您具有相应的权限）。

可以编程该定位以根据调度（调度器）或事件（外部信号、文件导入等）自动执行。

与执行定位工作流相关的操作（启动、停止、暂停等） 是 **异步** 进程：命令已保存，一旦服务器可以应用它就会生效。

利用工具栏图标，可采取有关执行定位工作流的操作。

* 启动或重新启动

   * 此 **[!UICONTROL Start]** 图标可让您启动定位工作流。 单击此图标时，将激活所有没有输入过渡的活动（端点跳转除外）。

      ![](assets/s_user_segmentation_start.png)

      服务器会将该请求考虑在内，如其状态所示：

      ![](assets/s_user_segmentation_start_status.png)

      进程状态更改为 **[!UICONTROL Started]**.

   * 您可以通过相应的工具栏图标重新启动定位工作流。 在以下情况下，此命令可能很有用： **[!UICONTROL Start]** 图标不可用，例如，正在停止定位工作流时。 在这种情况下，单击 **[!UICONTROL Restart]** 图标来预期重新启动。 服务器会将请求考虑在内，其状态显示为：

      ![](assets/s_user_segmentation_restart_status.png)

      然后，该进程进入 **[!UICONTROL Started]** 状态。

* 停止或暂停

   * 利用工具栏图标，可停止或暂停正在进行的定位工作流。

      当您单击 **[!UICONTROL Pause]**，正在执行操作 **[!UICONTROL are not]** 已暂停，但在下次重新启动之前不会启动其他活动。

      ![](assets/s_user_segmentation_pause.png)

      服务器会考虑该命令，其状态显示为：

      ![](assets/s_user_segmentation_pause_status.png)

      当定向工作流执行到特定活动时，您也可以自动暂停定向工作流。 要实现此目的，请右键单击要暂停定向工作流的活动，然后选择 **[!UICONTROL Enable but do not execute]**.

      ![](assets/s_user_segmentation_donotexecute.png)

      此配置由一个特殊图标显示。

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >在高级定位营销活动设计和测试阶段，此选项非常有用。

      单击 **[!UICONTROL Start]** 以继续执行。

   * 单击 **[!UICONTROL Stop]** 图标来停止正在进行的执行。

      ![](assets/s_user_segmentation_stop.png)

      服务器会考虑该命令，其状态显示为：

      ![](assets/s_user_segmentation_stop_status.png)
   当执行到达活动时，您还可以自动停止定位工作流。 要实现此目的，请右键单击将从中停止定位工作流的活动，然后选择 **[!UICONTROL Do not activate]**.

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   此配置由一个特殊图标显示。

   >[!NOTE]
   >
   >在高级定位营销活动设计和测试阶段，此选项非常有用。

* 无条件停止

   在资源管理器中，选择 **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** 访问每个活动工作流并对其执行操作。

   您可以通过单击 **[!UICONTROL Actions]** 图标并选择 **[!UICONTROL Unconditional]** 停下。 此操作终止您的营销活动工作流。

   ![](assets/s_user_segmentation_stop_unconditional.png)

## 添加控制组 {#defining-a-control-group}

控制组是不接收投放的群体；它用于通过与接收投放的目标群体的行为进行比较，来跟踪投放后的行为和营销活动影响。

控制组可以从主目标中提取和/或来自特定组或查询。

### 为营销活动激活控制组 {#activating-the-control-group-for-a-campaign}

您可以在活动级别定义控制组，在这种情况下，控制组将应用于相关活动的每次投放。

1. 编辑相关的营销活动，然后单击 **[!UICONTROL Edit]** 选项卡。
1. 单击 **[!UICONTROL Advanced campaign settings]**。

   ![](assets/s_ncs_user_edit_op_target.png)

1. 选择 **[!UICONTROL Enable and edit control group configuration]** 选项。
1. 单击 **[!UICONTROL Edit...]** 配置控制组。

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

有关配置过程的介绍，请参见 [从主目标中提取控制组](#extracting-the-control-group-from-the-main-target) 和 [添加控制组](#adding-a-population).

### 为投放激活对照组 {#activating-the-control-group-for-a-delivery}

您可以在投放级别定义控制组，在这种情况下，控制组将应用于相关营销活动的每次投放。

默认情况下，在营销活动级别定义的控制组配置将应用于该营销活动的每次投放。 但是，您可以为单个投放调整控制组。

>[!NOTE]
>
>如果您为营销活动定义了控制组，并且还为链接到此营销活动的投放配置了该控制组，则只会应用为该投放定义的控制组。

1. 编辑相关的投放，然后单击 **[!UICONTROL To]** 中的链接 **[!UICONTROL Email parameters]** 部分。

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. 单击 **[!UICONTROL Control group]** 选项卡，然后选择 **[!UICONTROL Enable and edit control group configuration]**.
1. 单击 **[!UICONTROL Edit...]** 配置控制组。

有关配置过程的介绍，请参见 [从主目标中提取控制组](#extracting-the-control-group-from-the-main-target) 和 [添加控制组](#adding-a-population).

### 从主目标中提取控制组 {#extracting-the-control-group-from-the-main-target}

您可以从投放的主要目标中提取收件人。 在这种情况下，收件人将从受此配置影响的投放操作目标中获取。 此提取可以是随机的，也可以是对收件人进行排序的结果。

![](assets/s_ncs_user_extract_from_target_population.png)

要提取控制组，请为活动或投放启用控制组，然后选择以下选项之一： **[!UICONTROL Activate random sampling]** 或 **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** ：此选项将随机取样应用于目标群体中的收件人。 如果您随后将阈值设置为100，则控制组将由从目标群体中随机选择的100位收件人组成。 随机抽样取决于数据库引擎。
* **[!UICONTROL Keep only the first records after sorting]**：通过此选项可根据一个或多个排序顺序定义限制。如果您选择 **[!UICONTROL Age]** 字段作为排序标准，然后将100定义为阈值，则控制组将由100个最年轻的收件人组成。 例如，定义包含很少购买的收件人或频繁购买的收件人的控制组，并将其行为与联系的收件人的行为进行比较，这可能很有趣。

单击 **[!UICONTROL Next]** 以定义排序顺序（如有必要）并选择收件人限制模式。

![](assets/s_ncs_user_edit_op_target_param.png)

此配置等同于工作流中的共享活动，可让您将目标划分为子集。 控制组是上述子组之一。 请参阅 [本节](../../workflow/using/architecture.md) 了解更多信息。

### 使用新群体作为对照组 {#adding-a-population}

您可以定义用作控制组的新群体。 此群体可以来自一组收件人，也可以通过特定查询创建此群体。

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign查询编辑器的介绍 [本节](../../workflow/using/query.md).


#### 教程视频 {#create-email-video}

此视频介绍如何在Adobe Campaign中创建活动和电子邮件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

提供了其他Campaign操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
