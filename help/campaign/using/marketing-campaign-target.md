---
solution: Campaign Classic
product: campaign
title: 营销活动目标受众
description: 了解如何定义营销活动的受众
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 1%

---


# 选择活动{#marketing-campaign-deliveries}的受众

在营销活动中，您可以为每个投放定义：

* 受众 — 在[在工作流](#building-the-main-target-in-a-workflow)中构建受众和[选择目标群](#selecting-the-target-population)中了解更多信息。
* 对照组 — 在[本节](#defining-a-control-group)中了解更多信息。
* 种子地址 — 了解有关[本节](../../delivery/using/about-seed-addresses.md)的详细信息。

其中某些信息可以从[活动模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)继承。

要构建投放目标，您可以为收件人库中的定义筛选条件。 此收件人选择模式显示在[此部分](../../delivery/using/steps-defining-the-target-population.md)中。

## 发送到组

可以将人口导入列表，然后以投放目标此列表。 为此请执行以下操作步骤：

1. 编辑相关投放，然后单击&#x200B;**[!UICONTROL To]**&#x200B;链接以更改目标人口。

1. 在&#x200B;**[!UICONTROL Main target]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL Defined via the database]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL Add]**&#x200B;选择收件人。

![](assets/s_user_target_group_add.png)

1. 选择&#x200B;**[!UICONTROL A list of recipients]**&#x200B;并单击&#x200B;**[!UICONTROL Next]**&#x200B;以选择它。

![](assets/s_user_target_group_next.png)

## 在活动工作流{#building-the-main-target-in-a-workflow}中构建受众

投放的主目标也可以在活动工作流中定义：此图形环境允许您使用查询、测试和运算符构建目标:合并、外部重复数据删除、共享等

>[!IMPORTANT]
>
>一个活动中不得添加超过28个工作流。 超出此限制后，其他工作流在界面中不可见，并且可能生成错误。

### 创建工作流{#creating-a-targeting-workflow}

可以通过工作流中图形序列中的过滤条件组合来创建定位。 您可以根据您的需求创建目标群体和子群体。 要显示工作流编辑器，请单击“活动”仪表板中的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡。

![](assets/s_ncs_user_edit_op_wf_link.png)

通过放置在工作流中的一个或多个目标从Adobe Campaign数据库中提取查询。 要了解如何构建查询，请参阅[本节](../../workflow/using/query.md)。

您可以启动查询并通过合并、交叉、共享、排除等框共享人口。

从工作区左侧的列表中选择对象，并链接它们以构建目标。

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

在图中，在图中链接目标构建所需的定位和计划查询。 在施工过程中，您可以执行定位，以检查从数据库提取的人口。

>[!NOTE]
>
>[本节](../../workflow/using/query.md)中介绍了定义查询的示例和过程。

编辑器的左侧部分包含表示活动的图形对象库。 第一个选项卡包含定位活动，第二个选项卡包含流控制活动，这些控制活动偶尔用于协调定位。

可通过图编辑器工具栏访问定位工作流执行和格式设置功能。

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>构建图的可用活动以及所有显示和布局功能在[使用工作流自动化指南](../../workflow/using/architecture.md)中有详细介绍。

您可以为单个活动创建多个定位工作流。 要添加工作流，请执行以下操作：

1. 转到工作流创建区域的左上角部分，右键单击，然后选择&#x200B;**[!UICONTROL Add]**。 您还可以使用位于此区域上方的&#x200B;**[!UICONTROL New]**&#x200B;按钮。

   ![](assets/s_ncs_user_add_a_wf.png)

1. 选择&#x200B;**[!UICONTROL New workflow]**&#x200B;模板并命名此工作流。
1. 单击&#x200B;**[!UICONTROL OK]**&#x200B;确认创建工作流，然后创建此工作流的图。

### 执行工作流{#executing-a-workflow}

定位工作流可以通过工具栏中的&#x200B;**[!UICONTROL Start]**&#x200B;按钮手动启动，前提是您具有相应的权限。

该目标可被编程以根据计划(调度程序)或事件（外部信号、文件导入等）自动执行。

与执行定位工作流（启动、停止、暂停等）相关的操作 是&#x200B;**异步**&#x200B;进程：命令将保存，并在服务器可用时生效。

通过工具栏图标，您可以执行定位工作流。

* 开始或重新启动

   * 通过&#x200B;**[!UICONTROL Start]**&#x200B;图标可启动定位工作流。 单击此图标时，将激活所有没有输入过渡的活动（终点跳转除外）。

      ![](assets/s_user_segmentation_start.png)

      服务器会考虑请求，如其状态所示：

      ![](assets/s_user_segmentation_start_status.png)

      进程状态将更改为&#x200B;**[!UICONTROL Started]**。

   * 您可以通过相应的工具栏图标重新启动定位工作流。 如果&#x200B;**[!UICONTROL Start]**&#x200B;图标不可用，例如当定位工作流正在停止时，此命令可能很有用。 在这种情况下，请单击&#x200B;**[!UICONTROL Restart]**&#x200B;图标以预测重新启动。 服务器会考虑请求，其状态如下：

      ![](assets/s_user_segmentation_restart_status.png)

      进程随后进入&#x200B;**[!UICONTROL Started]**&#x200B;状态。

* 停止或暂停

   * 工具栏图标允许您停止或暂停正在进行的定位工作流。

      单击&#x200B;**[!UICONTROL Pause]**&#x200B;时，正在进行的&#x200B;**[!UICONTROL are not]**&#x200B;操作暂停，但直到下次重新启动后，才会启动其他活动。

      ![](assets/s_user_segmentation_pause.png)

      服务器会考虑该命令，其状态如下：

      ![](assets/s_user_segmentation_pause_status.png)

      您还可以在定位工作流执行到达特定活动时自动暂停该工作流。 为此，请右键单击要暂停定位工作流的活动，然后选择&#x200B;**[!UICONTROL Enable but do not execute]**。

      ![](assets/s_user_segmentation_donotexecute.png)

      此配置由特殊图标显示。

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >此选项在高级定位活动设计和测试阶段非常有用。

      单击&#x200B;**[!UICONTROL Start]**&#x200B;以继续执行。

   * 单击&#x200B;**[!UICONTROL Stop]**&#x200B;图标以停止执行。

      ![](assets/s_user_segmentation_stop.png)

      服务器会考虑该命令，其状态如下：

      ![](assets/s_user_segmentation_stop_status.png)
   您还可以在执行到达活动时自动停止定位工作流。 为此，请右键单击要停止定位工作流的活动，然后选择&#x200B;**[!UICONTROL Do not activate]**。

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   此配置由特殊图标显示。

   >[!NOTE]
   >
   >此选项在高级定位活动设计和测试阶段非常有用。

* 无条件停止

   在资源管理器中，选择&#x200B;**[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]**&#x200B;以访问每个活动工作流并对其执行操作。

   单击&#x200B;**[!UICONTROL Actions]**&#x200B;图标并选择&#x200B;**[!UICONTROL Unconditional]**&#x200B;停止，即可无条件停止您的工作流。 此操作将终止您的活动工作流。

   ![](assets/s_user_segmentation_stop_unconditional.png)

## 添加对照组{#defining-a-control-group}

对照组是不会获得投放的人；它通过与已接收投放的目标群体的行为进行比较来跟踪活动后行为和投放影响。

对照组可从主目标中提取和/或来自特定组或查询。

### 激活活动{#activating-the-control-group-for-a-campaign}的对照组

您可以在活动级别定义对照组，在这种情况下，对照组将应用于相关活动的每个投放。

1. 编辑相关活动，然后单击&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡。
1. 单击 **[!UICONTROL Advanced campaign settings]**.

   ![](assets/s_ncs_user_edit_op_target.png)

1. 选择&#x200B;**[!UICONTROL Enable and edit control group configuration]**&#x200B;选项。
1. 单击&#x200B;**[!UICONTROL Edit...]**&#x200B;以配置对照组。

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

配置过程在[从主目标](#extracting-the-control-group-from-the-main-target)提取对照组和[添加对照组](#adding-a-population)中介绍。

### 激活投放{#activating-the-control-group-for-a-delivery}的对照组

您可以在投放级别定义对照组，在这种情况下，对照组将应用于相关活动的每个投放。

默认情况下，在对照组级别定义的活动配置适用于该活动的每个投放。 但是，您可以调整对照组以适应单个投放。

>[!NOTE]
>
>如果您为活动定义了对照组，并且还为链接到此活动的投放配置了该对照组，则只会应用为投放定义的。

1. 编辑相关投放，然后单击&#x200B;**[!UICONTROL Email parameters]**&#x200B;部分的&#x200B;**[!UICONTROL To]**&#x200B;链接。

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. 单击&#x200B;**[!UICONTROL Control group]**&#x200B;选项卡，然后选择&#x200B;**[!UICONTROL Enable and edit control group configuration]**。
1. 单击&#x200B;**[!UICONTROL Edit...]**&#x200B;以配置对照组。

配置过程在[从主目标](#extracting-the-control-group-from-the-main-target)提取对照组和[添加对照组](#adding-a-population)中介绍。

### 从主目标{#extracting-the-control-group-from-the-main-target}提取对照组

您可以从投放的主目标提取收件人。 在这种情况下，将从受此配置影响的投放操作的目标中进行收件人。 此提取可以是随机的，也可以是对收件人排序的结果。

![](assets/s_ncs_user_extract_from_target_population.png)

要提取对照组，请为活动或投放启用对照组，然后选择以下选项之一：**[!UICONTROL Activate random sampling]**&#x200B;或&#x200B;**[!UICONTROL Keep only the first records after sorting]**。

* **[!UICONTROL Activate random sampling]** :此选项将随机采样应用于目标人口中的收件人。如果随后将阈值设置为100，则对照组将由从目标人口中随机选择的100个收件人组成。 随机采样取决于数据库引擎。
* **[!UICONTROL Keep only the first records after sorting]**：通过此选项可根据一个或多个排序顺序定义限制。如果选择&#x200B;**[!UICONTROL Age]**&#x200B;字段作为排序标准，然后将100定义为阈值，则对照组将由100个最年轻的收件人组成。 例如，定义一个包含购买量很少的收件人或频繁购买的收件人的对照组，并将其行为与联系的收件人进行比较，这可能会很有意思。

单击&#x200B;**[!UICONTROL Next]**&#x200B;定义排序顺序（如有必要）并选择收件人限制模式。

![](assets/s_ncs_user_edit_op_target_param.png)

此配置等同于工作流中的共享活动，它允许您将目标分解为子集。 对照组是这些子集之一。 有关详细信息，请参阅[此部分](../../workflow/using/architecture.md)。

### 将新人口用作对照组{#adding-a-population}

您可以定义要用作对照组的新人口。 此群体可以来自一组收件人，也可以通过特定查询创建。

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>Adobe Campaign查询编辑器显示在[此部分](../../workflow/using/query.md)中。


#### 教程视频{#create-email-video}

此视频介绍如何在Adobe Campaign中创建活动和电子邮件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

其他活动操作视频[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)可用。