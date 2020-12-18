---
solution: Campaign Classic
product: campaign
title: 等待
description: 进一步了解等待工作流活动
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---


# 等待{#wait}

**等待**&#x200B;活动在几秒到几个月的时间延迟后激活其过渡。 等待任务不会阻止执行其他任务;当此任务处于挂起状态时，工作流可以并行执行任务。

您可以使用编辑器输入标签和等待时间，如下例所示：

![](assets/edit_wait.png)

在&#x200B;**[!UICONTROL Duration]**&#x200B;字段中，值可以以您选择的单位表示：（根据运营商的区域设置）:

* 如果未指定区域设置：**s**&#x200B;秒，**m**&#x200B;分钟，**h**&#x200B;小时，**d**&#x200B;天，**y**&#x200B;年。 在批准时，值会自动转换为最可读的单元。

   默认单位为日(**d**)。

* 但是，例如，如果区域设置设置为“Français”:**s**&#x200B;秒，**mn**&#x200B;分钟，**h**&#x200B;小时，**j**&#x200B;天，**m**&#x200B;月，**a**&#x200B;年。 在批准时，该值被自动转换为最可读单元，如上例中的&#x200B;**90s**&#x200B;被转换为&#x200B;**1mn 30s**。

   默认单位为日(**d**)。

