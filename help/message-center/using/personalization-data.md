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
translation-type: tm+mt
source-git-commit: 95dff2f3704e316e9ec9e454a8f3fb9835508ccd
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 5%

---


# 个性化数据{#personalization-data}

可以使用消息模板中的数据来测试事务性消息个性化。 此功能用于生成预览或发送验证。 如果您安装了 **Deliverability** 模块，则此数据允许您显示各种互联网访问提供商的邮件呈现(收件箱&#x200B;**呈现**:有关此内容的详细信息，请参 [阅本部分](../../delivery/using/inbox-rendering.md))。

此数据的目的是在消息最终投放之前测试消息。 这些消息与消息中心要处理的实际数据不一致。 但是，XML结构必须与存储在事件中的执行实例结构相同，如下所示。

![](assets/messagecenter_create_custo_006.png)

此信息允许您使用个性化标记来个性化消息内容(有关详细信息，请参阅 [创建消息内容](../../message-center/using/creating-message-content.md))。

1. 在消息模板中，单击选 **[!UICONTROL Seed addresses]** 项卡。
1. 在事件内容中，以XML格式输入测试信息。

   ![](assets/messagecenter_create_custo_001.png)
