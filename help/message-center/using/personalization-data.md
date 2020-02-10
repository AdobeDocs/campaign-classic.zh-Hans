---
title: 个性化数据
seo-title: 个性化数据
description: 个性化数据
seo-description: null
page-status-flag: never-activated
uuid: d3d66216-502a-410b-b062-fb413eb9363f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 2cd8a320-37e8-410a-b71b-0c13c8e15482
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 个性化数据{#personalization-data}

可以使用消息模板中的数据来测试事务消息个性化。 此功能用于生成预览或发送校样。 如果您安装了 **Deliverability** 模块，则此数据允许您为各种Internet访问提供商显示消息的渲染(收件箱&#x200B;**渲染**:有关此内容的详细信息，请参 [阅本节](../../delivery/using/about-deliverability.md))。

此数据的目的是在消息最终交付之前测试消息。 这些消息与消息中心要处理的实际数据不一致。 但是，XML结构必须与存储在执行实例中的事件结构相同，如下所示。

![](assets/messagecenter_create_custo_006.png)

此信息允许您使用个性化标记来个性化消息内容(有关详细信息，请参阅创 [建消息内容](../../message-center/using/creating-message-content.md))。

1. 在消息模板中，单击选 **[!UICONTROL Seed addresses]** 项卡。
1. 在活动内容中，输入XML格式的测试信息。

   ![](assets/messagecenter_create_custo_001.png)

