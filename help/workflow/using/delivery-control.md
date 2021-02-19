---
solution: Campaign Classic
product: campaign
title: 投放控制
description: 进一步了解投放控制工作流活动
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 5%

---


# 投放控制{#delivery-control}

通过&#x200B;**投放控件**&#x200B;类型操作，可以开始、暂停或停止投放。

这可以是在过渡中指定的投放、显式选择的投放或由脚本计算的投放。 有关详细信息，请参阅[投放](../../workflow/using/delivery.md)。

![](assets/edit_diffusion_act.png)

如果选择&#x200B;**[!UICONTROL Start]**,活动将执行开始投放(目标计算、内容准备、投放)所需的所有步骤。 如果这些步骤中的某些步骤已经由以前的工作流活动执行，则不会再次执行这些步骤。 例如，如果目标估计已由&#x200B;**[!UICONTROL Delivery]**&#x200B;类型活动执行(请参阅[投放](../../workflow/using/delivery.md))，则&#x200B;**[!UICONTROL Act on the delivery]**&#x200B;活动将启动其余步骤(内容准备和投放)。

可以使用以下选项：

* **[!UICONTROL Generate an outbound transition]**

   创建将在执行结束时激活的出站过渡。 您可以选择是否检索出站投放的目标。

* **[!UICONTROL Processing errors]**

   请参阅[处理错误](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## 输入参数{#input-parameters}

* deliveryId

投放标识符，如果所选操作为&#x200B;**[!UICONTROL Specified in the transition]**。
