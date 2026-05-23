---
product: campaign
title: 使用已命名权限设置权限
description: 了解如何使用已命名权限来设置权限
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
TQID: https://experienceleague.adobe.com/GApH-ZtovMX--PzISD-Pvafo3pfcbG-OqHzp5kCvcNQ
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2:
  - id: e3988c18-3cfa-4f16-b812-ac2d2b1056fa
  - id: efa38731-2723-4334-8d8b-a778af834835
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 652
ht-degree: 4%

---

# 使用已命名权限设置权限{#named-rights}

默认情况下，Adobe Campaign建议一组已命名权限，用于定义分配给操作员和操作员组的授权。 可以从树的&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;节点编辑这些权限。

![](assets/s_ncs_admin_named_rights.png)

这些权利如下：

* **[!UICONTROL ADMINISTRATION]**：具有&#x200B;**[!UICONTROL ADMINISTRATION]**&#x200B;权限的操作员对该实例具有完全访问权限。 管理员用户可以执行/创建/编辑/删除任何对象，例如工作流、投放、脚本等。

  >[!IMPORTANT]
  >
  >**迁移到IMS后：**&#x200B;迁移到Adobe Identity Management System (IMS)后，任何产品配置文件或命名权限在其名称中包含“管理员”一词（如“管理员”、“管理员”、“管理员”等） 将自动授予对Campaign控制面板的访问权限。 我们建议避免在命名权限或角色名称中使用“admin”，除非您希望这些用户具有控制面板访问权限。 了解有关[IMS迁移](../../technotes/using/migrate-users-to-ims.md)和[管理控制面板访问权限](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans){target="_blank"}的更多信息。

* **[!UICONTROL APPROVAL ADMINISTRATION]**：您可以在工作流和投放中设置多个批准步骤，以确保当前状态已由分配的操作员或组批准。 具有&#x200B;**[!UICONTROL APPROVAL ADMINISTRATION]**&#x200B;权限的用户可以设置批准步骤，还可以分配应批准这些步骤的操作员或操作员组。

  >[!IMPORTANT]
  >
  >**迁移到IMS后：**&#x200B;产品配置文件或包含“管理员”一词的已命名权限（如“审批管理员”）将授予对Campaign控制面板的访问权限。 了解有关[IMS迁移](../../technotes/using/migrate-users-to-ims.md)和[管理控制面板访问权限](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans){target="_blank"}的更多信息。

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

* **[!UICONTROL PRIVACY DATA RIGHT]**：有权收集和删除隐私数据。 有关详细信息，请参见此 [&#x200B; 页面](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**：有权执行各种编程语言的命令。

* **[!UICONTROL RECIPIENT IMPORT]**：有权导入收件人。 具有&#x200B;**[!UICONTROL RECIPIENT IMPORT]**&#x200B;权限的用户可以将本地文件导入收件人表。

* **[!UICONTROL SQL SCRIPT EXECUTION]**&#x200B;直接在数据库上执行任何SQL命令的权限。

* **[!UICONTROL START DELIVERIES]**：有权批准以前分析的投放。 投放分析后，投放将在各种审批步骤暂停，并且需要获得审批才能恢复。 允许具有&#x200B;**[!UICONTROL START DELIVERIES]**&#x200B;权限的用户批准投放。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**：有权使用SQL数据管理活动编写您自己的SQL脚本，以便创建和填充工作表。 请参阅[Campaign v8文档](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/sql-data-management.html?lang=zh-Hans){target="_blank"}。

* **[!UICONTROL WORKFLOW]**：有权执行工作流。 如果没有此权限，用户将无法启动、停止或重新启动工作流。

* **[!UICONTROL WEBAPP]**：有权使用Web应用程序。

>[!NOTE]
>
>此列表可能会因平台上安装的加载项而异。

## 访问权限矩阵 {#access-rights-matrix}

默认组和已命名权限允许操作员访问导航层次结构中的特定文件夹，并授予读取、写入和删除权限。

[此处](/help/platform/using/assets/access-rights-matrix.pdf)提供Adobe Campaign访问权限矩阵。

[![image](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=zh-Hans)
