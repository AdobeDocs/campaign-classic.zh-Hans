---
solution: Campaign Classic
product: campaign
title: 个性化数据
description: 个性化数据
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# 个性化数据{#personalization-data}

可以使用消息模板中的数据来测试事务性消息个性化。 此功能用于生成预览或发送验证。 如果安装&#x200B;**Deliverability**&#x200B;模块，则此数据允许您显示各种互联网访问提供商的消息呈现（**收件箱呈现**）：有关详细信息，请参阅[本节](../../delivery/using/inbox-rendering.md))。

此数据的目的是在消息最终投放之前测试消息。 这些消息与消息中心要处理的实际数据不符。 但是，XML结构必须与存储在执行实例中的事件结构相同，如下所示。

![](assets/messagecenter_create_custo_006.png)

此信息使您能够使用个性化标记来个性化消息内容（有关详细信息，请参阅[创建消息内容](../../message-center/using/creating-message-content.md)）。

1. 在消息模板中，单击&#x200B;**[!UICONTROL Seed addresses]**&#x200B;选项卡。
1. 在事件内容中，输入XML格式的测试信息。

   ![](assets/messagecenter_create_custo_001.png)
