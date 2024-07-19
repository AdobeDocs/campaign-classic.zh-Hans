---
product: campaign
title: 管理对Campaign文件夹的访问
description: 了解如何授予对Campaign文件夹的访问权限并创建视图
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 1%

---

# 管理对文件夹的访问{#folder-access-management}



Explorer导航树的每个文件夹都具有附加的读、写和删除访问权限。 要访问文件，操作员或操作员组必须至少具有文件的读取权限。

## 文件夹和视图 {#folders-and-views}

### 什么是文件夹 {#about-folders}

文件夹是Adobe Campaign树中的节点。 这些节点是通过&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜单右键单击树创建的。 默认情况下，第一个菜单允许您添加对应于当前上下文的文件夹。

![](assets/s_ncs_user_add_folder_in_tree.png)

可以自定义Explorer导航树。 在本节](adobe-campaign-workspace.md)中了解配置步骤和最佳实践[。

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

在下面的示例中，我们将创建新文件夹以显示特定数据：

1. 创建新的&#x200B;**[!UICONTROL Deliveries]**&#x200B;类型文件夹，并将其命名为&#x200B;**投放France**。
1. 右键单击此文件夹并选择&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_add_folder_exple.png)

1. 在&#x200B;**[!UICONTROL Restriction]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL This folder is a view]**。 随后将显示数据库中的所有投放。

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 在窗口的中间部分通过查询编辑器定义投放过滤器条件：随后将显示与定义的过滤器对应的营销活动。

   >[!NOTE]
   >
   >查询编辑器出现在[此部分](../../platform/using/about-queries-in-campaign.md)中。

   过滤条件为：

![](assets/s_ncs_user_add_folder_exple00.png)

视图中将显示以下投放：

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>管理[事务性消息传递](../../message-center/using/about-transactional-messaging.md)事件时，**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;文件夹不能设置为执行实例上的视图，因为这会导致访问权限问题。 有关事件集合的详细信息，请参阅[此部分](../../message-center/using/about-event-processing.md#event-collection)。

## 文件夹的权限

### 编辑文件夹权限 {#edit-permissions-on-a-folder}

要编辑树中特定文件夹的权限，请执行以下步骤：

1. 右键单击该文件夹并选择&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_folder_properties.png)

1. 单击&#x200B;**[!UICONTROL Security]**&#x200B;选项卡可查看此文件夹的授权。

   ![](assets/s_ncs_user_folder_properties_security.png)

### 修改权限 {#modify-permissions}

要修改权限，您可以：

* **替换组或操作员**。 为此，请单击对该文件夹具有权限的组（或操作员）之一，然后从下拉列表中选择一个新组（或新操作员）：

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **授权组或操作员**。 为此，请单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后选择要为此文件夹分配授权的组或运算符。
* **禁止群组或操作员**。 为此，请单击&#x200B;**[!UICONTROL Delete]**&#x200B;并选择要从中移除此文件夹授权的组或运算符。
* **选择分配给组或操作员的权限**。 为此，请单击相关的组或操作员，然后选择要授予的访问权限并取消选择其他权限。

  ![](assets/s_ncs_user_folder_properties_security03.png)

### 传播权限 {#propagate-permissions}

您可以传播授权和访问权限。 为此，请在文件夹属性中选择&#x200B;**[!UICONTROL Propagate]**&#x200B;选项。

此窗口中定义的授权随后将应用于当前节点的所有子文件夹。 然后，您可以对每个子文件夹重载这些授权。

>[!NOTE]
>
>为文件夹清除此选项不会自动为子文件夹清除它。 您必须为每个子文件夹显式清除它。

### 向所有操作员授予访问权限 {#grant-access-to-all-operators}

在&#x200B;**[!UICONTROL Security]**&#x200B;选项卡中，如果选择&#x200B;**[!UICONTROL System folder]**&#x200B;选项，则所有操作员都将有权访问此数据，不论他们具有什么权限。 如果清除此选项，则必须将运算符（或其组）明确添加到授权列表，以便他们能够访问。

![](assets/s_ncs_user_folder_properties_security03b.png)
