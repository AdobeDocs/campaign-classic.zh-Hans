---
product: campaign
title: 管理用户档案
description: 管理用户档案
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 26%

---

# 管理轮廓{#managing-profiles}



## 收件人树状结构 {#recipient-tree}

要访问高级收件人管理功能，您需要编辑Adobe Campaign树。 为此，请单击工具栏中的&#x200B;**[!UICONTROL Explorer]**&#x200B;按钮。

默认情况下，收件人存储在Adobe Campaign树的&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;节点中。 在相同的节点中，您可以创建一个或多个文件夹和子文件夹来存储收件人用户档案。

每个节点都与一个文件夹重合。 必须将来自每个文件夹的数据视为彼此分区。 也就是说，对于多个收件人文件夹，很难管理重复的项目。

>[!NOTE]
>
>要显示数据库中所有收件人的列表，您必须创建一个视图。 在[文件夹和视图](../../platform/using/access-management-folders.md)中了解详情。

## 移动收件人 {#moving-recipients}

您可以选择一个或多个收件人，将其从收件人列表中拖放到所需文件夹中。 警告消息会要求您确认此操作。

## 复制收件人 {#copying-a-recipient}

通过右键单击所需的收件人并选择&#x200B;**[!UICONTROL Copy]**，您可以复制同一文件夹中的收件人。

## 删除收件人 {#deleting-recipients}

要删除收件人，请将他们移至特定文件夹，然后清除该文件夹的内容。 在这种情况下，**强烈建议不要使用**&#x200B;的&#x200B;**[!UICONTROL Delete]**&#x200B;选项。

要清除文件夹，请使用&#x200B;**[!UICONTROL Actions > Purge folder]**&#x200B;菜单，可通过右键单击所需文件夹来访问。

![](assets/s_ncs_user_purge_folder.png)

单击&#x200B;**[!UICONTROL Start]**&#x200B;启动操作。 窗口的中间会显示进度状态，如下所示：

![](assets/s_ncs_user_purge_folder_start.png)
