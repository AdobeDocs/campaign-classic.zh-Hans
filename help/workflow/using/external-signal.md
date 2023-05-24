---
product: campaign
title: 外部信号
description: 了解有关外部信号工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 外部信号{#external-signal}



此 **外部信号** 活动允许您在工作流中向计划触发一组任务的执行。

激活“外部信号”任务时，该任务会无限期暂停或一直暂停到指定的时间段结束。 其过渡由SOAP调用激活 **PostEvent(sessionToken， workflowId， activity， transition， parameters， complete)。** 此 **[!UICONTROL complete]** 参数允许任务完成，因此不会对后续调用做出反应。

有关PostEvent函数的更多信息，请参阅有关SOAP调用的联机文档。

您可以配置此活动，以便在未收到信号时定义事件。 要执行此操作，请编辑活动并单击 **[!UICONTROL Expiration]** 选项卡。 单击 **[!UICONTROL Insert]** 按钮创建和配置事件。

![](assets/edit_signal.png)

有关过期配置的详情，请参见 [过期时间](defining-approvals.md).

此 **延迟** 字段可让您以所选择的单位指定过期延迟。 参见 [等待](wait.md).

每行表示一种到期类型，并与过渡重合。

![](assets/external_sign_diag.png)
