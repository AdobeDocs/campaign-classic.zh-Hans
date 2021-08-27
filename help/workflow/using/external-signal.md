---
product: campaign
title: 外部信号
description: 了解有关外部信号工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 外部信号{#external-signal}

![](../../assets/common.svg)

通过&#x200B;**外部信号**&#x200B;活动，您可以触发对某个计划的工作流中一组任务的执行。

激活“外部信号”任务后，该任务将被无限期地暂停，或一直持续到指定时间段结束。 其过渡由SOAP调用&#x200B;**PostEvent(sessionToken， workflowId， activity， transition， parameters， complete)激活。** 参 **[!UICONTROL complete]** 数允许任务完成，因此不会对后续调用做出反应。

有关PostEvent函数的更多信息，请参阅有关SOAP调用的在线文档。

您可以配置此活动，以便在未收到信号时定义事件。 为此，请编辑活动，然后单击&#x200B;**[!UICONTROL Expiration]**&#x200B;选项卡。 单击&#x200B;**[!UICONTROL Insert]**&#x200B;按钮以创建和配置事件。

![](assets/edit_signal.png)

[过期日期](defining-approvals.md)中详细描述了过期日期的配置。

通过&#x200B;**Delay**&#x200B;字段，可以指定以所选单位表示的过期延迟。 请参阅[Wait](wait.md)。

每行表示过期类型，并与过渡一致。

![](assets/external_sign_diag.png)
