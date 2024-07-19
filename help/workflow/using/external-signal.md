---
product: campaign
title: 外部信号
description: 了解有关外部信号工作流活动的更多信息
feature: Workflows
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 外部信号{#external-signal}



**外部信号**&#x200B;活动允许您在工作流中触发对计划的一组任务的执行。

激活“外部信号”任务后，该任务将无限期暂停或直到指定时间段结束。 其过渡由SOAP调用&#x200B;**PostEvent(sessionToken， workflowId， activity， transition， parameters， complete)激活。** **[!UICONTROL complete]**&#x200B;参数允许完成任务，因此不会对后续调用做出反应。

有关PostEvent函数的更多信息，请参阅有关SOAP调用的在线文档。

您可以配置此活动，以便在未收到信号时定义事件。 为此，请编辑该活动并单击&#x200B;**[!UICONTROL Expiration]**&#x200B;选项卡。 单击&#x200B;**[!UICONTROL Insert]**&#x200B;按钮创建和配置事件。

![](assets/edit_signal.png)

[有效期](defining-approvals.md)中详细介绍了有效期的配置。

**延迟**&#x200B;字段允许您以您选择的单位指定到期延迟。 请参阅[等待](wait.md)。

每行表示一种到期类型，并与过渡一致。

![](assets/external_sign_diag.png)
