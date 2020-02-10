---
title: 外部信号
seo-title: 外部信号
description: 外部信号
seo-description: null
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 外部信号{#external-signal}

“外 **部信号** ”(External signal)活动允许您触发到某个计划的工作流中一组任务的执行。

当“外部信号”任务被激活时，它将无限期地暂停或直到指定时间段结束。 其过渡由SOAP调用PostEvent(sessionToken, workflowId, activity, transition, parameters, complete) **激活。** 该参 **[!UICONTROL complete]** 数允许任务完成，因此它不会对后续调用做出响应。

有关PostEvent函数的更多信息，请参阅有关SOAP调用的在线文档。

您可以配置此活动，以便在未收到信号时定义事件。 为此，请编辑活动，然后单击选 **[!UICONTROL Expiration]** 项卡。 单击该 **[!UICONTROL Insert]** 按钮可创建和配置活动。

![](assets/edit_signal.png)

过期的配置在过期中有详细 [介绍](../../workflow/using/executing-a-workflow.md#expirations)。

“延 **迟** ”(Delay)字段允许您以您选择的单位指定到期延迟。 请参 [阅等待](../../workflow/using/wait.md)。

每行表示过期类型，并与过渡一致。

![](assets/external_sign_diag.png)

