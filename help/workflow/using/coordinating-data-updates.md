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

此用例详细描述了工作流的创建过程，该工作流允许您在使用工作流的多个执行时管理伴随更新。

其目的是在执行另一个更新操作之前检查更新过程是否已结束。 为此，我们将设置一个实例变量，并让工作流测试该实例是否正在运行，以决定是否继续执行工作流并执行更新。

![](assets/uc_dataupdate_wkf.png)

此工作流由以下部分组成：

* **调度程序**&#x200B;活动，在特定频率上执行工作流。
* **测试**&#x200B;活动，用于检查工作流是否已执行。
* **在工** 作 **流** 尚未执行时进行查询并更新数据活动，然后再执行一个Endactivity， **** 将工作流实例变量重新初始化为false。
* 如果工作流已在执行，则显示&#x200B;**结束**&#x200B;活动。

要构建工作流，请按照以下步骤操作：

1. 添加&#x200B;**调度程序**&#x200B;活动，然后根据需要配置其频率。
1. 添加&#x200B;**Test**&#x200B;活动以检查工作流是否已执行，然后按如下配置。

   >[!NOTE]
   >
   >“isRunning”是我们为此示例选择的实例变量名称。 这不是内置变量。

   ![](assets/uc_dataupdate_test.png)

1. 将&#x200B;**End**&#x200B;活动添加到&#x200B;**No**&#x200B;分叉。 这样，如果工作流已在执行，则不会执行任何操作。
1. 将所需活动添加到&#x200B;**Yes**&#x200B;叉。 在我们的案例中，**查询**&#x200B;和&#x200B;**更新数据**&#x200B;活动。
1. 打开第一个活动，然后在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中添加&#x200B;**instance.vars.isRunning = true**&#x200B;命令。 这样，实例变量就设置为正在运行。

   ![](assets/uc_dataupdate_query.png)

1. 在&#x200B;**[!UICONTROL Yes]**&#x200B;分叉的末尾添加&#x200B;**End**&#x200B;活动，然后在&#x200B;**[!UICONTROL Advanced]**&#x200B;选项卡中添加&#x200B;**instance.vars.isRunning = false**&#x200B;命令。

   这样，只要工作流正在执行，就不会执行任何操作。

   ![](assets/uc_dataupdate_end.png)

**相关主题：**

* [防止同时执行多个](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [更新数据活动](../../workflow/using/update-data.md)

