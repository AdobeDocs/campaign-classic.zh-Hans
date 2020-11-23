---
solution: Campaign Classic
product: campaign
title: 协调数据更新
description: 协调数据更新
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---


# 协调数据更新{#coordinating-data-updates}

此用例详细介绍了工作流的创建，该工作流允许您在使用工作流的多个执行时管理伴随更新。

目的是在执行另一个更新操作之前检查更新过程是否已结束。 为此，我们将设置一个实例变量，并让工作流测试该实例是否正在运行，以决定是否继续执行工作流并执行更新。

![](assets/uc_dataupdate_wkf.png)

此工作流由以下部分组成：

* 调度程序 **活动** ，它在特定频率上执行工作流。
* 一个 **测试活动** ，它检查工作流是否已执行。
* **查询** 和 **更新数据活动** （如果工作流尚未执行），后跟一个结束 **** 活动，将工作流实例变量重新初始化为false。
* 结束 **活动** （如果工作流已执行）。

要构建工作流，请按照以下步骤操作：

1. 添加 **调度程序** 活动，然后根据您的需求配置其频率。
1. 添加测 **试活动** ，检查工作流是否已执行，然后按如下方式配置它。

   >[!NOTE]
   >
   >“isRunning”是我们为此示例选择的实例变量名称。 这不是内置变量。

   ![](assets/uc_dataupdate_test.png)

1. 向“ **No** ”叉添加 **“End** ”活动。 这样，如果工作流已执行，则不执行任何操作。
1. 将所需活动添加 **到** Yes分叉。 在我们的例子中， **查询****和更新数据** 活动。
1. 打开第一个活动，然 **后在选项卡中添加** instance.vars.isRunning = **[!UICONTROL Advanced]** true命令。 这样，实例变量就设置为正在运行。

   ![](assets/uc_dataupdate_query.png)

1. 在分 **叉的末尾添** 加一个End **[!UICONTROL Yes]** 活动，然后在选 **项卡中添加instance.vars.isRunning =****[!UICONTROL Advanced]** false命令。

   这样，只要工作流正在执行，就不会执行任何操作。

   ![](assets/uc_dataupdate_end.png)

**相关主题：**

* [防止同时执行多个执行](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [更新数据活动](../../workflow/using/update-data.md)

