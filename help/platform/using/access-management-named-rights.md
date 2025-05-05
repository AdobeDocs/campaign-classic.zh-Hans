---
product: campaign
title: 使用已命名权限设置权限
description: 了解如何使用已命名权限来设置权限
badge: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 5%

---

# 使用已命名权限设置权限{#named-rights}

>[!NOTE]
>
>此页面仅适用于使用本机身份验证连接到Campaign的操作员。 有关Adobe IMS身份验证，请参阅[此文档](https://helpx.adobe.com/cn/enterprise/using/manage-permissions-and-roles.html)。

默认情况下，Adobe Campaign建议一组已命名权限，用于定义分配给操作员和操作员组的授权。 可以从树的&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;节点编辑这些权限。

![](assets/s_ncs_admin_named_rights.png)

这些权利如下：

* **[!UICONTROL ADMINISTRATION]**：具有&#x200B;**[!UICONTROL ADMINISTRATION]**&#x200B;权限的操作员对该实例具有完全访问权限。 管理员用户可以执行/创建/编辑/删除任何对象，例如工作流、投放、脚本等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**：您可以在工作流和投放中设置多个批准步骤，以确保当前状态已由分配的操作员或组批准。 具有&#x200B;**[!UICONTROL APPROVAL ADMINISTRATION]**&#x200B;权限的用户可以设置批准步骤，还可以分配应批准这些步骤的操作员或操作员组。

* **[!UICONTROL CENTRAL]**：集中管理（分布式营销）权限。

* **[!UICONTROL DELETE FOLDER]**：有权删除文件夹。 使用此权限，用户可以从资源管理器视图中删除文件夹。

* **[!UICONTROL EDIT FOLDERS]**：更改文件夹属性（如内部名称、标签、关联的图像、子文件夹顺序等）的权限。

* **[!UICONTROL EXPORT]**：用户可以使用&#x200B;**[!UICONTROL EXPORT]**&#x200B;工作流活动，将数据从其Adobe Campaign实例导出到服务器或本地计算机上的文件中。

* **[!UICONTROL FILES ACCESS]**：有权通过脚本读取和写入文件，该脚本可在&#x200B;**[!UICONTROL JavaScript]**&#x200B;工作流活动中写入以读取/写入服务器上的文件。

* **[!UICONTROL IMPORT]**：通用数据导入权限。 **[!UICONTROL IMPORT]**&#x200B;允许您将数据导入任何其他表，而&#x200B;**[!UICONTROL RECIPIENT IMPORT]**&#x200B;权限仅允许将数据导入收件人表。

* **[!UICONTROL INSERT FOLDERS]**：有权插入文件夹。 具有&#x200B;**[!UICONTROL INSERT FOLDERS]**&#x200B;权限的用户可以在资源管理器视图的文件夹树中创建新文件夹。

* **[!UICONTROL LOCAL]**：本地管理权限（分布式营销）。

* **[!UICONTROL MERGE]**：有权将选定记录合并为一个。 如果收件人作为重复项存在，则通过&#x200B;**[!UICONTROL MERGE]**&#x200B;权限，用户可以选择重复项并将其合并到主收件人中。

* **[!UICONTROL PREPARE DELIVERIES]**：有权创建、编辑和保存投放。 具有&#x200B;**[!UICONTROL PREPARE DELIVERIES]**&#x200B;权限的用户也可以启动投放分析流程。

* **[!UICONTROL PRIVACY DATA RIGHT]**：有权收集和删除隐私数据。 有关详细信息，请参见此 [ 页面](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**：有权执行各种编程语言的命令。

* **[!UICONTROL RECIPIENT IMPORT]**：有权导入收件人。 具有&#x200B;**[!UICONTROL RECIPIENT IMPORT]**&#x200B;权限的用户可以将本地文件导入收件人表。

* **[!UICONTROL SQL SCRIPT EXECUTION]**&#x200B;直接在数据库上执行任何SQL命令的权限。

* **[!UICONTROL START DELIVERIES]**：有权批准以前分析的投放。 投放分析后，投放将在各种审批步骤暂停，并且需要获得审批才能恢复。 允许具有&#x200B;**[!UICONTROL START DELIVERIES]**&#x200B;权限的用户批准投放。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**：有权使用SQL数据管理活动编写您自己的SQL脚本，以便创建和填充工作表（请参阅[此章节](../../workflow/using/sql-data-management.md)）。

* **[!UICONTROL WORKFLOW]**：有权执行工作流。 如果没有此权限，用户将无法启动、停止或重新启动工作流。

* **[!UICONTROL WEBAPP]**：有权使用Web应用程序。

>[!NOTE]
>
>此列表可能会因平台上安装的加载项而异。

## 访问权限矩阵 {#access-rights-matrix}

默认组和已命名权限允许操作员访问导航层次结构中的特定文件夹，并授予读取、写入和删除权限。

[此处](/help/platform/using/assets/access-rights-matrix.pdf)提供Adobe Campaign访问权限矩阵。

[![图像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=zh-Hans)
