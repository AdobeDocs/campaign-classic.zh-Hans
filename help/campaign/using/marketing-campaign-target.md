---
product: campaign
title: 营销活动目标受众
description: 了解如何定义营销活动的受众
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: 04daa67c-4057-42a7-b993-a6eddf2b883d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 2%

---

# 选择营销活动受众 {#marketing-campaign-deliveries}

在营销活动中，您可以为每个投放定义：

* 受众 — 在[在工作流中构建受众](#building-the-main-target-in-a-workflow)和[选择目标群体](#selecting-the-target-population)中了解更多信息。
* 控制组 — 在[此部分](#defining-a-control-group)中了解详情。
* 种子地址 — 在[此部分](../../delivery/using/about-seed-addresses.md)中了解详情。

其中某些信息可以从[营销活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)继承。

要构建投放目标，您可以在数据库中为收件人定义筛选条件。 此收件人选择模式在[此部分](../../delivery/using/steps-defining-the-target-population.md)中显示。

## 发送到群组

您可以将群体导入列表，然后在投放中定位此列表。 为此请执行以下操作步骤：

1. 编辑相关投放，然后单击&#x200B;**[!UICONTROL To]**&#x200B;链接以更改目标群体。

1. 在&#x200B;**[!UICONTROL Main target]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Defined via the database]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;以选择收件人。

![](assets/s_user_target_group_add.png)

1. 选择&#x200B;**[!UICONTROL A list of recipients]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**&#x200B;以将其选中。

![](assets/s_user_target_group_next.png)

## 在营销活动工作流{#building-the-main-target-in-a-workflow}中构建受众

投放的主要目标也可以在营销活动工作流中定义：此图形环境允许您使用查询、测试和运算符来构建目标：并集、重复数据删除、共享等。

>[!IMPORTANT]
>
>在营销活动中添加的工作流不得超过28个。 超出此限制后，其他工作流在界面中不可见，并且可能会生成错误。

### 创建工作流{#creating-a-targeting-workflow}

可以通过工作流中图形序列中的筛选条件组合来创建定位。 您可以创建群体和子群体，这些群体和子群体将根据您的要求进行定位。 要显示工作流编辑器，请单击营销活动仪表板中的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡。

![](assets/s_ncs_user_edit_op_wf_link.png)

目标群体通过置于工作流中的一个或多个查询从Adobe Campaign数据库中提取。 要了解如何构建查询，请参阅[此部分](../../workflow/using/query.md)。

您可以通过“并集”、“交集”、“共享”、“排除”等框启动查询并共享群体。

从工作区左侧的列表中选择对象，并链接它们以构建目标。

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

在图中，将图中目标构建所需的定位和计划查询关联起来。 在施工过程中，您可以执行定位，以检查从数据库提取的群体。

>[!NOTE]
>
>[此部分](../../workflow/using/query.md)中介绍了定义查询的示例和过程。

编辑器的左侧部分包含一个表示活动的图形对象库。 第一个选项卡包含定位活动，第二个选项卡包含流量控制活动，这些活动有时用于协调定位活动。

可通过图编辑器工具栏访问定向工作流执行和格式设置功能。

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>[使用工作流实现自动化](../../workflow/using/architecture.md)指南中详细介绍了可用于构建图表的活动以及所有显示和布局功能。

您可以为单个营销活动创建多个定位工作流。 要添加工作流，请执行以下操作：

1. 转到工作流创建区域的左上角部分，右键单击并选择&#x200B;**[!UICONTROL Add]**。 您还可以使用位于此区域上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮。

   ![](assets/s_ncs_user_add_a_wf.png)

1. 选择&#x200B;**[!UICONTROL New workflow]**&#x200B;模板并命名此工作流。
1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;以确认创建工作流，然后创建此工作流的图表。

### 执行工作流{#executing-a-workflow}

如果您拥有相应的权限，则可以通过工具栏中的&#x200B;**[!UICONTROL Start]**&#x200B;按钮手动启动定位工作流。

可以根据调度（调度器）或事件（外部信号、文件导入等）对定向进行编程以自动执行。

与执行定位工作流（启动、停止、暂停等）相关的操作 是&#x200B;**异步**&#x200B;进程：命令已保存，一旦服务器可以应用该命令，该命令将立即生效。

利用工具栏图标，可执行定位工作流相关的操作。

* 启动或重新启动

   * 使用&#x200B;**[!UICONTROL Start]**&#x200B;图标可启动定位工作流。 单击此图标时，将激活所有没有输入过渡的活动（端点跳转除外）。

      ![](assets/s_user_segmentation_start.png)

      服务器会考虑请求，如其状态所示：

      ![](assets/s_user_segmentation_start_status.png)

      进程状态将变为&#x200B;**[!UICONTROL Started]**。

   * 您可以通过相应的工具栏图标重新启动定位工作流。 如果&#x200B;**[!UICONTROL Start]**&#x200B;图标不可用，例如当正在停止定向工作流时，此命令可能很有用。 在这种情况下，单击&#x200B;**[!UICONTROL Restart]**&#x200B;图标以预见重新启动。 服务器考虑了该请求，其状态如下所示：

      ![](assets/s_user_segmentation_restart_status.png)

      然后，该进程进入&#x200B;**[!UICONTROL Started]**&#x200B;状态。

* 停止或暂停

   * 利用工具栏图标，可停止或暂停正在进行的定位工作流。

      单击&#x200B;**[!UICONTROL Pause]**&#x200B;后，正在进行的&#x200B;**[!UICONTROL are not]**&#x200B;操作暂停，但直到下次重新启动后才会启动任何其他活动。

      ![](assets/s_user_segmentation_pause.png)

      服务器考虑了该命令，其状态如下所示：

      ![](assets/s_user_segmentation_pause_status.png)

      您还可以在定位工作流执行到达特定活动时自动暂停该工作流。 为此，请右键单击要暂停定位工作流的活动，然后选择&#x200B;**[!UICONTROL Enable but do not execute]**。

      ![](assets/s_user_segmentation_donotexecute.png)

      此配置由一个特殊图标显示。

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >此选项在高级定位营销活动设计和测试阶段非常有用。

      单击&#x200B;**[!UICONTROL Start]**&#x200B;以继续执行。

   * 单击&#x200B;**[!UICONTROL Stop]**&#x200B;图标以停止正在执行的操作。

      ![](assets/s_user_segmentation_stop.png)

      服务器考虑了该命令，其状态如下所示：

      ![](assets/s_user_segmentation_stop_status.png)
   您还可以在执行到达活动时自动停止定位工作流。 为此，请右键单击要停止定位工作流的活动，然后选择&#x200B;**[!UICONTROL Do not activate]**。

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   此配置由一个特殊图标显示。

   >[!NOTE]
   >
   >此选项在高级定位营销活动设计和测试阶段非常有用。

* 无条件停止

   在资源管理器中，选择&#x200B;**[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]**&#x200B;以访问每个营销活动工作流并对其执行操作。

   单击&#x200B;**[!UICONTROL Actions]**&#x200B;图标并选择&#x200B;**[!UICONTROL Unconditional]**&#x200B;停止，可以无条件停止工作流。 此操作会终止您的营销活动工作流。

   ![](assets/s_user_segmentation_stop_unconditional.png)

## 添加控制组{#defining-a-control-group}

控制组是未收到交货的群体；它通过与已收到投放的目标群体的行为进行比较，用于跟踪投放后行为和促销活动影响。

控制组可以从主目标中提取和/或来自特定组或查询。

### 激活营销活动{#activating-the-control-group-for-a-campaign}的控制组

您可以在营销活动级别定义控制组，在这种情况下，控制组将应用于相关营销活动的每个投放。

1. 编辑相关营销活动，然后单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。
1. 单击 **[!UICONTROL Advanced campaign settings]**。

   ![](assets/s_ncs_user_edit_op_target.png)

1. 选择&#x200B;**[!UICONTROL Enable and edit control group configuration]**&#x200B;选项。
1. 单击&#x200B;**[!UICONTROL Edit...]**&#x200B;以配置控制组。

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

[从主目标提取控制组](#extracting-the-control-group-from-the-main-target)和[添加控制组](#adding-a-population)中介绍了配置过程。

### 为{#activating-the-control-group-for-a-delivery}投放激活控制组

您可以在投放级别定义控制组，在这种情况下，控制组将应用于相关营销活动的每个投放。

默认情况下，营销活动级别定义的控制组配置适用于该营销活动的每个投放。 但是，您可以根据单个交付情况调整控制组。

>[!NOTE]
>
>如果您为营销活动定义了控制组，并且还为链接到此营销活动的投放配置了该控制组，则只会应用为投放定义的控制组。

1. 编辑相关投放，然后单击&#x200B;**[!UICONTROL Email parameters]**&#x200B;部分中的&#x200B;**[!UICONTROL To]**&#x200B;链接。

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. 单击&#x200B;**[!UICONTROL Control group]**&#x200B;选项卡，然后选择&#x200B;**[!UICONTROL Enable and edit control group configuration]**。
1. 单击&#x200B;**[!UICONTROL Edit...]**&#x200B;以配置控制组。

[从主目标提取控制组](#extracting-the-control-group-from-the-main-target)和[添加控制组](#adding-a-population)中介绍了配置过程。

### 从主目标{#extracting-the-control-group-from-the-main-target}提取控制组

您可以从投放的主目标提取收件人。 在这种情况下，将从受此配置影响的投放操作目标中获取收件人。 此提取可以是随机的，也可以是对收件人进行排序的结果。

![](assets/s_ncs_user_extract_from_target_population.png)

要提取控制组，请为营销活动或投放启用控制组，然后选择以下选项之一：**[!UICONTROL Activate random sampling]**&#x200B;或&#x200B;**[!UICONTROL Keep only the first records after sorting]**。

* **[!UICONTROL Activate random sampling]** :此选项对目标群体中的收件人应用随机取样。如果随后将阈值设置为100，则控制组将由100个从目标群体中随机选择的收件人组成。 随机取样取决于数据库引擎。
* **[!UICONTROL Keep only the first records after sorting]**：通过此选项可根据一个或多个排序顺序定义限制。如果选择&#x200B;**[!UICONTROL Age]**&#x200B;字段作为排序条件，然后将100定义为阈值，则控制组将由100个最年轻的收件人组成。 例如，定义一个控制组（包含很少购买的收件人或频繁购买的收件人），并将他们的行为与联系的收件人的行为进行比较可能很有趣。

单击&#x200B;**[!UICONTROL Next]**&#x200B;以定义排序顺序（如有必要）并选择收件人限制模式。

![](assets/s_ncs_user_edit_op_target_param.png)

此配置等同于工作流中的共享活动，允许您将目标划分为子集。 控制组是这些子集之一。 有关更多信息，请参阅[此部分](../../workflow/using/architecture.md)。

### 将新群体用作控制组{#adding-a-population}

您可以定义新群体以用作控制组。 此群体可以来自一组收件人，也可以通过特定查询创建。

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign查询编辑器显示在[此部分](../../workflow/using/query.md)中。


#### 教程视频{#create-email-video}

此视频介绍如何在Adobe Campaign中创建营销活动和电子邮件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他Campaign操作方法视频。
