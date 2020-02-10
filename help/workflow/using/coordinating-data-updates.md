---
title: 协调数据更新
seo-title: 协调数据更新
description: 协调数据更新
seo-description: null
page-status-flag: never-activated
uuid: 003d63f8-3169-4190-882e-e360a83ccafb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: efe09c66-b74b-48f0-9042-5da4342e014e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 协调数据更新{#coordinating-data-updates}

此用例详细介绍了工作流的创建，该工作流允许您在使用工作流的多个执行时管理伴随更新。

其目的是在执行另一个更新操作之前检查更新过程是否已结束。 为此，我们将设置一个实例变量，并让工作流测试该实例是否正在运行以决定是否继续执行工作流并执行更新。

![](assets/uc_dataupdate_wkf.png)

此工作流由以下几部分组成：

* 调 **度程序** ，它在特定频率上执行工作流。
* 检查 **** 工作流是否已执行的测试活动。
* **查询****和更新数据活动** （如果工作流尚未执行），然后是将工作流实例变量重新初始化为false的 **End** 活动。
* 如果 **工作流已在执行** ，则为“结束”活动。

要构建工作流，请按照以下步骤操作：

1. 添加“ **调度程序** ”活动，然后根据您的需要配置其频率。
1. 添加测 **试活动** ，检查工作流是否已执行，然后如下配置。

   >[!NOTE]
   >
   >“isRunning”是我们为此示例选择的实例变量名称。 这不是内置变量。

   ![](assets/uc_dataupdate_test.png)

1. 将“结 **束** ”活动添 **加到** No分叉。 这样，如果工作流已经执行，则不会执行任何操作。
1. 将所需的活动添加到 **Yes** 分叉。 在我们的例子中， **查询****和更新数据** 。
1. 打开第一个活动，然后在选 **项卡中添加instance.vars.isRunning = true** 命 **[!UICONTROL Advanced]** 令。 这样，实例变量就设置为正在运行。

   ![](assets/uc_dataupdate_query.png)

1. 在 **fork的结尾添加** End活动，然后在 **[!UICONTROL Yes]** 选项卡中添加 **instance.vars.isRunning = false** 命 **[!UICONTROL Advanced]** 令。

   这样，只要工作流正在执行，就不会执行任何操作。

   ![](assets/uc_dataupdate_end.png)

**相关主题：**

* [防止同时执行多个执行](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [更新数据活动](../../workflow/using/update-data.md)

