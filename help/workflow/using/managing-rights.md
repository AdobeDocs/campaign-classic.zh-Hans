---
product: campaign
title: 管理工作流权限
description: 了解如何管理工作流权限
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---

# 管理工作流权限{#managing-rights}



如果不是管理员，Adobe Campaign操作员需要拥有创建、执行或修改工作流的访问权限。

一般而言，操作工作流操作员需要访问包含各种活动（收件人、收件人列表、订阅、投放等）期间使用的数据的文件，并且可能需要访问其子文件。

它们还必须映射到与它们会影响的工作流执行的操作（收件人导入、文件访问、融合、SQL脚本执行等）一致的已命名权限。

有关管理操作员和权限的详细信息，请参阅此[部分](../../platform/using/access-management.md)。

## 操作员组 {#operator-groups-wf}

以下运算符组与工作流相关联：

* 通过&#x200B;**[!UICONTROL Workflow execution]**&#x200B;组，您可以控制定位工作流的执行和批准：命名权限的工作流将映射到此组的操作员。 除了对数据文件的访问权限之外，需要对工作流执行所有操作。 默认情况下，**[!UICONTROL Workflow execution]**&#x200B;组对标准定位工作流文件和工作流模板具有只读访问权限。 此组中的操作员还具有对待处理审批文件的读写访问权限。
* **[!UICONTROL Workflow supervisors]**&#x200B;组允许操作员管理工作流审批。
* 用于访问营销活动工作流的&#x200B;**[!UICONTROL Operation Managers]**&#x200B;组。

## 已命名权限 {#named-rights}

只有工作流指明权限才是工作流所特有的：它允许您创建、启动和停止工作流。 已命名权限需要工作流文件的读取权限才能适用。 对于定位工作流，需要对&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;文件的读取权限。

## 工作流执行帐户 {#workflow-execution-account}

您可以配置要在工作流模板级别使用的执行帐户。 无论是否使用Adobe Campaign运算符开始执行，执行帐户都允许您直接将授权映射到工作流。 默认情况下，每个工作流都使用启动它的操作员的权限执行。

要将执行帐户映射到工作流，请转到工作流模板列表，并右键单击链接到工作流的模板。 选择&#x200B;**[!UICONTROL Action > Change execution account...]**，然后选择要使用的帐户。
