---
title: 投放执行
seo-title: 投放执行
description: 投放执行
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 631e29bd6e59b8ae46084dee3a1d470916a2032b

---


# 投放执行{#delivery-execution}

>[!NOTE]
>
>MTA优先处理事务性消息，而不是处理任何其他投放。

在执行实例上，一旦扩充阶段完成并且投放模板已链接到事件，就发送投放。 所有投放都在文件夹中进 **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** 行分组。

![](assets/messagecenter_deliveries_execinstances_001.png)

默认情况下，它们按投放月分类到子文件夹中。

可以在消息模板属性中更改此排序，如下所示。

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>对于托管或混合安装，如果您已升级到增强的MTA，则所有事务性消息也可以与Adobe Campaign增强的MTA一起发送，以改进交付性、吞吐量和弹回处理。 所有影响与标准营销消息相同，并在Adobe Campaign增强的MTA [文档中详细介绍](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html) 。