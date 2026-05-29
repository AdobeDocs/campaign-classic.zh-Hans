---
product: campaign
title: 投放控制
description: 了解有关投放控制工作流活动的更多信息
feature: Workflows
hide: true
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
TQID: https://experienceleague.adobe.com/WVXqtjcGQQOQJfVi58BqtLPqgG7AkgslAzQk4Vjbl9k
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 164
ht-degree: 5%

---

# 投放控制{#delivery-control}



**投放控制**&#x200B;类型的操作允许您启动、暂停或停止投放。

这可以是过渡中指定的投放、显式选择的投放或由脚本计算的投放。 有关详情，请参阅[投放](delivery.md)。

![](assets/edit_diffusion_act.png)

如果选择&#x200B;**[!UICONTROL Start]**，活动将执行启动投放所需的所有步骤（目标计算、内容准备、投放）。 如果上一工作流活动已经执行了其中的某些步骤，则将不再执行它们。 例如，如果目标估计已由&#x200B;**[!UICONTROL Delivery]**&#x200B;类型活动（请参阅[投放](delivery.md)）执行，**[!UICONTROL Act on the delivery]**&#x200B;活动将启动剩余步骤（内容准备和投放）。

可以使用以下选项：

* **[!UICONTROL Generate an outbound transition]**

  创建将在执行结束时激活的叫客过渡。 您可以选择是否检索出站投放的目标。

* **[!UICONTROL Processing errors]**

  请参阅[处理错误](monitoring-workflow-execution.md#processing-errors)。

## 输入参数 {#input-parameters}

* deliveryId

投放标识符（如果所选操作为&#x200B;**[!UICONTROL Specified in the transition]**）。
