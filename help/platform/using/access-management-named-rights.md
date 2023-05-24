---
product: campaign
title: 使用已命名权限设置权限
description: 了解如何使用已命名权限设置权限
badge: label="v7" type="信息性" tooltip="仅适用于Campaign Classicv7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 5%

---

# 使用已命名权限设置权限{#named-rights}



默认情况下，Adobe Campaign建议一组已命名的权限，该权限允许您定义分配给操作员和操作员组的授权。 这些权限可以从 **[!UICONTROL Administration > Access management > Named rights]** 树节点。

![](assets/s_ncs_admin_named_rights.png)

这些权利如下：

* **[!UICONTROL ADMINISTRATION]**：运算符和 **[!UICONTROL ADMINISTRATION]** 权限对实例具有完全访问权限。 管理员用户可以执行/创建/编辑/删除任何对象，例如工作流、投放、脚本等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**：您可以在工作流和投放中设置多个批准步骤，以确保当前状态已由分配的操作员或组批准。 具有的用户 **[!UICONTROL APPROVAL ADMINISTRATION]** 权限可以设置批准步骤，还可以分配应批准这些步骤的操作员或操作员组。

* **[!UICONTROL CENTRAL]**：集中管理权限（分布式营销）。

* **[!UICONTROL DELETE FOLDER]**：有权删除文件夹。 凭借此权限，用户可以从资源管理器视图中删除文件夹。

* **[!UICONTROL EDIT FOLDERS]**：更改文件夹属性（如内部名称、标签、关联的图像、子文件夹顺序等）的权利。

* **[!UICONTROL EXPORT]**：用户可以使用将数据从其Adobe Campaign实例导出到服务器或本地计算机上的文件中。 **[!UICONTROL EXPORT]** 工作流活动。

* **[!UICONTROL FILES ACCESS]**：有权通过脚本读取和写入文件，该脚本可以写入 **[!UICONTROL JavaScript]** 用于在服务器上读/写文件的工作流活动。

* **[!UICONTROL IMPORT]**：一般数据导入权限。 **[!UICONTROL IMPORT]** 允许您将数据导入到任何其他表中，而 **[!UICONTROL RECIPIENT IMPORT]** 权限仅允许导入收件人表。

* **[!UICONTROL INSERT FOLDERS]**：有权插入文件夹。 具有的用户 **[!UICONTROL INSERT FOLDERS]** 可在资源管理器视图的文件夹树中创建新文件夹。

* **[!UICONTROL LOCAL]**：本地管理权限（分布式营销）。

* **[!UICONTROL MERGE]**：有权将选定的记录合并为一条记录。 如果收件人作为重复项存在，则 **[!UICONTROL MERGE]** 权限允许用户选择重复项并将它们合并到主收件人中。

* **[!UICONTROL PREPARE DELIVERIES]**：有权创建、编辑和保存投放。 具有的用户 **[!UICONTROL PREPARE DELIVERIES]** 右侧还可以启动投放分析过程。

* **[!UICONTROL PRIVACY DATA RIGHT]**：有权收集和删除隐私数据。 有关详细信息，请参见此 [ 页面](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**：有权执行各种编程语言的命令。

* **[!UICONTROL RECIPIENT IMPORT]**：导入收件人的权限。 具有的用户 **[!UICONTROL RECIPIENT IMPORT]** 权限可以将本地文件导入收件人表。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 有权直接在数据库上执行任何SQL命令。

* **[!UICONTROL START DELIVERIES]**：有权批准之前分析的投放。 投放分析后，投放将在各种批准步骤暂停，并且需要获得批准才能恢复。 具有的用户 **[!UICONTROL START DELIVERIES]** 允许权限审批投放。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**：有权使用SQL数据管理活动编写自己的SQL脚本，以便创建和填充工作表(请参阅 [本节](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**：有权执行工作流。 如果没有此权限，用户将无法启动、停止或重新启动工作流。

* **[!UICONTROL WEBAPP]**：有权使用Web应用程序。

>[!NOTE]
>
>此列表可能会因平台上安装的加载项而异。

## 访问权限矩阵 {#access-rights-matrix}

默认组和命名权限允许操作员访问导航层次结构中的特定文件夹，并授予读取、写入和删除权限。

Adobe Campaign访问权限矩阵可用 [此处](/help/platform/using/assets/access-rights-matrix.pdf).

[![图像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf)
