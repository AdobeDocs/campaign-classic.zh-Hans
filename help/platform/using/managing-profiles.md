---
product: campaign
title: 管理用户档案
description: 管理用户档案
feature: Profiles
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 28%

---

# 管理用户档案{#managing-profiles}



## 收件人树状结构 {#recipient-tree}

要访问高级收件人管理功能，您需要编辑Adobe Campaign树。 要执行此操作，请单击 **[!UICONTROL Explorer]** 工具栏中的按钮。

默认情况下，收件人存储在 **[!UICONTROL Profiles and targets]** Adobe Campaign树的节点。 在相同的节点中，您可以创建一个或多个文件夹和子文件夹来存储收件人用户档案。

每个节点都与一个文件夹重合。 必须将来自每个文件夹的数据视为彼此分区。 也就是说，对于多个收件人文件夹，很难管理重复的项目。

>[!NOTE]
>
>要显示数据库中所有收件人的列表，您必须创建一个视图。 了解详情，请参阅 [文件夹和视图](../../platform/using/access-management-folders.md).

## 移动收件人 {#moving-recipients}

您可以选择一个或多个收件人，将其从收件人列表中拖放到所需文件夹中。 警告消息会要求您确认此操作。

## 复制收件人 {#copying-a-recipient}

您可以右键单击所需的收件人，然后选择 **[!UICONTROL Copy]**.

## 删除收件人 {#deleting-recipients}

要删除收件人，请将他们移至特定文件夹，然后清除该文件夹的内容。 它是 **强烈建议不要使用** 该 **[!UICONTROL Delete]** 选项。

要清除文件夹，请使用 **[!UICONTROL Actions > Purge folder]** 菜单，可通过右键单击所需的文件夹来访问。

![](assets/s_ncs_user_purge_folder.png)

单击 **[!UICONTROL Start]** 以启动操作。 窗口的中间会显示进度状态，如下所示：

![](assets/s_ncs_user_purge_folder_start.png)
