---
solution: Campaign Classic
product: campaign
title: 使用已命名权限设置权限
description: 了解如何使用已命名权限设置权限
feature: Access Management
role: Business Practitioner, Administrator
level: Beginner
translation-type: tm+mt
source-git-commit: f2bd093d3a010e079b7f5adf3371e21d07a4f3ae
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 4%

---


# 使用已命名权限设置权限{#named-rights}

默认情况下，Adobe Campaign建议使用一组已命名权限来定义分配给运算符和操作员组的授权。 可以从树的&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;节点编辑这些权限。

![](assets/s_ncs_admin_named_rights.png)

这些权利如下：

* **[!UICONTROL ADMINISTRATION]**:对实例具有 **[!UICONTROL ADMINISTRATION]** 完全访问权限的运算符。管理员用户可以执行/创建/编辑/删除任何对象，如工作流、投放、脚本等。

* **[!UICONTROL APPROVAL ADMINISTRATION]**:您可以在工作流和投放中设置多个批准步骤，以确保当前状态已经由指定的操作员或组批准。具有&#x200B;**[!UICONTROL APPROVAL ADMINISTRATION]**&#x200B;权限的用户可以设置批准步骤，还可以分配应批准这些步骤的操作员或操作员组。

* **[!UICONTROL CENTRAL]**:中央管理权(分布式营销)。

* **[!UICONTROL DELETE FOLDER]**:删除文件夹的权利。通过此权限，用户可以从资源管理器视图中删除文件夹。

* **[!UICONTROL EDIT FOLDERS]**:有权更改文件夹属性，如内部名称、标签、关联图像、子文件夹顺序等。

* **[!UICONTROL EXPORT]**:用户可以使用工作流Adobe Campaign将其活动实例中的数据导出到服务器或本地计算机上的 **[!UICONTROL EXPORT]** 文件中。

* **[!UICONTROL FILES ACCESS]**:有权通过脚本对文件进行读和写访问，该脚本可以写入工作流 **[!UICONTROL JavaScript]** 活动，以在服务器上读/写文件。

* **[!UICONTROL IMPORT]**:通用数据导入的权利。**[!UICONTROL IMPORT]** 允许您将数据导入任何其他表，而 **[!UICONTROL RECIPIENT IMPORT]** 右侧仅允许导入到收件人表。

* **[!UICONTROL INSERT FOLDERS]**:右键插入文件夹。具有&#x200B;**[!UICONTROL INSERT FOLDERS]**&#x200B;权限的用户可以在资源管理器视图的文件夹树中创建新文件夹。

* **[!UICONTROL LOCAL]**:本地管理(分布式营销)权。

* **[!UICONTROL MERGE]**:将选定记录合并为一个的权利。如果收件人作为重复存在，则右侧的&#x200B;**[!UICONTROL MERGE]**&#x200B;允许用户选择重复并将其合并到主收件人。

* **[!UICONTROL PREPARE DELIVERIES]**:创建、编辑和保存投放的权利。具有&#x200B;**[!UICONTROL PREPARE DELIVERIES]**&#x200B;权限的用户还可以开始投放分析进程。

* **[!UICONTROL PRIVACY DATA RIGHT]**:收集和删除隐私数据的权利。有关详细信息，请参见此 [ 页面](https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html)。

* **[!UICONTROL PROGRAM EXECUTION]**:使用各种编程语言执行命令的权利。

* **[!UICONTROL RECIPIENT IMPORT]**:有权导入收件人。具有&#x200B;**[!UICONTROL RECIPIENT IMPORT]**&#x200B;权限的用户可以将本地文件导入收件人表。

* **[!UICONTROL SQL SCRIPT EXECUTION]** 直接在数据库上执行任何SQL命令的权利。

* **[!UICONTROL START DELIVERIES]**:有权批准先前分析的投放。在投放分析后，投放将在各个批准步骤中暂停，并需要获得批准才能继续。 具有&#x200B;**[!UICONTROL START DELIVERIES]**&#x200B;权限的用户可以批准投放。

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**:使用SQL数据管理活动编写您自己的SQL脚本，以便创建和填充工作表(请参 [阅本节](../../workflow/using/sql-data-management.md))。

* **[!UICONTROL WORKFLOW]**:执行工作流的权利。没有此权限，用户将无法开始、停止或重新启动工作流。

* **[!UICONTROL WEBAPP]**:使用Web应用程序的权利。

>[!NOTE]
>
>此列表可能因平台上安装的加载项而异。

## 访问权限矩阵{#access-rights-matrix}

默认组和已命名权限允许操作员访问导航层次结构中的特定文件夹，并授予读取、写入和删除权限。

Adobe Campaign访问权限矩阵可在[此处](/help/platform/using/assets/access-rights-matrix.pdf)获得。

[![图像](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
