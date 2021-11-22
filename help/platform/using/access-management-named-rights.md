---
product: campaign
title: 使用已命名权限设置权限
description: 了解如何使用命名权限设置权限
feature: Access Management
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 7%

---

# 使用已命名权限设置权限{#named-rights}

![](../../assets/common.svg)

默认情况下，Adobe Campaign会提供一组命名权限，用于定义分配给操作员和操作员组的授权。 这些权限可从 **[!UICONTROL Administration > Access management > Named rights]** 树的节点。

![](assets/s_ncs_admin_named_rights.png)

这些权限如下：

* **[!UICONTROL ADMINISTRATION]**:运算符 **[!UICONTROL ADMINISTRATION]** 权限对实例具有完全访问权限。 管理员用户可以执行/创建/编辑/删除任何对象，如工作流、交付、脚本等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**:您可以在工作流和投放中设置多个批准步骤，以确保已分配的操作员或组批准当前状态。 具有 **[!UICONTROL APPROVAL ADMINISTRATION]** 权限可以设置批准步骤，还可以分配应批准这些步骤的操作员或操作员组。

* **[!UICONTROL CENTRAL]**:中央管理权（分布式营销）。

* **[!UICONTROL DELETE FOLDER]**:有权删除文件夹。 在此权限下，允许用户从资源管理器视图中删除文件夹。

* **[!UICONTROL EDIT FOLDERS]**:有权更改文件夹属性，如内部名称、标签、关联图像、子文件夹顺序等。

* **[!UICONTROL EXPORT]**:用户可以使用将其Adobe Campaign实例中的数据导出到服务器或本地计算机上的文件 **[!UICONTROL EXPORT]** 工作流活动。

* **[!UICONTROL FILES ACCESS]**:有权通过脚本读取和写入文件，该脚本可在 **[!UICONTROL JavaScript]** 工作流活动，用于在服务器上读/写文件。

* **[!UICONTROL IMPORT]**:通用数据导入的权限。 **[!UICONTROL IMPORT]** 允许您将数据导入任何其他表，而 **[!UICONTROL RECIPIENT IMPORT]** right仅允许导入到收件人表中。

* **[!UICONTROL INSERT FOLDERS]**:有权插入文件夹。 具有 **[!UICONTROL INSERT FOLDERS]** 在“资源管理器”视图的文件夹树中，右侧可以创建新文件夹。

* **[!UICONTROL LOCAL]**:本地管理权（分布式营销）。

* **[!UICONTROL MERGE]**:有权将选定的记录合并到一个记录中。 如果收件人存在为重复项，则 **[!UICONTROL MERGE]** 右侧允许用户选择重复项并将其合并到主收件人中。

* **[!UICONTROL PREPARE DELIVERIES]**:有权创建、编辑和保存投放。 具有 **[!UICONTROL PREPARE DELIVERIES]** 右侧还可以启动投放分析流程。

* **[!UICONTROL PRIVACY DATA RIGHT]**:收集和删除隐私数据的权利。 有关详细信息，请参见此 [ 页面](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**:以各种编程语言执行命令的权利。

* **[!UICONTROL RECIPIENT IMPORT]**:有权导入收件人。 具有 **[!UICONTROL RECIPIENT IMPORT]** 权限可以将本地文件导入收件人表。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 有权直接在数据库上执行任何SQL命令。

* **[!UICONTROL START DELIVERIES]**:有权批准之前分析的投放。 投放分析后，投放将在各个批准步骤中暂停，并需要获得批准才能继续。 具有 **[!UICONTROL START DELIVERIES]** 允许批准投放。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**:有权使用SQL数据管理活动编写您自己的SQL脚本，以便创建和填充工作表(请参阅 [此部分](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**:有权执行工作流。 如果没有此权限，用户将无法启动、停止或重新启动工作流。

* **[!UICONTROL WEBAPP]**:有权使用Web应用程序。

>[!NOTE]
>
>此列表可能因平台上安装的加载项而异。

## 访问权限矩阵 {#access-rights-matrix}

默认组和命名权限允许操作员访问导航层次结构中的某些文件夹，并授予读取、写入和删除权限。

Adobe Campaign访问权限矩阵可用 [此处](/help/platform/using/assets/access-rights-matrix.pdf).

[![图像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
