---
product: campaign
title: 投放控制
description: 了解有关投放控制工作流活动的更多信息
feature: Workflows
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 5%

---

# 投放控制{#delivery-control}



A **投放控制**-type操作允许您启动、暂停或停止投放。

这可以是过渡中指定的投放、显式选择的投放或由脚本计算的投放。 有关详细信息，请参见 [投放](delivery.md).

![](assets/edit_diffusion_act.png)

如果您选择 **[!UICONTROL Start]**，则该活动将执行开始投放所需的所有步骤（目标计算、内容准备、投放）。 如果上一工作流活动已经执行了其中的某些步骤，则将不再执行它们。 例如，如果目标估计已经由 **[!UICONTROL Delivery]** 类型活动(请参阅 [投放](delivery.md))，则 **[!UICONTROL Act on the delivery]** 活动将启动剩余步骤（内容准备和交付）。

可以使用以下选项：

* **[!UICONTROL Generate an outbound transition]**

  创建将在执行结束时激活的叫客过渡。 您可以选择是否检索出站投放的目标。

* **[!UICONTROL Processing errors]**

  请参阅 [正在处理错误](monitoring-workflow-execution.md#processing-errors).

## 输入参数 {#input-parameters}

* deliveryId

投放标识符，如果所选操作为 **[!UICONTROL Specified in the transition]**.
