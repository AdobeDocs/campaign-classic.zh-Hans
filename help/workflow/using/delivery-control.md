---
title: 交付控制
seo-title: 交付控制
description: 交付控制
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 交付控制{#delivery-control}

“交 **付控件类型**”(Delivery control-type)操作允许您开始、暂停或停止交付。

这可以是在过渡中指定的交付、明确选择的交付或由脚本计算的交付。 For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

如果您选 **[!UICONTROL Start]**&#x200B;择，则活动将执行开始交付所需的所有步骤（目标计算、内容准备、交付）。 如果这些步骤中的某些步骤已经由以前的工作流活动执行，则不会再执行这些步骤。 例如，如果目标估计已由类型活动执行(请参 **[!UICONTROL Delivery]** 阅“交付” [)，则活动将启](../../workflow/using/delivery.md)**[!UICONTROL Act on the delivery]** 动其余步骤（内容准备和交付）。

可以使用以下选项：

* **[!UICONTROL Generate an outbound transition]**

   创建将在执行结束时激活的出站过渡。 您可以选择是否检索出站分发的目标。

* **[!UICONTROL Processing errors]**

   请参阅处 [理错误](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## 输入参数 {#input-parameters}

* deliveryId

交付标识符（如果选定的操作为） **[!UICONTROL Specified in the transition]**。
