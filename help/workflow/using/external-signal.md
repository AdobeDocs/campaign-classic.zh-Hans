---
solution: Campaign Classic
product: campaign
title: 外部信号
description: 进一步了解外部信号工作流活动
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---


# 外部信号{#external-signal}

使用&#x200B;**外部信号**&#x200B;活动，可以触发在工作流中执行任务集到计划。

激活“外部信号”任务时，它将无限期地暂停或直到指定时间段结束。 其过渡由SOAP调用&#x200B;**PostEvent(sessionToken, workflowId,活动,过渡，参数，complete)激活。** 该 **[!UICONTROL complete]** 参数允许任务完成，因此不会对后续调用做出响应。

有关PostEvent函数的更多信息，请参阅有关SOAP调用的在线文档。

您可以配置此活动，以便在未收到信号时定义事件。 为此，请编辑活动并单击&#x200B;**[!UICONTROL Expiration]**&#x200B;选项卡。 单击&#x200B;**[!UICONTROL Insert]**&#x200B;按钮以创建和配置事件。

![](assets/edit_signal.png)

过期配置详见[过期](../../workflow/using/defining-approvals.md)。

使用&#x200B;**延迟**&#x200B;字段，可以以所选单位指定到期延迟。 请参阅[等待](../../workflow/using/wait.md)。

每行表示过期类型，并与过渡重合。

![](assets/external_sign_diag.png)

