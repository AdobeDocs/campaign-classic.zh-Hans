---
title: 管理权限
seo-title: 管理权限
description: 管理权限
seo-description: null
page-status-flag: never-activated
uuid: 07039fec-c957-4548-acc7-22dc7827a54b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: f78603e9-f6ff-4ebe-941b-b3fbd1924b71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 管理权限{#managing-rights}

如果Adobe Campaign运营商不是管理员，则需要访问权限才能创建、执行或修改工作流。

一般而言，对工作流进行操作的操作员需要访问包含各种活动（收件人、收件人列表、订阅、分发等）期间使用的数据的文件，以及可能的子文件。

它们还必须映射到与工作流执行的操作（收件人导入、文件访问、融合、SQL脚本执行等）一致的指定权限。

有关管理操作符和权限的详细信息，请参阅此 [部分](../../platform/using/access-management.md)。

## 运算符组 {#operator-groups}

以下操作符组与工作流相关联：

* 通过 **[!UICONTROL Workflow execution]** 该组，您可以控制定位工作流的执行和批准：名为right的工作流将映射到此组的运算符。 除了对数据文件的访问权限外，工作流上的所有操作都必须执行此操作。 默认情况下，组 **[!UICONTROL Workflow execution]** 对标准定位工作流文件和工作流模板具有只读访问权限。 该组中的操作员也具有对待处理批准文件的读写权限。
* 该组 **[!UICONTROL Workflow supervisors]** 允许运营商管理工作流批准。
* 用于 **[!UICONTROL Operation Managers]** 访问营销活动工作流的组。

## 指定权限 {#named-rights}

只有名为right的WORKFLOW特定于工作流：它允许您创建、启动和停止工作流。 要使命名的权利适用，必须对工作流文件具有读取权限。 对于定位工作流，必须在文件上 **[!UICONTROL Profiles and Targets]** 正确读取。

## 工作流执行帐户 {#workflow-execution-account}

您可以配置要在工作流模板级别使用的执行帐户。 通过执行帐户，您可以直接将授权映射到工作流，而不管Adobe Campaign运营商是否开始执行。 默认情况下，每个工作流都由启动该工作流的操作员权限执行。

要将执行帐户映射到工作流，请转到工作流模板列表，然后右键单击链接到该工作流的模板。 选 **[!UICONTROL Action > Change execution account...]** 择要使用的帐户。
