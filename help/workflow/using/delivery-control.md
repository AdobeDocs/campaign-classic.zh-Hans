---
title: 投放控制
seo-title: 投放控制
description: 投放控制
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 8%

---


# 投放控制{#delivery-control}

投放 **控件**-类型操作允许您开始、暂停或停止投放。

这可以是过渡中指定的投放、显式选择的投放或由脚本计算的投放。 For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

如果您选 **[!UICONTROL Start]**&#x200B;择，活动将执行开始投放所需的所有步骤(目标计算、内容准备、投放)。 如果这些步骤中的某些步骤已经由以前的工作流活动执行，则不会再执行这些步骤。 例如，如果目标估计已由类型活动 **[!UICONTROL Delivery]** 执行(请参 [阅投放](../../workflow/using/delivery.md))，则 **[!UICONTROL Act on the delivery]** 活动将启动其余步骤(内容准备和投放)。

可以使用以下选项：

* **[!UICONTROL Generate an outbound transition]**

   创建将在执行结束时激活的出站过渡。 您可以选择是否检索出站目标的投放。

* **[!UICONTROL Processing errors]**

   请参阅处 [理错误](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## 输入参数 {#input-parameters}

* deliveryId

投放标识符(如果所选操作为 **[!UICONTROL Specified in the transition]**)。
