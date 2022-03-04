---
product: campaign
title: 协调数据更新
description: 协调数据更新
feature: Workflows, Data Management
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# 协调数据更新{#coordinating-data-updates}

![](../../assets/common.svg)

此用例详细介绍了如何创建工作流，利用该工作流，您可以在使用工作流的多次执行时管理伴随的更新。

目的是在执行另一更新操作之前检查更新过程是否已结束。 为此，我们将设置一个实例变量，并让工作流测试实例是否正在运行，以确定是否继续执行工作流并执行更新。

![](assets/uc_dataupdate_wkf.png)

此工作流由以下部分组成：

* a **调度程序** 活动，可在特定频率上执行工作流。
* a **测试** 活动，用于检查工作流是否已执行。
* **查询** 和 **更新数据** 活动（如果工作流尚未执行），然后是 **结束** 活动，将工作流实例变量重新初始化为false。
* 安 **结束** 活动。

要构建工作流，请执行以下步骤：

1. 添加 **调度程序** 活动，然后根据需要配置其频度。
1. 添加 **测试** 活动以检查工作流是否已在执行，然后按照以下方式对其进行配置。

   >[!NOTE]
   >
   >“isRunning”是我们为此示例选择的实例变量名称。 这不是内置变量。

   ![](assets/uc_dataupdate_test.png)

1. 添加 **结束** 活动 **否** 分叉。 这样，如果工作流已在执行，则不会执行任何操作。
1. 将所需的活动添加到 **是** 分叉。 以我们为例， **查询** 和 **更新数据** 活动。
1. 打开第一个活动，然后添加 **instance.vars.isRunning = true** 命令 **[!UICONTROL Advanced]** 选项卡。 这样，实例变量将设置为正在运行。

   ![](assets/uc_dataupdate_query.png)

1. 添加 **结束** 的 **[!UICONTROL Yes]** 分叉，然后添加 **instance.vars.isRunning = false** 命令 **[!UICONTROL Advanced]** 选项卡。

   这样，只要执行工作流，就不会执行任何操作。

   ![](assets/uc_dataupdate_end.png)

**相关主题：**

* [防止同时执行多次](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [更新数据活动](update-data.md)
