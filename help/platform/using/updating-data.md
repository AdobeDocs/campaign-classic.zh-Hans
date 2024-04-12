---
product: campaign
title: 更新数据
description: 更新数据
feature: Data Management
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 34%

---

# 更新数据{#updating-data}



可以手动或自动更新已链接至收件人用户档案的数据。

## 设置自动更新 {#setting-up-an-automatic-update}

可以通过工作流配置自动更新。 如需详细信息，请参阅[此小节](../../workflow/using/update-data.md)。

## 执行批量更新 {#performing-a-mass-update}

要执行手动更新，请右键单击选定的收件人以使用 **[!UICONTROL Actions]** 快捷菜单，或使用 **[!UICONTROL Actions]** 图标。

![](assets/s_ncs_user_action_icon.png)

有两种类型的更新：对一组收件人进行批量更新，以及在两个用户档案之间合并数据。 对于这两种操作，向导可帮助您配置更新工作。

### 大量更新 {#mass-update}

要成批更新，请使用 **[!UICONTROL Action > Mass update of selected lines...]**. 向导可帮助您配置并运行更新。

向导的第一步是指定要更新的字段。

向导的左侧部分显示可用字段列表。 使用 **[!UICONTROL Find]** 字段以运行对这些字段的搜索。 按 **输入** 键浏览列表。 符合您所输入条件的字段名称会以粗体显示，如下所示。

双击要更新的字段，从而在向导的右侧显示它们。

![](assets/s_ncs_user_update_wizard01_1.png)

如果出现错误，请使用 **[!UICONTROL Delete]** 按钮从要更新的字段列表中删除字段。

选择或输入值，从而将其应用到需更新的用户档案。

![](assets/s_ncs_user_update_wizard01_12.png)

您可以单击 **[!UICONTROL Distribution of values]** 为当前文件夹中存在的收件人（不仅是受更新影响的收件人）显示所选字段的值分布。

![](assets/s_ncs_user_update_wizard01_2.png)

您可以定义筛选器以显示此窗口中的值分布，或修改当前文件夹以显示另一个文件夹中的值分布。 这些操作都是只读的，不会影响所定义更新的配置。

![](assets/s_ncs_user_update_wizard01_3.png)

关闭此窗口并单击 **[!UICONTROL Next]** 以显示第二个更新向导步骤。 在此步骤中，您可以通过单击 **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

有关更新执行的信息会显示在向导的上部。

此 **[!UICONTROL Stop]** 允许您取消更新，但某些记录可能已更新，停止进程将不会取消这些更新。 进度条会显示目前操作的进度。

### 合并数据 {#merge-data}

选择 **[!UICONTROL Merge selected lines...]** 以启动两个收件人用户档案的合并。 在选择选项之前，必须选择要合并的配置文件。 使用向导来配置和开始合并操作。

向导显示在一个或其他源配置文件中完成的每个字段要检索的值。 如果要合并的用户档案中的一个或多个字段具有不同的值，则它们将显示在 **[!UICONTROL List of conflicts]** 部分。 您可使用列表下方的单选按钮来选择默认的用户档案，如以下示例所示：

![](assets/s_ncs_user_merge_wizard01_1.png)

单击 **[!UICONTROL Compute]** 以显示您选择的结果。

![](assets/s_ncs_user_merge_wizard01_2.png)

查看 **[!UICONTROL Result]** 窗口两个部分的列，然后单击 **[!UICONTROL Finish]** 以运行合并。

## 导出数据 {#exporting-data}

列表的内容可以导出。 要配置并执行导出：

1. 选择要导出的记录。
1. 右键单击并选择 **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. 然后选择要提取的数据。 默认情况下，会将显示的所有列都添加到输出列中。

   ![](assets/s_ncs_user_export_list_start.png)

   有关如何配置导出向导的详细信息，请参阅 [本节](../../platform/using/executing-export-jobs.md).

## 订阅服务 {#subscribing-to-a-service}

在大多数情况下，收件人会通过专用的登陆页面订阅新闻稿，如中所述 [本节](../../delivery/using/managing-subscriptions.md). 但是，可以手动订阅服务（新闻稿或病毒式服务）的已过滤收件人的用户档案。 操作步骤：

1. 选择您想要订阅的收件人，然后单击鼠标右键。
1. 选择 **[!UICONTROL Actions > Subscribe selection to a service]**。

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. 选择所需的服务并单击 **[!UICONTROL Next]**：

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >此编辑器允许您创建新服务：单击 **[!UICONTROL Create]** 按钮。

1. 您可以 **[!UICONTROL Send a confirmation message]** 发送给收件人。 可在链接到所选服务的订阅场景中配置此消息的內容。
1. 单击 **[!UICONTROL Start]** 按钮以运行订阅进程。

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

通过窗口的上半部分，您可以监视执行过程。 此 **[!UICONTROL Stop]** 按钮允许您停止进程。 但是，已处理的收件人将被订阅。

如果您取消选中 **[!UICONTROL Do not keep a trace of this job in the database]** 选项，您可以选择（或创建）执行文件夹，其中将存储有关此进程的信息。

要检查该流程，请转到 **[!UICONTROL Subscriptions]** 选项卡上或选项卡上与此操作相关的收件人的用户档案 **[!UICONTROL Subscriptions]** 选项卡，访问方式： **[!UICONTROL Profiles and Targets > Services and Subscriptions]** 节点。

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>如需有关创建和配置信息服务的详细信息，请参阅[此页面](../../delivery/using/managing-subscriptions.md)。
