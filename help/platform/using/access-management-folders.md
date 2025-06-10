---
product: campaign
title: 管理对Campaign文件夹的访问
description: 了解如何授予对Campaign文件夹的访问权限并创建视图
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: 6e83067cef2b08b5bee37610bfef515714756ada
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 2%

---

# 管理对文件夹的访问{#folder-access-management}



Explorer导航树的每个文件夹都具有附加的读、写和删除访问权限。 要访问文件，操作员或操作员组必须至少具有文件的读取权限。

>[!NOTE]
>
>要了解有关文件夹权限的更多信息，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}。


## 文件夹和视图 {#folders-and-views}

### 什么是文件夹 {#about-folders}

文件夹是Adobe Campaign树中的节点。 这些节点是通过&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜单右键单击树创建的。 默认情况下，第一个菜单允许您添加对应于当前上下文的文件夹。

![](assets/s_ncs_user_add_folder_in_tree.png)

可以自定义Explorer导航树。 在本节[&#128279;](adobe-campaign-workspace.md)中了解配置步骤和最佳实践。

### 什么是视图 {#about-views}

此外，您还可以创建视图以限制对数据访问，并组织树的内容以满足您的要求。 然后，可以为视图分配权限。

视图是一个文件夹，它显示实际存储在相同类型的一个或多个其他文件夹中的记录。 例如，如果您创建了一个视图的Campaign文件夹，则该文件夹会默认显示数据库中存在的所有Campaign，无论其来源如何。 然后，可以过滤此数据。

将文件夹转换为视图时，与数据库中存在的文件夹类型对应的所有数据都会显示在视图中，无论其保存在哪个文件夹中。 然后，您可以对其进行筛选，以限制显示的数据列表。

>[!IMPORTANT]
>
>视图包含数据并提供对数据的访问，但数据并未实际存储在视图文件夹中。 操作员必须在数据源文件夹中拥有所需操作的适当权限（至少具有读取权限）。
>
>要在不授予视图源文件夹访问权限的情况下授予视图访问权限，请不要授予对源文件夹父节点的读取权限。

为了区分视图和文件夹，每个视图的名称以不同的颜色（深青色）显示。

![](assets/s_ncs_user_view_name_color.png)

### 添加文件夹和创建视图 {#adding-folders-and-creating-views}

>[!IMPORTANT]
>
>开箱即用的文件夹不应标记为视图。


在下面的示例中，我们将创建新文件夹以显示特定数据：

1. 创建新的&#x200B;**[!UICONTROL Deliveries]**&#x200B;类型文件夹，并将其命名为&#x200B;**投放France**。
1. 右键单击此文件夹并选择&#x200B;**[!UICONTROL Properties...]**。

   ![屏幕截图显示右键单击属性](assets/s_ncs_user_add_folder_exple.png)

1. 在&#x200B;**[!UICONTROL Restriction]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL This folder is a view]**。 随后将显示数据库中的所有投放。

   ![显示正在检查的视图框的屏幕](assets/s_ncs_user_add_folder_exple01.png)

1. 在窗口的中间部分通过查询编辑器定义投放过滤器条件：随后将显示与定义的过滤器对应的营销活动。

   >[!NOTE]
   >
   >查询编辑器出现在[此部分](../../platform/using/about-queries-in-campaign.md)中。

   过滤条件为：

![显示不同筛选条件的屏幕截图](assets/s_ncs_user_add_folder_exple00.png)

视图中将显示以下投放：

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>管理[事务性消息传递](../../message-center/using/about-transactional-messaging.md)事件时，**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;文件夹不能设置为执行实例上的视图，因为这会导致访问权限问题。 有关事件集合的详细信息，请参阅[此部分](../../message-center/using/about-event-processing.md#event-collection)。

<!--
## Permissions on a folder

### Edit permissions on a folder {#edit-permissions-on-a-folder}

To edit permissions on a specific folder of the tree, follow the steps below:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modify permissions {#modify-permissions}

To modify permissions, you can:

* **Replace a group or an operator**. To do this, click one of the groups (or operators) with rights to the folder, and select a new group (or a new operator) from the drop-down list:

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **Authorize a group or an operator**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Forbid a group or an operator**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Select the rights assigned to a group or an operator**. To do this, click the group or operator concerned, then select the access rights you want to grant and deselect the others.

  ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagate permissions {#propagate-permissions}

You can propagate authorizations and access rights. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

The authorizations defined in this window will then be applied to all the sub-folders of the current node. You can then overload these authorizations for each of the sub-folders.

>[!NOTE]
>
>Clearing this option for a folder does not automatically clear it for the sub-folders. You must clear it explicitly for each of the sub-folders.

### Grant access to all operators {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. If this option is cleared, you must explicitly add the operator (or their group) to the list of authorizations in order for them to have access.

![](assets/s_ncs_user_folder_properties_security03b.png)
-->