---
product: campaign
title: 外部信号
description: 了解有关外部信号工作流活动的更多信息
feature: Workflows
hide: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
TQID: https://experienceleague.adobe.com/2fWd7-VtAc2x-MQm-o5rpGmDsrn6rszSfZxjVDzleTw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 168
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
