---
product: campaign
title: 外部信号
description: 了解有关外部信号工作流活动的更多信息
feature: Workflows
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 外部信号{#external-signal}

![](../../assets/v7-only.svg)

的 **外部信号** 活动允许您在工作流中触发对计划的一组任务的执行。

激活“外部信号”任务后，该任务将被无限期地暂停，或一直持续到指定时间段结束。 其过渡由SOAP调用激活 **PostEvent(sessionToken， workflowId， activity， transition， parameters， complete)。** 的 **[!UICONTROL complete]** 参数允许任务完成，因此不会对后续调用做出反应。

有关PostEvent函数的更多信息，请参阅有关SOAP调用的在线文档。

您可以配置此活动，以便在未收到信号时定义事件。 为此，请编辑活动，然后单击 **[!UICONTROL Expiration]** 选项卡。 单击 **[!UICONTROL Insert]** 按钮以创建和配置事件。

![](assets/edit_signal.png)

过期日期的配置详见 [过期](defining-approvals.md).

的 **延迟** 字段，可以使用所选的单位指定过期延迟。 请参阅 [等待](wait.md).

每行表示过期类型，并与过渡一致。

![](assets/external_sign_diag.png)
