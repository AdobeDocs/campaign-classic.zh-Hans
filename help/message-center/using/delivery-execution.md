---
title: 交付执行
seo-title: 交付执行
description: 交付执行
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
source-git-commit: bc227c2da2e8b1a78714748809ad40bbcefe0458

---


# 交付执行{#delivery-execution}

>[!NOTE]
>
>MTA优先处理事务性消息，而不是任何其他传送。

在执行实例上，一旦富集阶段完成并且传送模板已链接到该事件，则发送传送。 所有分发都在文件夹中进 **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** 行分组。

![](assets/messagecenter_deliveries_execinstances_001.png)

默认情况下，这些文件夹按交货月份排序。

可以在消息模板属性中更改此排序，如下所示。

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>对于托管或混合安装，如果您已升级到增强MTA，则所有交易消息也可以与Adobe Campaign增强MTA一起发送，以改进交付性、吞吐量和弹回处理。 所有影响与标准营销消息相同，并在 [Adobe Campaign增强的MTA文档中详细介绍](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) 。