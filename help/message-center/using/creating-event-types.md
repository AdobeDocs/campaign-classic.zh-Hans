---
title: 创建事件类型
seo-title: 创建事件类型
description: 创建事件类型
seo-description: null
page-status-flag: never-activated
uuid: 70c8325e-a6ef-4e47-85f9-a9fa04c2ef30
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 5c0a428f-a3e7-4848-8c47-b72832ba97c2
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 13%

---


# 创建事件类型{#creating-event-types}

事件类型必须在控制实例中创建目标为Adobe Campaign处理的。 这可以通过树的 **[!UICONTROL Administration > Platform > Enumerations]** 文件夹完成。 每个事件类型与明细列表中的值匹 **[!UICONTROL eventType]** 配。 这可以是订单确认、密码或订单投放更改等。

![](assets/messagecenter_eventtype_enum_001.png)

有关详细列表的详细信息，请参阅 [明细列表管理](../../platform/using/managing-enumerations.md)。

创建明细列表值后，注销并重新登录实例，以便创建生效。
