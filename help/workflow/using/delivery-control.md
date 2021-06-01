---
product: campaign
title: 投放控制
description: 了解有关投放控制工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 5%

---

# 投放控制{#delivery-control}

**投放控件**&#x200B;类型操作允许您开始、暂停或停止投放。

这可以是过渡中指定的投放、明确选择的投放或由脚本计算的投放。 有关更多信息，请参见[Delivery](../../workflow/using/delivery.md)。

![](assets/edit_diffusion_act.png)

如果选择&#x200B;**[!UICONTROL Start]**，则活动将执行开始投放（目标计算、内容准备、投放）所需的所有步骤。 如果之前的工作流活动已经执行了其中某些步骤，则不会再执行这些步骤。 例如，如果目标估计已由&#x200B;**[!UICONTROL Delivery]**&#x200B;类型活动执行（请参阅[投放](../../workflow/using/delivery.md)），则&#x200B;**[!UICONTROL Act on the delivery]**&#x200B;活动将启动其余步骤（内容准备和投放）。

可以使用以下选项：

* **[!UICONTROL Generate an outbound transition]**

   创建将在执行结束时激活的叫客过渡。 您可以选择是否检索叫客投放的目标。

* **[!UICONTROL Processing errors]**

   请参阅[处理错误](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## 输入参数{#input-parameters}

* deliveryId

投放标识符（如果选定的操作为&#x200B;**[!UICONTROL Specified in the transition]**）。
