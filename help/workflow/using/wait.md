---
product: campaign
title: 等待
description: 了解有关等待工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 等待{#wait}

**Wait**&#x200B;活动在几秒到几个月之间的时间延迟后激活其过渡。 等待任务不会阻止其他任务的执行；当此任务处于待处理状态时，工作流可以并行执行任务。

您可以使用编辑器输入标签和等待时间，如以下示例所示：

![](assets/edit_wait.png)

在&#x200B;**[!UICONTROL Duration]**&#x200B;字段中，该值可以以您选择的单位表示：（根据操作员的区域设置）：

* 如果未指定区域设置：**s**&#x200B;表示秒，**m**&#x200B;表示分钟，**h**&#x200B;表示小时，**d**&#x200B;表示天，**y**&#x200B;表示年。 在批准时，该值会自动转换为最易读的单位。

   默认单位为日(**d**)。

* 而例如，如果区域设置设置为“Français”，则：**s**&#x200B;表示秒，**mn**&#x200B;表示分钟，**h**&#x200B;表示小时，**j**&#x200B;表示天，**m**&#x200B;表示月，**a**&#x200B;表示年。 在批准时，该值会自动转换为最易读的单元，如上面的示例中的&#x200B;**90s**&#x200B;被转换为&#x200B;**1mn 30s**。

   默认单位为日(**d**)。
