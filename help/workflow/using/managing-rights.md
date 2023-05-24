---
product: campaign
title: 管理工作流权限
description: 了解如何管理工作流权限
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---

# 管理工作流权限{#managing-rights}



如果不是Administrators，则Adobe Campaign操作员需要拥有创建、执行或修改工作流的访问权限。

一般而言，对工作流执行操作的操作员需要访问包含各种活动（收件人、收件人列表、订阅、投放等）期间使用的数据的文件，并且可能需要访问其子文件。

它们还必须映射到与它们将影响的工作流执行的操作（收件人导入、文件访问、融合、SQL脚本执行等）一致的命名权限。

有关管理操作员和权限的更多信息，请参阅此 [部分](../../platform/using/access-management.md).

## 操作员组 {#operator-groups-wf}

以下运算符组与工作流相关联：

* 此 **[!UICONTROL Workflow execution]** 组允许您控制定位工作流的执行和批准：已命名权限的工作流将映射到此组的操作员。 除了对数据文件的访问权限之外，还需要对工作流执行所有操作。 默认情况下， **[!UICONTROL Workflow execution]** 组对标准定位工作流文件和工作流模板具有只读访问权限。 此组中的操作员还具有对待处理审批文件的读写访问权限。
* 此 **[!UICONTROL Workflow supervisors]** 组允许操作员管理工作流审批。
* 此 **[!UICONTROL Operation Managers]** 组以访问活动工作流。

## 已命名权限 {#named-rights}

只有工作流命名权限特定于工作流：它允许您创建、启动和停止工作流。 已命名权限需要工作流文件的读取权限才能适用。 对于定位工作流，请阅读右上 **[!UICONTROL Profiles and Targets]** 文件是必需的。

## 工作流执行帐户 {#workflow-execution-account}

您可以配置要在工作流模板级别使用的执行帐户。 执行帐户允许您将授权直接映射到工作流，而不管Adobe Campaign运算符是何时开始执行的。 默认情况下，每个工作流都使用启动它的操作员的权限执行。

要将执行帐户映射到工作流，请转到工作流模板列表，并右键单击链接到工作流的模板。 选择 **[!UICONTROL Action > Change execution account...]** 然后选择要使用的帐户。
