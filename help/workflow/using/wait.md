---
product: campaign
title: 等待
description: 了解有关等待工作流活动的更多信息
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 等待{#wait}



**等待**&#x200B;活动在几秒到几个月之间的任何时间延迟后激活其过渡。 等待任务不会阻止执行其他任务；当此任务处于挂起状态时，工作流可以并行执行任务。

您可以使用编辑器输入标签和等待时间，如以下示例所示：

![](assets/edit_wait.png)

在&#x200B;**[!UICONTROL Duration]**&#x200B;字段中，该值可以按您选择的单位表示：（根据操作员的区域设置）：

* 如果未指定区域设置：**s**&#x200B;代表秒数，**m**&#x200B;代表分钟数，**h**&#x200B;代表小时数，**d**&#x200B;代表天数，**y**&#x200B;代表年数。 审批时，该值将自动转换为最易读的单位。

  默认单位为天(**d**)。

* 例如，如果将区域设置设置为“Français”，则&#x200B;**s**&#x200B;表示秒，**mn**&#x200B;表示分钟，**h**&#x200B;表示小时，**j**&#x200B;表示天，**m**&#x200B;表示月，**a**&#x200B;表示年。 在批准时，该值将自动转换为最可读的单位，如上例中的&#x200B;**90s**&#x200B;转换为&#x200B;**1mn 30s**。

  默认单位为天(**d**)。
